---
title: Bagaimana Memecahkan Cryptography Caesar?
layout: default
author: Paulus Triswandani
categories: [cryptography]
comments: true
---

Setelah kita membahas bagaimana mengamankan pesan kita pada blog cryptography caesar, sekarang kita akan membahas bagaimana memecahkannya. Kalau kita mengamankan pesan kita dengan rot13, maka cara memecahkannya mudah saja. Kita tingggal menggunakan fungsi yg sama pada pesan terenkripsi kita. Sebelumnya kita sudah membahas program caesar dan rot13 yg di-install di sistem operasi linux ubuntu. Sebagai contoh kita bisa memecahkan pesan rot13 dengan mudah menggunakan program ini.

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
	if(len(sys.argv)==3):
		print(encrypt(sys.argv[1],int(sys.argv[2])))
	else:
		for i in range(26):
			print(encrypt(sys.argv[1],i))
```

Hanya ada sedikit penyesuaian dari program pada blog sebelumnya. Fungsi encrypt sama persis. Pada if __name___ terdapat len(sys.argv). Fungsi len ini membaca banyaknya argumen pada perintah di terminal. Misalnya kita men-save kode di atas ke file caesar.py lalu menggunakan perintah :
```
python caesar.py "IniPlainText" 13
```

Fungsi len(sys.argv) akan mengembalikan angka tiga. Yg pertama adalah sys.argv[0] yg merupakan file yg kita panggil yaitu caesar.py. Yg kedua, sys.argv[1] merupakan "IniPlainText". Sedangkan yg ketiga adalah 13. Perlu diingat bahwa semua yg dikenali oleh sys berbentuk string, jadi argumen ketiga yaitu 13 berbentuk string. Jadi perlu di-casting ke angka bila ingin digunakan di fungsi encrypt.

Berikutnya coba kita coba pecahkan pesan terenkripsi "VavCynvaGrkg". Kalau kita sudah tahu pesan terenkripsi itu digeser berapa banyak maka mudah saja. Misalkan kita memakai rot13. Maka kita tinggal menggunakan perintah :
```
python caesar.py "VavCynvaGrkg" 13
```

Tapi bila kita tidak tahu sebelumnya pesan terenkripsi itu harus digeser berapa banyak, maka kita dapat melakukan brute force dengan perintah:
```
python caesar.py "VavCynvaGrkg"
```

Perintah di atas akan melakukan pergeseran sebanyak 0 sampai 25 kali dan menampilkannya di terminal. Kalau kita ingin program kita mengetahui bahwa kita memasukkan bahasa Indonesia itu lebih rumit lagi. Kita harus me-list kata2 bahasa Indonesia yg akan digunakan dan mencocokkannya dengan hasil brute force kita. Ini yg jauh lebih sederhana. Bagaimana kalau kita memasukkan spasi maka spasi itu tidak akan diproses di fungsi encrypt? Bahasan ini akan kita lakukan di blog selanjutnya.