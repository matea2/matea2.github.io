---
layout: post
categories: blog
tags: Fedora awesome nitrogen xcompmgr xorg xrandr
title: マルチモニター設定
date: 2012-03-31T14:23:00+09:00
---


ひょんなことからノートパソコンを入手。古かったデスクトップ機のかわりに、メインのFedora機として使うことにした。さよなら灼熱のマイP4マシン...。

OSは入れ直しただけで特別問題なく動作し、USB機器とかもちゃんと認識してくれた。んで、変わったのがディスプレイ。ノートパソコンの画面と、持っていたモニターを接続して2画面にしてみた。

ということで、マルチモニター(ディアルディスプレイ？) の設定をメモしておく。

<!-- more -->

# XRandR

モニターは接続するだけで自動的に2画面に出力された。使っているウィンドウマネージャーのawesomeでも問題なく表示されている。ただ画面の配置と出力の並びが違う。これを `xrandr` コマンドで操作。

まずそのままコマンドを入力して、出力デバイスを確認。

```
xrandr
```


ノートパソコンの画面がLVDS1、外部出力の画面がVGA1だった。VGA1を右側に持って行きたいので以下のように実行。

```
xrandr --output VGA1 --right-of LVDS1
```


うむちゃんとできた。他にも一方の出力を消したり、同じ画面を出力したり、回転したり、コマンドからいろいろ操作できるようだ。


# X設定

コマンドからの操作はわかったので、起動時の設定をする。アカウントの設定ファイルからxrandrコマンドを読み込ませてもいいけど、ログイン画面とかも外部出力に持って行きたいので、[ここ][cite-aptosid]を参考にしてXの設定を書くことにした。

*/etc/X11/xorg.conf.d/30-screen.conf* を作成。VGA1をPrimaryにして、LVDS1の右側に来るように設定した。

{% gist matea2/4149291a45481b3de66fe1705204f039 30-screen.conf %}


# 壁紙

画面配置の設定はできたけど、せっかくだから画面ごとに別々の壁紙にしたい。awesomeのawsetbgだと、同じ壁紙がそれぞれの画面に設定されている。xscreensaverは自動的に2画面検出して別々のスクリーンセーバーを表示してくれているんだけど。

調べてみたが、awsetbg (で使っていたfeh)からだとどうやったらいいのかよく分からなかった。でも [nitrogen] というので設定できるらしい。yumにあったのでインストールして使ってみる。

```
sudo yum install nitrogen
```


実行してみた画面。

[![nitrogen window]][nitrogen window link]


Preferencesから壁紙のあるディレクトリを追加して、画面と好きな壁紙を選択してApplyするだけ。問題なく動作したし、xcompmgrの透過もOK。配置の方法も、Automatic・Scaled・Centered・Tiled・Zoomed・Zoomed Fillと合って融通が利く。

しかしコマンドから操作できないと起動時の設定がなぁーと思ったら、restoreオプションというものがあった。このオプションをつけると、前回の設定を復元するだけでウィンドウは開かない。

```
nitrogen --restore
```


これを起動時に読み込むようにさせれば完了！自分はawesomeのテーマ設定ファイル *~/.config/awesome/theme.lua* で wallpaper\_cmd に書いておいた。

{% gist matea2/4149291a45481b3de66fe1705204f039 theme.lua %}


デスクトップ画面はこんな感じになった。

[![multi monitor desktop]][multi monitor desktop link]


壁紙は、[朝日放送｜スマイルプリキュア！]と、[nicomi.com]からいただいた[のと]さん壁紙を使わせてもらいました。


# 使用環境

+ Fedora 16 (3.3.0-4.fc16.x86\_64)
+ xorg-x11-server-Xorg 1.11.4
+ awesome 3.4.11
+ xcompmgr 1.1.6
+ xrandr 1.3.5 (Server reports RandR version 1.3)
+ nitrogen 1.5.2
+ xscreensaver 5.15


# 参考サイト

+ [モニタの解像度を変更するには - Ubuntu Japanese Wiki][cite-ubuntutips]
+ [本を読む XRandRでUbuntuの外部モニタ出力を切り替える][cite-emasaka]
+ [aptosid Manuals - Screen Resolutions and Dualhead][cite-aptosid]
+ [Nitrogen - l3ib.org][nitrogen]
+ [Linux Certif - Man nitrogen(1)][cite-linuxcertif]



[nitrogen]: http://projects.l3ib.org/nitrogen/
[朝日放送｜スマイルプリキュア！]: http://asahi.co.jp/precure/
[nicomi.com]: http://nicomi.com/
[のと]: http://sora.nicomi.com/

[nitrogen window]: https://lh3.googleusercontent.com/hQL9r_4E-oEvzZWJ9yXWeItQ7GsNKs2hwW3aZ3kSGa6cst9dCLE3znxu2FhfvjrNZ9rLIwiF0wdzijs1YanyK9dtjExMF5PTbV1jqgcg0tN507XkPU5rY_aR5_0xMCdn-OSsx2L4GQ=w500
[nitrogen window link]: https://photos.google.com/share/AF1QipOFp8xb8uf2VLbAfGKPgpOymBZpfj8grGF2kGmeN9bJM2mbZHN2uJeLPZ--KEKS2Q/photo/AF1QipMb7TWBTinBCplela38rYGVtC0xHZ-akcankxmC?key=TUtVVjFTekE3UlpTRVhpek45VHJfZXhnTnE3VWZ3

[multi monitor desktop]: https://lh3.googleusercontent.com/4BrXCYrvMwgF2ofujMRwsQSdT-ozYa-RV-e47nqvlfksjhszoYdUFHT-r-Afg5a37Ouw7peDO0GyWx68Un3DJca0FKvnwmVtp_sK1xC9UvFcEMCwPIJt-Yq_fQLRdF5wZKRnFukm6A=w800
[multi monitor desktop link]: https://photos.google.com/share/AF1QipOFp8xb8uf2VLbAfGKPgpOymBZpfj8grGF2kGmeN9bJM2mbZHN2uJeLPZ--KEKS2Q/photo/AF1QipNCSd98XyeK8VeTgzKIIXD8Kmycl-NJJHzOeCm6?key=TUtVVjFTekE3UlpTRVhpek45VHJfZXhnTnE3VWZ3

[cite-ubuntutips]: https://wiki.ubuntulinux.jp/UbuntuTips/Hardware/HowToChangeMonitorResolution
[cite-emasaka]: http://emasaka.blog65.fc2.com/blog-entry-358.html
[cite-aptosid]: http://manual.aptosid.com/ja/hw-dev-mon-ja.htm
[cite-linuxcertif]: http://www.linuxcertif.com/man/1/nitrogen/
