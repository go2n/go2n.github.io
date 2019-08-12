---
layout: post
title: "Update PKGBUILD ownCloud client 1.6.1"
date: 2014-07-10
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
thumbnailImagePosition: right
thumbnailImage: https://go2n.github.io/2014/07/10/update-pkgbuild-owncloud/2014-07-10-update-pkgbuild-owncloud.png
---

Beberapa saat yang lalu saya meng-_update_ PKGBUILD untuk owncloud client menjadi versi 1.6.1. Selain perubahan versi, saya juga menambahkan fungsi [prepare()](https://github.com/go2n/archlinux-pkgbuild/commit/f89123c889a9c614bc539318dc17a5d3869b6e7e) pada PKGBUILD sesuai dengan artikel di [halaman wiki archlinux](https://wiki.archlinux.org/index.php/Creating_packages#The_prepare.28.29_function).
<!--more-->

{% alert danger %}
_PKGBUILD owncloud-client sudah dihapus dari [repo](https://github.com/go2n/archlinux-pkgbuild)_
{% endalert %}

Buat yang mau membangun paket owncloud client 1.6.1 dengan PKGBUILD saya, monggo lho: ~~https://github.com/go2n/archlinux-pkgbuild/tree/master/owncloud-client~~.

{% image fancybox center 2014-07-10-update-pkgbuild-owncloud.png "ownCloud Client" %}
