---
title: Akhirnya…
date: 2012-10-11 08:52:28
categories: linux
tags:
    - archlinux
    - xfce
    - framework
keywords:
    - linux
    - archlinux
    - xfce
    - framework
thumbnailImage: xfce.png
thumbnailImagePosition: right
---

Di tulisan yang [sebelumnya](https://go2n.github.io/2012/10/10/tidak-ada-lagi-aif/) saya sempat mengeluh mengenai ribetnya instalasi Arch Linux tanpa AIF (Arch Installation Framework). Saya akui, memang tidak mengenakkan alias tidak manusiawi memasang Arch Linux tanpa AIF tersebut, ditambah dengan tidak adanya jaringan internet untuk PC saya. 😐
<!-- more -->

Namun, karena rasa penasaran saya tetep nekat memasang Arch Linux meski tanpa AIF. Hal yang paling *mumet* saat akan instalasi adalah bagaimana membuat PC yang saya *ihik* bisa mengambil repository dari laptop saya. Pada awalnya saya berencana untuk menyalin repository ke harddisk eksternal. Tetapi karena tidak punya, ya apa boleh buat? Gagal wis rencana saya. Akhirnya saya minta kabel LAN P2P pada teman *mburuh* untuk menghubungkan PC dengan laptop. Nah! Kalo gini caranya malah bisa buat konek ke internet juga. 😂

Untuk pengambilan repository, cukup atur kartu jaringan laptop dan PC dihubungkan dengan kabel LAN kemudian nyalakan layanan httpd untuk server repository. Ada sedikit kendala sewaktu saya mengatur server repository tersebut. Saya belum membuat alias direktori untuk repository agar bisa diakses melalui http. Setelah membuat alias ternyata akses forbidden. Nah lho! Kenapa lagi ini? Usut punya usut ternyata alias pada konfigurasi `httpd.conf` ada yang kurang. Pwekkkoookk 🤣

```
Alias /repository "/hdd/warehouse/software/repos/"
    <Directory "/hdd/warehouse/software/repos/">
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
```

Harusnya seperti berikut ini:

```
Alias /repository "/hdd/warehouse/software/repos/"
    <Directory "/hdd/warehouse/software/repos/">
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
```

Sukses mengatur layanan httpd di server repository (laptop), instalasi Arch Linux tanpa AIF pun berjalan dengan lancar. Setelah instalasi selesai saya reboot PC, dan hasilnya: **kernel panic!** 😱

{% image fancybox center clear nocaption kernel-panic.jpg "Kernal Panic" %}

Heuheuheu… ternyata ada yang salah. Berdasarkan investigasi, kesalahan tersebut gara-gara salah partisi root. Padahal pada saat instalasi saya mengikuti petunjuk dari wiki. Ternyata masalah kernel panic itu gara-gara syslinux mem-boot root namun partisinya bukan `/dev/sda1` tetapi `/dev/sda3`, padahal `/dev/sda3` adalah partisi swap. Dengan terpaksa mem-boot ulang dengan live-system menggunakan usb-flash untuk membenahi kesalahan pada `syslinux.cfg`. Reboot dan *sakses* masuk ke sistem Arch Linux yang masih *kinyis-kinyis.*

Satu masalah telah terselesaikan dan muncul masalah baru lagi. Masalah tersebut adalah root dinyatakan read-only. Walaahh. Masalah tersebut terletak pada kesalahan mount point `/dev/sda1` yang seharusnya pada `/` tetapi di-mount-kan ke `/mnt`. Asal kesalahan tersebut terjadi saat `# genfstab -p /mnt >> /mnt/etc/fstab` pada proses instalasi. Ppfftt…

Setelah memastikan tidak ada masalah, saya coba memasang berbagai macam paket dan berjalan dengan lancar. Untuk memasang paket dari AUR (Arch User Repository), PC memerlukan koneksi internet. Hmm… ini bukan masalah, cukup berbagi koneksi dengan laptop yang terhubung langsung dengan internet melalui kabel. Dengan pengaturan dan perintah `iptables` berikut ini, laptop sudah siap berbagi koneksi dengan PC:

```
[root@archlinux me]# ifconfig eth0 192.168.0.1 netmask 255.255.255.0
[root@archlinux me]# ip link set eth0 up
[root@archlinux me]# sysctl net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
[root@archlinux me]# iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

Pengaturan IP, gateway dan nameserver pada PC:

```shell
[root@archlinux]# ifconfig eth0 192.168.0.2 netmask 255.255.255.0
[root@archlinux]# ip link set eth0 up
[root@archlinux]# route add default gw 192.168.0.1
[root@archlinux]# echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```

Pasang paket dari AUR pun lancar jaya. Hehehe… Berikut ini penampakan PC yang berhasil saya *ihik*:

{% image fancybox center clear nocaption xfce.png "Desktop XFCE nangkring di PC" %}

Sebagai pengguna KDE saya merasa gagal 😐
