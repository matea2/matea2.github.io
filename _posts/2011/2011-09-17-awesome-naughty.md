---
layout: post
categories: blog
tags: Fedora awesome
title: awesome naughty 設定
date: 2011-09-17T20:10:00+09:00
---


以前awesomeの通知 naughty の設定した。でもなんかBansheeからの通知が、ジャケットの画像サイズそのままにでかでかと表示されていた。他にも設定通り表示されたりされなかったりして、どうしてかなーと思ってたけど、 urgency level ごとに設定すれば良いことがわかった。

<!-- more -->

[以前]は default\_preset を使って設定していた。これだと通常使う preset ( = normal ) のみ設定されて、それ以外は適用されないようだ。

[![naughty image (before)]][naughty image (before) link]


そこで normal, low, critical それぞれに値を設定するよう変更した。

{% gist matea2/feec5e2ef38227183552a4c15dc821cc rc.lua %}


これで他の通知と並んで表示されるようになった。

[![naughty image (after)]][naughty image (after) link]


壁紙は [朝日放送｜スイートプリキュア♪] からいただきました。


# 使用環境

+ Fedora 15 (2.6.40.4-5.fc15.i686)
+ awesome 3.4.10



[以前]: {{ site.baseurl }}{% post_url /2011/2011-01-02-awesome-notification %}
[朝日放送｜スイートプリキュア♪]: http://asahi.co.jp/precure/

[naughty image (before)]: https://lh3.googleusercontent.com/6dEP5HPF89_FkN5-dSAs3H06QlOeekZJqoh4pVAz1FlW2yFgpn8zihjrYS5WUb0G3XR7wEiVRLPuXn_ctGiE0Dz_fvfhN5pH0-aVa76awfLSgDSKWZn94BPobhbw3DuFmYyCTk6TEA=w500
[naughty image (before) link]: https://photos.google.com/share/AF1QipPHkW4Wq-muSzhDMKVF22iE2_drKpsSs4xD2EDLnL4UnSSPaCaXvZevaL3Fqb_lLg/photo/AF1QipN8KoNiAwpqQ9rZzjum3An3i850f0N-p63UgbXH?key=MnRpMnpubElGc2RlckxZTDVtWGFMVGx3TFUwSFVR

[naughty image (after)]: https://lh3.googleusercontent.com/mCcVCJJdQKAhnmHs_JDLVRnqtjkCo5IRX0Hj0z07A1gU5plU5MyqNHLOsUVfMaFZMmxOa1ILFQB9yGwJx858Ac03RY02zqdfljFcfkTAJF9YOzk4mOBaPzrfVV91zZ41bXqN5PodWw=w500
[naughty image (after) link]: https://photos.google.com/share/AF1QipPHkW4Wq-muSzhDMKVF22iE2_drKpsSs4xD2EDLnL4UnSSPaCaXvZevaL3Fqb_lLg/photo/AF1QipOXqwc5Wf9p06YMow6AKhndROiZuCja4x62e1PM?key=MnRpMnpubElGc2RlckxZTDVtWGFMVGx3TFUwSFVR
