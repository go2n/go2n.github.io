---
title: Ganti Nama Branch di Git
date: 2018-03-27 11:00:10
categories: notes
tags: git
---

> Sebuah catatan biar nggak lupa perintah git

Ada 2 perintah yang bisa digunakan untuk untuk mengganti nama branch:
{% codeblock lang:bash %}
git branch -m blog-posts # « jika sedang berada di branch yang akan diganti nama
git branch -m blog-source blog-posts # « jika sedang berada di branch lain
{% endcodeblock %}

<!-- more -->Hapus remote branch-lama:
{% codeblock %}
$ git push origin -d blog-source
To github.com:go2n/go2n.github.io.git
 - [deleted]         blog-source
{% endcodeblock %}

Push remote branch-baru:
{% codeblock %}
$ git push origin blog-posts 
Counting objects: 127, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (110/110), done.
Writing objects: 100% (127/127), 3.67 MiB | 732.00 KiB/s, done.
Total 127 (delta 26), reused 32 (delta 0)
remote: Resolving deltas: 100% (26/26), done.
To github.com:go2n/go2n.github.io.git
 * [new branch]      blog-posts -> blog-posts
{% endcodeblock %}

Atur upstream untuk branch baru:
{% codeblock %}
$ git push -u origin blog-posts 
Branch 'blog-posts' set up to track remote branch 'blog-posts' from 'origin'.
Everything up-to-date
{% endcodeblock %}

Rujukan: [manpage git-branch](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-branch.html)
