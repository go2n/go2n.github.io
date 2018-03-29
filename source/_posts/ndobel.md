---
layout: post
title: "Ndobel monitor di KF5 & Plasma 5"
date: 2014-10-30
categories: linux
tags:
    - archlinux
    - KDE
keywords:
    - archlinux
    - KDE
    - linux
comments: True
---

Di tulisan kali ini saya akan sedikit surhat tentang dua(l) monitor/layar pada KDE Frameworks 5 dan Plasma 5 di mesin Archlinux saya.
<!--more-->

Saya suka mbuka laptop dengan dua layar. Jadi saat ngihik sesuatu saya bisa buka di layar pertama (primary), lalu di layar kedua saya bisa buka-buka halaman internet untuk membaca dokumentasi atau howto. Di KDE 4 saya bisa mengatur dua monitor melalui System Settings > Display and Monitor. Sayangnya, di KDE 5 saya tidak bisa :(

Pada pengaturan Display and Monitor KDE 5 hanya ada dua sub-kategori saja yaitu: Compositor dan Screen Locking.

{% image fancybox center ssnd-snapshot140.png "Display and Monitor KDE 5 System Settings" %}

Sedangkan di KDE 4 ada 4 sub-kategori

{% image fancybox center settings-display-and-monitor.png "Display and Monitor KDE 4 System Settings" %}

Untungnya ada program `xorg-xrandr`, sebuah program cli primitif untuk RandR extension. Dengan xrandr saya bisa mengatur KDE saya tampil di dua layar. 

Untuk mengetahui monitor yang sudah nancep di mesin saya gunakan perintah `xrandr -q`

{% image fancybox center ssnd-snapshot141.png "xrandr" %}

Untuk menampilkan KDE di dua layar saya gunakan perintah ini:

{% codeblock lang:bash %}
xrandr --output LVDS1 --mode 1366x768 --output VGA1 --primary --mode 1440x900 --left-of LVDS1
{% endcodeblock %}

Jadi gini penjelasannya, output-nya dua layar yaitu: LVDS1 dengan mode 1366x768 dan VGA1 dengan mode 1440x900 sebagai layar utama, posisi layar VGA1 di sebelah kiri layar LVDS1.

Nah udah gitu aja sih, ketok sederhana ya? Untuk keterangan lebih lanjut mengenai `xorg-xrandr` baca saja [manualnya](ftp://www.x.org/pub/X11R7.5/doc/man/man1/xrandr.1.html).

Hidop poligami! Hidop KDE!

_Rujukan: [Archwiki: Multihead](https://wiki.archlinux.org/index.php/multihead)._
