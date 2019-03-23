---
layout: post
categories: blog
tags: Fedora yum
title: yum から ソースをダウンロード
date: 2011-02-06T16:30:00+09:00
---


yumからソースをダウンロードして覗いてみたメモ。

<!-- more -->

まず目的のファイルがどのパッケージに含まれているのかを調べる。ここでは `ls` で。 ls は *coreutils* に含まれている。

```
rpm -qf /bin/ls
```


パッケージ名がわかったら `yumdownloader` でダウンロードする。 yumdownloader は *yum-utils* パッケージにあるので、コマンドがない場合は yum からインストールしておく。

```
yumdownloader --source coreutils
```


そうするとパッケージの rpm がダウンロードされるので、 `rpm2cpio` と `cpio` を使って中身を確認する。

```
rpm2cpio coreutils-8.5-7.fc14.src.rpm | cpio --list
```


で目的のファイルを取り出す。

```
rpm2cpio coreutils-8.5-7.fc14.src.rpm | cpio -id coreutils-8.5.tar.xz
```


# 使用環境

+ Fedora 14 (2.6.35.10-74.fc14.i686)
+ yum (yum 3.2.28-5)
+ yumdownloader 1.0 (yum-utils 1.1.28-1)
+ rpm 4.8.1, rpm2cpio (rpm 4.8.1-5)
+ cpio (cpio 2.11-2)
