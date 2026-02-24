# Pemrograman Aplikasi Bergerak 

Nama : Mohamad Ariel Saputra D Loi

NIM : 2409116087

# Struktur

<img width="441" height="297" alt="image" src="https://github.com/user-attachments/assets/3631bf2a-9b29-4bae-bf48-d9ee8b714ea9" />

## DOkumentasi


## Penjelasan
### Penjelasan File main.dart

File main.dart merupakan titik awal (entry point) dari aplikasi Flutter. Ketika aplikasi dijalankan, fungsi main() akan dipanggil terlebih dahulu oleh sistem. Di dalam fungsi ini digunakan runApp() untuk menjalankan widget utama aplikasi. Aplikasi ini menggunakan package provider untuk mengelola state keranjang belanja, sehingga ChangeNotifierProvider digunakan untuk menyediakan objek CartModel ke seluruh widget di aplikasi. Dengan demikian, setiap halaman dapat mengakses dan memperbarui data keranjang tanpa perlu mengirim data secara manual antar halaman.

Class MyApp merupakan widget utama yang bertugas mengatur konfigurasi aplikasi seperti judul, tema warna, dan halaman awal yang ditampilkan. Di dalam MaterialApp, properti home diatur ke ProductListPage, yang berarti halaman daftar produk akan menjadi halaman pertama yang muncul ketika aplikasi dijalankan. Tema aplikasi menggunakan Material Design 3 dengan warna utama biru, sehingga tampilan aplikasi terlihat modern dan konsisten.

### Penjelasan File product.dart

File product.dart berisi definisi class Product yang digunakan sebagai model data untuk produk. Class ini merepresentasikan struktur data sebuah produk yang dijual dalam aplikasi. Setiap produk memiliki atribut id, name, price, emoji, dan description. Atribut id digunakan sebagai identitas unik produk, name untuk menyimpan nama produk, price untuk harga produk dalam bentuk numerik, emoji digunakan sebagai representasi gambar produk tanpa menggunakan file gambar eksternal, dan description untuk menyimpan deskripsi produk. Class ini hanya berfungsi sebagai penyimpan data (data model) dan tidak memiliki logika bisnis atau tampilan.

### Penjelasan File cart_item.dart

File cart_item.dart berisi class CartItem yang merepresentasikan satu item di dalam keranjang belanja. Class ini memiliki atribut product yang bertipe Product dan quantity yang menunjukkan jumlah produk yang dimasukkan ke keranjang. Selain itu, terdapat properti totalPrice yang dihitung secara otomatis dengan mengalikan harga produk dengan jumlahnya. Class ini digunakan untuk menyimpan informasi detail setiap item di keranjang dan memudahkan perhitungan subtotal harga per produk.

### Penjelasan File cart_model.dart

File cart_model.dart merupakan inti dari logika aplikasi karena berfungsi sebagai manajer keranjang belanja. Class CartModel mewarisi ChangeNotifier, sehingga dapat memberi notifikasi kepada widget lain ketika data berubah. Data keranjang disimpan dalam bentuk Map<String, CartItem> dengan key berupa ID produk, sehingga pencarian dan manipulasi data menjadi cepat dan efisien.

Class ini menyediakan berbagai getter untuk mengambil data keranjang, seperti daftar item, jumlah item unik, total jumlah produk, dan total harga keseluruhan. Selain itu, terdapat metode untuk menambahkan produk ke keranjang, menghapus produk, menambah dan mengurangi jumlah produk, serta mengosongkan keranjang. Setiap kali data berubah, method notifyListeners() dipanggil agar seluruh widget yang menggunakan data keranjang dapat memperbarui tampilan secara otomatis. Dengan menggunakan Provider, aplikasi tidak perlu melakukan refresh manual karena perubahan data langsung tercermin di UI.

### Penjelasan File product_list_page.dart

File product_list_page.dart berfungsi sebagai halaman utama untuk menampilkan daftar produk yang tersedia. Pada halaman ini dibuat daftar produk dummy menggunakan class Product sebagai simulasi data produk tanpa database. Produk ditampilkan menggunakan GridView.builder sehingga layout terlihat seperti katalog e-commerce dengan dua kolom produk per baris.

Di bagian AppBar, terdapat ikon keranjang belanja yang menggunakan Consumer<CartModel> untuk menampilkan jumlah item di keranjang secara real-time. Ketika pengguna menekan tombol “Add”, aplikasi akan memanggil method addItem() dari CartModel untuk menambahkan produk ke keranjang. Setelah produk berhasil ditambahkan, aplikasi menampilkan notifikasi menggunakan SnackBar sebagai feedback kepada pengguna. Halaman ini berfungsi sebagai simulasi katalog produk seperti pada aplikasi e-commerce.

### Penjelasan File cart_page.dart

File cart_page.dart berfungsi sebagai halaman keranjang belanja yang menampilkan produk yang telah ditambahkan pengguna. Halaman ini menggunakan Consumer<CartModel> untuk membaca data keranjang secara real-time. Jika keranjang kosong, aplikasi menampilkan tampilan kosong dengan ikon dan tombol untuk kembali ke halaman produk.

Jika keranjang berisi produk, data ditampilkan menggunakan ListView.builder, di mana setiap item keranjang menampilkan emoji produk, nama, harga, jumlah, dan subtotal harga. Pengguna dapat menambah atau mengurangi jumlah produk menggunakan tombol plus dan minus, serta menghapus produk menggunakan tombol delete. Di bagian bawah halaman, terdapat ringkasan total harga dan tombol checkout. Ketika tombol checkout ditekan, aplikasi menampilkan dialog konfirmasi dan setelah dikonfirmasi, keranjang akan dikosongkan sebagai simulasi proses pembelian.

### Kesimpulan Umum Aplikasi

Secara keseluruhan, aplikasi ini merupakan simulasi sistem keranjang belanja (shopping cart) berbasis Flutter yang menggunakan state management Provider. File model digunakan untuk merepresentasikan data produk dan keranjang, file page digunakan untuk menampilkan antarmuka pengguna, dan file main.dart digunakan sebagai konfigurasi awal aplikasi. Konsep utama yang digunakan dalam aplikasi ini adalah pemisahan antara data model, logika bisnis, dan antarmuka pengguna, sehingga kode menjadi lebih terstruktur, mudah dipahami, dan mudah dikembangkan.
