---
layout: post
categories: blog
tags: ArchLinux アップグレード
title: Arch Linux をインストール
date: 2012-10-27T23:00:00+09:00
---


サブのノートPCのUbuntuをアップグレード...ではなくて、 Arch Linux をインストールしてみた。

Ubuntuは前々からパッケージ古いのが気になってたし、あとそろそろクリーンインストールしたいけど、うちの低スペックだと最近のインストーラーが動かない。

で、Archは最近なんか人気あるようだし興味を持った。パッケージ更新が早いのと、ローリングリリースってのがよさそう。Wikiも充実してて私でもなんとか使えそうだったってことで入れ替えることにした。

<!-- more -->

インストールは[ここ][cite-kenkovlog]が参考になった。書かれている手順をそのまま実行しただけ。ありがたい。


# イメージの作成と起動

まずは [Arch Linux] のページからisoをダウンロードしてCDを作成。CDからブートしてインストーラーを起動する。起動したらホームに *install.txt* ってのがあるので目を通しておくと良いかも。


# キーボードレイアウトの設定

デフォルトのキーボード設定だと使いづらいので、最初に設定しておく。

```
loadkeys jp106
```


# パーティションの設定

インストールするハードディスクのパーティションを設定する。私は以下のようなパーティションにした。

+ /boot: 100MB
+ swap: 1024MB
+ /: 残り


容量少ないし個人設定はメインPCから引っ張ってこれるので、 /home は作らなかった。通常つかうなら分けとくといいかも。

`cfdisk` コマンドで、インストールするハードディスクのパーティションを設定する。

```
cfdisk /dev/sda
```


メニューが表示されるのでわりとわかりやすい。矢印キー上下でパーティションを選んで、左右で実行動作を選択する感じ。

既存のパーティションを *[Delete]* で削除したら、 Free Space に順番に作成していく。

+ /boot を sda1 に。
  *[New]* -> *[Primary]* -> *Size (in MB): 100* -> *[Beginning]* と選んで、 *[Bootable]* でFlagsをBootにしといた。

+ swap を sda5 に。
  *[New]* -> *[Logical]* -> *Size (in MB): 1024* -> *[Beginning]* と選んで、 *[Type]* -> *Enter filesystem type: 82* で *Linux swap / Solaris* に指定。

+ / を sda6 に。
  *[New]* -> *[Logical]* -> *Size (in MB): 30295.84* そのまま -> *[Beginning]* と指定。

パーティション分けが完了したら、 *[Write]* して *[Quit]* する。


# フォーマット

パーティション分けができたら、 `mkfs` コマンドでパーティションをフォーマットする。

```
mkfs.ext4 /dev/sda1
mkfs.btrfs /dev/sda6
```


ここで両方btrfsにしようとしてちょっとハマった。btrfsは/bootと分割して別に作成できないらしい？ややこしそうなので/bootはext4にしといた。

swapは後で設定する。


# マウント

フォーマットしたパーティションをマウントする。

/ を /mnt にマウントする。

```
mount /dev/sda6 /mnt
```


/boot を /mnt/boot にマウントする。

```
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
```


# ベースシステムのインストール

いよいよベースシステムのインストール。ネットからインストールするのでインターネットに接続できるようにしておく。私はあらかじめLANケーブルを繋いでおいたので、以下コマンドを実行するだけで大丈夫だった。

```
dhcpcd eth0
```


マウントしたパーティションにインストール開始。

```
pacstrap /mnt base base-devel
```


grubをインストール。

```
pacstrap /mnt grub-bios
```


fstabに書き込む。

```
genfstab -p /mnt >> /mnt/etc/fstab
```


# システムをマウント

ここがちょっとよくわからんかったが /mnt にchroot。インストールしたシステムに入るってことかな？以下のコマンドを実行する。

```
arch-chroot /mnt
```


するとプロンプトが *root@archiso* から *sh-4.2#* に変わった。

hostname を設定。ファイルに名前を書くだけ。

```
vi /etc/hostname
```


localtime 設定。

```
ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
```


locale 設定。 */etc/local.conf* の使う部分のコメントを解除。

{% gist matea2/29455b22b8b84133531b948f898f3cc7 local.conf %}


`local-gen` を実行して更新。

```
locale-gen
```


起動イメージを作成。 *file not found: fsck.btrfs* とエラーが出るけど、 *Image generation successful* だからきっと大丈夫だろう。

```
mkinitcpio -p linux
```


grubをMBRにインストール。

```
grub-install /dev/sda
```


grubの設定を作成。

```
grub-mkconfig -o /boot/grub/grub.cfg
```


rootパスワードを設定。

```
passwd
```


/mnt から抜ける。

```
exit
```


# 再起動

マウントしたパーティションをアンマウント。

```
umount /mnt/boot
umount /mnt
```


ここまできたら再起動！これでハードディスクから起動できるはず！

```
reboot
```


# swap設定

あとはrootでログインしてから、swapを設定。

```
mkswap /dev/sda5
swapon /dev/sda5
```


*/etc/fstab* にswapを追記する。

{% gist matea2/29455b22b8b84133531b948f898f3cc7 fstab %}


とりあえずここでインストール編は終了。


# 使用環境

+ TOSHIBA Dynabook SS SX/210LE
+ Arch Linux (archlinux-2012.10.06-dual.iso)


# 参考サイト

+ [Arch Linux]
+ [Installation Guide - ArchWiki][cite-arch-wiki]
+ [2012.07.15 Arch Linux インストール --- kenkovlog][cite-kenkovlog]



[Arch Linux]: https://www.archlinux.org/

[cite-arch-wiki]: https://wiki.archlinux.org/index.php/Installation_Guide
[cite-kenkovlog]: http://kenkov.jp/blog/2012/07/24/install_archlinux.html
