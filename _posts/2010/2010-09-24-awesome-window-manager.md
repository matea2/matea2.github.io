---
layout: post
categories: blog
tags: Ubuntu awesome gdm
title: awesome を使ってみる
date: 2010-09-24T20:36:00+09:00
---


ウィンドウマネージャに [awesome] を使ってみる。ノートパソコンではタイル型ウィンドウマネージャが使いやすいかなあと思ったし、以前から試してみたいと思っていた。

<!-- more -->

ログインマネージャは *gdm* のままにしたかったので、gdmでユーザ名を入力したあと、下の方に出てくるリストからセッションを選択する。事前に設定を読み込む必要がなければ、リストからそのままawesomeを選べば良い。

自分はXの設定やらアプリケーションの起動やらがあるので *~/.xsession* にその他設定とawesomeの実行を書いておいて、リストから *User Definied Session* を選択。最後にパスワードを入力してログイン。

デフォルトの画面はこんな感じ。

[![awesome desktop screenshot]][awesome desktop screenshot link]



[awesome]: http://awesome.naquadah.org/

[awesome desktop screenshot]: https://lh3.googleusercontent.com/qxRYfjKxUlfg7dnE4urLO6s7aIhM071-bC_8ohzZ8FtNrSWTuVT9tAm7QKvIgtA82qGN7Gon9xBTFw026umMKM__JTj7Ds3EOXJSlXf24TEjlt3VmYYNndnaWymSCVXN66SeucIYeg=w600
[awesome desktop screenshot link]: https://photos.google.com/share/AF1QipNGettUqeebRW_SmTH7XH9RnARornOSR1rSlYX5WQe3nrN2XJIDmQTv-szQkgi1vw/photo/AF1QipPLFoQIORkjHWzZ41TToeiX50r1Nmzyn44qf6dM?key=Z2Y5dkVzTVRLZGtGVkZGVk1RanhGZkpsaEwyTFhB
