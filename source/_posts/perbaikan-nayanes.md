---
layout: post
title: "Perbaikan Nayanes"
date: 2014-03-19
categories: iseng
tags:
    - php
    - html
    - slims
    - senayan
    - perpustakaan
    - library
keywords:
    - php
    - html
    - slims
    - senayan
    - perpustakaan
    - library
comments: True
thumbnailImagePosition: right
thumbnailImage: https://go2n.github.io/2014/03/19/perbaikan-nayanes/2014-03-19-perbaikan-nayanes-single.png
---

Saya merasa ada yang aneh dengan hasil pencarian katalog dengan Nayanes pada pencarian di satu lokasi. Nayanes menampilkan semua hasil pencarian pada setiap lokasi (node) dengan mode pencarian semua lokasi (multiple node search).
<!-- more -->

{% image fancybox nocaption center 2014-03-19-perbaikan-nayanes.png "Nayanes node search" %}

Namun saat Nayanes melakukan pencarian katalog pada satu lokasi (single node search) tidak ada hasil yang ditampilkan. Padahal tidak ada pesan kesalahan, aneh to? 😕

Pada mode multiple search node dengan kata kunci pencarian dan lokasi yang sama ada 574 rekaman yang ditampilkan. Nah piye jal? Saking frustasinya saya pun minta bantuan pak Aziz untuk membantu memperbaiki Nayanes.

Perubahan kode `lib/contents/search.inc.php`:

{% codeblock  %}
$('.no-result-list').append('<li>REQUEST TIMEOUT from <strong><?php echo $node_data['desc']; ?></strong></li>')
{% endcodeblock %}

menjadi:

{% codeblock  %}
$('.no-result-list').append('<li>REQUEST TIMEOUT from <strong><?php echo $sysconf['node'][$nodeid]['desc']; ?></strong></li>')
{% endcodeblock %}

Setelah diuji coba, akhirnya ada hasil pencarian yang ditampilkan. Memang pak Aziz, senior saya ini juara! Jios pokoke! 👍🏼

{% image fancybox center 2014-03-19-perbaikan-nayanes-single.png "Single node search" %}

#### Nayanes repository:
[https://github.com/go2n/nayanes](https://github.com/go2n/nayanes)
