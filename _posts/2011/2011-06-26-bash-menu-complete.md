---
layout: post
categories: blog
tags: Fedora bash
title: bash menu-complete
date: 2011-06-26T11:49:00+09:00
---


bashの補完で、候補の中から順番に選んで補完する。

<!-- more -->

Ctrl + F で順方向、 Ctrl + B で逆方向に補完する例。

```
bind C-F:menu-complete
bind C-B:menu-complete-backward
```


*~/.bashrc* に書くとwarningが出るので *~/.inputrc* に書くと良いっぽい。

{% gist matea2/9f3a84c708aaadd02793114ea3037d8f .inputrc %}


日本語のファイル名を補完したい時にとっても便利。この機能はあるんじゃないかなあとは思っていたけど、ずっとどうやるのかわからなかった。bashが更新されたときにマニュアルをちらちら読んでいたら発見。
