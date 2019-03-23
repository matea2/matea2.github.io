---
layout: post
categories: blog
tags: Ubuntu awesome notification-daemon
title: awesome 通知設定
date: 2011-01-02T20:08:00+09:00
---


Ubuntu 10.10 で、 [awesome] のポップアップ通知の設定をした。

awesome ではデフォルトでは右上の方に通知が表示される。私は基本的に情報は下の方に表示したいので、設定を変更してみた。

<!-- more -->

通知は *naughty* というライブラリを使っているらしい。ドキュメントの [naughty] のとこを参考に、 *~/.config/awesome/rc.lua* に以下の設定を追加した。

{% gist matea2/cd626825e50092b195a118e0d588bbb0 rc.lua %}


とりあえず表示位置と、あと幅も指定しておいた。

もともとこんな感じに表示されていたが、

[![awesome naughty before]][awesome naughty before link]


右下に表示されるようになった。

[![awesome naughty after]][awesome naughty after link]


ただ nm-applet からの通知が言うことを聞かないんだが。また別の設定なのかな[^note-2011-09-17]。どうでもいいけど「awesome naughty」とか検索してると、気分的になんか...アレだな...。

壁紙は [朝日放送 \| ハートキャッチプリキュア！] からいただきました。


# 使用環境

+ Ubuntu 10.10 (2.6.35-24-generic)
+ awesome 3.4.5
+ notify-send 0.5.0



[awesome]: http://awesome.naquadah.org/
[naughty]: http://awesome.naquadah.org/doc/api/modules/naughty.html
[朝日放送 | ハートキャッチプリキュア！]: http://asahi.co.jp/precure/

[awesome naughty before]: https://lh3.googleusercontent.com/gCjx5g47YOg4UD0xR4BG1emku3Qu_ak_Ka-kStHBfI2Yi_w0FhZhdpHUrPnXnoeGsEOxW4fPlcDrJSa6J9Fd3lI47sPohmpIiXfsh73JVI2xlu09k_Lu-N75BJwzMddcuWVS-N9zBQ=w600
[awesome naughty before link]: https://photos.google.com/share/AF1QipM61Sojj33aL2NzOBDKcHQ7nqOGa9Sx-rnAgQzkFDsR5ArblePoauMBiJja8EXM2w/photo/AF1QipN6bfoNPtE7cdJ90OTX0MeKyMf-BP6iYbFOTNgC?key=aHlScGdUYWN2RWNJUVF4RUt3QWxPV1NreHRRVjBR

[awesome naughty after]: https://lh3.googleusercontent.com/z-iDJAWn9Bk2bZNmtyo78KwUzJnVND45yxgyqnNOzZ3BB48ZsjzANELYWKt1Y0Tx59ZpIdIXQKV-PGQe06NlLn6LWnaC73nVzEs3DRzZX2UCziESZZNsYtQPSr63xLjryV4A2EkohA=w600
[awesome naughty after link]: https://photos.google.com/share/AF1QipM61Sojj33aL2NzOBDKcHQ7nqOGa9Sx-rnAgQzkFDsR5ArblePoauMBiJja8EXM2w/photo/AF1QipNpUNZPhoiCTAZcq9d4nhIpo399vWgoooJ_BKqh?key=aHlScGdUYWN2RWNJUVF4RUt3QWxPV1NreHRRVjBR

[^note-2011-09-17]: awesome naughty の設定を修正した。([記事][note-2011-09-17 link])
[note-2011-09-17 link]: {{ site.baseurl }}{% post_url 2011/2011-09-17-awesome-naughty %}
