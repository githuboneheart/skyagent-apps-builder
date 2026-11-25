---
name: skyagent-qa
description: >-
  Skill untuk melakukan Quality Assurance pada kode Apps Script yang dihasilkan SkyAgent.
  Memeriksa kode server-side, client-side, struktur database, keamanan, UI/UX, responsivitas,
  dan kesiapan deployment. Menghasilkan laporan QA dengan status pass/fail per item.
---

# SkyAgent QA — Quality Assurance Kode & Aplikasi

## Tujuan

Memeriksa seluruh kode, struktur database, UI, dan kesiapan deployment sebelum aplikasi diberikan ke member. Memastikan kode production-ready dan sesuai PRD.

## Checklist QA

### 1. Validasi Kode Server-side (.gs)

```
📋 QA — Server-side Code

□ Code.gs
  - [ ] doGet() berfungsi dengan semua parameter page
  - [ ] include() helper tersedia
  - [ ] Routing mencakup semua halaman di PRD
  - [ ] Error handling untuk page yang tidak ditemukan
  - [ ] Hanya gunakan .addMetaTag('viewport', ...), TIDAK menambahkan theme-color atau meta tag ilegal lainnya

□ Setup.gs
  - [ ] Semua sheet dari PRD bagian 10 dibuat
  - [ ] Header kolom sesuai PRD
  - [ ] Data default (admin) dibuat
  - [ ] Fungsi bisa dijalankan berulang tanpa error (idempotent)

□ Auth.gs
  - [ ] Login berfungsi dengan email + password
  - [ ] Password di-hash (bukan plain text)
  - [ ] Session management via PropertiesService
  - [ ] Logout menghapus session
  - [ ] getCurrentUser() mengembalikan data user
  - [ ] Role-based access sesuai PRD bagian 5

□ Database.gs
  - [ ] getSheetData() dengan dan tanpa filter
  - [ ] insertRow() dengan validasi
  - [ ] updateRow() berdasarkan ID
  - [ ] deleteRow() berdasarkan ID
  - [ ] Error handling untuk sheet tidak ditemukan

□ [Module].gs (per modul)
  - [ ] Fungsi CRUD lengkap untuk modul tersebut
  - [ ] Validasi input di server-side
  - [ ] Aturan bisnis (PRD bagian 12) terimplementasi
  - [ ] Kalkulasi otomatis (stok, total, dll) benar
  - [ ] Format data konsisten

□ Utils.gs
  - [ ] generateId_() menghasilkan UUID unik
  - [ ] hashPassword_() konsisten
  - [ ] formatCurrency() format Rupiah benar
  - [ ] formatDate() timezone Asia/Jakarta
```

### 2. Validasi Kode Client-side (.html)

```
📋 QA — Client-side Code

□ Index.html
  - [ ] Meta viewport tersedia (responsive)
  - [ ] Google Fonts ter-load
  - [ ] include() untuk Style, Script, Components berfungsi
  - [ ] Loading state saat halaman dimuat
  - [ ] Menggunakan Icon SVG Vector modern (bukan emoji OS kartun) untuk navigasi & tombol
  - [ ] Halaman login fullscreen murni (sidebar & navigasi aplikasi tersembunyi total sebelum login)

□ Style.html
  - [ ] Palet warna sesuai UI Plan
  - [ ] Responsive breakpoint tersedia
  - [ ] Mobile-first / desktop-first sesuai UI Plan
  - [ ] Font sesuai UI Plan
  - [ ] Tidak ada hardcoded pixel yang merusak di mobile
  - [ ] Form element styled konsisten
  - [ ] Table responsive (scroll horizontal di mobile)
  - [ ] Rule body.is-guest menyembunyikan sidebar, topbar, dan navbar saat belum login

□ Script.html
  - [ ] google.script.run digunakan untuk panggil server
  - [ ] Loading state saat request ke server
  - [ ] Error handling untuk request gagal
  - [ ] Toast/notification setelah aksi
  - [ ] Konfirmasi sebelum hapus data
  - [ ] Form validation di client-side
  - [ ] Navigasi antar halaman berfungsi
  - [ ] switchPage() mencegah akses halaman kasir/admin sebelum user berhasil login

□ Components.html
  - [ ] Modal component berfungsi (open/close)
  - [ ] Toast/notification component
  - [ ] Loading spinner
  - [ ] Confirm dialog
  - [ ] Komponen reusable yang konsisten

□ [Page].html (per halaman)
  - [ ] Layout sesuai wireframe UI Plan
  - [ ] Data binding dari server berfungsi
  - [ ] Semua aksi (CRUD) terhubung ke server function
  - [ ] Validasi form lengkap
  - [ ] Empty state ditangani
  - [ ] Error state ditangani
```

