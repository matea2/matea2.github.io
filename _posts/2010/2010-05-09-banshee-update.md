---
layout: post
categories: blog
tags: Fedora banshee
title: Bansheeがアップデート
date: 2010-05-09T15:48:00+09:00
---


ミュージックプレイヤーの [Banshee] がアップデートされて、バージョンが 1.6.0 になった。 1.5.x での更新が適用された安定版。

<!-- more -->

まず何よりありがたいのが、日本語名のアーティストやアルバムに対応したこと。アルバムのジャケットやコンテキストペインでばっちり表示されるようになった。自動取得もなかなかのようで、 [少女病] の *慟哭ルクセイン (同人作品)* のジャケットも取得されてちょっとびっくり。自動で取得できない場合はもちろん手動で設定できる。

[![banshee screenshot]][banshee screenshot link]


以前このブログで日本語名のジャケットが取得できないと不満を書いたが、これで問題は解消。ジャケット画像のファイルは、 *~/.cache/media-art/* に入って、アーティスト名・アルバム名を使わずハッシュ値？を使うようになっている。

ほかにも目につくところでは、アルバムのグリッド表示やイコライザー、コンテキストペインのYoutube表示など。日本語化もほぼ完璧。

あとは、私がBansheeを使う大きな理由の一つ、豊富なシャッフル機能のバリエーションも強化されているのでありがたい。



[Banshee]: http://banshee-project.org/
[少女病]: http://www.girldisease.com/

[banshee screenshot]: https://lh3.googleusercontent.com/7buiMjH9N3pFZfXEyXKfJmMSAPZ0DlZcIn7bJRCgXiAuxSO_GxZScaOsSJs7VzusPsXmE0H2lK5L8Sia0IvAhzY3m1YwEwbrZHdTPuVsn1dyWrpiSetHuWJ-B64roP0VGrLSkUy_Uw=w600
[banshee screenshot link]: https://photos.google.com/share/AF1QipNFEqjTvyGyWXY5ZuOSAesz-KR7fegcA7gU2CG-zRCKLgvA9qbN4Zw0jplnaPh35Q/photo/AF1QipN8HPYLtZo8GHBaVVnEoiqCxNZZFLY7UylU0rtN?key=TFRBc3ZZUFVSbHFlVlBlUHV1bzd4ZUdQQzBGTTFR
