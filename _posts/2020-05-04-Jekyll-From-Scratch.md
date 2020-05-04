---
title: Jekyll From Scratch - Cara menampilkan site.title dan page.title
layout: post
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
title: Home
layout: default
---
```
SELESAI