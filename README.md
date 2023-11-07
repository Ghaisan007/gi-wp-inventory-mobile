__Nama    : Ghaisan Luqyana Aqila__

__NPM     : 2206830460__

__Kelas   : PBP A__



Program ini didesain untuk membuat sebuah _Weapon Inventory_ untuk game Genshin Impact dalam mobile. 

Berikut adalah shortcut untuk tugas :

- [Tugas 7](#tugas-7)

#  Tugas 7

## Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?

Dalam konteks pengembangan aplikasi Flutter, perbedaan utama antara _stateless_ dan _stateful widget_ terletak pada cara mereka menangani perubahan data dan interaksi pengguna.

1. **Stateless Widget**
- **Karakteristik Utama**: _Stateless widget_ adalah widget yang tidak menyimpan status (_state_) internal. Setiap kali ada perubahan yang diperlukan, widget ini dirender ulang secara keseluruhan. _Stateless widget_ tidak memiliki informasi status internal atau tidak bisa berubah seiring waktu.
- **Kapan Digunakan**: _Stateless widget_ cocok untuk widget yang tidak memerlukan perubahan status internal, seperti widget yang hanya menampilkan teks statis, gambar, atau tata letak statis yang tidak berubah.

2. **Stateful Widget**
- **Karakteristik Utama**: _Stateful widget_ adalah widget yang menyimpan status (state) internal dan dapat diperbarui seiring waktu. Hal ini memungkinkan untuk memperbarui tampilan widget secara dinamis berdasarkan interaksi pengguna atau perubahan data. _Stateful widget_ dapat memicu pembaharuan pada bagian-bagian tertentu tanpa harus merender ulang seluruh widget.
- **Kapan Digunakan**: _Stateful widget_ digunakan ketika perlu memperbarui atau mengelola status internal widget, misalnya ketika perlu menangani input _user_, mengubah tampilan berdasarkan kondisi tertentu, atau ketika memerlukan perubahan dinamis pada tata letak aplikasi.

## Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.

- `MaterialApp`: MaterialApp adalah widget yang mengimplementasikan desain material dari Google. Ini adalah root widget dari aplikasi Flutter yang memungkinkan untuk mengatur hal-hal seperti judul aplikasi, tema, bahasa, rute, dan sebagainya.
- `ThemeData`: ThemeData adalah kelas yang berisi konfigurasi tema untuk aplikasi, seperti warna, tipografi, dan faktor gaya lainnya yang memungkinkan untuk menyesuaikan tampilan visual aplikasi secara konsisten.
- `ColorScheme`: ColorScheme adalah kumpulan warna yang direpresentasikan oleh berbagai properti, seperti warna primer, warna aksen, dan warna latar belakang. Widget ini digunakan untuk menetapkan skema warna secara konsisten di seluruh aplikasi.
- `Scaffold`: Scaffold adalah widget yang mengimplementasikan struktur dasar dari tata letak aplikasi material. Widget ini menyediakan bingkai visual untuk menempatkan elemen-elemen seperti AppBar, body content, bottom navigation, dan sebagainya.
- `AppBar`: AppBar adalah komponen UI yang menampilkan judul, tindakan, dan mungkin juga ikon. AppBar sering digunakan sebagai bagian atas (header) dari antarmuka pengguna.
- `Text`: Text adalah widget yang digunakan untuk menampilkan teks di antarmuka pengguna sehingga dapat menyesuaikan gaya teks, ukuran, dan berbagai atribut lainnya.
- `Padding`: Padding adalah widget yang menambahkan jarak kosong (padding) di sekeliling widget yang diberikan. Padding membantu dalam mengatur ruang di antara elemen-elemen antarmuka pengguna.
- `Column`: Column adalah widget yang menyusun widget-child secara vertikal, dari atas ke bawah. Column berguna ketika kita perlu menampilkan beberapa widget secara berurutan.
- `GridView.count`: GridView.count adalah widget yang menyusun widget-child dalam bentuk grid dengan jumlah kolom yang ditentukan. Widget ini berguna untuk menampilkan daftar item dalam bentuk grid.
- `Material`: Material adalah widget yang menerapkan efek material design pada widget-childnya. Material memberikan respons visual seperti efek bayangan dan tepi yang menonjol.
- `InkWell`: InkWell adalah widget yang memberikan respons saat ditekan, seperti animasi efek air ketika tombol ditekan.
- `Container`: Container adalah widget yang memungkinkan untuk menyesuaikan tata letak, dekorasi, padding, dan sebagainya. Ini adalah wadah serbaguna untuk menempatkan elemen-elemen lain.
- `Icon`: Icon adalah widget yang menampilkan ikon yang dapat dipilih dari kumpulan ikon bawaan di Flutter atau ikon kustom.
- `SnackBar`: SnackBar adalah widget untuk menampilkan pesan singkat kepada pengguna. SnackBar biasanya digunakan untuk memberi tahu pengguna tentang status aplikasi atau tindakan yang sedang dilakukan.

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)

1. Pertama-tama, _generate_ proyek Flutter baru dengan nama **gi_wp_inventory**.
2. Dibuat file baru dengan nama `menu.dart` pada direktori `gi_wp_inventory/lib`. Selanjutnya tambahkan import seperti berikut : 
```dart
import 'package:flutter/material.dart';
```
3. Pada file `main.dart`, ditambahkkan import sebagai berikut :
```dart
import 'package:flutter/material.dart';
import 'package:gi_wp_inventory/menu.dart';
```
4. Pada file `main.dart`, ditambahkan tipe Material Color sebagai berikut :
```dart
colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
```
Lalu `MyHomePage(title: 'Flutter Demo Home Page')` diubah menjadi `MyHomePage()`.
5. Pada `menu.dart`, dilakukan perubahan untuk `class MyHomePage` menjadi seperti berikut, dan menghapus fungi **State** yang ada di bawah stateless widget tersebut :
```dart
class MyHomePage extends StatelessWidget {
  MyHomePage({Key? key}) : super(key: key);

  final List<ShopItem> items = [
    ShopItem("Lihat Produk", Icons.checklist, Colors.green),
    ShopItem("Tambah Produk", Icons.add_shopping_cart, Colors.redAccent),
    ShopItem("Logout", Icons.logout, Colors.orange),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'Genshin Impact Weapon Inventory',
          style: TextStyle(color: Colors.white),
        ),
        backgroundColor: Colors.indigo,
      ),
      body: SingleChildScrollView(
        child: Padding(
          padding: const EdgeInsets.all(10.0),
          child: Column(
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                child: Text(
                  'PBP Shop',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              GridView.count(
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```
6. Selanjutnya, didefinisikan list untuk `ShopItem` sebagai berikut :
```dart
class ShopItem {
  final String name;
  final IconData icon;
  final Color color;
  ShopItem(this.name, this.icon, this.color);
}
```
7. Selanjutnya, dibuat _widget stateless_ baru untuk menampilkan _card_ sebagai berikut :
```dart
class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key}); // Constructor

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        child: Container(
          // Container untuk menyimpan Icon dan Text
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```