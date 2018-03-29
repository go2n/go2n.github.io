---
layout: post
title: "Lupa Password Root MySQL di FreeBSD"
description: "Sekedar catatan saja saat lupa password root MySQL di mesin FreeBSD"
date: 2015-03-12
categories:
    - notes
    - freebsd
tags:
    - freebsd
    - mysql
    - database
keywords:
    - freebsd
    - mysql
    - database
comments: True
---
> _Sekedar catatan saja saat lupa password root MySQL di mesin FreeBSD._

Ubah /etc/rc.conf, buka komentar pada mysql_args, restart MySQL dan login. Dengan asumsi isi dari mysql_args adalah `"--skip-grant-tables --skip-networking"`
<!--more-->

{% codeblock lang:shell %}
[root@server] # perl -pi -e "s/#mysql_args/mysql_args/g" /etc/rc.conf
[root@server] # /usr/local/etc/rc.d/mysql-server restart
[root@server] # mysql -u root
{% endcodeblock %}

Ubah Password

{% codeblock lang:sql %}
mysql> UPDATE mysql.user SET Password=PASSWORD('PASSWORD BARU') WHERE user='root';
{% endcodeblock %}

Edit /etc/rc.conf, berikan komentar pada mysql_args dan restart MySQL

{% codeblock lang:shell %}
[root@server] # perl -pi -e "s/mysql_args/#mysql_args/g" /etc/rc.conf
[root@server] # /usr/local/etc/rc.d/mysql-server restart
{% endcodeblock %}

Udah gitu aja, tinggal login MySQL dengan password root yang baru.
