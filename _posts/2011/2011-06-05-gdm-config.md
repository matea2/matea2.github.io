---
layout: post
categories: blog
tags: Fedora gdm
title: gdm 設定
date: 2011-06-05T18:07:00+09:00
---


Fedora 15 にしたらSLiMがなんかうまく動かないので、GDMを設定して使ってみた。

<!-- more -->


# xsession 読み込み

まず自分設定を読ませたいので *~/.xsession* の読み込み設定。いろいろやってもうまくいかんなあとおもったら、 *xorg-x11-xinit-session* をインストールするらしい。

```
sudo yum install xorg-x11-xinit-session
```


それで、GDMのメニューで *User Script* が選べるようになる。あと *~/.xsession* は実行権限が必要みたい。

```
chmod +x ~/.xsession
```


# ユーザ名一覧を非表示

ログイン画面に出るユーザ名一覧を非表示にする。gconfの設定を変更すれば良い。これもうまくいかんなあと思ったら、gdmユーザでやるらしい。

```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type=bool true
```


--all-entries オプションで値を確認。

```
sudo -u gdm gconftool-2 --all-entries /apps/gdm/simple-greeter
```


# サウンドをオフ

同様にgconftoolで設定。

```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/settings-manager-plugins/sound/active --type=bool false
```
