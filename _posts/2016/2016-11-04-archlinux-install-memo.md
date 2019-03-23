---
layout: post
categories: blog
tags: ArchLinux アップグレード
title: Arch Linux を再インストール
---


Lenovo g570 に、 Arch Linux を再インストールしたので手順をメモしておく。

<!-- more -->

# インストールUSB作成

まずは、インストール用のUSBを作成する。 Arch Linux の[ダウンロード]ページから、ISOイメージと、検証用の md5sum をダウンロード。手っ取り早く *HTTP Direct Downloads* から、 *Japan jaist.ac.jp* 選んでダウンロードした。

+ ftp.jaist.ac.jp/pub/Linux/ArchLinux/iso/2016.11.01/archlinux-2016.11.01-dual.iso
+ ftp.jaist.ac.jp/pub/Linux/ArchLinux/iso/2016.11.01/md5sums.txt


ダウンロードができたら、ISOイメージが正常にダウンロードできているかチェック。

```
md5sum -c md5sums.txt
```


問題なければ、差し込んだUSBデバイスに `dd` で書き込む。今回は */dev/sdb* だが、書き込み先を間違えないように注意。

```
sudo dd if=archlinux-2016.11.01-dual.iso of=/dev/sdb
```


これで、インストール用USBの作成は完了。


# 起動

reboot して、BIOSのブートメニューを開く。g570では *F12* キーを押したら開いた。メニューから *Boot Arch Linux (x86_64)* を選択して、USBから起動する。


# インストール

起動したら、インストール開始。

とりあえず、キー配列を日本語に設定しておく。

```
loadkeys jp106
```


それから、パーティションを作成。インストールするSSDに対して `cfdisk` を実行。上下キーでパーティションを選択して、左右キーで動作を選択する感じ。

```
cfdisk /dev/sda
```


以下の手順のように作成した。

1.  [Delete] で既存パーティションを全消去
1.  [New] でパーティション作成、 [Type] で種別を設定
  + /dev/sda1: 200M, Primary, Linux (83)
  + /dev/sda2: 2G, Primary, Linux Swap / Solaris (82)
  + /dev/sda3: 27.6G(残り), Primary, Linux (83)
1.  [Write]
1.  [Quit]


できたら、作成したパーティションにファイルシステムを作成。

```
mkfs.ext4 /dev/sda1
mkfs.btrfs /dev/sda3
```


/dev/sda3 を基本に、 /dev/sda1 は boot にしてマウント。

```
mount /dev/sda3 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
```


ネットワークの設定をする。

`ip` コマンドで、デバイス名を確認。

```
ip link
```


接続している無線のデバイスが *wlp2s0b1* だったので、それを使ってネットワークの設定をする。サンプルのファイルをコピーして、 *wireless* の名前で設定ファイルを作成。

```
cp -ai /etc/netctl/examples/wireless-wpa /etc/netctl/wireless
```


自分の環境に合わせてファイルを編集。

{% gist matea2/9e2caeb24ed4a38b59ded6451680a06d wireless %}


ネットワークを接続。

```
netctl start wireless
```


接続できたら、インストールを開始する。 *base* と、 *grub* 、あと無線用に *wpa_supplicant* を入れる。

```
pacstrap /mnt base base-devel
pacstrap /mnt grub
pacstrap /mnt wpa_supplicant
```


終わったら、現在の環境から *fstab* を生成。

```
genfstab -p /mnt >> /mnt/etc/fstab
```


rootから *grub* のインストール。

```
arch-chroot
mkinitcpio -p linux
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
exit
```


これでひとまずインストール完了。
再起動してちゃんと起動するか確認。

```
umount /mnt/boot
umount /mnt

reboot
```


# 初期設定

無事 Arch Linux が起動できたら、rootでログインして初期設定をする。

とりあえずパスワードを変更。

```
passwd
```


swap の設定。

```
mkswap /dev/sda2
swapon /dev/sda2
```


fstab をUUID表記に変更。 `blkid` でUUIDを調べる。

```
blkid /dev/sda1
```


出力されたUUIDを元に /etc/fstab を修正。以下のような形に書き換えた。

{% gist matea2/9e2caeb24ed4a38b59ded6451680a06d fstab %}


再起動して、問題なく起動するかを確認。

```
reboot
```


GRUBの表示時間が長く感じたので、 */etc/default/grub* のタイムアウトを修正。

{% gist matea2/9e2caeb24ed4a38b59ded6451680a06d grub %}


再度設定を反映。

```
grub-mkconfig -o /boot/grub/grub.cfg
```


また再起動して問題ないか確認。

```
reboot
```


ユーザーの追加。自分は wheel グループに入れておく。

```
useradd -m -G wheel username
passwd username
```


`visudo` で wheel に権限を与える。

```
%wheel ALL=(ALL) ALL
```


これで sudo できるようになるので、 root をログアウト。

```
exit
```


作成したアカウントでログインし、以降は sudo から設定。

ホスト名とタイムゾーンの変更。

```
sudo hostnamectl set-hostname g570
sudo timedatectl set-timezone Asia/Tokyo
```


locale の変更。 `sudoedit /etc/locale.gen` して以下を記入。

{% gist matea2/9e2caeb24ed4a38b59ded6451680a06d locale.gen %}


設定を反映。

```
sudo locale-gen
sudo localectl set-locale LANG=ja_JP.utf8
```


ネットワークの設定でパスフレーズを直接ファイルに記入していたので、ハッシュ化して記入。覚えられにくいってだけで、あんまり意味はないらしいが。

もう一度インターフェースを確認しておく。

```
ip link
```


*wpa_supplicant* の `wpa_passphrase` コマンドを使って、パスフレーズを取得。

```
wpa_passphrase essid passphrase
```


設定していた /etc/netctl/wireless の *Key* のところに、先頭に \\" を加えて記入すれば良いらしい。

{% gist matea2/9e2caeb24ed4a38b59ded6451680a06d wireless2 %}


ネットワーク設定を有効化＆起動。

```
sudo netctl enable wireless
sudo netctl start wireless
```


接続できたらパッケージを更新。

```
sudo pacman -Syu
```


あとは適当に使うものをインストール。お好みで自分が必要なものを。

+ xorg
+ xdm-archlinux
+ awesome
+ pulseaudio
+ fcitx
+ fcitx-mozc
+ rxvt-unicode
+ tmux
+ conky
+ feh
+ xscreensaver
+ xcompmgr
+ cbatticon
+ gnome-themes-standard
+ archlinux-wallpaper
+ vim
+ bash-completion
+ openssh
+ git
+ nitrogen
+ imagemagick
+ btrfs-progs
+ chromium
+ firefox
+ firefox-i18n-ja
+ thunderbird
+ thunderbird-i18n-ja
+ libreoffice-fresh
+ libreoffice-fresh-ja
+ gimp
+ vlc


[ダウンロード]: http://www.archlinux.org/download
