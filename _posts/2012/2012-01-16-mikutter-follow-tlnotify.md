---
layout: post
categories: blog
tags: Fedora mikutter
title: mikutterでフォロー通知をタイムラインに流すプラグイン
date: 2012-01-16T03:00:00+09:00
---


以前作ったmikutterでフォロー通知をタイムラインに流すプラグイン。いちおうこっちにも載せておこう。

<!-- more -->

mikutterには標準でポップアップと音声の通知があるけど、けっこう見逃しちゃう。これはタイムラインに載るのであとからでも見返せる[^note-2012-02-05][^note-2012-03-31]。

[![mikutter timeline]][mikutter timeline link]


下のファイルをmikutterのプラグインディレクトリに入れれば動いたり動かなかったり。たまに全アンフォロー通知が来るのでびびる(けど実際にアンフォローはされていない)。mikutterがうまくフォロワー一覧を取得できないとアンフォロー通知がだばっと来るのかな？

{% gist matea2/1493487 follow_tlnotify.rb %}



[mikutter timeline]: https://lh3.googleusercontent.com/bzZTpwHYv-LLFiOUHVuIsNk4fZGHWZOh9OqO2DTNMdrDqDB1oOcHeSGVE5QM1ZHPtdEsZ-hyl_76s07gbpo5Ox0TpMuprG8Cn_MDpEaWgoR3lo_cMopK_tgGaHHaN5fTKTkiR7eJww=w800
[mikutter timeline link]: https://photos.google.com/share/AF1QipOJ7AJvh7EcXSI5OiNUCNItb0ke3xMGDAnCx2EJk0kEoMhpA-OIPdYrcPZ0MxzmpQ/photo/AF1QipOPTRxVGD5owUECvoGZ9h__jiduSgpI8k_jmUpj?key=UEFUYVA5aHM2bVJwT1hGUTAyYkZqVE42dzN5RGJ3

[^note-2012-02-05]: 見た目の画像を追加しといた。
[^note-2012-03-31]: rev707あたりでアクティビティタブにフォロー通知が流れるようになったので、あまり必要なくなったかも。
