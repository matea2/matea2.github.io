---
layout: post
categories: blog
tags: Ubuntu awesome
title: awesome 設定
date: 2010-09-24T23:32:00+09:00
---


[awesome] をちょっとずつ設定してみる。私は他の環境を使うことが良くあるので、とりあえず似た感じにしてみる。

<!-- more -->

まずキー設定をしておく。awesomeはキーボードでいろいろ操作できるのだが、このとき使うのが *modkey* 。modkeyはデフォルトでは *Mod4* 、つまりウィンドウズキーに割り当てられている。しかしウィンドウズキーはちょっと押しにくいので、皆にならって無変換キーを使う。

これは無変換キーにMod4を割り当てるのが楽っぽいので、 *xmodmap* を使う。 *~/.xsession* なりに追加。awesomeはいろいろショートカットが複雑なので場合によっては無変換キーは押しにくい場合もある。私はついでに変換キーにも割り当てておいた。

{% gist matea2/fb2f2e53bf036312524721306fed6399 .xsession %}


ここからawesomeの設定。まず共通設定の */etc/xdg/awesome/rc.lua* を *~/.config/awesome/rc.lua* にコピー。これを編集していく。

ターミナルはurxvt使い、エディタはvi使いなのでそのへんを設定。自分の使うものを適当に。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-def.lua %}


でステータスバーの設定。 *mywibox* ってのが表示されているステータスバーのよう。まずステータスバーを下に持っていく。position が top になっているのを bottom に。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-wibox.lua %}


時計のフォーマットを自分好みに設定[^note-2010-10-02]。これは align のあとにフォーマットを記述すれば良いようだ。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-textclock.lua %}


時計は一番右に持っていきたいので並び替え。mywiboxの中身は、*mywibox[s].widgets = { ... }* ってとこで設定されている。 { } の中身に "layout = ... leftright" 、外には "layout = ... rightleft" って書いてあるので、左から右に詰めるものは { } 内に、右から左は { } の外に記述していけばよいようだ。ということで時計の右にあるレイアウト表示 mylayoutbox[s] を mytextclock の下に移動。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-widgets.lua %}


次にタイトルバーの表示。これはコメントアウトされている一文をコメント解除するだけでOK。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-titlebar.lua %}


あとはテーマの設定もしてみる。awesomeでは beautiful ってライブラリを使っているらしい。最初のほうに記述さている beautiful.init でテーマのパスを指定する。 */usr/share/awesome/themes/* に default, sky, zenburn ってのが入っていたので、 zenburn を使ってみた。

{% gist matea2/fb2f2e53bf036312524721306fed6399 rc-beautiful.lua %}


以上の設定でできたデスクトップ画像はこんな感じ。

[![awesome desktop screenshot]][awesome desktop screenshot link]


壁紙は [朝日放送 \| ハートキャッチプリキュア！] からいただきました。



[awesome]: http://awesome.naquadah.org/
[朝日放送 | ハートキャッチプリキュア！]: http://asahi.co.jp/precure/

[awesome desktop screenshot]: https://lh3.googleusercontent.com/BAffoX_3Sc9P_-YLGXCiMKpKeYL1X6upPT6fr5og7bcZWoGub7i2tWRcW7va_RSXnnb2Itv85spSK4SMTmZzjtD6ZbEIKdp25wi9awWLe2RlER2mPgalLQcA2w2kxizDMAX_pfntIA=w600
[awesome desktop screenshot link]: https://photos.google.com/share/AF1QipPrLBDcZF_TXBBXT1y3DOqjEB3-WIfONpsykV92y2vItFEQZQUPJB_z9I0HxCYx5A/photo/AF1QipOxlby5xejGPprDwjm4nrRgkdB9UW7VZt_ZSRib?key=bWloVzhwbFo5d3FPUHpCME1Gb1ZZOU00S3hXamRB

[^note-2010-10-02]: 時計の設定を修正した。([記事][note-2010-10-02 link])
[note-2010-10-02 link]: {{ site.baseurl }}{% post_url 2010/2010-10-02-awesome-textclock %}
