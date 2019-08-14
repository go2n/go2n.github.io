---
title: 'Oxygen Font: KDE Desktop Font'
date: 2012-01-07 05:06
categories:
    - linux
    - KDE
tags:
    - linux
    - archlinux
    - KDE
    - fonts
keywords:
    - linux
    - archlinux
    - KDE
    - oxygen
    - fonts
thumbnailImage: oxygen1.png
thumbnailImagePosition: right
---

Pagi ini membuka akregator dan membaca feeds yang ada. Ada 2 feed yang judulnya menarik perhatian saya:
<!-- more -->

- [Oxygen Font, The New KDE Desktop Font Family, Available For Testing](http://www.webupd8.org/2012/01/oxygen-font-new-kde-desktop-font-family.html)
- [KDE Font ‘Oxygen’ Available for Testing](http://www.omgubuntu.co.uk/2012/01/kde-font-oxygen-available-for-testing/)

Hmm.. font Oxygen sekarang sudah tersedia untuk testing yang saat ini masih dalam tahap alpha. Oxygen Font adalah sebuah proyek font desktop/GUI (*graphical user interface*) yang digunakan untuk terintegrasi dengan KDE Desktop.

Pada rilis alpha ini Oxygen Font membawa tipe *Regular*, *Bold* dan *Mono*

{% image fancybox fig-50 nocaption ./oxygen1.png "Oxygen Font - Regular" %}
{% image fancybox fig-50 nocaption oxygen2.png "Oxygen Font - Bold" %}
{% image fancybox fig-100 nocaption oxygen3.png "Oxygen Font - Mono" %}
{% image fancybox center fig-100 nocaption oxygen4.png "Oxygen Font - Mono di Konsole" %}

Oxygen Font dapat didownload di:

- [projects.kde.org](https://projects.kde.org/projects/playground/artwork/oxygen-fonts/repository).

- anongit.kde.org dengan menggunakan git

  ```
  git clone git://anongit.kde.org/oxygen-fonts
  ```

Untuk instalasi Oxygen Font:

1. Salin direktori `oxygen-fonts` yang telah didownload ke direktori /usr/share/fonts
2. Jalankan perintah `fc-cache -f` untuk build font cache

Bagi pengguna [Arch Linux](http://www.archlinux.org/), instalasi Oxygen Font melalui [AUR](http://aur.archlinux.org/packages.php?ID=55564): `yaourt -S oxygen-fonts-git`. Untuk informasi lebih lanjut mengenai Oxygen Font silakan kunjungi https://github.com/KDE/oxygen-fonts.
