---
layout: post
title: "Mengatasi masalah barcode generator SLiMS di Mesin FreeBSD 9.1"
date: 2014-09-10
category: freebsd
tags:
    - freebsd
    - linux
    - php
    - slims
    - senayan
    - perpustakaan
    - library
keywords:
    - freebsd
    - linux
    - php
    - slims
    - senayan
    - perpustakaan
    - library
comments: True
---

Halo...

Ada yang pernah mengalami barcode generator [SLiMS](http://slims.web.id/) yang nge-blank di mesin FreeBSD ndak? Begini permasalahannya, pustakawan Fakultas Teknik meminta saya untuk mengatur masalah barcode yang nge-blank di mesin server dhemit alias FreeBSD. Jadi beliau pada saat mau generate barcode melalui menu **System > Barcode Generator**, SLiMS tidak menampilkan barcode sama sekali.
<!--more-->

Pernah suatu waktu di tahun 2013 saya ubek-ubek forum SLiMS untuk mengatasi hal tersebut. Di [thread ini](http://slims.web.id/forum/viewtopic.php?f=38&t=29) katanya sih gara-gara masalah permissions. Namun, setelah saya `chmod +x genbarcode` ternyata malah muncul error seperti ini:

{% codeblock lang:bash %}
ELF binary type "0" not known.
./genbarcode: Exec format error. Binary file not executable.
{% endcodeblock %}

Dalam benak saya waktu itu nggak mungkin bisa file biner Linux dijalankan di FreeBSD. Tanpa pikir panjang saya pun download kode sumber [php-barcode](http://www.ashberg.de/php-barcode/) kemudian ngompel dan berhasil jalan lewat command line:

{% codeblock lang:bash %}
$ ./genbarcode 123456 128
02112321122321311233311211321312331112
11:9:1 16.5:9:2 22:9:3 27.5:9:4 33:9:5 38.5:9:6 
code 128
{% endcodeblock %}

Eh, tapi ternyata saat saya coba masuk halaman admin SLiMS dan mencoba membuat barcode ternyata hasilnya masih blank. Telo! Lha gimana nggak jengkel coba? Sudah mbulet pasang dependensi buat kompel kode di FreeBSD ternyata masih nge-blank. Saat itu kepikiran mau ganti OS dari FreeBSD ke Linux tapi kok ribet backup dan restore data yang sudah ada di server.

Baru tadi pagi agak siangan dikit saya ngobrol sama mas [Arif](http://twitter.com/arifalien) dan mas [Harun](http://twitter.com/runnov) mengenai rencana ganti OS. Namun, mas Harun bilang kalau di FreeBSD bisa menjalankan file biner Linux dengan mengatur Linux® Binary Compatibility.

Setelah memasang hal yang diperlukan sekarang file biner `lib/phpbarcode/bin/nix/genbarcode` bisa dijalankan tanpa perlu kompel untuk FreeBSD. Sip deh! Masalahnya sudah beres, tinggal perlu mengubah file `lib/phpbarcode/php-barcode.php` biar barcode yang dibuat melalui menu **System > Barcode Generator** di mesin FreeBSD muncul.

{% image fancybox center barcode-generator-slims-di-freebsd.png "Barcode Generator" %}

### Begini Langkahnya

1. Load linux kernel
`# kldload linux`
2. Cek apakah modul sudah ok
{% codeblock lang:shell %}
root@library:/root # kldstat 
Id Refs Address            Size     Name
 1    6 0xffffffff80200000 1323408  kernel
 2    1 0xffffffff81612000 1f417    linux.ko
{% endcodeblock %}
3. Pasang emulators/linux-base-f10 melalui port
{% codeblock lang:shell %}
root@library:/root # cd /usr/ports/emulators/linux_base-f10
root@library:/usr/ports/emulators/linux_base-f10 # make install distclean
=> basesystem-10.0-1.noarch.rpm doesn't seem to exist in /usr/ports/distfiles/rpm/i386/fedora/10.
=> Attempting to fetch http://critical.ch/distfiles/rpm/i386/fedora/10/basesystem-10.0-1.noarch.rpm
basesystem-10.0-1.noarch.rpm                  100% of 2915  B 7713 kBps
=> bash-3.2-30.fc10.i386.rpm doesn't seem to exist in /usr/ports/distfiles/rpm/i386/fedora/10.
=> Attempting to fetch http://critical.ch/distfiles/rpm/i386/fedora/10/bash-3.2-30.fc10.i386.rpm
....
--- TUNGGU SAMPAI SELESAI ---
...
{% endcodeblock %}

4. Tambahkan baris berikut pada `/etc/rc.conf` biar modul aktif tiap boot:
`linux_enable="YES"`
5. Edit file `lib/phpbarcode/php-barcode.php` menjadi seperti berikut (baris 51):
{% codeblock php-barcode.php lang:php %}
// genbarcode binary location
if (stripos(PHP_OS, 'Darwin') !== false) {
    $genbarcode_loc = './bin/darwin/genbarcode';
} else if (stripos(PHP_OS, 'Linux') !== false) {
    if (PHP_INT_SIZE == 4) {
        $genbarcode_loc = './bin/nix/genbarcode';
    } elseif (PHP_INT_SIZE == 8) {
        $genbarcode_loc = './bin/nix/genbarcode64';
    } else {
        $genbarcode_loc = './bin/nix/genbarcode';
    }
} else if (stripos(PHP_OS, 'FreeBSD') !== false) {
		$genbarcode_loc = './bin/nix/genbarcode';
} else {
    $genbarcode_loc = '.\bin\win\genbarcode.exe';
}
{% endcodeblock %}

Nah! Udah gitu aja...
