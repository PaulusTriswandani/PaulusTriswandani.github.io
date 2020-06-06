---
title: Jekyll From Scratch - Cara menginstall theme
layout: default
author: Paulus Triswandani
categories: [jekyll]
comments: true
---

Sebenarnya cara menginstall theme dapat dilihat dari github resmi theme yg mau di-install. Pada kasus ini adalah [theme architect](https://github.com/pages-themes/architect). Theme architect ini memiliki license [Creative Commons Zero](https://creativecommons.org/share-your-work/public-domain/cc0/), jadi kita bebas menggunakannya tanpa batasan apapun.

Berikut ini adalah cara menginstallnya di sistem operasi ubuntu :
```
sudo gem install github-pages
```

Tambahkan baris ini di file _config.yml :
```
theme: jekyll-theme-architect
```

Tambahkan baris ini di file Gemfile :
```
gem "github-pages", group: :jekyll_plugins
```