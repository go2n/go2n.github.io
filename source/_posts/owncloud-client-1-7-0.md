---
layout: post
title: "ownCloud client 1.7.0"
description: "Update PKGBUILD ownCloud client 1.7.0"
date: 2014-11-17
category: linux
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

Hae... Tanggal 7 November 2014 kemarin ownCloud client 1.7.0 ternyata sudah dirilis, dan saya baru sempat kompel hari ini. Berikut ini changelog ownCloud client 1.7.0:<!--more-->

{% alert danger %}
_PKGBUILD owncloud-client sudah dihapus dari [repo](https://github.com/go2n/archlinux-pkgbuild)_
{% endalert %}

* oC7 Sharing: Handle new sharing options of ownCloud 7 correctly.
* Added Selective sync: Ability to unselect server folders which are excluded from syncing, plus GUI and setup GUI
* Improved local change detection: consider file size, detect files with ongoing changes and do not upload immediately
* Improved HTTP request timeout handler: all successful requests reset the timeout counter
* Improvements for syncing command line tool: netrc support, improved SSL support, non interactive mode
* Added a socket based API to provide file management shells with status information about the sync status of files. That is a prerequisite for the overlay icons in the file managers.
* Permission system: ownCloud 7 delivers file and folder permissions, added ability to deal with it for shared folders and more.
* Ignore handling: Do not recurse into ignored or excluded directories
* Major sync journal database improvements for more stability and performance
* New library interface to sqlite3
* Improve "resync handling" if errors occur
* Blacklist improvements
* Improved logging: more useful meta info, removed noise
* Updated to latest Qt5 versions on Windows and OS X
* OS X: Sparkle update to provide pkg format properly
* OS X: Change distribution format from dmg to pkg with new installer.
* Win: Fix handling of filenames with trailing dot or space

Buat yang mau membangun paket owncloud client 1.7.0 dengan PKGBUILD saya monggo lho: ~~https://github.com/go2n/archlinux-pkgbuild/tree/master/owncloud-client~~.

{% image fancybox center owncloud-client-1-7-0.png "ownCloud Client" %}
