---
layout: post
categories: blog
tags: Ubuntu firefox keyconfig
title: Firefox keyconfig
date: 2012-01-29T20:45:00+09:00
---


ひさびさFirefoxアドオンを探していたら、 *keyconfig* が更新されていたので使ってみた。以前使ってみようとは思っていたが、使用していたバージョンのFirefoxに対応していなかったのもあって見送っていた。

<!-- more -->

[Dorando] から *keyconfig.xpi* をダウンロードしてファイルからインストール。現在最新版の 20110522 はFirefox 10.0 にも対応している。

インストールしたら、アドオンの設定画面からキー設定を編集できる。

[![keyconfig menu]][keyconfig menu link]


新しいキーを追加または既存のキーを編集して、自分の好みに設定。

[![keyconfig entry]][keyconfig entry link]


以下のページ遷移のキーを追加してみた。うむこれは便利[^note-2012-07-01]。


次の行にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-line-down.js %}


前の行にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-line-up.js %}


次のページにスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-page-down.js %}


前のページにスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-page-up.js %}


先頭にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-top.js %}


末尾にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-bottom.js %}


右にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-right.js %}


左にスクロール

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-scroll-left.js %}


次のタブに移動

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-select-next-tab.js %}


前のタブに移動

{% gist matea2/1e6103bbbdec03e75767b4eb6cc1a0e3 prefs-select-previous-tab.js %}


# 使用環境

+ Ubuntu 11.10 (3.0.0-15-generic)
+ Firefox 9.0.1
+ keyconfig 20110522



[Dorando]: http://mozilla.dorando.at/

[keyconfig menu]: https://lh3.googleusercontent.com/cpeM7kEqDKHMhrCRN30vVf4xOpy2Co5P2ue0PjjeGik0v3hiW9mC8lZ0aOwESDmmSXJ87n9KLihQV0_Yb4EWGqywZ0qsVKGeU3C25RZ7jCtjQ5tZKL42MeTtF96oxV8mHQtKmYb6Tw=s400
[keyconfig menu link]: https://photos.google.com/share/AF1QipOmY35aXTzl5slip3amqemDkBBnpltllB_g2OyUMhAIIR-EROHSMCTLg_igu84NAQ/photo/AF1QipMB5BE4Of6LVRWw_oLQS0GeaDT-ktgF8Sda4Fzx?key=dWpuX1BUbHYzamdGcXpaVTl4cktoUDJkdzNDN1N3

[keyconfig entry]: https://lh3.googleusercontent.com/0z27j_B-BorEy9npK8JXNvof3N2MmYosvVutQpjYpJ2-E2Bw7hjIjFprqllcxDvp0UO33owML4qOX4VhoflopUqojTACgUaJCLfuYJF-vLOBAAFg0nMrRwopjBESk_3RpuHTg6NaQA=s400
[keyconfig entry link]: https://photos.google.com/share/AF1QipOmY35aXTzl5slip3amqemDkBBnpltllB_g2OyUMhAIIR-EROHSMCTLg_igu84NAQ/photo/AF1QipNEt1HbFdJ9Jpec0hCAnLoHNPpW_1AbykBjaJ82?key=dWpuX1BUbHYzamdGcXpaVTl4cktoUDJkdzNDN1N3

[^note-2012-07-01]: 追加の設定を書いた。([記事][note-2012-07-01 link])
[note-2012-07-01 link]: {{ site.baseurl }}{% post_url 2012/2012-07-01-firefox-keyconfig %}
