---
layout: post
categories: blog
tags: Fedora awesome
title: awesome size hints honor
date: 2011-09-10T16:52:00+09:00
---


awesome 小ネタ。ターミナルとかウィンドウのサイズ調整が細かくないと、タイルで並べたときに微妙な隙間ができて気持ち悪い。

[![size hints honor true]][size hints honor true link]


<!-- more -->

そんなときは、プロパティに *size_hints_honor = false* と書いておくと隙間なく並ぶ。ただ隙間がウィンドウ外からウィンドウ内に移動しただけなので、どっちが良いかはお好みで。

[![size hints honor false]][size hints honor false link]


設定は、 *~/.config/awesome/rc.lua* のRulesのところを修正する。

{% gist matea2/da805bb00a903cf77bae7347c96d7f28 rc.lua %}


# 使用環境

+ Fedora 15 (2.6.40.4-5.fc15.i686)
+ awesome 3.4.10



[size hints honor true]: https://lh3.googleusercontent.com/1H0FwqM4m0Tu4EzUh8NMJ9NdHOdpzowTny09oZsXXQ3V1-YVlBzwoGixUA4CschX0NY4B1uCLhDe5Mf--hRUf7FFQzVQdcsZ04gsB9rwBfCwnF19bCURe63ryKKoWLeoHe_GjkqXGA=w500
[size hints honor true link]: https://photos.google.com/share/AF1QipM0EDN_ooY1hFY6Xh8ziaNlRchBLY1-ff8E7JQPksMcwe9BdFjtCJw6z8gY-UV-zA/photo/AF1QipNuXoxpiDH12ZbSjhsHHQV4dm2qdAWDxNG5jnZp?key=QzV2dG91WmI2S1VPNDljUHo2YnBqZW1tT29mRmZn

[size hints honor false]: https://lh3.googleusercontent.com/3bxykf1B0RCP9s73cql6vFoz3mWeuU6EVxb8qhCQLTbVc-jqlB-ReECCVWTw3uEA2-Mi3qfQdzOqLkBOhvtt2inZ52OP2LaScHZ2TwFaBQkn3oWhDew9HZR-q0z7LNSE_N1tmSzStQ=w500
[size hints honor false link]: https://photos.google.com/share/AF1QipM0EDN_ooY1hFY6Xh8ziaNlRchBLY1-ff8E7JQPksMcwe9BdFjtCJw6z8gY-UV-zA/photo/AF1QipOMjh_Ip4bT_zmWu7M39uW1qAXnQI8e_RvLp4Ih?key=QzV2dG91WmI2S1VPNDljUHo2YnBqZW1tT29mRmZn
