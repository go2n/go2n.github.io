---
title: Integrasi KDE dengan Android menggunakan KDE Connect
date: 2013-09-20 21:18
categories: linux
tags:
  - kde
  - android
keywords:
  - linux
  - kde
  - android
thumbnailImagePosition: right
thumbnailImage: ./snapshot44.png
---

## Instalasi 
<!-- more -->

- Arch Linux: [kdeconnect](https://aur.archlinux.org/packages/kdeconnect/) atau [kdeconnect-git](https://aur.archlinux.org/packages/kdeconnect-git/) (AUR)
- openSUSE 12.3: [kdeconnect-kde](http://software.opensuse.org/ymp/KDE:Extra/openSUSE_12.3/kdeconnect-kde.ymp?base=openSUSE%3A12.3&query=kdeconnect-kde) (1 Click Install)
- Android: [KDE Connect](https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp)

## Instalasi dari kode sumber
- Clone: `git clone git://anongit.kde.org/kdeconnect-kde`
- Install dependensi: `kdelibs, qjson`
- Kompilasi:
  - `cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
  - `make`
  - `sudo make install atau su -c "make install"`

Penampakan:

{% image fancybox nocaption fig-50 ./snapshot44.png "KDE Connect Plasmoid Notifications" %}
{% image fancybox nocaption fig-50 ./snapshot46.png "KDE Connect Plasmoid" %}
{% image fancybox nocaption fig-100 ./snapshot45.png "KDE Control Module" %}
{% image fancybox nocaption fig-25 ./screenshot-20130920-210928.png "KDE Connect Android" %}
{% image fancybox nocaption fig-25 ./screenshot-20130920-210937.png "KDE Connect Android Device" %}
{% image fancybox nocaption fig-25 ./screenshot-20130920-210954.png "KDE Connect Android Settings" %}
{% image fancybox nocaption fig-25 clear ./screenshot-20130920-211003.png "KDE Connect Android Multimedia control" %}

Diuji coba dengan KDE 4.11.1 di openSUSE 12.3 dan ponsel Android Samsung Galaxy Fit.

[Rujukan](http://albertvaka.wordpress.com/2013/09/08/releasing-kde-connect-technology-preview/)
