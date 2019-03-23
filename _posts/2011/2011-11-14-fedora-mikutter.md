---
layout: post
categories: blog
tags: Fedora mikutter ruby twitter
title: Fedora 16 で mikutter
date: 2011-11-14T01:00:00+09:00
---


Fedora 16 で [mikutter] を使ってみたメモ。

<!-- more -->

最近のmikutterは *Ruby 1.9系* と *Ruby-Gtk2 1.0系* が必要になる。まずRubyをインストール。 Fedora 16 の標準のyumリポジトリのバージョンを確認してみる。

```
yum info ruby
```


バージョンは1.8.7、まだ古いバージョンだった。どうしようかなーと思うも、まあせっかくなので自分で最新のバージョンをコンパイルして動かすことにしてみた。

ということで、Rubyのサイトからソースコードをダウンロードする。このときの最新安定版 [ruby 1.9.3-p0] を取ってきた。

ファイルを展開して出てきたディレクトリに移動。コンパイルの前に、gem関連で必要になるので *libyaml* を入れておく。

```
sudo yum install libyaml
```


でいつもの。

```
./configure
make
sudo make install
```


エラーがなければRubyがインストールできたので確認。

```
ruby -v
```


続いてRuby-Gtk2をインストール。yumのruby-gtk2は1.0系だが、一緒にRubyもインストールしようとするのでgemから入れちゃう。とりあえず更新確認。

```
sudo gem update
```


しかしここでエラーが起きて、

> no such file to load -- zlib (LoadError)

と言われてしまった。[ここ][cite-stack-overflow]のページを参考に、Rubyソース内の *ext/zlib/* に移動して、パスを追加してコンパイル。zlibとzlib-develが入ってない人はyumから入れておく。

```
cd ext/zlib/
ruby extconf.rb --with-zlib-include=/usr/include --with-zlib-lib=/usr/lib
make
sudo make install
```


再度 `gem update` で更新確認ができた。次はgtk2をインストール...の前に必要なパッケージをまとめて入れておく。必要だったかどうかよくわからなかったけど node パッケージもインストールしている。

```
yum install glib2-devel atk-devel cairo-devel pango-devel gdk-pixbuf2-devel gtk2-devel
```


でようやくgtk2をインストール。

```
sudo gem install gtk2
```


よっしこれでmikutterが動...かない。

```
ruby mikutter.rb
```


実行すると、

> cannot load such file -- openssl (LoadError)

と言われる。openssl関連が不足していたようだ。

```
sudo yum install openssl openssl-devel
```


yumでパッケージをインストールした後、 Rubyソース内の *ext/openssl/* に移動。もいっかいコンパイル。

```
cd ext/openssl/
ruby extconf.rb
make
sudo make install
```


今度こそ

```
ruby mikutter.rb
```


これで動いた。めでたしめでたし。

[![mikutter window]][mikutter window link]


# 使用環境

+ Fedora 16 (3.1.1-1.fc16.i686)
+ mikutter 0.1 (svn r578)
+ Ruby 1.9.3p0 (2011-10-30)
+ Ruby-Gtk2 1.0.3


# 参考サイト

+ [オブジェクト指向スクリプト言語 Ruby][cite-ruby]
+ [ruby - Ubuntu noob rails install fails on zlib - Stack Overflow][cite-stack-overflow]



[mikutter]: http://mikutter.hachune.net/
[ruby 1.9.3-p0]: ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.bz2

[mikutter window]: https://lh3.googleusercontent.com/gKA-Vw-WXo86t1mF2ECAI2ztVcbsGliCBsFzflIPAdsTHoN9sLbr3draIXKAxh_UqgcKlSwK7VMs_5Pcpb6hoVPR16dkMOecqlalCVE3sOm19Kni9hwTXya01vKxlHUFJrEPad4-MQ=w800
[mikutter window link]: https://photos.google.com/share/AF1QipNyUaZZYbN-rAMtPN4hYEPNoLiNuNtASRm2S4AbGZbIZnuxDiCP9gSB9f4eUp_HWg/photo/AF1QipNFqLYvbQKnQ3ETAGAKCk0QFgBxBF6Sc49vL2ya?key=bU5TcTlfNjFiQk5PTHdUMXJ4TGNkNFdtTFBWRWZn

[cite-ruby]: http://www.ruby-lang.org/
[cite-stack-overflow]: http://stackoverflow.com/questions/769496/ubuntu-noob-rails-install-fails-on-zlib

[^2012-08-11]: Fedora 17 からは標準で Ruby 1.9.3系になったので、yumからさくっとインストールできる。
