---
layout: post
categories: blog
tags: Ubuntu デバイス
title: dynabook SS SX/210LE を SSD に交換した
date: 2011-09-03T16:40:00+09:00
---


めずらしくおかたい話。もらいものの dynabook SS SX/210LE のハードディスクがおかしくなったようなので、SSDに交換してみた。ついでにメモリも増強。結果動作はずいぶん早くなって、そこそこ普通に使えるレベルになった。

<!-- more -->

用意したSSDは、Transcend TS32GSSD25-M。2.5インチでIDEのSSD。Amazonでてきとうに選んだ安いやつだが、それでも8000円弱とそこそこのお値段。メモリはBuffalo DN333-A512M/E。PC2700 (DDR333)ってのであれば良いのかな。2000円ちょい。

交換は[ここ][cite-squops]のページを参考にさせてもらった。


# SSDの交換

とりあえずドライバ1本用意。あとは、ネジがいっぱいなので、容れておくケースとかあると良いかも。

[![pc and tools]][pc and tools link]


まずはバッテリとか余計なものを外す。そんで裏面の *B6* と書いてあるネジを外す。

[![eject battery]][eject battery link]


次はノートを開いて、キーボードの少し上の、左右に1箇所ずつあるカバーを外す。するとネジが出てくるので、これも外す。

[![screw cover]][screw cover link]


これでキーボードが外れるので、モニタの方にスライドさせる感じでひっぺがす。右側にハードディスクが入っているので、くっついているネジ2箇所を外す。

[![keyboard open]][keyboard open link]


ケースをそっと取り出して、IDEケーブルを外す。このときぺきっと外しちゃってケーブル大丈夫か心配になったので、慎重に。

[![disconnect hdd]][disconnect hdd link]


ケースに4箇所ついてるネジを外したら、SSDに交換。あとは順番に元に戻したらOK。


# メモリの交換

メモリの交換は、裏の *注意* と書いてある蓋を外す。

[![memory cover]][memory cover link]


外したら、新しいメモリを斜めに差す。

[![insert memory]][insert memory link]


ゆっくり倒して、左右のフックがかちゃりとメモリを抑えればOK。

[![connect memory]][connect memory link]


あとは蓋を戻すだけ。


# 動作確認

さて、パーツやら線やらつないで電源を入れてみる。BIOSを見ると、メモリは無事認識しているようだ。

[![bios photo]][bios photo link]


ハードディスクは...書いてないか。うーん、まあそのままUbuntuインストールに突入。

[![ubuntu install]][ubuntu install link]


進めていくと、パーティション設定の画面。無事SSDも認識されているようだ。

[![ubuntu partition]][ubuntu partition link]


問題なくインストールできました。 おしまい。

[![ubuntu login]][ubuntu login link]



[cite-squops]: http://www.geocities.jp/squops/dynabooksx/03.html

