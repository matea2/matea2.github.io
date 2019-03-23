---
layout: post
categories: blog
tags: Fedora Ubuntu gdm imagemagick
title: gdm のスクリーンショットを取得
date: 2011-01-30T19:10:00+09:00
---


gdm のスクリーンショットをとりたかったので調べてみたが、コンソールから画面を指定すれば普通に取得できるようだ。

<!-- more -->

PCを起動するとログイン画面になるので、 *Ctrl-Alt-F1* なんかでコンソールに移動してログイン。私は ImageMagick を使って取得した。取得には管理者権限が必要みたいだ。

だが単純に実行するだけだと gdm が休止してて真っ暗な画像になる。そこで pause オプションを使って取得するのを待ってもらって、その間に *Ctrl-Alt-F7* なんかでまた gdm の画面に戻る。それで取得できた。

```
sudo import -display :0.0 -window root -pause 5 gdm.png
```


これなら他のログインマネージャでもできそう。 SLiM はもともとスクリーンショットが取れるようになっているのでこんなめんどくさいことをする必要はないが。


# 取得した画像

Fedora

[![fedora gdm screenshot]][fedora gdm screenshot link]


Ubuntu

[![ubuntu gdm screenshot]][ubuntu gdm screenshot link]


# 使用環境

+ Fedora 14 (2.6.35.10-74.fc14.i686)
+ GDM 2.32.0
+ ImageMagick 6.6.4-1

+ Ubuntu 10.10 (2.6.35-25-generic)
+ GDM 2.30.5
+ ImageMagick 6.6.2-6



[fedora gdm screenshot]: https://lh3.googleusercontent.com/xu5jTA3WpTIGGWnkNtoYkLAFBOo_f71IyVDZEfXRGR2y0S0B3N8B31tjlcq8sWfBA8v3FYtKgGITOXvnu_t4fcjr4eUnTiTjWjVzoYsgNKblvXO7ng2WVJt31Q5qg98j69NwGpfiZw=w600
[fedora gdm screenshot link]: https://photos.google.com/share/AF1QipPQ7lu_1T4cuJ8kDP-9G8zTtouWLVnBSltczeGvx4swdcJZ8eTXjd15YLy9pWnedw/photo/AF1QipMc6ZdpPdUj-vRrQQOMNrWYEdNfc2rNlOEgeeQ1?key=VWc2Tmpmc0lEWGRZZlRIVzBvQjN2LTNvbnp3V1Z3

[ubuntu gdm screenshot]: https://lh3.googleusercontent.com/MGRcc8HgqFeU84CwvD8bpwzY4ngovt6P6ytIQnk67uE_uT6sl8jifqomKzhLsjrjUuxbJBlAYHUwmku6Px-0Ik-2LG4pa7Bgl-i2H0hjXC4cikYYaVkOqV3i9rL-GQXLTtvg5FJ9Rg=w600
[ubuntu gdm screenshot link]: https://photos.google.com/share/AF1QipPQ7lu_1T4cuJ8kDP-9G8zTtouWLVnBSltczeGvx4swdcJZ8eTXjd15YLy9pWnedw/photo/AF1QipNhacbSA5xhp2QBZCA9LLI-A9FgfrADpzbzeVx8?key=VWc2Tmpmc0lEWGRZZlRIVzBvQjN2LTNvbnp3V1Z3
