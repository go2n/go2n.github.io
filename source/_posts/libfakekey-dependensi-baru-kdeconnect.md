---
layout: post
title: "Libfakekey, dependensi baru kdeconnect?"
date: 2014-08-18
categories: linux
tags: 
    - archlinux
    - pkgbuild
    - KDE
keywords:
    - archlinux
    - pkgbuild
    - KDE
    - linux
comments: True
---

Hae! Selamat hari raya senin! :)

Siang ini tugas saya di unit Registrasi agak selo dan saya bersemangat untuk membuat paket kdeconnect versi git yang baru. Nggak pake lama saya nyetater konsole buat narik kode sumbernya dan mencoba membuat paket dengan PKGBUILD buatan [Kuba Serafinowski](https://aur.archlinux.org/packages/kdeconnect-git/). Berhubung proses narik kode terbaru dan kompelnya agak lama akibat koneksi di kantor Registrasi yang agak-agak ho oh jadi bisa ditinggal udud. Hhe... 
<!--more-->

Setelah beberapa saat saya cek di terminal ternyata paket kdeconnect gagal dibuat, ada error pas kompel. Pesan errornya seperti ini:

{% codeblock lang:bash %}
Scanning dependencies of target kdeconnect_share
/home/tiyok/Development/aur/kdeconnect-git/src/kdeconnect-git/plugins/mousepad/mousepadplugin.cpp:26:29: fatal error: fakekey/fakekey.h: No such file or directory
 #include <fakekey/fakekey.h>
                             ^
compilation terminated.
plugins/mousepad/CMakeFiles/kdeconnect_mousepad.dir/build.make:77: recipe for target 'plugins/mousepad/CMakeFiles/kdeconnect_mousepad.dir/mousepadplugin.o' failed
make[2]: *** [plugins/mousepad/CMakeFiles/kdeconnect_mousepad.dir/mousepadplugin.o] Error 1
CMakeFiles/Makefile2:1354: recipe for target 'plugins/mousepad/CMakeFiles/kdeconnect_mousepad.dir/all' failed
make[1]: *** [plugins/mousepad/CMakeFiles/kdeconnect_mousepad.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
{% endcodeblock %}

Agak mumet juga baca pesan error seperti itu. Kalau dilihat-lihat sih kompelnya gagal gara-gara nggak nemu `fakekey/fakekey.h`. Nah, biar nggak *error* lagi PKGBUILD perlu di-edit, pada array `depends=()` perlu ditambahkan paket libfakekey jadi begini:

{% codeblock lang:bash %}
# Maintainer: Kuba Serafinowski <zizzfizzix(at)gmail(dot)com>
# https://github.com/zizzfizzix/pkgbuilds

##############################################################
#### The section below can be adjusted to suit your needs ####
##############################################################

# What type of build do you want?
# See http://techbase.kde.org/Development/CMake/Addons_for_KDE#Buildtypes to check what is supported.

_buildtype='RelWithDebInfo'

##############################################################

pkgname=kdeconnect-git
pkgver=515.ea5d9c8
pkgrel=1
pkgdesc='KDE Connect kded and kcm - development version'
url='https://albertvaka.wordpress.com/'
license=('GPL')
arch=('i686' 'x86_64')
depends=('kdelibs' 'qjson' 'qca-ossl' 'libfakekey')
makedepends=('automoc4' 'git' 'cmake')
optdepends=('sshfs: remote file browsing')
provides=('kdeconnect')
conflicts=('kdeconnect')
install=kdeconnect.install
source=("${pkgname}::git://anongit.kde.org/kdeconnect-kde")
md5sums=('SKIP')

if [[ ! ${_buildtype} == 'Release' ]] && [[ ! ${_buildtype} == 'release' ]]; then
  options=('debug')
fi

pkgver() {
  cd ${pkgname}
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  if [[ -e ${pkgname}-build ]]; then rm -rf ${pkgname}-build; fi
  mkdir ${pkgname}-build
}

build() {
  cd ${pkgname}-build

  cmake -DCMAKE_INSTALL_PREFIX=/usr \
        -DKDE4_BUILD_TESTS=OFF \
        -DCMAKE_BUILD_TYPE=${_buildtype} \
        ../${pkgname}
  make
}

package() {
  cd ${pkgname}-build
  make DESTDIR=${pkgdir} install
}
{% endcodeblock %}

Yes! Setelah dicoba menjalankan `makepkg` dengan PKGBUILD yang udah diedit paket kdeconnect-git akhirnya jadi juga. \o/
