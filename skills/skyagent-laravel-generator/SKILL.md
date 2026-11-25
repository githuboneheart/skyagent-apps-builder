---
name: skyagent-laravel-generator
description: >-
  Skill untuk menghasilkan kode aplikasi Laravel lengkap dan production-ready berdasarkan
  PRD dan UI Plan yang sudah disetujui member. Menghasilkan struktur MVC Laravel standar:
  Database Migrations, Eloquent Models dengan relasi & fillable, Controllers dengan Form
  Request validation, Web Routes, Blade/Tailwind/Livewire/Inertia Views, Database Seeders,
  .env.example, panduan instalasi Laragon, serta modul migrasi data dari Google Apps Script ke Laravel.
---

# SkyAgent Laravel Generator — Pembuat Kode Aplikasi Laravel

## Tujuan

Menghasilkan kode aplikasi Laravel lengkap, aman, terstruktur rapi, dan siap jalan di lingkungan lokal Laragon/XAMPP maupun server cPanel/VPS. Skill ini juga menangani migrasi/upgrade data dari aplikasi Google Apps Script lama ke database relasional Laravel (MySQL/PostgreSQL).

## Prasyarat

Sebelum generate kode Laravel, pastikan:
- ✅ PRD lengkap (17 bagian) sudah disetujui member (dengan tech stack Laravel terkonfirmasi).
- ✅ UI Plan sudah dikonfirmasi member.
- ✅ Pilihan frontend stack Laravel sudah dipilih member (Blade + Tailwind, Livewire, Inertia + Vue, atau REST API).
- ✅ Member mengonfirmasi pembuatan projek di direktori lokal (misal: `c:\laragon\www\<nama-projek>`).

---

## 4 Pilihan Frontend Stack Laravel

SkyAgent mendukung 4 varian stack frontend Laravel yang dapat dipilih member sesuai kebutuhan:

1. **Blade + Tailwind CSS (Recommended & Default)**
   - *Kelebihan*: Paling mudah dipahami member pemula, tanpa perlu *build tools* rumit, sangat cepat dijalankan di Laragon dan mudah di-upload ke shared hosting cPanel biasa.
   - *Teknologi*: Laravel Blade, Tailwind CSS (via CDN atau Vite), Alpine.js ringan untuk interaktivitas modal & dropdown.

2. **Laravel Livewire + Alpine.js**
   - *Kelebihan*: Interaktif secara real-time tanpa reload halaman (seperti SPA) namun seluruh logika tetap ditulis dalam PHP.
   - *Teknologi*: Livewire v3, Blade components, Alpine.js.

3. **Inertia.js + Vue.js (Modern Enterprise)**
   - *Kelebihan*: Pengalaman Single Page Application (SPA) penuh dengan Vue 3 untuk dashboard interaktif berskala besar.
   - *Teknologi*: Laravel Breeze/Inertia, Vue 3, Tailwind CSS.

4. **REST API Backend Only**
   - *Kelebihan*: Backend murni penghasil JSON endpoint terproteksi (Laravel Sanctum) untuk dihubungkan ke Mobile App (Flutter / React Native) atau sistem POS hardware terpisah.
   - *Teknologi*: API Controllers, Eloquent API Resources, Sanctum Tokens.

---

## Standar Kualitas & Arsitektur Kode Laravel (WAJIB)

1. **DILARANG KERAS Menggunakan Emoji OS di Seluruh Bagian Aplikasi**:
   - Seluruh icon tombol, navigasi, badge, status, dan data awal seed HARUS menggunakan **Icon SVG Vector modern** (Lucide / Heroicons).
2. **Pola MVC Bersih & Terstandar**:
   - Controller tidak boleh menampung query database mentah. Gunakan Eloquent ORM.
   - Validasi input formulir menggunakan **Form Request** (`app/Http/Requests/...`) atau `$request->validate([...])` terpusat.
   - Password wajib di-hash menggunakan `Hash::make()` atau bcrypt.
3. **Database Relasional & Integritas Data**:
   - Seluruh tabel wajib dibuat lewat **Database Migration** (`database/migrations/...`) dengan tipe data yang tepat, foreign key constraints, `cascadeOnDelete()` atau `restrictOnDelete()`, dan index kolom pencarian.
   - Sediakan **Database Seeder** (`database/seeders/...`) dengan akun admin default dan data sampel awal siap uji.
4. **Keamanan Bawaan**:
   - Proteksi CSRF di setiap form (`@csrf`).
   - Proteksi otorisasi halaman menggunakan Route Middleware (`auth`, `role:admin`, `role:kasir`).
   - Proteksi Mass Assignment menggunakan `$fillable` atau `$guarded` di setiap Model.
5. **Autentikasi & Auth Wall**:
   - Tampilan login harus rapi dan fullscreen. Sebelum pengguna login, seluruh menu admin/kasir disembunyikan total.

