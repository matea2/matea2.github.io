---
layout: post
categories: blog
tags: Ubuntu awesome
title: awesome 時計設定
date: 2010-10-02T23:38:00+09:00
---


この前 [awesome] ステータスバーの時計のフォーマットを変更したが、よく見たら秒が動いてなかったので設定。

<!-- more -->

[前回]設定したのがこれ。

{% gist matea2/4af8f453d5e87c16865fe15142ed3c3e rc-textclock-old.lua %}


[Lua API documentation] を見ると *awful.widget.textclock* の項を発見。フォーマットの後に更新時間を書けば良いようだ。 *~/.config/awesome/rc.lua* の textclock のところに、毎秒更新するように 1 を記述。

{% gist matea2/4af8f453d5e87c16865fe15142ed3c3e rc-textclock-new.lua %}


これで秒まできっちり表示できた。

使用バージョンくらい書いておかないといかんと思った。

+ awesome 3.4.5



[awesome]: http://awesome.naquadah.org/
[Lua API documentation]: http://awesome.naquadah.org/doc/api
[前回]: {{ site.baseurl }}{% post_url /2010/2010-09-24-awesome-config %}
