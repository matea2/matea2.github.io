---
layout: post
categories: blog
tags: Windows mikutter ruby twitter
title: mikutter on windows
date: 2011-05-30T00:36:00+09:00
---


mikutter をwindowsで動かしてみたので手順をメモ。

環境は Windows Vista SP2 で、コマンド入力は [msysGit] (MINGW32) から行った。XPや7ならきっと同様にできるはず。コマンドもコマンドプロンプトとかでいけるんじゃないかと思う。

<!-- more -->


# mikutter 取得

まず [mikutter] を取って来ましょう。適当なディレクトリに移動してリポジトリから取得。

```
svn checkout svn://toshia.dip.jp/mikutter/trunk
```


# Ruby のインストール

んで、mikutterは [ruby-gnome2] で動くので ruby をインストールする。 [Ruby] のページのダウンロードからWindows版バイナリを取ってくる。私は msysGit 使ってるし、MINGW32ベースで簡単そうな [One-Click Ruby Installer for Windows] を使った。

インストーラーをダウンロードしてきて、実行。ダイアログにしたがってインストールする。

[![one-click ruby installer dialog]][one-click ruby installer dialog link]


パスと関連付けにチェック入れとくと楽かも。インストールが完了したら、OSを再起動しておく。それでコマンド打ってみて動作するか確認。

```
ruby -v
```


# Ruby-Gnome のインストール

次は、 ruby-gnome2 (ruby-gtk2) をインストールする。 gems からインストールしちゃいます。

```
gem install gtk2
```


これだけでメッセージが流れてインストールができたはず。 gtk2 を使ってみて、エラーが出ないか確認してみる。

```
ruby -e "require 'gtk2'"
ruby -e "require 'gtk2';Gtk::Window.new.show;Gtk.main"
```


# ruby-hmac のインストール

これもgemsから[^note-2011-05-28]。

```
gem install ruby-hmac
```


# mikutter の実行

さあこれで必要なものはそろった。コマンドで実行！

```
ruby mikutter.rb
```


ファイアウォールの確認が出るのでブロックを解除しておく (のが良いのか？)

[![uac dialog]][uac dialog link]


そして、

...

...

もうしわけねぇもうしわけねぇの嵐！

なにがおかしいのかわからず困っていたが、エクスプローラーから mikutter.rb をダブルクリックしたら大丈夫だった。なんかmsysGit的な問題か？

[![mikutter timeline]][mikutter timeline link]


しかしこれ書いてるときの最新版 rev376 だとあんまりうまく動かないようだ。ためしにリビジョンをさかのぼってみたら、 rev332 あたりなら問題なく動くようだ。

```
svn update -r 332
```


mikutter はどんどん開発が進んでるので、まずは最新版で試してみるのがよいかも。それで動かないようなら適当なところまでリビジョンを戻してみよう。

[![mikutter version]][mikutter version link]


# 使用環境

+ Windows Vista SP2
+ Ruby 1.9.2p180 (2011-02-18) \[i386-mingw32\]
+ ruby-gtk2 (0.90.8 x86-mingw32)
+ ruby-hmac (0.4.0)
+ mikutter 0.0.3.6 (rev376) -\> 0.0.3.4 (rev332)



[msysGit]: http://code.google.com/p/msysgit/
[mikutter]: http://mikutter.hachune.net/
[ruby-gnome2]: http://ruby-gnome2.sourceforge.jp/
[Ruby]: http://www.ruby-lang.org/
[One-Click Ruby Installer for Windows]: http://rubyinstaller.org/

[one-click ruby installer dialog]: https://lh3.googleusercontent.com/Ce4zTkDJOy24REhXooiROkVyQIm0rxOZM-DPo9GlJi3OWVFTWNwrPk11mm1PFj4D0U9uAzlvJ514KSvXn8k2HJyK6MWn2tFILJhC_zdzQSjExYoMU1orGD9xzH1DmwNG8Fz9tjM2Og=w400
[one-click ruby installer dialog link]: https://photos.google.com/share/AF1QipPcOVHSbNRSbn0VRPea-mugOd0tT6BjVFScWfgA71PWBnGMeQGwl2_DIV8Nbk29fA/photo/AF1QipN7PKGPyc7iTGzXu4QPB34GyhBd7O-SBgKsaM39?key=OXEtUlVkdW1JTTRQaF9PcHYycTdLLUczVnlNb0xn

[uac dialog]: https://lh3.googleusercontent.com/deio660v0RLYI8-pX1tiFZLnvMJljhiiHfeMyAG2eaTll9jdnl4m6cs39-Wwjv-QaXsqDT3hCVT9M66PBrTfbaWN6TsfU1DVaSt5u30AX1-fYaNeSsL56YeOqNrnk9xuPCY0KqCyXw=w400
[uac dialog link]: https://photos.google.com/share/AF1QipPcOVHSbNRSbn0VRPea-mugOd0tT6BjVFScWfgA71PWBnGMeQGwl2_DIV8Nbk29fA/photo/AF1QipPPPGJzjnwX9k7At0fBwe5TMRZ-n8eNjSZen1hC?key=OXEtUlVkdW1JTTRQaF9PcHYycTdLLUczVnlNb0xn

[mikutter timeline]: https://lh3.googleusercontent.com/CJ8VvNB8uITfysCy8uQEB7PbdPQexEK6q6MjjcoNVoCNmm7FLAY0-DYHqG66HjfYLJUx67EPYyqjptiBjX0gt2YjfJqy6pV2QO2suALdw7Pk2Z3FzquogM3A3rR1slaOtuQ7lZ3u2A=w800
[mikutter timeline link]: https://photos.google.com/share/AF1QipPcOVHSbNRSbn0VRPea-mugOd0tT6BjVFScWfgA71PWBnGMeQGwl2_DIV8Nbk29fA/photo/AF1QipOGn_K_XQwCg8yEQzLgc2YpqG6UYD_Tc_9zojNo?key=OXEtUlVkdW1JTTRQaF9PcHYycTdLLUczVnlNb0xn

[mikutter version]: https://lh3.googleusercontent.com/SShG7i-g5rvzqT8Wn2FR-WAoNIJKmxLIVtpGXLLeXvZUAOaAjZW_Q_sGPkVmY2m8NTZVlzqEl_UZZEgDw3eWaFPSlRHod-wylSo_acUVP4X4I4W7p6k4Nfhpz9NXij21b-8wd6dx0Q=w400
[mikutter version link]: https://photos.google.com/share/AF1QipPcOVHSbNRSbn0VRPea-mugOd0tT6BjVFScWfgA71PWBnGMeQGwl2_DIV8Nbk29fA/photo/AF1QipMXsqof6B6TnvSNpSUqi-HYO0qD2V8-VkqM8beq?key=OXEtUlVkdW1JTTRQaF9PcHYycTdLLUczVnlNb0xn

[^note-2011-05-28]: rev371 から ruby-hmac のインストールは不要になっていると思う。
