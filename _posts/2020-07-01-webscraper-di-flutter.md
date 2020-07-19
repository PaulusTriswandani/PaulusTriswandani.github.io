---
title: Web Scraper di Flutter
layout: default
author: Paulus Triswandani
categories: [flutter]
comments: true
---

Saya mencoba hasil pertama googling dengan kata kunci web scraper di flutter dan ternyata berhasil, tapi tidak lengkap.

Berikut adalah sumber yg saya ambil : [https://medium.com/@almanalfaruq/flutter-beginner-tutorial-web-scraping-untuk-manga-reader-part-1-2bf27db3a643](https://medium.com/@almanalfaruq/flutter-beginner-tutorial-web-scraping-untuk-manga-reader-part-1-2bf27db3a643)

Mengedit pubspec.yaml
```
dependencies:
  http: ^0.12.0+2
  html: ^0.14.0+2
  url_launcher: ^5.1.3
```

Struktur folder di folder lib :
- mangascan
	- helper.dart
	- manga.dart
- main.dart

Isi dari manga.dart :
```
class Manga {
  String title;
  String url;

  Manga({this.title, this.url});
}
```

Isi dari helper.dart :
```
import 'package:http/http.dart';
import 'package:jubei/mangascan/manga.dart';
import 'package:html/dom.dart';
import 'package:html/parser.dart';

class Helper {

  Client _client;

  Helper() {
    this._client = Client();
  }

  Future<List<Manga>> getAllManga() async {
    List<Manga> allManga = [];
    final response = await _client.get('http://www.mangacanblog.com/daftar-komik-manga-bahasa-indonesia.html');
    final document = parse(response.body);
    final mangasPerTitle = document.getElementsByClassName('blix');
    for (Element mangaPerTitle in mangasPerTitle) {
      final mangas = mangaPerTitle.getElementsByTagName('li');
      for (Element m in mangas) {
        final aTag = m.getElementsByTagName('a')[0];
        final title = aTag.text;
        final url = aTag.attributes['href'];
        final manga = Manga(title: title, url: url);
        allManga.add(manga);
      }
    }
    return allManga;
  }
}
```

Isi dari main.dart :
```
import 'package:flutter/material.dart';
import 'package:jubei/mangascan/helper.dart';
import 'package:jubei/mangascan/manga.dart';
import 'package:url_launcher/url_launcher.dart';

/**
  ..
  Kode void main()
  Kode MyHomePage extends StatefulWidget
  ..
**/

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "Mangascan",
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title:'Hello Manga')
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  Helper _helper = Helper();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: FutureBuilder<List<Manga>>(
        initialData: List<Manga>(),
        future: _helper.getAllManga(),
        builder: (BuildContext context, AsyncSnapshot<List<Manga>> snapshot) {
          switch(snapshot.connectionState) {
            case ConnectionState.active:
            case ConnectionState.waiting:
              return Center(
                child: RefreshProgressIndicator(),
              );
            case ConnectionState.none:
              return Center(
                child: Text('Tidak ada koneksi'),
              );
            case ConnectionState.done:
              if (snapshot.hasError) {
                return Center(
                  child: Text('Data yang diterima salah'),
                );
              }
              return ListView.builder(
                itemCount: snapshot.data.length,
                itemBuilder: (context, index) {
                  return ListTile(
                    leading: Icon(Icons.book),
                    title: Text(snapshot.data[index].title),
                    onTap: () async {
                      if (await canLaunch(snapshot.data[index].url)) {
                        await launch(snapshot.data[index].url);
                      }
                    },
                  );
                },
              );
          }
        },
      ),
    );
  }
}
```

Keterangannya lihat di sumber artikel yah. Soalnya saya jg gak ngerti kenapa bisa kayak gitu. Material design adalah hal yg baru bagi saya dan dasar bahasa pemrograman dart saya masih sangat rendah. Selamat menikmati.