---
layout: post
categories: blog
tags: Web posterous
title: Posterousを使ってみた
date: 2010-07-19T18:09:00+09:00
---


[Posterous] を使ってみたメモ。

Posterousは、メールを送るだけでいろいろなところにポストするサービス。FacebookやTwitterなど多様なサービスと連携することができる。いまだにスマートフォンを買う気配がない私としては、メールからいろいろ投稿できると便利かなあと思って試してみた。

<!-- more -->

とりあえず登録。Posterousの特徴として「めんどくさいアカウント登録は不要。メールを送ったら勝手に専用のブログ作っちゃうよ。」ってのがあるけど、自分でつけた名前のアドレスが欲しかったのでLogin画面から *Sign up with Posterous* ボタンを押して、アカウントを作成。ここで使用する自分のメールアドレスを登録しておく（後から追加や変更も可能）。

[![posterous login]][posterous login link]


それから *Autopost* の設定画面で、自分のTwitterやらBloggerやらのアカウントを関連付ける。あとはメールをばんばん送るだけでOK。送った投稿は、投稿先に加えて、自分のPosterousブログにまとめられる。

送信先のメールアドレスは、 *○○○@posterous.com* となる。この○○○の部分を変えることでいろいろな方法でポストできる。基本は *post* で、関連付けられたサービスすべてに投稿される。そして *twitter* とすればTwitterに、 *blogger* とすればBloggerに投稿といった具合。 *twitter+blogger* のように複数のサービスを指定することもできる。とりあえずPosterousだけに投稿しておく場合は *posterous* でよい。

[![posterous address list]][posterous address list link]


単純かつ柔軟で便利だと思ったが、いくつか気になる点があった。

まずタイムゾーンが変更できない[^note-2010-08-20]。私は過去の出来事メモとして使いたかったので、ぱっと見時間がずれているのは気になる。まあBloggerなど投稿先では日本時間に設定しているので問題ないといえば問題ないが。対応中みたいだしそんなに難しいことでもないと思うので、しばらくしたら解決するかも。

投稿の細かなところも気になった。投稿の設定はもう少し細かく設定できると良い。Twitterであれば、ちょっとしたつぶやきで画像とかもなければ、URLは無くしたい。Bloggerは投稿に「via Posterous」みたいのが付いてくる。設定で消せるけど、消したら消したでゴミが残る。画像も投稿したら「フルサイズはPosterousで！」みたいになる。普通にBloggerから投稿するように、画像もPicasaに保存されると良かったんだけど。

インポートの機能も、Bloggerのアドレスを入れて試してみたが、時間がかかる上に全角の記号はところどころ文字化けがあった。エクスポートの機能が見つからなかったのも残念。

といった感じで、便利に使えそうではあるがちょっとした不満もある。まだサービスが始まってからそんなに立ってないようだし、これから機能が洗練されていくといいなあ。



[Posterous]: http://posterous.com/

[posterous login]: https://lh3.googleusercontent.com/qxeR442uPD6odMNwJcp6CtZMYtU3gnBWGeWie4TczJUb8SlBS1sBh8SVme4sKc2nAjfA5dX34a_nsOFiErEApFrJ-FlAfTrYlItGSW9EqpEe62Rlg_huU1owQZnn_eTj6hij9Bjtzw=w600
[posterous login link]: https://photos.google.com/share/AF1QipOTuIp-ckEfoOJz4ZKdVnRuq5z6VLKYmRTewquSG7MQFHbSMaCQqlCESZoWMkInDQ/photo/AF1QipMDPM_0iquP9szU8J7oB3-Hsx2ZV7FuuwyI_Ww9?key=R0dVUjJLZFBWTzRCVEQzSFNoclU2LXBHdXp5YVdB

[posterous address list]: https://lh3.googleusercontent.com/T4Dm_7fuDPfVMcl_A8L-Mb1tUD6YcwWUu6vwOxh4TLI-RwhHwhfjZ7YRx5ztnb_NXkCX8MyffhlYv2D9O3bji-OiPHjwWk3jWWbb-WrO5tOd4OUFv-Y70MjFHRDYtBhgDq3NLDHpgQ=w600
[posterous address list link]: https://photos.google.com/share/AF1QipOTuIp-ckEfoOJz4ZKdVnRuq5z6VLKYmRTewquSG7MQFHbSMaCQqlCESZoWMkInDQ/photo/AF1QipPf0I9LpR7kyjGv3F8nNH2F7P0uG6-DM4wQWe-J?key=R0dVUjJLZFBWTzRCVEQzSFNoclU2LXBHdXp5YVdB

[^note-2010-08-20]: タイムゾーンの設定ができるようになった。([記事][note-2010-08-20 link])
[note-2010-08-20 link]: {{ site.baseurl }}{% post_url /2010/2010-08-20-posterous-timezone %}
