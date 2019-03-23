---
layout: post
categories: blog
tags: Fedora texlive
title: Fedora 16 で texlive 2011
date: 2012-01-15T18:29:00+09:00
---


ちょっと久しぶりにLaTeXを触ってみようと思ったので、Fedoraに [Tex Live] の環境を整えてみた。

<!-- more -->

# インストール

yumで標準のfedoraリポジトリを調べてみたらtexliveのバージョンは2007だった。2011はutf-8が使えるらしいし、新しくtexliveのリポジトリを [fedorapeople] のとこから追加。Fedora 16なので packages.fc16 から。

```
sudo rpm -i http://jnovy.fedorapeople.org/texlive/2011/packages.fc16/texlive-release.noarch.rpm
```


yumでインストール。

```
sudo yum install texlive
```


# platex

早速使おうと思ったら、 `platex` コマンドがない。うむむーと思いながら調べてみると texlive-east-asian てのを発見。fedoraリポジトリなんだけど良いんかいなーと思いつつ試しにインストールを実行。

```
sudo yum install texlive-east-asian
```


すると、

> パッケージ texlive-east-asian は texlive-collection-langcjk によって不要になりました。代わりにtexlive-collection-langcjk-2011-3.20111207\_r24786.svn24462.fc16.noarchのインストールを試みています。

と言われた。という事で texlive-collection-langcjk をインストール。

```
sudo yum install texlive-collection-langcjk
```


これでplatexコマンドが入って、utf-8のtexファイルも問題なくコンパイルできた。

```
platex test.tex
```


# pxdvi

pxdviでdviファイルを見ようと思ったらこれも入ってない。これは調べてみてもよく分からず...。 `xdvik` をインストールしようとすると

> 既にインストール済みのtexlive-xdvi-bin によって不要扱いになりました。

と言われるんだが...。texliveには入ってないんかな？今回はpdfを作りたいだけだったので断念。


# dvipdfmx

お次は dvipdfmx。platexで出力されたdviをpdfに変換する。ふつうにやったらフォントがなんかおかしいみたいで怒られた。 -f オプションで cid-x.map を指定してやったらできた。

```
dvipdfmx -f /usr/share/texlive/texmf/fonts/map/dvipdfmx/cid-x.map test.dvi
```


設定ファイル */usr/share/texlive/texmf/dvipdfmx/dvipdfmx.cfg* を見てみると、 cid-x.map のところがコメントアウトされていたので、コメントを解除。

{% gist matea2/291b4bf18bab24415c675b1aa286df6c dvipdfmx1.cfg %}


ついでにWarningが出ていた kanjix.map をコメントアウトしといた。

{% gist matea2/291b4bf18bab24415c675b1aa286df6c dvipdfmx2.cfg %}


これで -f オプション無しでもすっきり実行。

```
dvipdfmx test.dvi
```


うーん、全体的にあんまりよくわからんがpdfができたので良し！


# 使用環境

+ Fedora 16 (3.1.8-2.fc16.i686)
+ Tex Live 2011 (3.20111207\_r24786.fc16)
+ texlive-collection-langcjk 2011 (3.20111207\_r24786.svn24462.fc16)


# 参考サイト

+ [Features/TeXLive - FedoraProject][cite-fedoraproject]
+ [Linux に最短でLaTeX を導入する « digimuura][cite-digimuura]



[Tex Live]: http://www.tug.org/texlive/
[fedorapeople]: http://fedorapeople.org/

[cite-fedoraproject]: http://fedoraproject.org/wiki/Features/TeXLive
[cite-digimuura]: http://digimuura.wordpress.com/2011/01/16/linux-%E3%81%AB%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%EF%BC%91%E8%A1%8C%E3%81%A7latex-%E3%82%92%E5%B0%8E%E5%85%A5%E3%81%99%E3%82%8B/