### 3. Validasi Struktur Database (Sheet)

```
📋 QA — Database Structure

□ Kesesuaian dengan PRD
  - [ ] Semua sheet dari PRD bagian 10 ada di Setup.gs
  - [ ] Kolom per sheet sesuai PRD
  - [ ] Tipe data konsisten (string, number, date)
  - [ ] Primary key (ID) di setiap sheet
  - [ ] Relasi antar sheet konsisten

□ Data Integrity
  - [ ] Tidak ada kolom duplikat
  - [ ] Validasi data diterapkan saat insert/update
  - [ ] Format tanggal konsisten (ISO / dd/MM/yyyy)
  - [ ] Format angka konsisten (tanpa format di sheet, format di UI)
  - [ ] ID generate otomatis

□ Performa
  - [ ] Tidak ada sheet yang akan melebihi 50.000 baris dalam setahun
  - [ ] Query dioptimasi (batch read, bukan per-row)
  - [ ] Cache digunakan jika perlu
```

### 4. Validasi Keamanan

```
📋 QA — Security

□ Autentikasi
  - [ ] Password di-hash sebelum disimpan
  - [ ] Session token unique dan unpredictable
  - [ ] Session bisa expired (opsional)
  - [ ] Logout menghapus semua session data

□ Otorisasi
  - [ ] Role-based access diterapkan di server-side
  - [ ] User biasa tidak bisa akses fungsi admin
  - [ ] Setiap endpoint cek autentikasi

□ Data
  - [ ] Input disanitasi (XSS prevention)
  - [ ] Tidak ada SQL injection (N/A untuk Sheets, tapi validasi tetap)
  - [ ] Data sensitif tidak di-log
  - [ ] Password default ada instruksi untuk diganti
```

### 5. Validasi UI/UX

```
📋 QA — UI/UX

□ Responsivitas
  - [ ] Tampil baik di HP (< 768px)
  - [ ] Tampil baik di tablet (768-1024px)
  - [ ] Tampil baik di laptop/desktop (> 1024px)
  - [ ] Tabel bisa di-scroll horizontal di mobile
  - [ ] Form mudah diisi di mobile
  - [ ] Tombol cukup besar untuk touch

□ Usability
  - [ ] Alur kerja intuitif sesuai PRD bagian 9
  - [ ] Feedback jelas setelah setiap aksi
  - [ ] Loading state mencegah double-click
  - [ ] Empty state informatif (bukan halaman kosong)
  - [ ] Error message ramah dan actionable
  - [ ] Navigasi konsisten di semua halaman

□ Aksesibilitas
  - [ ] Kontras warna cukup (teks terbaca)
  - [ ] Label form tersedia
  - [ ] Urutan tab logis
  - [ ] Icon punya tooltip atau label teks
```

### 6. Validasi Kesesuaian PRD

```
📋 QA — PRD Compliance

□ Fitur
  - [ ] Semua fitur wajib (PRD bagian 7) terimplementasi
  - [ ] Fitur opsional yang disetujui terimplementasi
  - [ ] Tidak ada fitur ekstra yang tidak di PRD

□ Alur
  - [ ] Alur penggunaan (PRD bagian 9) bisa dilalui end-to-end
  - [ ] Aturan bisnis (PRD bagian 12) diterapkan

□ Laporan
  - [ ] Semua laporan (PRD bagian 13) tersedia
  - [ ] Filter laporan berfungsi
  - [ ] Data laporan akurat

□ Acceptance Criteria
  - [ ] Semua AC (PRD bagian 15) terpenuhi
```

### 7. Kesiapan Deployment

