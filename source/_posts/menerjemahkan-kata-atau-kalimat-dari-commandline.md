---
title: Menerjemahkan kata atau kalimat dari commandline
date: 2012-07-07 18:12
categories: linux
tags:
  - google
  - translate
  - kamus
    - bash
  - shell 
    - cli
keywords:
  - google
  - translate
  - kamus
    - bash
  - shell 
    - cli
thumbnailImage: https://www.akashtrehan.com/assets/images/emoji/terminal.png
thumbnailImagePosition: right
---

Mungkin tidak kita menerjemahkan kata atau kalimat menggunakan dari commandline? <!-- more --> Jawabannya, mungkin saja. Dengan memanfaatkan `bash`, `awk` dan `lynx` kita bisa membuat script shell sederhana untuk menerjemahkan suatu kata atau kalimat. Tentu saja script shell ini membutuhkan koneksi internet karena urusan penerjemahan akan diserahkan sepenuhnya pada [Google Translate](https://translate.google.com/).

Sebelum menuliskan shell script untuk menerjemahkan kata atau kalimat pastikan mesin GNU/Linux anda sudah terinstall [Lynx web browser](https://en.wikipedia.org/wiki/Lynx_%28web_browser%29) (browser berbasis text). Jika belum silakan anda install terlebih dahulu.

- Arch Linux 
	```
	# pacman -S lynx
	```
- openSUSE
	```
	zypper install lynx
	```
- Ubuntu
	```
	$ sudo apt-get install lynx
	```

Selanjutnya ketikkan script berikut ini menggunakan teks editor favorit anda:

{% codeblock lang:bash %}
#!/bin/bash 

if [ $# == 3 ]
then
	echo "From: $1 To: $2" lynx -dump "http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=$3&langpair=$1|$2"|awk -F'"' '{print $6}'
else
	lynx -dump "http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=$1&langpair=en|id"|awk -F'"' '{print $6}'
fi
{% endcodeblock %}

Simpan script tersebut dengan nama, misalkan `translate-cli`, ubah permission agar bisa di-execute dan jalankan script tersebut.
```
[me@archlinux ~]$ chmod +x translate-cli
[me@archlinux ~]$ translate-cli en id "try this at home"
From: en To: id 
coba ini di rumah

```
Jika script dijalankan tanpa argumen [bahasa asal] [bahasa terjemahan] maka script tersebut akan menerjemahkan kata atau kalimat dari Inggris ke Bahasa Indonesia secara default.

```
[me@archlinux ~]$ translate-cli "try this at home"
coba ini di rumah
```

> Tulisan ini ditulis setelah membaca artikel di [sini](http://gespadas.com/google-translate-terminal).

