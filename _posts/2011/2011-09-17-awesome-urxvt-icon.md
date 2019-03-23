---
layout: post
categories: blog
tags: Fedora awesome
title: awesomeでurxvtにアイコンを付けた
date: 2011-09-17T18:26:00+09:00
---


awesome ネタは続く。ターミナルはurxvtを使っててよくたくさん開いているが、タスクバーとかでアイコンが表示されなくて寂しいので付けてみた。

<!-- more -->

Rulesのところのpropertiesでiconを指定すればOK。

{% gist matea2/ee5d93985efc89cfe6e3da864e7fed28 rc.lua %}


クラス名とかは `xprop` で調べられるんだな。


# 使用環境

+ Fedora 15 (2.6.40.4-5.fc15.i686)
+ awesome 3.4.10
