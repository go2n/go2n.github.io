---
title: Membuat kamus dengan bahasa C
date: 2008-11-29 05:25
categories: linux
tags:
    - sql
    - sqlite
    - kamus
    - gcc
keywords:
    - linux
    - sql
    - sqlite
    - kamus
    - gcc
thumbnailImage: ./kamus.c.png
thumbnailImagePosition: right
---

Membuat kamus sendiri? Mungkin nggak ya…? Jawabannya adalah mungkin. Dengan memanfaatkan bahasa C, kompiler GCC dan SQLite 3 beserta pustakanya, kita bisa membuat kamus sendiri. Tak perlu interface yang canggih dan keren, yang penting kamus yang dibuat berguna. Pada contoh ini kamus yang dibuat berjalan pada modus command line. Source code pada contoh ini berdasarkan pada dokumentasi [SQLite](http://www.sqlite.org/).
<!-- more -->

Sebelum mulai menulis kodenya, pastikan SQLite3 dan pustaka devel-nya serta kompiler GCC sudah terinstall dengan baik pada komputer anda. Langkah-langkah yang dilakukan adalah sebagai berikut:

1. Buat database kamus dengan schema sebagai berikut:

   ```sqlite
   CREATE TABLE inggris (kata text, definisi text);
   CREATE TABLE indonesia (kata text, definisi text);
   ```

   Kemudian etik perintah berikut pada konsole/terminal anda:

   ```shell
   shell> sqlite3 kamus.db
   SQLite version 3.4.1
   Enter ".help" for instructions
   sqlite> CREATE TABLE inggris (kata text, definisi text);
   sqlite> CREATE TABLE indonesia (kata text, definisi text);
   ```

2. Isi kamus tersebut sesuai dengan bahasa yang hendak diisi, misalkan:

   ```
   sqlite> INSERT INTO inggris VALUES ('a', 'kb. huruf pertama dalam abjad Inggris. 2 angka yang baik sekali. 3 nada A. A- bomb bom atom. A-1 ks. 1 kelas satu. 2 ulung.')
   ```

3. Ketik kode program berikut:

   {% codeblock lang:c %}
   /*
   **  Copyright (C) 2008, Gogon
   **
   **  Lisensi: GNU General Public License
   **
   **  kamus.c v 0.0.1
   **
   */
    
   #include <stdio.h>
   #include <sqlite3.h>
    
   /*
   ** Fungsi untuk menampilkan hasil pencarian
   ** Berdasarkan pada dokumentasi SQLite3
   */
    
   static int hasil(void *GaKepake, int argc, char **argv, char **kolom)
   {
       printf("Kata: %s\n", argv[0] ? argv[0] : "NULL");
       printf("Arti: %s\n", argv[1] ? argv[1] : "NULL");
       printf("\n");
       return 0;
   }
    
   int main(int argc, char **argv)
   {
       sqlite3 *db;
       char *pesanErr = 0;
       char *cari = sqlite3_mprintf("SELECT kata, definisi FROM(%Q) WHERE kata=(%Q)", argv[2], argv[3]);
       int request;
    
       if( argc!=4 )
       {
           /*
           ** Buat menampilkan cara penggunaan kamus
           */
           fprintf(stdout, "\nKamus versi 0.0.1\n(c) 2008 Gogon\n");
           fprintf(stdout, "\nPenggunaan: %s [DATABASE] [BAHASA] [KATA-YANG-DICARI]\n", argv[0]);
           fprintf(stdout, "\nBahasa:\n");
           fprintf(stdout, "\tinggris, cari arti Indonesia dari kata bahasa Inggris\n");
           fprintf(stdout, "\tindonesia, cari arti Inggris dari kata bahasa Indonesia\n\n");
    
           return 1;
       }
    
       request = sqlite3_open(argv[1], &db);
    
       if( request )
       {
           fprintf(stderr, "Tidak dapat membuka database: %s\n", sqlite3_errmsg(db));
           sqlite3_close(db);
           return 1;
       }
    
       request = sqlite3_exec(db, cari, hasil, 0, &pesanErr);
    
       if( request!=SQLITE_OK )
       {
           fprintf(stderr, "SQL error: %s\n", pesanErr);
           sqlite3_free(pesanErr);
       }
    
       sqlite3_close(db);
       return 0;
   }
   {% endcodeblock %}

4. Kompilasi kode tersebut dengan gcc:

   ```
   shell> gcc -o kamus kamus.c `pkg-config --cflags --libs sqlite3`
   ```

   atau

   ```
   shell> gcc -o kamus kamus.c -lsqlite3
   ```

5. Jalankan kamus hasil kompilasi. Ada 3 parameter yang harus dimasukkan pada saat menjalankan kamus, yaitu **[DATABASE] [BAHASA] [KATA-YANG-DICARI]**, misalkan:

   ```
   shell> ./kamus kamus.db inggris a
   Kata: a
   Arti: kb. huruf pertama dalam abjad Inggris. 2 angka yang baik sekali. 3 nada A. A- bomb bom atom. A-1 ks. 1 kelas satu. 2 ulung.
   ```

6. Apabila parameter yang dimasukkan kurang dari 3 atau lebih maka kamus akan menampilkan keluaran sebagai berikut:

   ```
   shell> ./kamus kamus.db inggris
   Kamus versi 0.0.1
   (c) 2008 Gogon
    
   Penggunaan: kamus [BAHASA] [KATA-YANG-DICARI]
    
   Bahasa:
           inggris, cari arti Indonesia dari kata bahasa Inggris
           indonesia, cari arti Inggris dari kata bahasa Indonesia
   ```

Selesai…dan kamus siap digunakan. 😁
