---
layout: post
categories: blog
tags: ArchLinux gdm grub xorg yaourt フォント 無線LAN
title: Arch Linux 設定
date: 2012-10-28T18:00:00+09:00
---


Arch Linux インストールができたので、基本的なところを設定。

<!-- more -->

# ユーザー設定

通常使うユーザーを追加。管理者として使うので wheel グループに入れとく。 `adduser` コマンドで、ダイアログに従って入力。

```
Login name for new user []: matea2
User ID ('UID') [ defaults to next available ]: 1000
Initial group [ users ]:
Additional groups (comma separated) []: wheel
Home directory [ /home/matea2 ]
Shell [ /bin/bash ]
Expiry date (YYYY-MM-DD) []:
```


sudoを使えるようにする。とりあえず有線でネットワークを動かして `sudo` をインストール。

```
dhcpcd eth0
pacman -S sudo
```


`visudo` から設定して、 wheel グループの操作を許可。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 sudoers %}


# 無線LAN設定

無線LANを設定する。いつもNetworkManager使ってるのでインストール。

```
sudo pacman -S networkmanager
sudo systemctl enable NetworkManager.service
```


そのままだと GW-USMicroN-G はうまく動いてなかったが、[Ubuntuと同じ方法]でできた。 */etc/udev/rules.d/99-wireless.rules* に設定を記述。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 99-wireless.rules %}


もうひとつ */etc/modprobe.d/wireless.conf* に設定を書いて再起動。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 wireless.conf %}


# パッケージ追加

必要なパッケージを色々追加。すでに使っているけど、 `pacman` を実行する。リモートのリポジトリを見るときは *-S* 、ローカルは *-Q*、削除するときは *-R* を使う感じか。

基本は以下のオプションで良いかな。

```
pacman -Syu # システムをアップデート
pacman -Ss キーワード # パッケージを検索
pacman -S パッケージ名 # パッケージのインストール
```


ライセンスの問題などで pacman ではパッケージが見つからない場合もある。そんなときは *AUR* からインストール、これは *yaourt* を使うと楽そう。

[ここ][cite-tickstick]を参考に、 */etc/pacman.conf* を編集し、 archlinuxfr のサーバーを追加。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 pacman.conf %}


でpacmanからインストール。

```
sudo pacman -S yaourt
```


あとはpacmanと同じようにパッケージ名を指定してインストールする。日本語フォントとかはここでインストールできた。

```
yaourt -S otf-ipafont
yaourt -S ttf-mplus
```


ただ mozc は 

> ERROR: is not available for the 'i686' architecture.

って言われるなあ。


# サウンド設定

ユーザーを *audio* グループに追加する。

```
gpasswd -a matea2 audio
```


実はいろいろ設定しても音が全然鳴らなくて困ったのだが、OSごと再度インストールしなおして上の設定を行ったら音が鳴ったという。なぜ最初はうまく行かなかったかよくわからんけど、多分これだけで良いのだろう。


# GUI設定

さてそろそろグラフィカルな画面が欲しいのでXをインストール。 pacman から xorg を指定、 *Enter a selection* とか言われて必要なパッケージを選択するように言われたけどまあ全部つっこんどいた。

```
sudo pacman -S xorg
```


*runlevel* を変更。最近はArchでもsystemdらしいので *default.target* にリンク貼ったらいいんじゃないかな。

```
sudo ln -s /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target
```


ディスプレイマネージャをインストール。ふつうに *gdm* を入れた。

```
sudo pacman -S gdm
```


で起動時に動作するようにsystemdを設定。

```
sudo systemctl enable gdm.service
```


ウィンドウマネージャを入れる。自分はawesomeだけど、お好みでgnomeとかなんとか。

```
sudo pacman -S awesome
```


ついでにgrubの起動時間を設定。 */etc/default/grub* を編集。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 grub %}


変更を適用。

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```


再起動したらgdmが動く。メニューからウィンドウマネージャを選んで、ユーザー名とパスを入力してログイン。

で自分は *~/.xsession* に設定書いてるのでそこから読んで起動するようにしたい。[ここ][cite-bbs-topic]に書いてあったのを参考にして */usr/share/xsessions/xsession.desktop* を設定。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 xsession.desktop %}


もう一度再起動するとgdmのメニューに *Xsession* が増えるので、それを選んでめでたしめでたし。


# フォント設定

日本語フォントがなんだか変なので */etc/fonts/local.conf* を編集。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 local.conf %}


gtk-2系は `gtk-chtheme` を使ってテーマも一緒に設定。もしくは *~/.gtkrc-2.0* に適当に書いておく。

```
pacman -S gtk-chtheme
gtk-chtheme
```


gtk-3系は *~/.config/gtk-3.0/settings.ini* に記述。テーマとアイコンとフォントを書いておいた。

{% gist matea2/6a5523bf139bb1fe534b9928e84cf3c8 settings.ini %}


# 使用環境

+ Arch Linux (3.6.3-1-ARCH)


# 参考サイト

+ [Pacman (日本語) - ArchWiki][cite-pacman-wiki]
+ [GRUB2 - ArchWiki][cite-grub-wiki]
+ [[SOLVED] Awesome and GDM (Page 1) / Applications & Desktop Environments / Arch Linux Forums][cite-bbs-topic]
+ [Tick Stick Linux : Yaourt のインストール ArchLinux][cite-tickstick]



[Ubuntuと同じ方法]: {{ site.baseurl }}{% post_url /2011/2011-10-15-ubuntu-wireless-lan %}

[cite-pacman-wiki]: https://wiki.archlinux.org/index.php/Pacman_%28%E6%97%A5%E6%9C%AC%E8%AA%9E%29
[cite-grub-wiki]: https://wiki.archlinux.org/index.php/GRUB2
[cite-bbs-topic]: https://bbs.archlinux.org/viewtopic.php?pid=709573#p709573
[cite-tickstick]: http://blog.livedoor.jp/tickstick/archives/1028116.html
