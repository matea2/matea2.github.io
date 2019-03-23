---
layout: post
categories: blog
tags: Fedora awesome yum
title: Fedoraでawesome
date: 2011-08-28T16:36:00+09:00
---


Fedora 15 にawesomeをインストール。 [wiki] に書いてあった手順で、 yum repo から入れると簡単だった。

<!-- more -->

awesomeのyumリポジトリを追加。

```
sudo wget -nd -P /etc/yum.repos.d http://repos.fedorapeople.org/repos/thm/awesome/fedora-awesome.repo
```


でインストールするだけ。かんたん。

```
sudo yum install awesome
```


yum repo ってディレクトリに置いとくだけで良いのか。



[wiki]: http://awesome.naquadah.org/wiki/Awesome-3-fedora
