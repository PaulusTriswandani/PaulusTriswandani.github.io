---
title: Cryptography Caesar
layout: default
author: Paulus Triswandani
categories: [cryptography]
comments: true
---

Sekarang saya ingin membahas [kriptografi caesar](https://id.wikipedia.org/wiki/Sandi_Caesar).

Anda bisa melakukannya di terminal. Sistem operasi yg saya gunakan adalah Ubuntu. Pertama2 install dulu bsdgames :
```
sudo apt install bsdgames
```

Setelah itu anda bisa menggunakan perintah caesar dan rot13. rot13 adalah caesar yg digeser 13 karakter. Cara menggunakannya yg mudah adalah dengan memanfaatkan perintah echo dan |.
```
echo "abc" | caesar 13
echo "abc" | rot13
```

Sebenarnya anda jg bisa menggunakan perintah yg sedikit lebih rumit untuk terminal. Terminal biasanya ada perintah tr. Ini bisa anda gunakan untuk melakukan pergeseran karakter, tapi karena lebih rumit, jadi yah jadi alternatif saja. Berikut ini caranya :
```
echo "abc" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Berikut adalah kodenya bila menggunakan python
```python
import sys

def encrypt(text,s):
	result = ""
	for i in range(len(text)):
		char = text[i]

		if (char.isupper()):
			result += chr((ord(char) + s - 65) % 26 + 65)
		else:
			result += chr((ord(char) + s - 97) % 26 + 97)
	return result

if __name__ == "__main__":
	print(encrypt(sys.argv[1],int(sys.argv[2])))
```

Penjelasannya sedikit panjang. Pertama adalah kata def adalah bentuk untuk membuat fungsi yaitu fungsi dengan nama encrypt. Fungsi tersebut menerima dua parameter yaitu text(kata yg akan dienkripsi) dan s(banyaknya karakter akan digeser). Result akan dikembalikan pada akhir fungsi yaitu return result. for adalah perulangan (looping). range(len(text)) adalah berapa banyak perulangannya akan dijalankan, dalam hal ini mengacu pada jumlah karakter pada text. Kemudian ada variabel char yg diisi dengan karakter dari text yg ke i. Lalu ada if (percabangan). char(isupper()) memeriksa apakah variabel char huruf besar, digunakan dengan if else jadi percabangan bila huruf besar lakukan ini, bila huruf kecil lakukan itu. chr dan ord istilahnya adalah casting. chr mengubah tipe yg tadinya integer menjadi character. ord mengubah tipe yg tadinya character menjadi integer. Angka 65 adalah integer dari huruf A (a kapital), dan angka 97 adalah integer dari huruf a (a kecil). % adalah sisa pembagian.

Jadi cerita dari kode ini adalah komputer menyimpan huruf A-Z dan a-z secara berurutan tapi di rentang yg berbeda. A-Z adalah dari angka 65-90, sedangkan a-z adalah angka 97-122. Kita butuh mekanisme yg menerjemahkan angka2 ini menjadi karakter, karena kita tahu rentangnya adalah 26 karakter, maka angka2 tersebut dikurangi terlebih dahulu huruf pertama dan diambil sisa pembagian oleh angka 26, lalu dikembalikan menjadi karakter.

Bagaimana, susah kan jadi programmer. Makanya jadi petani atau peternak saja. Ini baru bahasa komputernya, cara menyelesaikan masalah adalah hal lain. Atau gunakan program jadi dan fokus pada penyelesaian masalah.