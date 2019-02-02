---
layout: post
categories: blog
tags: jekyll github
title: GitHub Pages のローカル環境
---


GitHub Pages に移行することにしてからだいぶ経って、
ようやく始動。
ローカルでチェックしてアップする流れができそうなので、
これで動き出すはず。
以下の感じでローカルでの実行と確認ができた。


# Jekyll のインストール
まずは github pages のプロジェクトをローカル環境で確認するために、
Jekyll を動かせるようにしておく。

gem から *github-pages* をインストールできるので、
`bundle` を使ってインストールした。
プロジェクトと同じ所だとごちゃごちゃするので、
適当にディレクトリを作ってそこに入れる。

```
mkdir ~/temp/github-pages
cd ~/temp/github-pages
```

ディレクトリ内に *Gemfile* を作り、
以下の内容を記入。

```ruby
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```

bundle で gem をインストールする。
システム内に入れてもいいけど、
まあディレクトリ内に。

```
bundle install --path vendor/bundle
```

これでディレクトリ内で `bundle exec jekyll` をすると実行できる。


# Jekyll のコマンド化
bundle exec で実行するのはめんどいので、
binstubs を使って bin内にコマンドを作る。

```
bundle binstubs jekyll
```

出来上がった bin に alias を貼る。

```
alias jekyll=~/temp/github-pages/bin/jekyll
```

これでプロジェクトのディレクトリ内で `jekyll serve` を実行すると、
ブラウザから http://localhost:4000/ を開いて確認できるはず。


# 使用環境
+ Arch Linux 4.20.3-arch1-1-ARCH
+ ruby 2.6.0p0
+ gem 3.0.2
+ Bundler 2.0.1
+ github-pages 193
+ jekyll 3.7.4

