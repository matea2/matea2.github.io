---
layout: post
categories: blog
tags: Fedora udev
title: CanoScan LiDE 40
date: 2010-01-31T21:03:00+09:00
---


Fedora 12 にしてから、USBスキャナの *CanoScan LiDE 40* が使えなかったが、先日のsaneの更新で使えるようになった。そのときにudevの設定を変更したのでメモ。

<!-- more -->

*/etc/udev/rules.d/99-local.rules* に以下を追加[^note-2010-06-07]。

{% gist matea2/6e8f5f0e0c4a384b4ba52bef96b26c57 99-local-old.rules %}


ここではファイル名を *99-local.rules* としているが、「番号-\*.rules」の形式であれば良い。番号が小さい方から順番に読み込まれるので、小さい場合は後から読んだ設定に書き換えられる可能性がある。

*idVendor* と *idProduct* はメーカーや機種によって違うので、 `dmesg` を参考に。 MODE に 0666 を設定することで、誰でも読み書きできるようにしている。



[^note-2010-06-07]: ルールの記述を修正した。 ([記事][note-2010-06-07 link])
[note-2010-06-07 link]: {{ base.url }}{% post_url /2010/2010-06-07-udev-rules %}
