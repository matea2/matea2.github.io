---
layout: post
categories: blog
tags: Ubuntu xinput タッチパッド
title: タッチパッド設定
date: 2010-09-26T17:50:00+09:00
---


ノートのUbuntuでタッチパッドの設定を変えてみた。タップでのクリックを無効に、水平スクロールを有効にしたかった。

<!-- more -->

調べると、 */etc/X11/xorg.conf* を修正する方法と `xinput` コマンドを使う方法なんかがあるらしい。今回は個人レベルで設定したかったので xinput を使った。

まず、デバイスの調査。 list オプションをつければ調べられるようだ。

```
xinput --list
```


Virtual core pointer と Virtual core keybord の一覧がずらっとでてきた。pointerを見てみて、おそらく *AlpsPS/2 ALPS GlidePoint* ってのがタッチパッドだろうと判断。もう一段階詳しく調べる。

```
xinput --list "AlpsPS/2 ALPS GlidePoint"
```


...まあこれで合ってるんかな？

でプロパティを調べる。

```
xinput --list-props "AlpsPS/2 ALPS GlidePoint"
```


またずらっとプロパティ一覧が出てきた。見てみるとおそらく *Synaptics Tap Action* ってのがタップしたときの設定、 *Synaptics Edge Scrolling* がスクロールの設定だろう。試しに 2, 3, 0, 0, 1, 2, 3 となっていた Synaptics Tap Action を 0, 0, 0, 0, 0, 0, 0 にしてみる。

```
xinput --set-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Action" 0, 0, 0, 0, 0, 0, 0
```


タップでクリックが反応しなくなった、よし。でも調べてみたが各数値が何を意味しているのかがわからなかった。まあクリックが反応しなくなったからとりあえず良いか。

次は Synaptics Edge Scrolling 。これは 1, 0, 0 となっていた。 Virtical, Horizontal, Corner を表すらしい。ということで、値を 1, 1, 0 に設定。

```
xinput --set-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Edge Scrolling" 1, 1, 0
```


無事水平スクロールが有効になった。あとは起動時に読み込むように、 *xinput --set-prop ～* を *~/.xsession* なりに追加して完了。

まあGnomeな人は、メニューから システム→設定→マウス を選べばかんたんだけど！
