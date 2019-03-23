---
layout: post
categories: blog
tags: Fedora network-manager 無線LAN
title: Fedora 14 で WLI-UC-G300N
date: 2010-11-23T18:03:00+09:00
---


[Fedora] 14 で無線LANを使えるようにした。デスクトップ機だけど、USB無線LAN子機の [Buffalo] の [WLI-UC-G300N] があまってたので利用してみた。

<!-- more -->

とりあえず差し込んでみると、デバイスはそのまま認識しているが無線の接続はうまくいっていないようだ[^note-2011-01-08]。ということでまず有線からドライバをインストール。 WLI-UC-G300N は、 [Ralink] の *rt2870* ドライバを使うらしい。これは [rpmfusion]-free のレポジトリから `yum` でインストールした。

```
sudo yum install rt2870
```


で rt2870 と依存性関連で kmod-rt2870 がインストールされるはず。

それから、デフォルトで読み込まれる rt2800 が動くといかんので、読み込まないようにする。 */etc/modprobe.d/blacklist-wlan.conf* とか作成して、そのファイルに blacklist を記述。

{% gist matea2/2ff6bb4d273e3edd14d7e303144260e2 blacklist-wlan.conf %}


これで再起動すればうまくいった。いろいろいじった上で使えるようになったので自信がないが、たぶんこれだけで良かったと思う。

あとはネットワークの設定をしておく。私は [NetworkManager] を使っているので `nm-applet` から設定。設定するときは管理者権限で動かしておいたほうが良さそう。

```
sudo nm-applet &
```


で `nm-applet` のトレイアイコンをクリックして、目的のネットワークを選ぶ。出てきたダイアログに正しいパスワードを入れるとそれだけでつながった。

[![nm applet dialog]][nm applet dialog link]


設定は Auto〜 で登録されているので、あとはお好みで修正しておけば良い。トレイアイコンの右クリックから「接続を編集する」で設定できる。私は「自動接続する」と「全てのユーザーに利用可能」にチェックいれておいた。「全てのユーザーに利用可能」はパスワードを入れるとチェックできるようになるっぽい。

[![nm applet config]][nm applet config link]


# 使用環境

+ Fedora 14 (2.6.35.6-48.fc14.i686)
+ nm-applet 0.8.1
+ Buffalo WLI-UC-G300N



[Fedora]: http://fedoraproject.org/
[Buffalo]: http://buffalo.jp/
[WLI-UC-G300N]: http://buffalo.jp/products/catalog/network/wli-uc-g300n/
[Ralink]: http://www.ralinktech.com/
[rpmfusion]: http://rpmfusion.org/
[NetworkManager]: http://projects.gnome.org/NetworkManager/

[nm applet dialog]: https://lh3.googleusercontent.com/-i_fKCdov2EkvtSyoPu36xPFwm8u6c0x2036fVfcNu2d02tO23cpqyvrcdsKB0h9wvpnOUJ9u3wF1p-dUKp1SLnVWbtY2MrkwPIF3PB9l7E0alucrkTQu41svp3bu6Gg0cF4Fcl6AQ=w400
[nm applet dialog link]: https://photos.google.com/share/AF1QipO3NgFWOxmpeVU_SNMD99LJN7lYKiV_l7tdb_cxphAqctxkx5weMLeNhBG6Sv5lKQ/photo/AF1QipPF-unJX4GsrakEsfFQN1B8yzASvPP9KvxBeVBs?key=UDM2SlNaOU81SGV0WVNxZUNuaWhzeHN0dXBBS3l3

[nm applet config]: https://lh3.googleusercontent.com/0p4ZXt1MW3SLBrVTvyMMs0MWnCa6csjCitxvp6N5nGfQJj-pEeof_hcyzqUjGTo1TKVcL_0_U-ORvbmpVCApueosxWLCS4M_8mj1T9uvZEb_DAaR_fkUJ-TC-LtO7cnOPipoayKaEg=w400
[nm applet config link]: https://photos.google.com/share/AF1QipO3NgFWOxmpeVU_SNMD99LJN7lYKiV_l7tdb_cxphAqctxkx5weMLeNhBG6Sv5lKQ/photo/AF1QipMZDGaxEeZAMd17TVLs8y8Qi7k3hmMv7sx7Pl2O?key=UDM2SlNaOU81SGV0WVNxZUNuaWhzeHN0dXBBS3l3

[^note-2011-01-08]: WLI-UC-G300N の設定はたぶん不要になった。([記事][note-2011-01-08 link])
[note-2011-01-08 link]: {{ site.baseurl }}{% post_url /2011/2011-01-08-fedora14-wli-uc-g300n %}
