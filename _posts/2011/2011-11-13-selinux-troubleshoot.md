---
layout: post
categories: blog
tags: Fedora selinux
title: 何かがおかしいです
date: 2011-11-13T22:07:00+09:00
---


Fedora 16 をインストール後、ログインしようとしたら「ああっ何かがおかしいです。」と言われてログアウトするしかない状態になっていた。

[![error message]][error message link]

<!-- more -->

どうやらSELinux関連で問題が起きたようだ。OSを入れ直したときに、ホームディレクトリは以前のものからそのまま引き継いだのだが、それが良くなかったのだろうか。

とりあえずCUIからログインして、以下コマンドでSELinuxを一時的に *Permissive* に。

```
sudo setenforce 0
```


再度ログインすると無事デスクトップが出てきた。アプリケーション一覧から *SELinux トラブルシューター* を開くと、何やらメッセージが出ている。Troubleshootで言われるまま、

```
sudo touch /.autorelabel; reboot
```


とすると、再起動していろいろとやったあと、問題は起きなくなった。けっこうじかんかかる。


# 使用環境

+ Fedora 16 (3.1.0-7.fc16.i686)
+ libselinux-2.1.6-4
+ selinux-policy-3.10.0-55



[error message]: https://lh3.googleusercontent.com/BMecRGyOQqpf98rxGn8Qqqa0GFiVZeVVRmsCmh8u1S5SdxYY8nlQ-D7_esx1Day4XxJokbEv9OZhLQtqwuhqqaITZDbY-3fb3zCjoGb6bMIEgOA_c-7PHxr8k4PrBzezsWU9Z79TiQ=w800
[error message link]: https://photos.google.com/share/AF1QipO4N-qIQa78ZIX1T4lQEDGH4XxJQ8sjlgsjW9FsKxIuOt_Pp8yAjBM9dhthsVmAew/photo/AF1QipPhkLaQY6VH1aJqVHqbf8meNKlBBgaSJjcsg9-w?key=TDhLT0pTZ3cybVZpbUltTk03ODlZWV9DQ1VGWHVB
