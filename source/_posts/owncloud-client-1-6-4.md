---
layout: post
title: "ownCloud client 1.6.4"
date: 2014-10-27
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
thumbnailImage: https://go2n.github.io/2014/10/27/owncloud-client-1-6-4/owncloud-client-1-6-4.png 
thumbnailImagePosition: right
---

Hae... Tanggal 23 Oktober kemarin ownCloud client 1.6.4 dirilis loh, sudah update belum? Berikut ini changelog ownCloud client 1.6.4:<!--more-->

* Fix startup logic, fixes bug #1989
* Fix raise dialog on X11
* Win32: fix overflow when computing the size of file > 4GiB
* Use a fixed function to get files modification time, the original one was broken for certain timezone issues, see core bug #9781 for details
* Added some missing copyright headers
* Avoid data corruption due to wrong error handling, bug #2280
* Do improved request timeout handling to reduce the number of timed out jobs, bug #2155

{% alert danger %}
_PKGBUILD owncloud-client sudah dihapus dari [repo](https://github.com/go2n/archlinux-pkgbuild)_
{% endalert %}

Buat yang mau membangun paket owncloud client 1.6.4 dengan PKGBUILD saya monggo lho: ~~https://github.com/go2n/archlinux-pkgbuild/tree/master/owncloud-client~~

{% image fancybox center owncloud-client-1-6-4.png "ownCloud Client" %}
