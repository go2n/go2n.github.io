---
layout: post
title: "PKGBUILD Update: mouseserver"
date: 2014-08-08
categories: linux
tags: 
    - archlinux
    - pkgbuild
    - mouse server
keywords:
    - archlinux
    - pkgbuild
    - mouse server
    - linux
comments: True
---

Kemarin malam dapat notifikasi via email bahwa ada komentar untuk paket AUR mouse server yang saya submit dari [Nuno Goncalves](https://aur.archlinux.org/account/ulukyn/). Dalam komentar tersebut dia menyebutkan bahwa ada kesalahan pada PKGBUILD saya karena source code mouse server baru dan dia menyertakan PKGBUILD yang benar.
<!--more-->

Nuno Goncalves mengganti pkgname menjadi `mouseserver-sourcecode-Linux` sesuai dengan hasil ekstrak dari source code. Namun saya lebih memilih pkgname yang lama sesuai dengan file biner hasil kompilasi. Untuk itu saya menambahkan variabel baru yaitu `pkgsrc=mouseserver-sourcecode-Linux`. Hhe 😁

{% image fancybox center mouse-server.png "Mouse Server for Linux" %}

Monggo lihat perubahannya di [sini](https://github.com/go2n/archlinux-pkgbuild/commit/a69d2382e365d5442aaa6a1fb6d286b21a45250a?diff=split#diff-fdf85429fb82f55d422abdce53acee2f), atau unduh di [https://aur.archlinux.org/packages/mouseserver/](https://aur.archlinux.org/packages/mouseserver/). 😊
