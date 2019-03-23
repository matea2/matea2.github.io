---
layout: post
categories: blog
tags: Fedora notification-daemon
title: notification-daemon テーマの変更
date: 2011-02-06T14:21:00+09:00
---


notification-daemon のテーマを変えてみたのでメモ。

<!-- more -->

下のように *gconftool-2* を使ってテーマを設定できる。

```
gconftool-2 -s -t string /apps/notification-daemon/theme standard
```


テーマの名前はデフォルトでは *standard* か *slider* があると思う。 */usr/lib/notification-daemon-1.0/engines/* にあるやつかな？

yum から notification-daemon-engine-nodoka をインストールしておけば *nodoka* も使えるようになる。


standard 外観

[![notification daemon standard]][notification daemon standard link]


solid 外観

画像では四角くなっちゃったけど、ほんとは角が丸くなってる。

[![notification daemon slider]][notification daemon slider link]


nodoka 外観

[![notification daemon nodoka]][notification daemon nodoka link]


ほんとはテーマをカスタマイズしてみたかったんだけど、簡単にはできそうにないなあ。壁紙は [朝日放送｜スイートプリキュア♪] からいただきました。


# 使用環境

+ Fedora 14 (2.6.35.10-74.fc14.i686)
+ notification-daemon 0.5.0
+ libnotify 0.5.1
+ notification-daemon-engine-nodoka 0.1.0



[朝日放送｜スイートプリキュア♪]: http://asahi.co.jp/precure/

[notification daemon standard]: https://lh3.googleusercontent.com/fpNvQn5PyFH7toZD6Pgnn8FBYugGZw-DK2LH-65vufQHNAHvO2sTg-fsthLxtpl1TBtjx08pDdY5Bj3j3uqWtquZr2FQAuqZc4FOuVyOesOUz6gRVSjIvRa8tgac3oxXnsnrdSAB6g=w600
[notification daemon standard link]: https://photos.google.com/share/AF1QipPrpCSAKAujMomU1E93nSCaG7BR4kPLb7HaT2itP1Qxi3TYKJ-c8Cu7GFgUU1VCyA/photo/AF1QipNOdoP7SpMuKWhEuYy9CZN1QPlnatjv3KsH2fb6?key=UktMTFNMUS1rSVdVTXJiUDFpQlJ5OVFfQnVqX01B

[notification daemon slider]: https://lh3.googleusercontent.com/Z0EejOln5E_1NBgAPXSGEPypikQiedI8qguHXp3VeTDydRZDpLAPG2-qAO6FsI8IV4KN22SMlVmj41hOybkYTzwYjShvj1MhB4f2JPk2UCEhpW47x_t7ausFfBgeMwI6lw38gSQEHA=w600
[notification daemon slider link]: https://photos.google.com/share/AF1QipPrpCSAKAujMomU1E93nSCaG7BR4kPLb7HaT2itP1Qxi3TYKJ-c8Cu7GFgUU1VCyA/photo/AF1QipPtKc1LKkanhmmbjN82XWKwusXE_Owx0PGPl1pQ?key=UktMTFNMUS1rSVdVTXJiUDFpQlJ5OVFfQnVqX01B

[notification daemon nodoka]: https://lh3.googleusercontent.com/plUQjvMAMTBim2pJoIa14WK66-GishcB8txjEwsv5iwEJsyoH9BGNax_5uTgDOJMMZEMcq5mX215w-o-PpXypawj-IZbfIdh05FauFZOnlROym07wXXZVAyni8tiFkrnYaFBEd9q5A=w600
[notification daemon nodoka link]: https://photos.google.com/share/AF1QipPrpCSAKAujMomU1E93nSCaG7BR4kPLb7HaT2itP1Qxi3TYKJ-c8Cu7GFgUU1VCyA/photo/AF1QipMeNWFjGrLQtcDk51HhCzffrou2TXWzZotioN71?key=UktMTFNMUS1rSVdVTXJiUDFpQlJ5OVFfQnVqX01B
