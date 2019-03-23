---
layout: post
categories: blog
tags: Fedora firefox tab-permissions
title: Firefox Tab Permissions
date: 2012-01-29T17:43:00+09:00
---


FirefoxでJavaScriptとかプラグインが重いってとき、タブの右クリックメニューから機能をオフにして使っていた(Tab Mix Plusの機能かな)。でも最近、基本的には無効にしておいて、必要なときに有効にしたらいいんじゃないかと思い始めたので、アドオンを入れてみた。

使ってみたのは、 [Tab Permissions] というアドオン。NoScriptとかもあるけど、重いと聞くしシンプルなのが良かったので。

<!-- more -->

設定画面。各機能をチェックボックスでオンオフするだけ。下段の「パーミッションボタン」ってのは、一括で切り替えられるボタン。そのボタンを押したときの挙動を設定できる。

[![tab permissions config]][tab permissions config link]


タブごとの機能の切り替えは、ツールバーのボタンで切り替えられる。ツールバーのカスタマイズから追加できるようになっている。

[![tab permissions toolbar]][tab permissions toolbar link]


またボタン以外にも、タブの右クリックメニューから設定できる。「(新規タブ)」ってのは、デフォルト設定の切り替えのようだ。

[![tab permissions menu]][tab permissions menu link]


# 使用環境

+ Fedora 16 (3.2.2-1.fc16.i686)
+ Firefox 9.0.1
+ Tab Permissions 11.01.11.01



[Tab Permissions]: https://addons.mozilla.org/ja/firefox/addon/tab-permissions/

[tab permissions config]: https://lh3.googleusercontent.com/JfuVH1-5VMuQJk8tDig2GUu4tZDP9bur9j3m0E4if8r6dhF2A7R0ZxruOVoIktWYdZ4OskFdjkzhi4_7CeFPRAg12luaVASdzsfXi5QlRBAmYUWMC_v-G2pXqjy43omu4_t7ayifew=w300
[tab permissions config link]: https://photos.google.com/share/AF1QipOO2WKa_g3jpJXhCUmAhqGi3Fy6ELCze0DiedK5aWeK_zS3Uy6yzio1cI59BFnorw/photo/AF1QipMx1R440tZeh2ihOfd1mdzUXwX-uCYCdl-xgnbQ?key=enNqWHpUa2FKMlNvNV8xZm1kZjMxSnBaeVJlNzN3

[tab permissions toolbar]: https://lh3.googleusercontent.com/6rS-by0vFTjGkH9pJYhT8w33fx2_Ktv1vZQBZAw6k4Pyvf5VGFfiF1g366qo_q6_wO9nwNpt-lURq3-0K0QJwnOkO1UjXXXUR1Z4hV-I5Fm1eHKr6ms2Dkt5a6da4QmvTjGDGOyfHg=w400
[tab permissions toolbar link]: https://photos.google.com/share/AF1QipOO2WKa_g3jpJXhCUmAhqGi3Fy6ELCze0DiedK5aWeK_zS3Uy6yzio1cI59BFnorw/photo/AF1QipPTl6PjvOmAT8lXBdbADO8hGFaiUZL27kK2SQqO?key=enNqWHpUa2FKMlNvNV8xZm1kZjMxSnBaeVJlNzN3

[tab permissions menu]: https://lh3.googleusercontent.com/E_8X5dAJaQi7LqcpQdlgs_tvW0I_WupThUzpzxUOb1JYeK2cIBMZFbxd_sZQwl0_pKEEQCSQtXFToGLCe9uZ2udERVHeWfgIgGglisoSW61PjJfOLp_FwDerAi4MCEIG0VPwRR-doA=w800
[tab permissions menu link]: https://photos.google.com/share/AF1QipOO2WKa_g3jpJXhCUmAhqGi3Fy6ELCze0DiedK5aWeK_zS3Uy6yzio1cI59BFnorw/photo/AF1QipOtpoLS4yrIyKAgjyKMPrRY8YGvhwG1TIF75FLH?key=enNqWHpUa2FKMlNvNV8xZm1kZjMxSnBaeVJlNzN3
