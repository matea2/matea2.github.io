---
layout: post
categories: blog
tags: ArchLinux jekyll github
title: GitHub Pages の設定
---


使いだした GitHub Pages 。最初はなるべくシンプルな状態でやろうと思うが、テーマを若干修正したのと、ホームをページネーションしてブログっぽい感じに変更した。

<!-- more -->

# ページネーション

ブログの「次へ」「前へ」みたいな、記事を何個かずつページに分けて表示するやつ。 Jekyll のドキュメントの [ページネーション] を参考に、作成した。

まずは *_config.yml* のプラグインの項に *jekyll-paginate* を追加して、設定を記入する。 *paginate* が一つのページに表示する記事の数で、 *paginate_path* でページごとのパスを設定する。

{% gist matea2/151205c28ae9c0e504360ef761d57738 _config.yml %}


ページネーションはHTMLファイル内でのみ動作するらしい。今回はホームにそのまま記事を表示したかったので、 *index.html* 内に記事を表記する部分を記述した。

{% gist matea2/151205c28ae9c0e504360ef761d57738 index.html %}


参考にしたページの記述とほとんど変わっていないが、内容を表示する部分の *post.content* の所を、内容の最初だけ表示する *post.excerpt* にした。あとは *date* の部分のフォーマットを変えてある。

これで、 index.html を表示すると、次のページ・前のページを順に辿れるようになっているはず。


# テーマの修正

テーマは、用意されているテーマの中からシンプルそうな *minima* を使ってみた。大体の感じは良さそうだが、フッターが少しごちゃごちゃしているのと、本文のコンテンツの配置が気になったので修正した。

[minima] のファイル構造を見ると、フッターは *_includes/footer.html* にあるので、自分のとこにも同じように *_includes/footer.html* をコピーして作成。 *footer-col* のところをすっきりさせる。

あとはテキストの配置とかマージンとかのスタイルを修正。 *assets/main.scss* に以下を記入して、あとは部分ごとに自分好みの修正を加えておいた。

{% gist matea2/151205c28ae9c0e504360ef761d57738 main.scss %}


# 使用環境

+ Arch Linux 4.20.6-arch1-1-ARCH
+ github-pages 193
+ ruby 2.6.0p0
+ jekyll 3.7.4
+ jekyll-paginate-1.1.0
+ minima 2.5.0



[ページネーション]: https://jekyllrb-ja.github.io/docs/pagination/
[minima]: https://github.com/jekyll/minima