[pc and tools]: https://lh3.googleusercontent.com/Kh0RTLpAJ8LxgFxge9Ze5qBM9ObmmNh88mZlE5-Kr46hD9tn0uaCSPNOHlA2l1o9p9M0cfJOZQ3s9TSLlebarNztHjDKlDo76a2Ii0zOfugjNhG5N5Q4F_Y_DeGRPNFuNVP_W24WOA=w600
[pc and tools link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipMqKY6J_VIXtD9b-3mkQHyGOeM5mL6505L0IGD1?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[eject battery]: https://lh3.googleusercontent.com/h5wGi8YAjLJ7OfPL_-hYXyJ9Dzm0Jkd8HQZckZOebX2Za6Po-CBor0WxHyN-o9WX_FDWuDzhti2kMgHvocNfOP4wS5ajnPg6Y7YignbQElk42YcZGG-fex0q4_fOYmm_rJs1x0iJmw=w600
[eject battery link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipN8VryQdSwLr_pSdbZG9fwKzIoLG24LsCjEEBRa?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[screw cover]: https://lh3.googleusercontent.com/NgwkA_jG615ic47krP3HMUbSyZzzSRejLmcWz6f_m2Ro1dfhuuxJB_yraFAZ6EIAoFn1iuaFn4rEna4xylZsOVLM7jgIkfPCiRk6hFbFUtzk-OEx_Wwf9iWj6X8VUtBgniRyGhqJ0A=w600
[screw cover link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipOOy2YLw2mj_eb6E_SCT91UONj0Jf_ZBd7HByJp?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[keyboard open]: https://lh3.googleusercontent.com/p9vbKqdJpk7hcYGf12g_k2RnfK8gtlW8FA_oCvYaxin96s2qegxLIgTrn03x8fbSA2iA09dYhBFohnPKC3yn75I30bOTGheTgs1IktLZMeMBIRc1I7SfcZyj_cv20oM5pLJR6CDNUw=w600
[keyboard open link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipPFxFMna8PFu1QD_s6zeiY_2-YcWs2hq4awjjty?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[disconnect hdd]: https://lh3.googleusercontent.com/Fy4h2Fp2-fKsSURGmR4PWEQ55wBcQmAfQp_plP6uboYCK6-S5OSe96TtGwjtFHaKwwVw5yup_5-3ZP82vJSH6O4u30h6-wuYbNqNvetXWMRxlbOYHuR1W03akSQX9sX58hWZscZ41g=w600
[disconnect hdd link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipOdt2Tjlj_4bG7q7wbzaaZSY3xOo9PPiJS11PgV?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[memory cover]: https://lh3.googleusercontent.com/EoxenRGrnKeqwYlebZ3-wh8GVpdr6TMghTS6t5CK1O9D5ptiuOKgcNuum5gBFhocSs03wtLjZudv2rgqZQjYKDKr2keaC1fP4MGxdwNPDF0leNzqtjUWDFl9cTEJyuLD0ZBSI7xG9A=w600
[memory cover link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipOkB3cPpUDCbkZzkHU5CwckwSnWNILId7MX7Sy_?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[insert memory]: https://lh3.googleusercontent.com/gTq6KuFBJV7xshYqGTYoQQ6x2NjW6WIfDtqkdnE6BhWwbv9lGVQAoBmRl3Y3im6zpY0v3rc7W5MBkptppX34-LPem-xQ2kj-at75idRxsXi-1wnCRbUxy0O59B-AkfEOixevLYTmig=w600
[insert memory link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipPYItjtFbZ1_L0WG8zkWddzfT8EnVVDEN18-bwK?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[connect memory]: https://lh3.googleusercontent.com/hbJp1evLhYXF-TpHlcBRgm8GUm9vyKgndRDfQLcNz1hMpwJGOyAFF2aPDv_MvTzW7N9glWwHtSq5JYVZ88UFJrhUrrMe73m3xNW4v3V6IntC7nd8_yF1xvKrsqVwwyUoIgaRkngkXg=w600
[connect memory link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipPIOBQyM8OwWPGNcJd5tQkh7z8DG4dOHQF2cWxJ?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[bios photo]: https://lh3.googleusercontent.com/hI4y47lbtk3rEJv9VDo2e-oA0dXH0xRAsHg4QuDI2jLNJ_jp9gEk4YyJkPo0A5HzHOlKy0JBvJqsNLo_vrWevqm6boZigDO_7UCEoAnenRcRZVxh_M8FxAuN4i4HbubNAhuDo0rBRg=w600
[bios photo link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipOcbQMQu3r6uBPyzdlZn3i2YoFCvjHggqM1Ttkw?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[ubuntu install]: https://lh3.googleusercontent.com/lvS2_fx25aK_6-FtK_zwku6ycORZLZngspG-FRSg2ahRlSklKoOQz3I_fTqEhx7a-QLt-Yn8Am6rmeVgCT4JvqgVoGkqVNdwY0U1fDxK0Qy_bsTlKr0ehDVNss-sucMGW50skxqwYQ=w600
[ubuntu install link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipNnCw-XPL7oMXqea-5ZC83LeP3-N9hicbvMVXOp?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[ubuntu partition]: https://lh3.googleusercontent.com/A0iHiWewuVi5N3-TIlcnUhxlT1hbDPHPVPA1Xe9xLES-Eh8xzqwDfFzgqVMYSXABdMH_tRek-McyF3vW0Hq0sTcZUrIfC47Letux3J8URe8ad_5UkZncjL8HcNwLNjY-gMzTbg6oKg=w600
[ubuntu partition link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipOvMJYhuTkTGwTA0UO2fuco9azRexrW96aWj9Zc?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR

[ubuntu login]: https://lh3.googleusercontent.com/czYv-UZkP5ePqdHMkLK8bquRqHWyYEtfLsqKmy3GrQaZiJRz28TBkJLw15XLtdtvrJIrKsPVvQRLXh3aVTjjiIxjJyeIRQrHnYY_GeWs_KLCRwoRLacs4Rr_BNF2P1T6BbQSuWRAdA=w600
[ubuntu login link]: https://photos.google.com/share/AF1QipMWcJAG_RmNCRBRF6QACkpU7yjjnImGEM0ExIb5tPnmk3diucaDG4oSmVQK0Lc5yw/photo/AF1QipM91mMCCJA4PeGd2uPxiIsdq-YNOVSl4oM7_FSG?key=NkRaY09oTGM5TEljMUlkS1dfeC03NV9WRVFoMjVR
