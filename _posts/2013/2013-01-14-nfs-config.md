---
layout: post
categories: blog
tags: ArchLinux Fedora iptables nfs
title: NFS設定
date: 2013-01-14T18:18:00+09:00
---


NFSでネットワーク越しにハードディスクをマウントしてみたメモ。

Fedora (サーバー) の */dir/path* を、Arch Linux (クライアント) の */mount/path* にマウントする感じ。

<!-- more -->

# サーバー側の設定

サーバー側のPC、Fedoraでの設定。まずはNFSをインストール。

```
[fedora]$ sudo yum install nfs-utils
```


*/etc/exports* を編集してマウントする場所と範囲を設定する。括弧内でオプションを指定する。

{% gist matea2/8f4776617eb9dada75cf7981cb74a656 exports %}


サービスを起動する。RPCってのを使うらしい。

```
[fedora]$ sudo systemctl start rpcbind.service
[fedora]$ sudo systemctl enable nfs-server.service
[fedora]$ sudo systemctl start nfs-server.service
```


# クライアント側の設定

で次はクライアント側、Arch LinuxなPCを設定。といっても特にすることはないけど、マウントするときにNFSがないといかんので、インストールする。

```
[arch]$ sudo pacman -S nfs-utils
```


# マウント & ファイアウォール設定

ためしにクライアントでマウントしてみる。

```
[arch]$ sudo mount -t nfs fedora:/dir/path /mount/path
```


がエラー。とりあえずサーバー側のiptablesをオフったら動いた。ファイアウォールでブロックされるらしい。

```
[fedora]$ sudo systemctl stop iptables.service
```


ということでファイアウォールを通す設定。デフォルトだとポートが定まってないらしいので、 */etc/sysconfig/nfs* を編集してポートを固定する。コメントでかかれた2つのポート設定をコメント解除。

{% gist matea2/8f4776617eb9dada75cf7981cb74a656 nfs %}


*/etc/sysconfig/iptables* を編集して、 rpc, nfs, mountd と上のポートを許可。

{% gist matea2/8f4776617eb9dada75cf7981cb74a656 iptables %}


止めてた iptables を起動。

```
[fedora]$ sudo systemctl start iptables.service
```


で、もういちどクライアントからマウント。無事マウントできるはず。

```
[arch]$ sudo mount -t nfs fedora:/dir/path /mount/path
```


最初 iptables うまく通らんなあと思ったら REJECT の下に書いてた...。以下コマンドでチェックするっぽいけど too weak とか言われるネットワーク！

```
[arch]$ sudo showmount -e fedora
[arch]$ sudo rpcinfo -p fedora
```


# 使用環境

+ Fedora 17 (3.6.11-1.fc17.x86\_64)
+ nfs-utils 1.2.6
+ iptables 1.4.14

+ Arch Linux (3.6.11-1-ARCH)
+ nfs-utils 1.2.6-3


# 参考サイト

+   [Fedora/nfsの設定 - Welcome to Life with Linux][cite-life-with-linux]
+   [brief tech notes: nfs configuration on fedora 16][cite-brief-tech-notes]
+   [nfs設定 - とみぞーノート][cite-tomizoo]



[cite-life-with-linux]: http://hy.xrea.jp/linux/index.php?Fedora%2Fnfs%E3%81%AE%E8%A8%AD%E5%AE%9A
[cite-brief-tech-notes]: http://yizhangid.blogspot.jp/2012/07/nfs-configuration-on-fedora-16.html
[cite-tomizoo]: http://wiki.bit-hive.com/tomizoo/pg/nfs%C0%DF%C4%EA
