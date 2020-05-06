---
title: Jekyll From Scratch - Quick Start
layout: default
author: Paulus Triswandani
categories: [jekyll]
---

Install dependency ruby, rubygems, gcc, g++, dan make. Cara instalasi bergantung dari sistem operasi yg dimiliki pengguna. Silakan [klik di sini](https://jekyllrb.com/docs/installation/) untuk link terkait. Sistem operasi yg saya miliki adalah linux ubuntu, maka cara2 berikut ini adalah cara menginstall-nya di linux ubuntu.

Pastikan perintah berikut tidak mengembalikan pesan error :
```
ruby -v
```
```
gem -v
```
```
gcc -v
```
```
g++ -v
```
```
make -v
```
Bila perintah2 di atas tidak menghasilkan error, jalankan perintah gem install berikut :
```
gem install jekyll bundler
```
Bila perintah di atas menghasilkan error, mungkin perlu sudo untuk menjalankannya. Jalankan perintah di atas dengan sudo seperti berikut ini :
```
sudo gem install jekyll bundler
```
Pastikan perintah jekyll -v berikut tidak menghasilkan error :
```
jekyll -v
```
Pada tahap ini jekyll sudah terinstall di sistem anda.

Untuk memulai dengan cepat silakan gunakan perintah berikut untuk men-generate kode jekyll dengan [theme minima](https://github.com/jekyll/minima) :
```
jekyll new myblog
```
myblog di sini adalah nama folder home dari website yg ingin anda buat. Kemudian anda bisa change directory ke folder myblog, lalu jalankan perintah berikut untuk menjalankan web servernya :
```
bundle exec jekyll serve
```
Perintah ini sebenarnya ada dua yg dijalankan, bundle exec dan jekyll serve. Bundle exec akan mengeksekusi Gemfile yg terkait dengan theme yg bersangkutan, dan jekyll serve akan menjalankan web server.

Jalankan browser seperti firefox atau chrome, dan masukkan :
```
localhost:4000
```

SELESAI