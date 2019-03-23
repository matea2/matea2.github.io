---
layout: post
categories: blog
tags: Fedora i3
title: i3 window manager 試してみた
date: 2011-09-10T16:20:00+09:00
---


タイル型ウィンドウマネージャ [i3] を試してみた。Fedoraのyumリポジトリに入ってるのでお手軽。

<!-- more -->

見た目。ターミナルを開きまくったところ。左側をタブ化、右側をスタッキング化している。

[![i3 window manager screenshot]][i3 window manager screenshot link]


操作がわかりやすいのでタイル型のとっかかりに良さそう。デフォルトの設定では、ウィンドウの移動等が j/k/l/; に割り当てられているので、vi派はまず h/j/k/l に替えておかないとこんがらがる。

基本的な設定もシンプル。キーコードを書くので下のコマンドで調べる。

```
xmodmap -pke
```


ただシンプルな分、本格的にカスタマイズするのは難しいのかも？


# 使用環境

+ Fedora 15 (2.6.40.4-5.fc15.i686)
+ i3 3.e-bf2 (2011-01-19)



[i3]: http://i3wm.org/

[i3 window manager screenshot]: https://lh3.googleusercontent.com/_6HdbyFVu9lgQIvjFKArkqMzu2GaFnuwjScXOoFr59jOXJRhweKx4Y-PMIZ2oofqIeoRQy-CVoYUaDVHJH20MJmq43xQDMRitIG9ZMB9QKL0Dcq46RYaY9jnoKKgbU8tRcptD6CVzg=w500
[i3 window manager screenshot link]: https://photos.google.com/share/AF1QipPeXpbxkuIjZWRTO3l0JZtelvBC2zxPJNMZSvWUdPJkIdNFSd-wewL8VKbG5g9LCQ/photo/AF1QipOM1tOYX_P7s8RVJRwrGeQZpRhnDg3RaemzjmR9?key=VkhqdGRqVjdvTUhFU1FqRWdtSlhkOVpUZnNFWDFn
