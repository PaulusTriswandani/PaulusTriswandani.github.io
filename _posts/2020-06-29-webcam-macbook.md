---
title: Instalasi webcam tidak jalan di Macbook versi lama?
layout: default
author: Paulus Triswandani
categories: [linux]
comments: true
---

Berikut ini adalah cara meng-install webcam di macbook white 2008.

Saya berusaha melakukan instalasi webcam pada macbook di ubuntu saya. Saya sudah mencobanya selama 2 jam, dan akhirnya saya berhasil. Sebelum itu mari kita bahas cara yg tdk berhasil.

Pertama kali saya menemukan [artikel ini](https://askubuntu.com/questions/990218/camera-not-working-on-macbook-pro) di google. Saya kira dengan mengikuti langkah2 di sini saya akan berhasil, tapi ternyata saya gagal.

Akhirnya saya menemukan [link ini](https://turanct.wordpress.com/tag/appleusbvideosupport/) dan mengikuti langkah2 di dalamnya dan saya berhasil!

Berikut ini adalah langkah2 yg menurut saya penting :
- download AppleUSBVideoSupport dari [link ini](http://dalmano.bplaced.net/turanct.zym.backup/AUVideoS.zip)
- extract file zip tersebut, misalnya ke /home/user/opt
- lakukan update repository dengan "sudo apt update"
- lakukan install isight firmware tools dengan "sudo apt install isight-firmware-tools"
- pada saat instalasi akan ditanyakan verifikasi dan lokasi tempat firmware yg akan kita convert dari AppleUSBVideo ke isight.fw, jawab y dan masukkan lokasi misalnya /home/user/opt/AppleUSBVideoSupport
- restart dan selamat menikmati!