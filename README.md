<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>
# Praktikum Laravel: CRUD Penjualan Sederhana

Aplikasi web untuk mencatat transaksi penjualan, dibuat untuk Modul Praktikum Laravel Lanjutan. Fokusnya alur kerja Laravel: migration, Eloquent Model, Resource Controller, Route, dan Blade View.

## Fitur

- Tambah, lihat daftar, lihat detail, ubah, dan hapus transaksi (CRUD)
- Validasi input di sisi server, dengan pesan error di form
- Total transaksi dihitung otomatis di server (`jumlah × harga_satuan`)
- Total omzet dari transaksi berstatus Selesai
- Ringkasan jumlah transaksi per status (Selesai, Pending, Batal)
- Badge warna berbeda untuk tiap status
- Flash message setelah tambah, ubah, dan hapus
- Tampilan responsif tanpa framework CSS

## Teknologi

- Laravel 13.x
- PHP 8.3+
- MySQL / MariaDB
- Laragon (lingkungan lokal)
- Blade (tanpa starter kit)

## Struktur Data

Tabel `penjualan`:

| Kolom | Tipe | Keterangan |
|---|---|---|
| id | bigint | Primary key |
| kode_transaksi | string(30), unique | Contoh: TRX-001 |
| tanggal | date | Tanggal transaksi |
| nama_pelanggan | string(100) | Nama pelanggan |
| nama_produk | string(120) | Nama barang |
| jumlah | unsigned integer | Jumlah unit |
| harga_satuan | decimal(12,2) | Harga per unit |
| total | decimal(14,2) | Dihitung server |
| status | string(20) | Selesai, Pending, atau Batal |
| catatan | text, nullable | Catatan tambahan |
| created_at, updated_at | timestamp | Dikelola Laravel |

## Struktur File Utama

```
app/Models/Penjualan.php
app/Http/Controllers/PenjualanController.php
database/migrations/..._create_penjualan_table.php
routes/web.php
resources/views/layouts/app.blade.php
resources/views/penjualan/index.blade.php
resources/views/penjualan/create.blade.php
resources/views/penjualan/edit.blade.php
resources/views/penjualan/show.blade.php
resources/views/penjualan/_form.blade.php
```

## Route

| Nama | Method | URL |
|---|---|---|
| penjualan.index | GET | /penjualan |
| penjualan.create | GET | /penjualan/create |
| penjualan.store | POST | /penjualan |
| penjualan.show | GET | /penjualan/{penjualan} |
| penjualan.edit | GET | /penjualan/{penjualan}/edit |
| penjualan.update | PUT/PATCH | /penjualan/{penjualan} |
| penjualan.destroy | DELETE | /penjualan/{penjualan} |

## Cara Menjalankan

1. Clone repository dan masuk ke foldernya.

   ```
   git clone https://github.com/USERNAME/praktikum-laravel.git
   cd praktikum-laravel
   ```

2. Pasang dependensi dan siapkan file environment.

   ```
   composer install
   copy .env.example .env
   php artisan key:generate
   ```

3. Buat database kosong di MySQL.

   ```sql
   CREATE DATABASE penjualan_laravel
   CHARACTER SET utf8mb4
   COLLATE utf8mb4_unicode_ci;
   ```

4. Atur koneksi database di `.env`.

   ```
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=penjualan_laravel
   DB_USERNAME=root
   DB_PASSWORD=
   ```

5. Jalankan migration lalu server.

   ```
   php artisan migrate
   php artisan serve
   ```

6. Buka `http://127.0.0.1:8000`. Halaman akan diarahkan ke `/penjualan`.



## Pengembangan Mandiri

- Ringkasan jumlah transaksi Selesai, Pending, dan Batal
- Badge status dengan warna berbeda



## Created by

Muhammad Taqiy Mumtaz (109062500135)