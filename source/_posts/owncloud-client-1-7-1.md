---
layout: post
title: "ownCloud client 1.7.1"
date: 2014-12-30
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
---

OwnCloud client 1.7.1 sudah dirilis tanggal 18 Desember kemarin, dan saya baru sempat kompel serta memperbarui PKGBUILD hari ini. Berikut ini changelog ownCloud client 1.7.1: <!--more-->
{% alert danger %}
_PKGBUILD owncloud-client sudah dihapus dari [repo](https://github.com/go2n/archlinux-pkgbuild)_
{% endalert %}

* Documentation fixes and updates
* Nautilus Python plugin fixed for Python 3
* GUI wording fixes plus improved log messages
* Fix hiding of the database files in the sync directories
* Compare http download size with the header value to avoid broken downloads, bug #2528
* Avoid initial ETag fetch job at startup, which is not needed.
* Add chunk size http header to PUT requests
* Fixed deteteCookie method of our CookieJar, fix for Shibboleth
* Added fallback for distros where XDG_RUNTIME_DIR is undefined
* Fix the setup wizard, bug #1989, #2264
* Fix scheduling of ETag check jobs, bug #2553
* Fix to avoid syncing more than one folder at a time, bug #2407
* Use fife minutes timeout for all network jobs
* Cleanup for Folderwizard wording
* Improve journal check: Remove corrupted journal files, bug #2547
* Fix item count in progress dialog for deletes, bug #1132
* Display correct file count on deletion (#1132)
* Fix reinitializing the folder using the wizard in certain cases (#2606)
* Mac OS: Fixed branding of the pkg file
* Mac OS: Fix display of overlay icons in certain situations (#1132)
* Mac OS: Use a bundled version of OpenSSL (#764, #2600, #2510)
* Win32: improved filesystem watcher
* Win32: Improve threading with shell integration
* Win32: Upgraded to OpenSSL 1.0.1j
* Win32: Improve reliability of Installer, fix removal of Shell Extensions

Buat yang mau membangun paket owncloud client 1.7.1 dengan PKGBUILD saya monggo lho: ~~https://github.com/go2n/archlinux-pkgbuild/tree/master/owncloud-client~~.

{% image fancybox center owncloud-client-1-7-1.png "ownCloud Client" %}
