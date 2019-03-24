---
layout: post
categories: blog
tags: Ubuntu awesome xcompmgr
title: awesome 透過設定
date: 2010-09-25T23:55:00+09:00
---


[awesome] で、非アクティブウィンドウを透過する設定をした。以前からやってみたかった...。

<!-- more -->

まず `xcompmgr` を起動しておく。

```
xcompmgr &
```


壁紙は `hsetroot` で設定。 root pixmaps が変更できるものなら良いっぽい。

```
hsetroot -full 壁紙のパス
```


このへんは *~/.xsession* なりに記述しておくと起動時に実行してくれるから便利かも。

で *~/.config/awesome/rc.lua* を設定。最後のほうにある client.add\_signal ってところで *opacity* を記述すれば良いようだ。非アクティブのとき 0.6 くらいに設定。

{% gist matea2/871fda813ae257a4cb127b39030160b7 rc-client.lua %}


これでできたー！ 画像はこんな感じ。

[![awesome desktop screenshot]][awesome desktop screenshot link]


壁紙は [朝日放送 \| ハートキャッチプリキュア！] からいただきました。



[awesome]: http://awesome.naquadah.org/
[朝日放送 | ハートキャッチプリキュア！]: http://asahi.co.jp/precure/

[awesome desktop screenshot]: https://lh3.googleusercontent.com/xijTQb_DEp_RIpRB5hvUsKLHX7EnKkN_xgL1kR0V8WBdu9xpgxmS1YJ9V2AsuGiQoHaiSUmZPdjF2rhZ5m-pay6M8CbNTBbUPQoMaFh5BVDEL_-teYTPu5oIjXObxMRqzTnXoLcltg=w600
[awesome desktop screenshot link]: https://photos.google.com/share/AF1QipP7JDDsgVszbRc06HbvqRHsvdHWJlL56bxX3SR1rZlCyTZP02qAdLMLA44oiBSf6g/photo/AF1QipPte1xSC2VDIj9LeRUMxAzjEnyu21jT1fkMI9TK?key=QnBtZTdIal84Y3dTZXdRYUg2aXpLZ1M5bjYxTnZR
