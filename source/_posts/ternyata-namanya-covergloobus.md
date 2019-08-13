---
title: Ternyata namanya CoverGloobus
date: 2012-11-13 20:40
categories: linux
tags:
  - linux
  - desktop 
  - archlinux
  - media 
  - music
  - python
  - gtk
  - art
keywords:
  - linux
  - desktop 
  - archlinux
  - media 
  - music
  - python
  - gtk
  - art
thumbnailImagePosition: right
thumbnailImage: https://go2n.github.io/2012/11/13/ternyata-namanya-covergloobus/snapshot102.png
---

Saat saya jalan-jalan di deviantart ada screenshot desktop GNU/Linux milik salah satu pengguna di sana yang menarik perhatian saya. Hal yang membuat saya tertarik adalah applet penampil cover art musik yang sedang diputar. Setelah mencari tahu dengan bantuan Google ternyata nama applet tersebut adalah CoverGloobus.
<!-- more -->
Menurut situsnya, CoverGloobus adalah adalah sebuah desktop (penampil) cover art dan pengontrol media yang juga dapat menampilkan lirik lagu yang sedang dimainkan. CoverGloobus dibangun menggunakan bahasa Python dan GTK+ (PyGTK).

## Dukungan

CoverGloobus mendukung banyak pemutar media/musik, antara lain:
- Amarok2
- Audacious
- Banshee
- Clementine
- Exaile 0.2.x
- Exaile 0.3.x
- gmusicbrowser
- Guayadeque
- Listen
- MOC
- MPD (requires python-mpd)
- QuodLibet
- Rythmbox
- Songbird (requires MPRIS plugin for Songbird)
- Spotify
- Totem
- VLC ( > 0.9.0)

Lyrics Engine:
- absolutelyrics.com
- lyrics.com
- lyrics.wikia.com
- lyricsfly.com
- lyricsplugin.com

Tablatures Engine:
- Ultimate guitar

Berikut ini tampilan CoverGloobus dan lirik lagu pada desktop KDE saya:

{% image fancybox center ./snapshot102.png "CoverGloobus" %}

{% image fancybox center ./snapshot103.png "Lirik" %}

## Instalasi

Instalasi CoverGloobus pada Arch Linux melalui AUR:

{% codeblock %}
yaourt -S covergloobus
{% endcodeblock %}

untuk versi bzr:
{% codeblock %}
yaourt -S covergloobus-bzr
{% endcodeblock %}

Sedangkan untuk distro GNU/Linux yang lain silahkan googling 😁. Untuk tema CoverGloobus silakan kunjungi http://covergloobus.deviantart.com/
