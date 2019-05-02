---
layout: post
categories: blog
tags: ArchLinux tmux
title: tmux の設定を修正
---


tmux が 2.8 から 2.9 にアップデートされて、

> invalid option: status-attr

と出るようになった。

<!-- more -->

検索してもすぐに対応方法が見つからんかったので `man tmux` を読んでたら、設定の書き方が変わっているっぽい。

こうなっていたのを、

{% gist matea2/dbb5bb90f099ab4f84fac36c1628c39e old.tmux.conf %}


以下のように修正したら、エラーは出なくなった。

{% gist matea2/dbb5bb90f099ab4f84fac36c1628c39e new.tmux.conf %}


# 使用環境

+ Arch Linux 5.0.10-arch1-1-ARCH
+ tmux 2.9a
