---
title: SocialRok – Amarok Social Networks
date: 2013-01-12 05:07:00
category: linux
tags:
    - amarok
    - KDE
    - music
keywords:
    - amarok
    - KDE
    - linux
comments: True
---

SocialRok merupakan Amarok 2 Script yang memungkinkan kamu untuk posting lagu yang sedang kamu dengarkan dengan Amarok pada jejaring sosial. SocialRok juga memungkinkan kamu untuk posting cover art dari lagu yang sedang diputar dan link pada Youtube untuk pencarian.
<!-- more -->

**Jejaring sosial yang tersedia:**
* Facebook
* Flickr
* Twitter
* Google Plus (masih Coming Soon katanya sih, menunggu Google merilis API untuk write access)
* Skype

Untuk instalasi bisa langsung unduh melalui Get Hot New Stuff pada Amarok (Menu Settings > Configure Amarok… > Scripts > Manage Scripts)

{% image fancybox center snapshot135.png "Amarok: Configure script" %}
{% image fancybox center snapshot136.png "Amarok: Add-on installer" %}

Restart Amarok lalu aktifkan SocialRok: Menu Settings > Configure Amarok… > Scripts (centang SocialRok). Untuk konfigurasi: Menu Settings > Configure SocialRok… Pada jendela konfigurasi kamu bisa mengatur jejaring sosial.

{% image fancybox center snapshot137.png "SocialRok: Configure" %}

Sebagai contoh jejaring sosial yang saya gunakan Twitter. User ID bukan user jejaring sosial, melainkan UserID yang didapat setelah memberikan akses ke jejaring sosial. Untuk mendapatkan User ID pilih Menu Tools > Grant Access for Twitter, selanjutnya kamu akan dibawa ke halaman web https://calm-river-6855.herokuapp.com/twitter.php untuk koneksi SocialRok dengan Twitter.

{% image fancybox center snapshot138.png "Rekonq: Twitter Auth" %}
{% image fancybox center snapshot139.png "Rekonq: Twitter Auth" %}

Isikan User ID yang didapat pada isian jendela konfigurasi.

{% image fancybox center snapshot140.png "SocialRok: Configure" %}

Setelah itu kamu bisa posting lagu yang kamu putar dengan Amarok pada jejaring sosial (Twitter). Pilih Menu Tools > Twitt Current Track.

{% image fancybox center snapshot142.png "Twitter" %}
