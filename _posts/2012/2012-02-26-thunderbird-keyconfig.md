---
layout: post
categories: blog
tags: Fedora keyconfig thunderbird
title: Thunderbird keyconfig
date: 2012-02-26T15:58:00+09:00
---


Thunderbirdにも keyconfig を設定してみた。

<!-- more -->

Firefoxと同じ拡張が使えるので、 [Dorando] ってとこからダウンロードしてインストール。

ページの遷移は[Firefoxのとき]と同様に設定した。


スレッド表示の切り替え。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-toggle-thread-view.js %}


メッセージ表示形式の切り替え。HTML表示とPlainText表示に切り替える。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-toggle-plaintext.js %}


ツリーのフォルダ移動や開閉は[ここ][cite-teramako]を参考にした。よくわからんのでそのまま利用。Thunderbird 2 の頃のようだが問題なく動いているようだ。

フォルダを閉じる。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-close-folder.js %}


フォルダを開く。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-open-folder.js %}


次のフォルダへ移動。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-select-next-folder.js %}


前のフォルダへ移動。

{% gist matea2/fc8b7361958793051b1f76ccc1a4823c prefs-select-previous-folder.js %}


# 使用環境

+ Fedora 16 (3.2.7-1.fc16.i686)
+ Thunderbird 10.0.1
+ keyconfig 20110522


# 参考サイト

+ [Keyconfig extension - MozillaZine Knowledge Base][cite-mozillazine]
+ [Keyconfig extension: Thunderbird - MozillaZine Knowledge Base][cite-mozillazine-thunderbird]
+ [keyconfig でフィードの URL 移動とフォルダ移動 - hogehoge @teramako][cite-teramako]



[Dorando]: http://mozilla.dorando.at/readme.html
[Firefoxのとき]: {{ site.baseurl }}{% post_url 2012/2012-01-29-firefox-keyconfig %}

[cite-mozillazine]: http://kb.mozillazine.org/Keyconfig_extension
[cite-mozillazine-thunderbird]: http://kb.mozillazine.org/Keyconfig_extension:_Thunderbird
[cite-teramako]: http://d.hatena.ne.jp/teramako/20070427/p1

[^note-2012-07-01]: 追加の設定を書いた。([記事][note-2012-07-01 link])
[note-2012-07-01 link]: {{ site.baseurl }}{% post_url 2012/2012-07-01-thunderbird-keyconfig %}
