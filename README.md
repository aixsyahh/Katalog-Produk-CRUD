# Katalog Produk: Fitur Edit dan Hapus

Aplikasi desktop katalog produk berbasis JavaFX dengan penyimpanan data SQLite. Pada tugas ini ditambahkan fitur **Edit** dan **Hapus** sehingga aplikasi memiliki operasi CRUD yang lengkap (*Create, Read, Update, Delete*).

## Ringkasan Aplikasi

Pengguna mengisi nama produk, harga, dan memilih foto (roti, susu, atau kopi), lalu menyimpannya. Setiap produk ditampilkan sebagai kartu di halaman katalog. Data disimpan di file database `data/katalog.db`, sehingga tetap ada saat aplikasi ditutup dan dibuka kembali.

## Status CRUD

| Operasi | Method di `ProdukRepository` | Perintah SQL | Cara memicu di aplikasi | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Create** | `add()` | `INSERT` | Tombol **Simpan** saat form dalam mode tambah | Sudah ada |
| **Read** | `getAll()` | `SELECT` | Otomatis saat aplikasi dibuka dan setelah setiap perubahan | Sudah ada |
| **Update** | `update()` | `UPDATE` | Tombol **Edit** pada kartu, lalu **Perbarui** | Ditambahkan |
| **Delete** | `delete()` | `DELETE` | Tombol **Hapus** pada kartu | Ditambahkan |

## Teknologi

- Java 17
- JavaFX 21
- SQLite melalui `sqlite-jdbc 3.49.1.0`
- Maven

## Alur Kerja
- Edit: klik Edit pada kartu -> form terisi data produk -> ubah data -> klik
- Perbarui > update() dijalankan -> katalog dimuat ulang. Tombol Batal membatalkan proses tanpa mengubah data.Hapus: klik
- Hapus pada kartu -> dialog konfirmasi muncul -> pilih OK -> delete() dijalankan -> katalog dimuat ulang.

## Cara Menjalankan
Prasyarat: JDK 17 atau lebih baru dan Maven.
Bash
mvn javafx:run
Aplikasi juga dapat dijalankan melalui NetBeans dengan menjalankan class main.MainApp. File data/katalog.db dibuat otomatis di folder kerja jika belum ada.

<img width="737" height="514" alt="image" src="https://github.com/user-attachments/assets/f589dbdc-fae2-46d4-87dc-b764eeb04d2b" />
<img width="487" height="304" alt="image" src="https://github.com/user-attachments/assets/7fcb37cd-5fe8-409d-8c9f-e32bb4fcc307" />

## Struktur Proyek

```text
KatalogProduk/
├── data/
│   └── katalog.db                  # file database SQLite
├── src/main/java/
│   ├── controller/
│   │   └── KatalogController.java  # diubah: logika edit dan hapus
│   ├── data/
│   │   └── ProdukRepository.java   # diubah: method update() dan delete()
│   ├── db/
│   │   └── Database.java           # koneksi dan pembuatan tabel
│   ├── main/
│   │   └── MainApp.java            # titik masuk aplikasi
│   └── model/
│       └── Produk.java             # model data dan validasi
└── src/main/resources/
    ├── image/                      # foto produk dan ikon edit.png, hapus.png (baru)
    └── view/
        ├── katalog.fxml            # diubah: fx:id tombol dan tombol Batal
        └── styles/app.css          # diubah: gaya tombol Edit dan Hapus
