---
layout: post
categories: blog
tags: Fedora firefox keyconfig
title: Firefox keyconfig 続き
date: 2012-07-01T19:33:00+09:00
---


FirefoxのキーからJavascriptとPluginのオンオフを切り替えられるように設定した。どっちも設定切り替えて更新するだけだった。更新のところはもともと登録されていたものを参考にした。

<!-- more -->

Javascriptの切り替え。

{% gist matea2/b998f89c400e9c330346ddc42b544d8a prefs-toggle-javascript.js %}


Pluginの切り替え。

{% gist matea2/b998f89c400e9c330346ddc42b544d8a prefs-toggle-plugins.js %}


# 使用環境

+ Fedora 17 (3.4.4-3.fc17.x86\_64)
+ Firefox 13.0.1
+ keyconfig 20110522


# 参考サイト

+ [keyconfig 20110522 • mozillaZine Forums][cite-mozillazine]



[cite-mozillazine]: http://forums.mozillazine.org/viewtopic.php?f=48&t=72994&start=1260