```
📋 QA — Deployment Readiness

□ File
  - [ ] appsscript.json valid
  - [ ] Semua file yang dibutuhkan ada
  - [ ] Tidak ada syntax error
  - [ ] Tidak ada reference error (fungsi/variabel undefined)

□ Setup
  - [ ] setupApplication() bisa dijalankan
  - [ ] Data default lengkap
  - [ ] Instruksi deployment jelas

□ Dokumentasi
  - [ ] Checklist deployment tersedia
  - [ ] Login default tercantum
  - [ ] Instruksi ganti password ada
  - [ ] Batasan dan known issues didokumentasi
```

### 8. Validasi Kode Laravel (Khusus Projek Laravel)

```
📋 QA — Laravel Code & Architecture

□ Database Migrations
  - [ ] Semua tabel dari PRD bagian 10 dibuat lewat migration
  - [ ] Foreign key constraints & onDelete cascading terpasang dengan benar
  - [ ] Indeks pada kolom pencarian sering (misal: order_number, user_id, status)
  - [ ] Kolom timestamps() dan softDeletes() (jika relevan)

□ Database Seeders
  - [ ] UserSeeder membuat akun default (admin & kasir)
  - [ ] Password di-hash menggunakan Hash::make()
  - [ ] Seeder dapat dijalankan berulang via php artisan db:seed tanpa error duplicate key

□ Eloquent Models
  - [ ] Properti $fillable atau $guarded terdefinisi untuk mencegah mass assignment vulnerability
  - [ ] Relasi antar model (hasMany, belongsTo, dll) berfungsi dua arah
  - [ ] Type casting pada atribut numerik / tanggal ($casts)

□ Controllers & Form Requests
  - [ ] Validasi input terpusat di Form Request atau $request->validate()
  - [ ] Tidak ada query database mentah di controller (gunakan Eloquent)
  - [ ] Error handling & redirect dengan flash message / toast alert

□ Keamanan & Middleware
  - [ ] Proteksi CSRF di setiap form Blade (@csrf)
  - [ ] Proteksi rute menggunakan Middleware (auth, role)
  - [ ] Auth wall: Halaman login fullscreen, menu admin/kasir terkunci sebelum login

□ Tampilan & Frontend (Blade / Livewire / Vue)
  - [ ] 100% bebas dari emoji OS di seluruh antarmuka
  - [ ] Seluruh tombol & navigasi menggunakan SVG vector modern
  - [ ] Responsif di desktop (> 992px) dan smartphone (<= 992px)
  - [ ] File .env.example tersedia dan siap dijalankan di Laragon
```

## Format Laporan QA

```markdown
# 📊 Laporan QA — [Nama Aplikasi]

**Tanggal:** [tanggal]
**Versi PRD:** [versi]
**Status Keseluruhan:** ✅ PASS / ⚠️ PASS with WARNINGS / ❌ FAIL

## Ringkasan

| Kategori | Total Item | Pass | Fail | Warning |
|----------|-----------|------|------|---------|
| Server-side | [n] | [n] | [n] | [n] |
| Client-side | [n] | [n] | [n] | [n] |
| Database | [n] | [n] | [n] | [n] |
| Security | [n] | [n] | [n] | [n] |
| UI/UX | [n] | [n] | [n] | [n] |
| PRD Compliance | [n] | [n] | [n] | [n] |
| Deployment | [n] | [n] | [n] | [n] |
| **TOTAL** | **[n]** | **[n]** | **[n]** | **[n]** |

## Detail Findings

### ❌ Items yang GAGAL (Harus Diperbaiki)
1. [item] — [penjelasan masalah] — [saran perbaikan]

### ⚠️ Items WARNING (Sebaiknya Diperbaiki)
1. [item] — [penjelasan] — [saran]

### ✅ Items yang LULUS
(Daftar ringkas)

## Rekomendasi
- [rekomendasi perbaikan prioritas]
```

## Aturan QA

1. **Setiap item harus dicek** — jangan skip item karena "pasti benar"
2. **Fail harus diperbaiki** sebelum kode diberikan ke member
3. **Warning boleh ditunda** tapi harus dicatat
4. **Jangan modifikasi kode saat QA** — catat findings, perbaikan di langkah terpisah
5. **Cross-check dengan PRD** — kode harus sesuai PRD, bukan asumsi
