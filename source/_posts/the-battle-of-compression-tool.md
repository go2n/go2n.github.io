---
title: The battle of compression tools (Sebuah perbandingan)
date: 2012-12-17 09:58
categories: linux
tags:
    - tools
    - utilities
    - compression
keywords:
    - linux
    - tools
    - utilities
    - compression
    - gunzip
    - bunzip2
    - gzip
    - bz2
    - xz
thumbnailImage: ./1.png
thumbnailImagePosition: right
---

Beberapa hari yang lalu saya iseng-iseng membandingkan 3 format kompresi berkas. Ketiga format yang saya coba bandingkan tersebut adalah **gunzip**, **bunzip2** dan **xz utils**. Untuk pengujian kompresi ketiga format tersebut saya menggunakan berkas sql dengan ukuran kurang lebih 475 MB
<!-- more -->

{% image fancybox center clear ./1.png %}

## gunzip

Tool kompresi pada pengujian pertama adalah gunzip. Opsi yang saya gunakan untuk proses kompresi adalah -9 atau --best untuk _compress better_. Hasil proses kompresi berkas sql adalah **75 MB** dari berkas asal sebesar **475 MB** dengan membutuhkan waktu kurang lebih **0m53.258s**.

{% image fancybox center clear ./gunzip1.png %}

Sedangkan penggunaan CPU **25%** dan penggunaan memori **192 K**.

{% image fancybox center clear ./gunzip2.png %}

Waktu yang dibutuhkan untuk dekompresi **0m5.398s**.

{% image fancybox center clear ./gunzip3.png %}

## bunzip2

Tool kompresi pada pengujian kedua adalah bunzip2. Seperti halnya pada pengujian pertama, opsi yang saya gunakan untuk proses kompresi adalah -9 atau –best dan -k atau –keep (agar berkas yang mau dikompresi tidak hilang). Hasil proses kompresi berkas sql adalah **57 MB** dari berkas asal sebesar **475 MB** dengan membutuhkan waktu kurang lebih **1m41.310s**.

{% image fancybox center clear ./bunzip1.png %}

Sedangkan penggunaan CPU **25%** dan penggunaan memori **6.380 K**.

{% image fancybox center clear ./bunzip2.png %}

Waktu yang dibutuhkan untuk dekompresi **0m28.764s**.

{% image fancybox center clear ./bunzip3.png %}

## XZ utils

Tool kompresi terakhir yang saya uji adalah XZ utils. Opsi yang saya gunakan untuk kompresi sama seperti kedua tool kompresi diatas yaitu -9. Opsi -k digunakan agar berkas asli tidak hilang. Hasil proses kompresi berkas sql adalah **41 M**B dari berkas asal sebesar **475 MB** dengan membutuhkan waktu kurang lebih **7m38.308s**.

{% image fancybox center clear ./xz1.png %}

Sedangkan penggunaan CPU **25%** dan penggunaan memori **689.228 K**.

{% image fancybox center clear ./xz2.png %}

Waktu yang dibutuhkan untuk dekompresi **0m7.908s**.

{% image fancybox center clear ./xz3.png %}

## Kesimpulan

Untuk ukuran hasil kompresi dari yang terkecil adalah **xz utils**, **bunzip2** dan yang terakhir adalah **gunzip**. Untuk lamanya proses kompresi dari yang tercepat adalah **gunzip**, **bunzip2** dan yang terakhir adalah **xz utils**, sedangkan lamanya proses dekompresi dari yang tercepat adalah **gunzip**, **xz utils** dan terakhir **bunzip2**. Peggunaan memori dari yang paling kecil adalah **gunzip**, **bunzip2** dan yang terakhir **xz utils**.

| Tool             | Size  | Compression Time | Decompression Time | Memory Usage |
| :--------------- | :---- | :--------------- | :----------------- | -----------: |
| **gunzip**       | 75 MB | 0m53.258s        | 0m5.398s           |        192 K |
| **bunzip2**      | 57 MB | 1m41.310s        | 0m28.764s          |      6.380 K |
| **xz** **utils** | 41 MB | 7m38.308s        | 0m7.908s           |    689.228 K |
