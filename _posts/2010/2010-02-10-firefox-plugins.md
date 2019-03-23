---
layout: post
categories: blog
tags: Fedora firefox thunderbird
title: Firefoxのプラグインを整理
date: 2010-02-10T12:17:00+09:00
---


*Firefox* のプラグインがごちゃごちゃしてたので、整理することにした。

<!-- more -->

まずプラグインの場所を確認。以下の2つのディレクトリに入っているようだ（Firefox以外にThunderbirdなどMozilla共用みたい）。

+ /usr/lib/mozilla/plugins
+ /usr/lib/mozilla/plugins-wrapped


試しに中のファイルを移動してみてFirefoxを再起動すると、プラグインの項目に表示されなくなった。でファイルを元に戻して再起動。すると、バージョン違いで複数表示されていたAdobeのプラグインは、最新のものだけ表示されるようになった。よし。

あとは、不要なプラグインに対応するファイルを削除する。いつの間にか入っていたメディア関係のものを調べると、Totemのプラグインで、 *totem-mozplugin* という1つのパッケージになっているようだ。これはyumから削除でOK。その他も適当に調べて整理。

ちなみに、言語パックやテーマの方は、FirefoxとThunderbirdでそれぞれ、以下の場所に入っていた。

+ /usr/lib/firefox-バージョン番号/extensions
+ /usr/lib/thunderbird-バージョン番号/extensions
