---
title: Ngeblog pakai Hexo
date: 2018-03-11 19:29:50
category: blog
tags:
    - hexo
    - jekyll
    - archlinux
keywords:
    - blog
    - github
    - jekyll
    - hexo
    - archlinux
    - linux
comments: true
---

Sudah dua tahun lebih saya tidak ngeblog, cukup lama juga blog ini nggak kopèn. Setelah sekian lama, akhirnya kelakon juga saya menulis di sini lagi. Kali ini saya akan menulis tentang framework untuk membuat blog ini. Sebelumnya blog ini dibuat menggunakan [Jekyll](https://jekyllrb.com/) dan dihosting di [GitHub Pages](https://pages.github.com/).
<!--more-->

Jekyll, kalau boleh saya bilang framework ini lumayan ribet dan rumit. Biasanya sebelum posting ke blog, saya melakukan pratinjau di mesin Linux saya dengan perintah:

{% codeblock %}
$ jekyll serve
{% endcodeblock %}

Tapi, entah kenapa setelah melakukan ritual update di mesin Arch Linux saya waktu itu Jekyll tidak bisa dijalankan seperti biasanya. Sekalinya sudah bisa dijalankan tampilan blog tidak sesuai dengan yang saya atur sebelumnya. Itulah yang menjadi salah satu alasan kenapa blog ini tidak update selama ini. 😅

Sekitar pertengahan tahun 2017 yang lalu saya mendengar tentang [Hexo](https://hexo.io/). Setelah membaca artikel tentang Hexo saya punya rencana untuk mulai membuat blog dengan Hexo dan memindahkan tulisan-tulisan saya. Berhubung waktu itu saya tidak selo dan lupa (halah), maka baru hari ini saya memulainya. Kemungkinan tulisan-tulisan saya di blog yang lain juga akan dipindahkan ke blog ini. 😁

## Apa itu Hexo?

Hexo adalah framework blog yang cepat, sederhana dan powerfull yang didukung oleh Node.js. Hexo ini konon katanya super cepat, hanya membutuhkan waktu beberapa detik untuk membangun sebuah website lengkap. Dokumentasi lengkapnya ada di https://hexo.io/docs/.

### Fitur
* Blazing fast generating
* Mendukung Markdownnya GitHub dan plugin-plugin Octopress
* One-command deploy ke GitHub Pages, Heroku, dll
* Sistem plugin yang powerfull

### Instalasi

Untuk instalasi cukup gampang, yang penting `nodejs` dan `git` sudah diinstall di mesin:

{% codeblock %}
$ npm install hexo-cli -g
{% endcodeblock %}

Instalasi Hexo di Arch Linux melalui [AUR](https://aur.archlinux.org/) menggunakan `yaourt`, `packer` atau [program yang sejenisnya](https://wiki.archlinux.org/index.php/AUR_helpers):

{% codeblock %}
$ yaourt -S nodejs-hexo-cli
{% endcodeblock %}

### Ngeblog

Perintah yang digunakan untuk mulai membuat blog dengan Hexo:

{% codeblock lang:shell %}
$ hexo init <blog>
$ cd <blog>
$ npm install
{% endcodeblock %}

Isi dari direktori `blog`:

{% codeblock %}
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
{% endcodeblock%}

Konfigurasi blog ada edit berkas `_config.yml`. Info lebih lanjut: https://hexo.io/docs/configuration.html.

#### Membuat tulisan baru

Untuk membuat tulisan baru cukup gampang:

{% codeblock %}
$ hexo new post "Judul"
INFO  Created: ~/dev/github/blog/source/_posts/Judul.md
{% endcodeblock %}

Info lebih lanjut: https://hexo.io/docs/writing.html

#### Jalankan server

Untuk melihat pratinjau blog yang baru saja dibuat:

{% codeblock %}
$ hexo server
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
{% endcodeblock %}

Info lebih lanjut: https://hexo.io/docs/server.html

#### Generate berkas statis

Membuat berkas statis dengan Hexo cukup gampang dan cepat:

{% codeblock %}
$ hexo generate
INFO  Start processing
INFO  Files loaded in 213 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: fancybox/blank.gif
INFO  Generated: fancybox/jquery.fancybox.css
INFO  Generated: fancybox/jquery.fancybox.pack.js
INFO  Generated: fancybox/jquery.fancybox.js
INFO  Generated: fancybox/fancybox_loading.gif
INFO  Generated: fancybox/fancybox_loading@2x.gif
INFO  Generated: fancybox/fancybox_overlay.png
INFO  Generated: fancybox/fancybox_sprite.png
INFO  Generated: fancybox/fancybox_sprite@2x.png
INFO  Generated: archives/2018/03/index.html
INFO  Generated: archives/2018/index.html
INFO  Generated: css/fonts/FontAwesome.otf
INFO  Generated: js/script.js
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
INFO  Generated: css/fonts/fontawesome-webfont.eot
INFO  Generated: css/fonts/fontawesome-webfont.woff
INFO  Generated: css/style.css
INFO  Generated: fancybox/helpers/fancybox_buttons.png
INFO  Generated: css/images/banner.jpg
INFO  Generated: css/fonts/fontawesome-webfont.svg
INFO  Generated: css/fonts/fontawesome-webfont.ttf
INFO  Generated: 2018/03/11/hello-world/index.html
INFO  Generated: 2018/03/11/Judul/index.html
INFO  29 files generated in 710 ms
{% endcodeblock %}

Info lebih lanjut: https://hexo.io/docs/generating.html

#### Deploy

Sebelum deploy ke GitHub, pasang dulu plugin `hexo-deployer-git`:
{% codeblock lang:bash %}
$ npm install hexo-deployer-git --save # <~ dijalankan di dalam direktori blog
{% endcodeblock %}

Edit berkas `_config.yml` lalu atur bagian deployment:

{% codeblock %}
deploy:
  type: git
  repo: <repo github>
  branch: master
  message: <message>
{% endcodeblock %}

Info lebih lanjut: https://hexo.io/docs/deployment.html

Untuk deploy blog bisa menggunakan salah satu perintah di bawah ini:

{% codeblock lang:bash %}
$ hexo deploy       # <~ deploy blog
atau
$ hexo deploy -g    # <~ generate blog lalu deploy
atau
$ hexo generate -d  # <~ generate blog lalu deploy
{% endcodeblock %}

Yeaah! Sekarang [go2n.github.io](http://go2n.github.io) sudah pakai Hexo! 🤘 😎
