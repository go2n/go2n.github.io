---
layout: post
title: "PKGBUILD Update: mouseserver 1.0.1-3"
date: 2015-01-28
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

Kemarin malam dapat notifikasi via email bahwa ada komentar untuk paket [AUR mouse server](https://aur.archlinux.org/packages/mouseserver/) yang saya submit dari [Tobse Topic](https://aur.archlinux.org/account/generalt/). Dalam komentar tersebut dia menyebutkan bahwa ada masalah pada CMakeLists.txt mouseserver. Katanya:
<!--more-->

> Hi there,
> 
> `/usr/sbin` is hard coded in CMakeLists.txt, so `CMAKE_INSTALL_PREFIX` parameter for cmake is ignored.
>
> I added the following line. Now cmake respects the INSTALL PREFIX:
> `sed -i 's,/usr/sbin,${CMAKE_INSTALL_PREFIX},g' ../CMakeLists.txt`
>
> If you want mouseserver to be installed to `/usr/bin` change next line to:
> `cmake ../ -DCMAKE_INSTALL_PREFIX=/usr/bin`

Duh, selama ini saya tidak memperhatikan. Untung saja ada yang mengoreksi 😓

Perubahan yang saya lakukan adalah menambahkan fungsi `prepare()` untuk persiapan membangun paket dan mengubah INSTALL PREFIX serta mengganti parameter `CMAKE_INSTALL_PREFIX` dari `/usr` menjadi `/usr/bin` pada fungsi `build()`.

Monggo kalau mau lihat perubahannya di [sini](https://github.com/go2n/archlinux-pkgbuild/commit/a69d2382e365d5442aaa6a1fb6d286b21a45250a?diff=split#diff-fdf85429fb82f55d422abdce53acee2f). Untuk paket AUR-nya saya submit di [sini](https://aur.archlinux.org/packages/mouseserver/). 😊

{% image fancybox center mouse-server.png "Mouse Server for Linux" %}