---

## Struktur File Standar yang Dihasilkan

```
📁 c:\laragon\www\<nama-projek>\
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── AuthController.php          # Login, logout, session
│   │   │   ├── PosController.php           # Transaksi kasir, keranjang, checkout
│   │   │   ├── MenuController.php          # CRUD katalog produk/menu
│   │   │   ├── ReportController.php        # Laporan omzet & performa
│   │   │   └── SettingController.php       # Profil toko & printer struk
│   │   ├── Middleware/
│   │   │   └── RoleMiddleware.php          # Validasi role (Admin vs Kasir)
│   │   └── Requests/
│   │       ├── StoreMenuRequest.php        # Validasi tambah/edit menu
│   │       └── CheckoutRequest.php         # Validasi transaksi pembayaran
│   └── Models/
│       ├── User.php                        # Akun staf & role
│       ├── Category.php                    # Kategori menu
│       ├── Menu.php                        # Item produk, harga modal, harga jual, stok
│       ├── Order.php                       # Header transaksi, nomor nota, total, kasir
│       ├── OrderItem.php                   # Detail menu yang dibeli, qty, subtotal
│       └── Setting.php                     # Nama toko, alamat, footer struk
├── database/
│   ├── migrations/
│   │   ├── 2026_01_01_000001_create_users_table.php
│   │   ├── 2026_01_01_000002_create_categories_table.php
│   │   ├── 2026_01_01_000003_create_menus_table.php
│   │   ├── 2026_01_01_000004_create_orders_table.php
│   │   ├── 2026_01_01_000005_create_order_items_table.php
│   │   └── 2026_01_01_000006_create_settings_table.php
│   └── seeders/
│       ├── DatabaseSeeder.php
│       ├── UserSeeder.php                  # Admin (admin/admin123) & Kasir (kasir/kasir123)
│       ├── CategorySeeder.php
│       ├── MenuSeeder.php
│       └── SettingSeeder.php
├── routes/
│   ├── web.php                             # Rute web aplikasi lengkap
│   └── api.php                             # Rute API jika dibutuhkan
├── resources/
│   └── views/
│       ├── layouts/
│       │   ├── app.blade.php               # Shell layout, sidebar desktop, topbar, bottom-nav mobile
│       │   └── guest.blade.php             # Shell halaman login
│       ├── auth/
│       │   └── login.blade.php             # Form login elegan & bersih
│       ├── pos/
│       │   ├── index.blade.php             # Antarmuka kasir utama (katalog 2-kolom & panel pesanan)
│       │   └── receipt-modal.blade.php     # Modal pratinjau struk thermal ESC/POS
│       ├── menu/
│       │   ├── index.blade.php             # Tabel manajemen stok & harga
│       │   └── form-modal.blade.php        # Modal tambah/edit menu
│       ├── reports/
│       │   └── index.blade.php             # Dashboard metrik & grafik omzet
│       └── settings/
│       │   └── index.blade.php             # Pengaturan toko & cetak struk
├── .env.example                            # Konfigurasi database MySQL Laragon
└── README.md                               # Panduan menjalankan projek di Laragon
```

---

## Modul Spesial: Migrasi dari Google Apps Script ke Laravel

Jika member sebelumnya sudah memiliki data di aplikasi Google Spreadsheet (GAS) dan ingin *upgrade* ke Laravel:

1. **Format Ekspor CSV / JSON**:
   - SkyAgent memberikan panduan mengekspor sheet `DATA_MENU` dan `TRANSAKSI` ke file `.csv` atau `.json`.
2. **Artisan Command / Seeder Migrasi**:
   - SkyAgent membuatkan custom command: `app/Console/Commands/ImportFromGoogleSheet.php`.
   - Member cukup meletakkan file CSV di folder `storage/app/import/` lalu menjalankan:
     ```bash
     php artisan skyagent:import-sheet
     ```
   - Skrip otomatis membaca kolom Google Sheet, mengonversi ID, dan memasukkannya ke tabel MySQL secara aman tanpa kehilangan riwayat transaksi!

---

## Panduan Langkah Menjalankan untuk Member (di Laragon)

Setelah kode selesai digenerate, SkyAgent selalu memberikan panduan 1-2-3 yang sangat ramah:

1. **Nyalakan Laragon**: Klik tombol **Start All** (Apache & MySQL).
2. **Buka Terminal di Laragon**:
   ```bash
   cd c:\laragon\www\<nama-projek>
   copy .env.example .env
   php artisan key:generate
   ```
3. **Jalankan Database & Data Awal**:
   ```bash
   php artisan migrate --seed
   ```
4. **Buka Aplikasi di Browser**:
   - Akses via browser: `http://<nama-projek>.test` atau `http://localhost/<nama-projek>/public`
   - Login dengan akun demo:
     - Admin: `admin` / `admin123`
     - Kasir: `kasir` / `kasir123`
