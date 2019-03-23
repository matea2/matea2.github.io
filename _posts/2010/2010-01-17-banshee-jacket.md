---
layout: post
categories: blog
tags: Fedora banshee
title: Bansheeのジャケット画像
date: 2010-01-17T15:31:00+09:00
---


[Banshee] (1.5.3) で設定したジャケット画像は、どうやら特殊記号と日本語文字（複数バイト文字？）を除いてファイルに保存されるようだ。つまり、日本語が含まれていても、歌手名とアルバム名両方に英数字が入っていれば設定できる。

<!-- more -->

でもそうするとやっぱり英数部分が同じになるアルバムは同じジャケットになる。下の画像は、アルバム名副題の日本語部分が違うけど同じ画像になってる例（右上のペインを参照）。ファイル名は *soundhorizon-elysion.jpg* になってる[^note-2010-05-09]。

[![banshee screenshot]][banshee screenshot link]



[Banshee]: http://banshee-project.org/

[banshee screenshot]: https://lh3.googleusercontent.com/3kOldjFxMaZ0Wvm9Hqsz8WzzB4SE54CK82YcHJA_yweLqLic1My9_x-NH3QESbbJavoNGdw_mF7xNCsvpDK4erEVH6J-rxi9abQFIrHSyOL7VwEpMrtzjsgdRoLtSibCn_baV1jXuw=w600
[banshee screenshot link]: https://photos.google.com/share/AF1QipMVa2Eaa9VOOJT2xmAPbReHf9YZWqPWEzmKYdWCoFGqL6YNFu5tHgC-0AChlmM4dg/photo/AF1QipMG4ugFLXmVSx6WI31QtMzlhz9cWlm7sUOa1mRU?key=cDlYdUk2VlVGTS1MZ0c5QVRkZUN0OVBRT1FnMkdR

[^note-2010-05-09]: Banshee 1.6.0 で日本語名ファイルのジャケット画像も正しく表示できるようになった。 ([記事][note-2010-05-09 link])
[note-2010-05-09 link]: {{ site.baseurl }}{% post_url 2010/2010-05-09-banshee-update %}
