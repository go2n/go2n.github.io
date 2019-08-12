---
layout: post
title: "ownCloud client 1.6.3"
date: 2014-09-10
categories: linux
tags:
    - archlinux
    - pkgbuild
    - owncloud
keywords:
    - archlinux
    - pkgbuild
    - owncloud
    - linux
comments: True
thumbnailImage: https://go2n.github.io/2014/09/10/owncloud-client-1-6-3/owncloud-client-1-6-3.png
thumbnailImagePosition: right
---

Hae... Sudah pada upgrade owncloud client 1.6.3 belum? Berikut ini changelog ownCloud client 1.6.3:<!--more-->

* Fixed updater on OS X
* Fixed memory leak in SSL button that could lead to quick memory draining
* Fixed upload problem with files >4 GB
* MacOSX, Linux: Bring Settings window to front properly
* Branded clients: If no configuration is detected, try to import the data from a previously configured community edition.

{% alert danger %}
_PKGBUILD owncloud-client sudah dihapus dari [repo](https://github.com/go2n/archlinux-pkgbuild)_
{% endalert %}

Buat yang mau membangun paket owncloud client 1.6.3 dengan PKGBUILD saya monggo lho: ~~https://github.com/go2n/archlinux-pkgbuild/tree/master/owncloud-client~~

{% image fancybox center owncloud-client-1-6-3.png "ownCloud Client" %}
