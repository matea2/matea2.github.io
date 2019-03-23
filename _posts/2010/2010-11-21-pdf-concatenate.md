---
layout: post
categories: blog
tags: Fedora pdftk
title: 複数のPDFを結合
date: 2010-11-21T18:13:00+09:00
---


最近、紙の書類をスキャンして整理しだした。ページごとにスキャンしてできたPDFを、1つのPDFに結合する方法を覚えたのでメモ。

<!-- more -->

今回は調べてみて情報が多かった [pdftk] ってのを利用した。インストールは `yum` でOK。結合のコマンドは以下のような感じ。

```
pdftk 01.pdf 02.pdf cat output 01-02.pdf
pdftk *.pdf cat output combined.pdf
```


ほかにも分割とか編集はいろいろできそう。日本語のファイル名はうまくいかないようなので、コマンドの実行前後にリネームをする必要があった。


# 使用環境

+ Fedora 14
+ pdftk 1.41



[pdftk]: http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/
