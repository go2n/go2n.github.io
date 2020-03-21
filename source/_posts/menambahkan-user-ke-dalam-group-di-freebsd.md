---
layout: post
title: "Menambahkan user ke dalam group di FreeBSD"
description: "Sebuah catatan biar nggak lupa perintah menambahkan user ke dalam group di mesin FreeBSD"
date: 2016-01-05
categories:
    - notes
    - freebsd
tags:
    - freebsd
keywords:
    - freebsd
comments: True
thumbnailImagePosition: right
thumbnailImage: https://go2n.github.io/2015/03/12/lupa-password-mysql-di-freebsd/dhemit.png
---

> _Sebuah catatan biar nggak lupa perintah menambahkan user ke dalam group di mesin FreeBSD._

Saat selesai setup server FreeBSD saya sering lupa menambahkan user ke dalam group wheel. Masalah datang pas ngremot server dan mau pindah sebagai user root nggak bisa. Telo!
<!--more-->

Ada dua cara buat menambahkan user ke dalam group, antara lain:

### 1. Menggunakan perintah `pw`:

{% codeblock lang:shell %}
[root@server] # pw group mod <nama group> -m <nama user>
{% endcodeblock %}

Contoh:

Menambahkan user go2n ke dalam group wheel

{% codeblock lang:shell %}
[root@server] # pw group mod wheel -m go2n
{% endcodeblock %}


### 2. Edit `/etc/group` sebagai root dan tambahkan user ###

{% codeblock lang:shell %}
...
wheel:*:0:root,go2n
...
{% endcodeblock %}

Gitu aja sih, tinggal pilih pakai cara yang mana. Sekian.

Rujukan: https://forums.freebsd.org/threads/add-yourself-to-the-wheel-and-operators-group.9796/
