__Nama    : Ghaisan Luqyana Aqila__

__NPM     : 2206830460__

__Kelas   : PBP A__



Program ini didesain untuk membuat sebuah _Weapon Inventory_ untuk game Genshin Impact dalam mobile app berbasis framework _Flutter_. 

Berikut adalah shortcut untuk tugas :

- [Tugas 7](#tugas-7)
- [Tugas 8](#tugas-8)
- [Tugas 9](#tugas-9)

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

# Tugas 8

## Jelaskan perbedaan antara `Navigator.push()` dan `Navigator.pushReplacement()`, disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!

Dalam konteks pengembangan perangkat lunak menggunakan Flutter, `Navigator` adalah bagian dari Flutter framework yang digunakan untuk mengelola tumpukan halaman (page stack) dalam aplikasi. Dua metode yang disebutkan, `Navigator.push()` dan `Navigator.pushReplacement()`, memiliki perbedaan dalam cara mereka memanipulasi tumpukan (stack) halaman.

Perbedaan antara `Navigator.push()` dan `Navigator.pushReplacement()` adalah sebagai berikut :
1. **Method `push()`**: menambahkan suatu _route_ ke dalam stack _route_ yang dikelola oleh `Navigator`. Method ini menyebabkan _route_ yang ditambahkan berada pada paling atas stack, sehingga _route_ yang baru saja ditambahkan tersebut akan muncul dan ditampilkan kepada pengguna.
- Contoh penggunaan :
```dart
// Contoh 1: Menambahkan halaman baru ke tumpukan halaman
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => MyNewPage()),
);
// Contoh 2: Menambahkan halaman baru dengan membawa data
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => DetailPage(data: myData)),
);
```
2. **Method `pushReplacement()`**: menghapus _route_ yang sedang ditampilkan kepada pengguna dan menggantinya dengan suatu _route_. Method ini menyebabkan aplikasi untuk berpindah dari _route_ yang sedang ditampilkan kepada pengguna ke suatu _route_ yang diberikan. Pada stack _route_ yang dikelola `Navigator`, _route_ lama pada atas stack akan digantikan secara langsung oleh _route_ baru yang diberikan tanpa mengubah kondisi elemen stack yang berada di bawahnya.
- Contoh penggunaan :
```dart
// Contoh 1: Menggantikan halaman saat ini dengan halaman baru
Navigator.pushReplacement(
  context,
  MaterialPageRoute(builder: (context) => MyReplacementPage()),
);
// Contoh 2: Menggantikan halaman dengan membawa data
Navigator.pushReplacement(
  context,
  MaterialPageRoute(builder: (context) => UpdatedPage(data: newData)),
);
```

## Jelaskan masing-masing _layout widget_ pada Flutter dan konteks penggunaannya masing-masing!

Dalam Flutter, terdapat beberapa layout widget yang digunakan untuk mengatur tata letak (layout) dari elemen-elemen interface pengguna. Berikut adalah beberapa layout widget utama beserta konteks penggunaannya:
1. **Container** : widget dasar yang digunakan untuk mengatur tata letak dan dekorasi suatu elemen. Digunakan ketika perlu mengelompokkan widget lain, menentukan _height_ dan _width_, serta memberikan _decoration_.
2. **Row dan Column** : widget yang mengatur elemen-elemen secara horizontal (Row) atau vertikal (Column). Digunakan untuk menyusun widget secara berurutan sesuai kolom atau baris yang diinginkan.
3. **ListView** : widget yang digunakan untuk membuat daftar elemen yang dapat di-scroll. Digunakan untuk menampilkan daftar panjang elemen, seperti daftar kontak atau pesan.
4. **GridView** : membuat tata letak elemen dalam bentuk grid. Digunakan ketika ingin menampilkan elemen dalam grid, seperti galeri gambar atau papan permainan.
5. **Stack** : membuat penumpukan widget di atas satu sama lain. Digunakan untuk menyusun widget secara tumpukan, seperti _overlay_ elemen atau menempatkan elemen-elemen di atas gambar latar belakang.
6. **Expanded dan Flexible** : digunakan untuk memberikan proporsi ruang kepada widget dalam `Row`, `Column`, atau `Flex`. Berguna untuk memberikan proporsi ruang yang dinamis, terutama dalam situasi di mana elemen-elemen perlu mengisi ruang yang tersedia secara fleksibel.

## Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!

- Pada tugas kali ini, elemen input pada form yang digunakan adalah `TextField`.
`TextField` adalah widget dalam Flutter yang digunakan untuk membuat elemen input teks atau string dalam _form_. Widget ini memungkinkan pengguna memasukkan teks melalui _interface_ aplikasi.
- Kali ini saya menggunakan elemen input `TextField` untuk menerima input nama produk, tipe produk, harga produk, dan deskripsi produk dalam bentuk teks, dimana pengguna bisa dapat langsung menuliskannya ke dalam _text box_ yang tersedia.

## Bagaimana penerapan _clean architecture_ pada aplikasi Flutter?

**_Clean Architecture_** adalah suatu pendekatan arsitektur perangkat lunak yang bertujuan untuk memisahkan kode menjadi lapisan-lapisan terpisah agar lebih mudah dipelihara, diuji, dan dikembangkan. Dalam konteks pengembangan aplikasi Flutter, penerapan _Clean Architecture_ melibatkan pembagian kode menjadi tiga lapisan utama:
1. **Lapisan Presentasi (_Presentation Layer_)**
Lapisan ini bertanggung jawab untuk menangani UI, interaksi pengguna, dan presentasi data. Widget-widget Flutter seperti `Widgets`, `Pages`, dan `ViewModels` berada di lapisan ini.
2. **Lapisan Domain (_Domain Layer_)**
Lapisan Domain berisi aturan bisnis dan logika aplikasi. Lapisan ini harus bersifat independen dan tidak bergantung pada detail implementasi apapun.
3. **Lapisan Data (_Data Layer_)**
Lapisan ini bertanggung jawab untuk mengelola sumber daya eksternal dan mengambil atau menyimpan data. Hal ini melibatkan pemanggilan API, operasi _database_, atau penyimpanan lokal.

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)

1. Pertama-tama dibuat berkas baru dengan nama `left_drawer.dart` pada direktori baru `widgets`. Kemudian ditambahkan kode sebagai berikut :
```dart
import 'package:flutter/material.dart';
import 'package:shopping_list/menu.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            // Bagian drawer header
          ),
          // Bagian routing
        ],
      ),
    );
  }
}
```

2. Selanjutnya dibuat routing untuk ke halaman utama dan halaman tambah produk pada bagian routing dengan kode sebagai berikut :
```dart
...
ListTile(
  leading: const Icon(Icons.home_outlined),
  title: const Text('Halaman Utama'),
  // Bagian redirection ke MyHomePage
  onTap: () {
    Navigator.pushReplacement(
        context,
        MaterialPageRoute(
          builder: (context) => MyHomePage(),
        ));
  },
),

ListTile(
  leading: const Icon(Icons.add_shopping_cart),
  title: const Text('Tambah Produk'),
  // Bagian redirection ke ShopFormPage
  onTap: () {
    Navigator.pushReplacement(
      context, 
      MaterialPageRoute(
        builder: (context) => ShopFormPage(),
      )
    );
  },
),
...
```

3. Selanjutnya dibuatlah drawer header dengan kode sebagai berikut :
```dart
const DrawerHeader(
  decoration: BoxDecoration(
    color: Colors.indigo,
  ),
  child: Column(
    children: [
      Text(
        'Shopping List',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontSize: 30,
          fontWeight: FontWeight.bold,
          color: Colors.white,
        ),
      ),
      Padding(padding: EdgeInsets.all(10)),
      Text(
          "Catat seluruh keperluan belanjamu di sini!",
          textAlign: TextAlign.center,
          style: TextStyle(
            fontSize: 15,
            color: Colors.white,
            fontWeight: FontWeight.normal
          ),
        ),
    ],
  ),
),
```

4. Setelah dibuat left drawer, maka masukkan drawer tersebut ke halaman `menu.dart` dengan cara tambahkan kode `drawer: const LeftDrawer()` pada `Scaffold`.

5. Selanjutnya untuk membuat form, dibuat berkas baru dengan nama `shoplist_form.dart` pada direktori `lib`. Form ini berfungsi untuk menerima input data `_name`, `_price`, `_type`, dan `_description` yang berupa string dan integer. Berikut adalah kode untuk form :
```dart
import 'package:flutter/material.dart';
import 'package:gi_wp_inventory/widgets/left_drawer.dart';

class ShopFormPage extends StatefulWidget {
    const ShopFormPage({super.key});

    @override
    State<ShopFormPage> createState() => _ShopFormPageState();
}

class _ShopFormPageState extends State<ShopFormPage> {
    final _formKey = GlobalKey<FormState>();
    String _name = "";
    int _price = 0;
    String _type = "";
    String _description = "";

    @override
    Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: const Center(
              child: Text(
                'Form Tambah Produk',
              ),
            ),
            backgroundColor: Colors.indigo,
            foregroundColor: Colors.white,
          ),
          drawer: LeftDrawer(),

          body: Form(
            key: _formKey,
            child: SingleChildScrollView(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: TextFormField(
                      decoration: InputDecoration(
                        hintText: "Nama Produk",
                        labelText: "Nama Produk",
                        border: OutlineInputBorder(
                          borderRadius: BorderRadius.circular(5.0),
                        ),
                      ),
                      onChanged: (String? value) {
                        setState(() {
                          _name = value!;
                        });
                      },
                      validator: (String? value) {
                        if (value == null || value.isEmpty) {
                          return "Nama tidak boleh kosong!";
                        }
                        return null;
                      },
                    ),
                  ),

                  Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: TextFormField(
                      decoration: InputDecoration(
                        hintText: "Harga",
                        labelText: "Harga",
                        border: OutlineInputBorder(
                          borderRadius: BorderRadius.circular(5.0),
                        ),
                      ),
                      onChanged: (String? value) {
                        setState(() {
                          _price = int.parse(value!);
                        });
                      },
                      validator: (String? value) {
                        if (value == null || value.isEmpty) {
                          return "Harga tidak boleh kosong!";
                        }
                        if (int.tryParse(value) == null) {
                          return "Harga harus berupa angka!";
                        }
                        return null;
                      },
                    ),
                  ),
                  
                  Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: TextFormField(
                      decoration: InputDecoration(
                        hintText: "Tipe Produk",
                        labelText: "Tipe Produk",
                        border: OutlineInputBorder(
                          borderRadius: BorderRadius.circular(5.0),
                        ),
                      ),
                      onChanged: (String? value) {
                        setState(() {
                          _type = value!;
                        });
                      },
                      validator: (String? value) {
                        if (value == null || value.isEmpty) {
                          return "Tipe tidak boleh kosong!";
                        }
                        return null;
                      },
                    ),
                  ),

                  Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: TextFormField(
                      decoration: InputDecoration(
                        hintText: "Deskripsi",
                        labelText: "Deskripsi",
                        border: OutlineInputBorder(
                          borderRadius: BorderRadius.circular(5.0),
                        ),
                      ),
                      onChanged: (String? value) {
                        setState(() {
                          _description = value!;
                        });
                      },
                      validator: (String? value) {
                        if (value == null || value.isEmpty) {
                          return "Deskripsi tidak boleh kosong!";
                        }
                        return null;
                      },
                    ),
                  ),

                  Align(
                    alignment: Alignment.bottomCenter,
                    child: Padding(
                      padding: const EdgeInsets.all(8.0),
                      child: ElevatedButton(
                        style: ButtonStyle(
                          backgroundColor:
                              MaterialStateProperty.all(Colors.indigo),
                        ),
                        onPressed: () {
                          if (_formKey.currentState!.validate()) {
                            ...
                          }
                        },
                        child: const Text(
                          "Save",
                          style: TextStyle(color: Colors.white),
                        ),
                      ),
                    ),
                  ),
                ],
              ),
            ),
          ),
        );
    }
}
```

6. Selanjutnya, untuk memunculkan data, pada `child: ElevatedButton()`, ditambahkan fungsi `showDialog()` pada bagian `onPressed()` dan munculkan widget `AlertDialog`. Kode nya adalah sebagai berikut :
```dart
...
onPressed: () {
  if (_formKey.currentState!.validate()) {
    showDialog(
        context: context,
        builder: (context) {
          return AlertDialog(
            title: const Text('Produk berhasil tersimpan'),
            content: SingleChildScrollView(
              child: Column(
                crossAxisAlignment:
                    CrossAxisAlignment.start,
                children: [
                  Text('Nama: $_name'),
                  Text('Tipe: $_type'),
                  Text('Harga: $_price'),
                  Text('Deskripsi: $_description')
                ],
              ),
            ),
            actions: [
              TextButton(
                child: const Text('OK'),
                onPressed: () {
                  Navigator.pop(context);
                },
              ),
            ],
          );
        },
      );
    _formKey.currentState!.reset();
  }
},
...
```

7. Untuk menambahkan fitur navigasi pada tombol, pada widget `ShopItem` pada berkas `menu.dart` ditambahkan kode sebagai berikut :
```dart
...
// Area responsive terhadap sentuhan
onTap: () {
  // Memunculkan SnackBar ketika diklik
  ScaffoldMessenger.of(context)
    ..hideCurrentSnackBar()
    ..showSnackBar(SnackBar(
        content: Text("Kamu telah menekan tombol ${item.name}!")));
  
  // Navigate ke route yang sesuai (tergantung jenis tombol)
  if (item.name == "Tambah Produk") {
    Navigator.push(
      context, 
      MaterialPageRoute(
        builder: (context) => ShopFormPage(),
      )
    );
  }
},
...
```

8. Terakhir, dibuat berkas baru dengan nama `shop_card.dart` pada direktori widgets. Lalu dipindahkan isi widget `ShopItem` pada `menu.dart` ke berkas `widgets/shop_card.dart`. Selanjutnya, dibuat folder baru bernama `screens` pada direktori `lib`, lalu dilakukan _refactoring file_ untuk memindahkan `menu.dart` dan `shoplist_form.dart` ke dalam folder `screens`.


# Tugas 9

## Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?



## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.



## Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.



## Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.



## Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.



## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).

