---
layout: post
categories: blog
tags: Fedora Ubuntu quote-colors thunderbird
title: Thunderbird 6.0.2 で Quote Colors 0.3 を使う
date: 2011-09-27T01:03:00+09:00
---


Thunderbird 6.0.2 でアドオン Quote Colors 0.3 を使えるようにしてみた。

<!-- more -->

Thunderbirdでは、引用を見やすくしてくれるアドオン *Quote Colors* を使っていたのだが、 Thunderbird 5 以降になってから互換性がなくなっていた。

[![addon compatible]][addon compatible link]


そろそろ更新入らんのかーとアドオンのページを見てみたら、更新はなかったもののコメント欄に「いじったらふつうに動くよー」と書いてあったのでやってみた[^note-2012-02-22]。

**ただし、もともと使えないものを無理やり使えるように修正しているので、どこか問題が起きるかもしれません。各自の責任のもと注意して行なってください。**


まず[アドオンのページ]からファイルをダウンロード。

[![addon page]][addon page link]


ファイルの確認をしてみる。

```
file quote_colors-0.3-tb+sm.xpi
```


> quote_colors-0.3-tb+sm.xpi: Zip archive data, at least v2.0 to extract

xpiの実態はZipファイルらしく、解凍すると中身が出てくる。 *quote_colors-0.3-tb+sm.xpi* を適当なディレクトリに入れて、 `unzip` 。

```
unzip quote_colors-0.3-tb+sm.xpi
```


> Archive: quote_colors-0.3-tb+sm.xpi  
> &nbsp;&nbsp;&nbsp;&nbsp;inflating: chrome.manifest  
> &nbsp;&nbsp;&nbsp;&nbsp;inflating: chrome/quotecolors.jar  
> &nbsp;&nbsp;&nbsp;&nbsp;inflating: defaults/preferences/quotecolors.js  
> &nbsp;&nbsp;&nbsp;&nbsp;inflating: install.rdf  
> &nbsp;&nbsp;&nbsp;&nbsp;inflating: license.txt  

出てきた *install.rdf* の16行目にThunderbirdの maxVersion ってのがあるので、 6.0.x で使えるようにテキストエディタで編集。

{% gist matea2/4d3c7894008735a7158a6579257d7ead install.rdf %}


これを編集するだけで良い。出来たら圧縮する。

```
zip -r -D new_quote_colors-0.3-tb+sm.xpi * -x quote_colors-0.3-tb+sm.xpi
```


いちおう `unizip -t` で元のファイルと作ったファイルの中身を比較、 `ls -l` でファイルサイズがだいたいおんなじ感じか確認しておいた。良ければ作ったファイルをThunderbirdにインストール。

[![addon install from file]][addon install from file link]


再起動が要求されるので再起動する。

[![restart message]][restart message link]


これで有効になったはず。設定とかして引用部分を見て正常に動いているか確認しよう。

[![addons window]][addons window link]


画像はUbuntuだが、Fedoraでも当然ながら出来た。Windowsな人も、圧縮解凍するときに拡張子を変更すれば同様にできると思う。


# 使用環境

+ Fedora 15 (2.6.40.4-5.fc15.i686) & Ubuntu 11.04 (2.6.38-11-generic)
+ Thunderbird 6.0.2
+ Quote Colors 0.3



[アドオンのページ]: https://addons.mozilla.org/ja/thunderbird/addon/quote-colors/

[addon compatible]: https://lh3.googleusercontent.com/XdcbzybGmshAqNhlNUau3GVk9PGtq0sta_jcoweMpDAPALOQcXyxJANZbL_uzUUF53vC_osOsZ4qES1Cot9SxK8HXybf9qZZZUOM28a6Z7da3LPia__DrUUbHHOv4IePoHSsjYrbxw=w500
[addon compatible link]: https://photos.google.com/share/AF1QipPQFfch3TYQ0QKQ6P67zrlaLE_4asla7uGYPK8neQt0Hj9HV7NIGRH3EIsv9CD-Eg/photo/AF1QipPOJozIcl5pHTPOKjXeKaaoLoMJeplqIyl3w2L1?key=ZWpSOU55NGxWVmFETXVwR1NETXN5alJ3RHRUQy1R

