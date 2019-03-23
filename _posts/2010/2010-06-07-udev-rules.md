---
layout: post
categories: blog
tags: Fedora udev
title: udevルールを微修正
date: 2010-06-07T11:54:00+09:00
---


以前スキャナーの設定で書いたudevの記述が、起動時に怒られてた。

> will be removed in a future udev version

らしい。言われるがまま BUS を SUBSYSTEM に、 SYSFS を ATTR に変更してみる。

<!-- more -->

マイルール */etc/udev/rules.d/99-local.rules* で、

{% gist matea2/6e8f5f0e0c4a384b4ba52bef96b26c57 99-local-old.rules %}


となってたのを、

{% gist matea2/6e8f5f0e0c4a384b4ba52bef96b26c57 99-local-new.rules %}


に修正。とりあえず文句は言われなくなった。
