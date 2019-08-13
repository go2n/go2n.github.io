---
title: Homerun Launcher
date: 2012-11-16 12:29
categories:
    - linux
    - KDE
tags:
    - archlinux
    - KDE
    - aur
keywords:
    - linux
    - kde
    - archlinux
    - aur
    - homerun
    - launcher
thumbnailImage: ./snapshot1061.png
thumbnailImagePosition: right 
---

Baru saja saya jalan-jalan di [Planet KDE](http://www.planetkde.org/), di sini saya menemukan tulisan yang cukup menarik mengenai launcher baru oleh [Aurélien Gâteau](http://agateau.com/). Launcher baru tersebut adalah [Homerun](http://userbase.kde.org/Homerun) yang dibuat oleh Shaun Reich dan Aurélien Gâteau dari [Blue Systems](http://blue-systems.com/).
<!-- more -->

## Deskripsi

{% alert info %}
Homerun is a fullscreen launcher with content organized in tabs. A tab is composed of several “sources”. A source can provide one or more sections to a tab. Homerun comes with a few built-in sources, but custom sources can be written using libhomerun.
{% endalert %}

## Instalasi

Berhubung saya menggunakan distribusi [Arch Linux](https://www.archlinux.org/), saya mencari PKGBUILD untuk di-*build* di [AUR](https://aur.archlinux.org/). Hasil [pencarian di AUR](https://aur.archlinux.org/packages/?O=0&C=0&SeB=nd&K=applets-homerun&outdated=&SB=n&SO=a&PP=50&do_Search=Go) homerun ada 2 versi, yaitu versi git dan non-git. Ada 2 metode instalasi, yang pertama yang termudah dengan menggunakan yaourt, dan yang kedua metode yang sedikit ribet.

- **Instalasi dengan yaourt**

  ```
  yaourt -S kdeplasma-applets-homerun
  ```

- **Download; ekstrak; build**

  1. Download [kdeplasma-applets-homerun.tar.gz](https://aur.archlinux.org/packages/kd/kdeplasma-applets-homerun/kdeplasma-applets-homerun.tar.gz) 

    {% codeblock %}
    wget https://aur.archlinux.org/packages/kd/kdeplasma-applets-homerun/kdeplasma-applets-homerun.tar.gz -O /tmp/kdeplasma-applets-homerun.tar.gz`
    {% endcodeblock %}

  2. Ekstrak

    {% codeblock %}
    `cd /tmp ; tar xzvf kdeplasma-applets-homerun.tar.gz
    {% endcodeblock %}

  3. Build

    {% codeblock %}
    cd kdeplasma-applets-homerun/ ; makepkg -si
    {% endcodeblock %}
    
    Setelah menjalankan perintah `makepkg` tinggal menunggu proses yang berjalan dan berikan konfirmasi instalasi saat ditanyakan.

## Penampakan

- **Home**

  Tab *Home* pada Homerun berisikan Favorite Applications (dapat ditambahkan), Favorite Places dan Recent Documents
  
  {% image fancybox center clear ./snapshot1061.png %}

- **Applications**

  Tab *Applications* ini berisikan kategori aplikasi yang terinstall

  {% image fancybox center clear ./snapshot1071.png %}

- **Files**

  Tab *Files* berisikan berkas-berkas yang ada $HOME

  {% image fancybox center clear ./snapshot108.png %}

- **Power**

  Tab *Power* berisikan *shorcut* untuk *session* dan *power*

  {% image fancybox center clear ./snapshot109.png %}

Sumber:

- http://userbase.kde.org/Homerun
- http://agateau.com/2012/11/14/introducing-homerun/
