---
layout: post
categories: blog
tags: Fedora Ubuntu Windows pulseaudio
title: PulseAudio の LAN 設定
date: 2010-10-18T00:36:00+09:00
---


[PulseAudio] を使って、デスクトップ機の音声をLANからノート機に転送することができたメモ。これでデスクトップ機にためこんである音楽を簡単にノート機でも聞ける。

<!-- more -->

まず聞く側の設定。 *module-native-protocol-tcp* を読み込んで、接続を許可するIPを指定しておく。デフォルトの設定を変更したり、コマンドからモジュールを読み込んだりとかでも良いと思うけど、私は *~/.pulse/tcp.pa* とか適当にファイルを作ってそこから読むようにする。

{% gist matea2/f07c4446fb1a9d4c9543c261ac0b682d tcp.pa %}


でファイルを読み込んで実行。

```
pulseaudio -F ~/.pulse/tcp.pa -D
```


Windowsノートでも聞けるように設定。WindowsではまあPulseAudioはふつう使わないので、デフォルトの設定を変えちゃう。バイナリと同じところに *default.pa* というファイルを作って以下を記述。

{% gist matea2/f07c4446fb1a9d4c9543c261ac0b682d default.pa %}


こっちは単に実行するだけでOK。

```
pulseaudio.exe
```


Vistaではファイアウォールのポップアップが出てきたので許可。

[![vista uac]][vista uac link]


次は音楽を飛ばす側の設定。コンソールから設定したかったので調べてみたら、 *~/.pulse/client.conf* に default-server を書くだけで良いようだ。

{% gist matea2/f07c4446fb1a9d4c9543c261ac0b682d client.conf %}


で起動。

```
pulseaudio -D
```


GUIの場合は *padechooser* から指定できる。

[![padechooser menu]][padechooser menu link]


アイコンを右クリックして、 Default Server から Other を選択。出てきたダイアログに転送先IPを指定する。

[![padechooser dialog]][padechooser dialog link]


あとは音楽を再生して、転送先のPCから聞こえれば成功。まあ音楽に限らずシステム音とかすべての音声が転送されるわけだが。

しかし、Windowsノートでは聞こえたがUbuntuノートでは聞こえない。ファイアウォールだっけなんだっけ？と悩んでいたら、hostsで制限がかかってたのだった。 */etc/hosts.allow* にPulseのポート 4713 を追加。

{% gist matea2/f07c4446fb1a9d4c9543c261ac0b682d hosts.allow %}


これで聞こえるようになった。


# 使用環境

+ Fedora 13
+ pulseaudio 0.9.21
+ GNOME padechooser 0.9.4

+ Ubuntu 10.10
+ pulseaudio 0.9.21

+ Windows Vista SP2
+ pulseaudio 0.9.6



[PulseAudio]: http://www.pulseaudio.org/

[vista uac]: https://lh3.googleusercontent.com/ePPhczhdsORgN7AT14fG_P594Jg2dumhVrDESZxec8j2GCCFL6j6IPUmkcATE6H57SWxLp9h6Uug9HyQ5AM9Ishz0q5M4SrSAFcKBiEC-MKpZTRW86yUoqwP_AAdIzhPn9fq5d4q0Q=w400
[vista uac link]: https://photos.google.com/share/AF1QipNhx761MEoZ8Cp5fo2BHgD-atKWWY3Yvajv2V80RlEpF3IhiePNcqDNVDgYUh7qSQ/photo/AF1QipNF1rk-PBuSD9LYPU9-DFzeld9p_l8QbPKY3GOE?key=WlNVSEQzS01tdThtZ094d0FrQUVKSFBTeXFNU0R3

[padechooser menu]: https://lh3.googleusercontent.com/bXYSP1wezFFGMVTOEFUQlw55_cYpOZWMd2SybML16Em7kF8OkvpTRINt2LD21Ct1JtUTa4nTZ2qzSFjWGMVpt2pm8NOdXZdYZ4Mfq_KB7_uvF2oFV3iR9C8680Dj6dTE5Hmjnf2FMg=w400
[padechooser menu link]: https://photos.google.com/share/AF1QipNhx761MEoZ8Cp5fo2BHgD-atKWWY3Yvajv2V80RlEpF3IhiePNcqDNVDgYUh7qSQ/photo/AF1QipPcCGHY5d_mfvqgsoD3Rti6heDUzAnmQ-ttOhWE?key=WlNVSEQzS01tdThtZ094d0FrQUVKSFBTeXFNU0R3

[padechooser dialog]: https://lh3.googleusercontent.com/9kbOp8LaDqrOVpArrlTyIEfN1r1-SsG0HIKJ5MvdRVx8gJB6_MfWEwUAhQeJdUGetnxr6QnzAGDUl8rM7J1V4pL5xhHtJnmD5Cm_UGy4GVOd8Rz-dQwFfsfsW--Vq1nFBH2lipWjHg=w300
[padechooser dialog link]: https://photos.google.com/share/AF1QipNhx761MEoZ8Cp5fo2BHgD-atKWWY3Yvajv2V80RlEpF3IhiePNcqDNVDgYUh7qSQ/photo/AF1QipMnjE2Cq7jkgXKrUA-Rw5qSATF-ipQWjAJebAJq?key=WlNVSEQzS01tdThtZ094d0FrQUVKSFBTeXFNU0R3