[addon page]: https://lh3.googleusercontent.com/H8zbOM87MHoTGZo2BDVT0Dko7MUCjX1DcH8tZZNhabrbX8Bc8rAsLbGykI-ki66ClaoGCpMhm1ead23VDpBSdX6P2hqGzm9geD997HdypEw-97aJP_zNZeB1rDtQKzbtfpeKMqspJg=w500
[addon page link]: https://photos.google.com/share/AF1QipPQFfch3TYQ0QKQ6P67zrlaLE_4asla7uGYPK8neQt0Hj9HV7NIGRH3EIsv9CD-Eg/photo/AF1QipPSM-KE3O80k7ovUUReRzuNZZ58WoNOzoFWlToF?key=ZWpSOU55NGxWVmFETXVwR1NETXN5alJ3RHRUQy1R

[addon install from file]: https://lh3.googleusercontent.com/xuZfmIY4HsKYwmwHrS66baV3tOPTuHuPb0uPRYWsS_DAdozlUocrbGTaQ4YuaV_G5ePUWWHl00abe8kPvy2xjrmqEH_3xJxV6ujwzcjrt8C_Lr4rN9rN31Nr56WecQs8ctNH2C5kAA=w500
[addon install from file link]: https://photos.google.com/share/AF1QipPQFfch3TYQ0QKQ6P67zrlaLE_4asla7uGYPK8neQt0Hj9HV7NIGRH3EIsv9CD-Eg/photo/AF1QipMUkDcTqDAoOeZjmpu3pQnunZA4Z2hkAdH92sF1?key=ZWpSOU55NGxWVmFETXVwR1NETXN5alJ3RHRUQy1R

[restart message]: https://lh3.googleusercontent.com/l7aO9uWFOwPCbtOHBONEZ5Lq4x9Rcb3GoNgmGrdu1X4e_ErJiBA0btLv6K4LKTp5MJS8A0MMGhAMdFzp-AksW9YXavRjyCc8ato0m1dCMw4nEngx7gipjfeyO9xfzmT_pVykSVFVDg=w500
[restart message link]: https://photos.google.com/share/AF1QipPQFfch3TYQ0QKQ6P67zrlaLE_4asla7uGYPK8neQt0Hj9HV7NIGRH3EIsv9CD-Eg/photo/AF1QipOlfmsqFfnxm10qYjgd2VlHQ5YzLzC_FgJsS1QS?key=ZWpSOU55NGxWVmFETXVwR1NETXN5alJ3RHRUQy1R

[addons window]: https://lh3.googleusercontent.com/HCLI3QuizAYwcIqLFPS67vI4z_nG1vhoRaiGy-hzribMow7PtaqolxET1DeBzTyVWVNKr_KF-kAcy7hHjvPasgNHHPDL8GnFPHUpxpySpQyTwO_iUMeVnfJfClP86URNFAOjWmEd3w=w500
[addons window link]: https://photos.google.com/share/AF1QipPQFfch3TYQ0QKQ6P67zrlaLE_4asla7uGYPK8neQt0Hj9HV7NIGRH3EIsv9CD-Eg/photo/AF1QipNX6j76r544kTKCG1VR5_vQ3pMPul-IJ_Q-XXod?key=ZWpSOU55NGxWVmFETXVwR1NETXN5alJ3RHRUQy1R

[^note-2012-02-22]: 拡張の互換性が改良された Thunderbird 10 以降はどうなったのか知らない。日本語版を提供しているページに対応版があったのでそれを使うのが簡単そう。([記事][note-2012-02-22 link])
[note-2012-02-22 link]: http://www.geocities.jp/chimantaea_mirabilis/QuoteColors/
