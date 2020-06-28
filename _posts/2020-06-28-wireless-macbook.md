---
title: Instalasi linux tidak jalan di Macbook? Wireless error?
layout: default
author: Paulus Triswandani
categories: [linux]
comments: true
---

Berikut ini adalah cara untuk mengatasi hardware wireless yg tidak terdeteksi di instalasi linux (debian, ubuntu, dan mungkin varian debian yg lain) pada macbook.

Sebenarnya bukan tidak terdeteksi tapi firmware yg bersangkutan tidak ditemukan pada instalasi yg biasa. Untuk mengatasi ini anda dapat men-download 2 file yg dibutuhkan yaitu :
- b43-fwcutter (file .deb)
- broadcom-wl-5.100.138.tar.bz2 (di websitenya lwfinger)

Anda bisa mencarinya di google untuk kedua file tersebut. Setelah itu copy manual ke macbook yg tidak bisa terkoneksi ke internet akibat wirelessnya tidak jalan. Setelah itu buka terminal pada macbook anda dan ketikkan :
```
sudo dpkg -i b43-fwcutter_019-4_amd64.deb
tar xfvj broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
```

Mungkin versi fwcutter ataupun firmware broadcom yg mengalami update berkala bisa berbeda. Tapi saat artikel ini ditulis, begitulah selengkapnya cara menjalankan wireless pada macbook yg di-install linux.

Selamat menikmati.