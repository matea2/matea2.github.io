---
layout: post
categories: blog
tags: Fedora slim
title: ディスプレイマネージャを変更
date: 2010-06-01T23:56:00+09:00
---


Fedora 13 のデフォルトのディスプレイマネージャGDMが重く感じたので、 [SLiM] に変更してみた。SLiMはyumからインストールできた。

<!-- more -->

変更は */etc/sysconfig/desktop* に以下の1行を書くだけ。今回はファイルがなかったので新規作成した。

{% gist matea2/2887a4c0a94f95b147d224ddec526c42 desktop %}


コマンドには */usr/bin/slim* と */usr/bin/slim-dynwm* があったがよくわかっていない。

画像が変更後のログイン画面。この画面のときに、 *F1キー* でセッション切り替え、 *F11キー* でスクリーンショット取得ができる。テーマも簡単に変えられそうなので、いじってみてもおもしろいかも。

[![SLiM screenshot]][SLiM screenshot link]


*~/.xinitrc* とかも読み込んでくれるようなので、コマンドラインから `startx` な人も簡単に移行できそうだ。



[SLiM]: http://slim.berlios.de/

[SLiM screenshot]: https://lh3.googleusercontent.com/ed0LWe6B4YjeSI-1Cjkwla8dUpH_rPACQZzDMzxRGn0IXZIm2fAWU4R7uAQVI24-6gSGUBgYdJoIZj74aK-ezI5jKyrAJXnWs8XYquInlcih54taV9WZvWPx7A2AUjBIIDjhYyCveQ=w600
[SLiM screenshot link]: https://photos.google.com/share/AF1QipOh8eO6tIkzirHu0_yGOKqpnPYniz_aTbZb2hNnbBbVJSRmh_gGhDf8W2EvNJspzg/photo/AF1QipMy6D7Wa3Ita82PTLsS8QSzxwTifaqWdX-QI4ON?key=NTExZzdzUlNnNHVGSWx2czRQcTVpM2NPTXNFREJB
