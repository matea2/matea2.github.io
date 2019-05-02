---
layout: post
categories: blog
tags: Web github gist jekyll
title: GitHub Pages で gist を埋め込む
---


GitHub Pages の記事に、 gist のコードを埋め込んでみた。

<!-- more -->

*_config.yml* のプラグインのところに、 *jekyll-gist* を追加。

{% gist matea2/e99b50e89be3205bfd888297b62ce09d _config.yml %}


記事の埋め込む部分に、 gist のコードを記入。ユーザー名と、gist ID、ファイル名を書く。ファイル名は複数ファイルが無ければ書かなくても良さそう。

{% gist matea2/e99b50e89be3205bfd888297b62ce09d sample.liquid %}


あとは、見た目が気になるのでスタイルを修正。[ここ][cite-reasonable-code]を参考に、 *main.scss* に追加。自分なりにアレンジしようと思ったけどだいたい同じ感じになってくやしい。

フォントサイズと罫線、背景色の統一。

{% gist matea2/e99b50e89be3205bfd888297b62ce09d style.scss %}


下部の余白と、メッセージ表示の修正。

{% gist matea2/e99b50e89be3205bfd888297b62ce09d bottom.scss %}


一行表示用の余白調整。

{% gist matea2/e99b50e89be3205bfd888297b62ce09d padding.scss %}



# 使用環境

+ github-pages 193
+ ruby 2.6.0p0
+ jekyll 3.7.4


# 参考サイト

+ [GitHub - jekyll/jekyll-gist: Liquid tag for displaying GitHub Gists in Jekyll sites.][cite-github-gist]
+ [jekyllなブログにgistを貼る \| shimar's blog][cite-shimar]
+ [Gistのコードをブログに埋め込む際のカスタマイズ【プラグインなし】 - Reasonable Code][cite-reasonable-code]



[cite-github-gist]: https://github.com/jekyll/jekyll-gist
[cite-shimar]: https://blog.shimar.me/2017/02/15/jekyll-gist.html
[cite-reasonable-code]: https://reasonable-code.com/gist-embed-customize/
