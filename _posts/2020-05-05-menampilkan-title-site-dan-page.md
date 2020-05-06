---
title: Jekyll From Scratch - Cara menampilkan site.title dan page.title
layout: default
author: Paulus Triswandani
categories: [jekyll]
---

Buat file \_config.yml yg isinya :
```
title: blog
```

Buat folder dan file _layouts/default.html yg isinya :
```
<html>
<head>
	<title>{% raw %} {{ page.title }} | {{ site.title }} {% endraw %}</title>
</head>
</html>
```
Buat index.html yg isinya :
```
---
layout: default
---
```
Buat folder dan file _posts/2020-05-06-postingan-pertama.md yg isinya :
```
---
title: Post
layout: default
---
```
Maka akan bisa dilihat perbedaannya di bagian title bar.
SELESAI