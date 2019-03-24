---
layout: post
categories: blog
tags: Ubuntu modprobe udev 無線LAN
title: Ubuntu 11.10 無線LAN設定
date: 2011-10-15T20:38:00+09:00
---


うちのUbuntuは、ノートPCにUSBの無線デバイス PLANEX GW-USMicroN-G を差し込んで使っている。 11.04 (Natty Narwhal) のときは差すだけで使えていたんだが、 11.10 (Oneiric Ocelot) にアップグレードしたら動かなくなってしまった。で、いくらか調べて設定してみたら動くようになった。

<!-- more -->


# コマンドで実行

まずUSBの状態を確認。

```
lsusb
```


> Bus 001 Device 003: ID 2019:ed14 PLANEX GW-USMicroN

と、デバイスは認識しているようだ。じゃあモジュールの確認。

```
lsmod
```


GW-USMicroN-G のモジュールは rt2800usb だったと思うが見当たらない。なので動かしてみる。

```
modprobe rt2800usb
```


まだ動かないようなので、調べたサイトを参考に以下をやってみる。 `lsusb` で出てきたベンダーIDとプロダクトIDを書き込む。

```
sudo -s
echo 2019 ed14 > /sys/bus/usb/drivers/rt2800usb/new_id
exit
```


これで動くようになった。しかし再起動すると元に戻ってしまうので、起動時に設定を
読み込むようにする。


# 起動時の設定

udev にUSBのルールを追加する。ファイル名はてきとうに */etc/udev/rules.d/99-wireless.rules* にしといた。

{% gist matea2/09494c87479a1ccaefdf3cf7cf791480 99-wireless.rules %}


それから、modprobeの設定を追加。こっちもてきとうに */etc/modprobe.d/wireless.conf* としとく。

{% gist matea2/09494c87479a1ccaefdf3cf7cf791480 wireless.conf %}


これで再起動しても動くようになった。そのうちカーネルの更新とかでなおるんかしら。



# 使用環境

+ Ubuntu 11.10 (3.0.0-12-generic)
+ PLANEX GW-USMicroN-G


# 参考サイト

+ [Ralink RT2870 based USB Wireless N adapters (Ubuntu) - The Linux Community Forum][cite-linux-forums]
+ [FreeBSDあれこれ: ubuntuでwli-uc-gnp(USB無線LAN)の使用][cite-freebsd-arkr]



[cite-linux-forums]: http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/150/
[cite-freebsd-arkr]: http://uls.fam.cx/freebsd/archives/003152.html
