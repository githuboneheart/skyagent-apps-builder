# Template Referensi: POS UMKM

## Deskripsi

Aplikasi kasir (Point of Sale) untuk Usaha Mikro, Kecil, dan Menengah. Sudah teruji
dan digunakan oleh beberapa pengguna UMKM di Indonesia.

## Fitur Wajib Template POS

### 1. Dashboard
- Ringkasan penjualan hari ini
- Income dan expense terbaru
- Persentase margin
- Produk terlaris
- Stok yang hampir habis
- Grafik penjualan (opsional, bisa tabel sederhana)

### 2. Manajemen Produk
- Tambah, edit, hapus produk
- Nama produk, harga jual, harga beli, satuan
- Kategori produk
- Foto produk (opsional, link URL)
- Status aktif/nonaktif
- Barcode/SKU (opsional)

### 3. Stok
- Stok masuk (dari supplier/pembelian)
- Stok keluar (dari penjualan — otomatis)
- Stok opname (penyesuaian manual)
- Riwayat pergerakan stok
- Alert stok minimum (opsional)

### 4. Transaksi Kasir
- Cari/pilih produk
- Keranjang belanja
- Kuantitas, harga, subtotal
- Diskon per item atau per transaksi
- Total bayar
- Metode pembayaran (tunai, transfer, e-wallet)
- Kembalian (untuk tunai)
- Simpan & cetak struk (opsional)
- Stok otomatis berkurang

### 5. Riwayat Transaksi
- Daftar transaksi per hari/periode
- Detail per transaksi
- Filter berdasarkan tanggal, kasir, metode bayar
- Void/batal transaksi (admin only)

### 6. Pengeluaran
- Tambah pengeluaran (sewa, listrik, bahan baku, dll)
- Kategori pengeluaran
- Tanggal, jumlah, keterangan
- Riwayat pengeluaran

### 7. Laporan
- Laporan penjualan (harian, mingguan, bulanan)
- Laporan pengeluaran
- Laporan laba kotor (penjualan - HPP - pengeluaran)
- Persentase margin
- Export ke format tabel (copy-paste atau print)

### 8. Pengaturan
- Profil toko (nama, alamat, logo)
- Manajemen user (admin & kasir)
- Kategori produk
- Kategori pengeluaran
- Metode pembayaran

## Struktur Google Sheet

### Sheet: Products
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | name | String |
| C | category | String |
| D | buyPrice | Number |
| E | sellPrice | Number |
| F | unit | String |
| G | stock | Number |
| H | minStock | Number |
| I | imageUrl | String |
| J | status | String (active/inactive) |
| K | createdAt | DateTime |
| L | updatedAt | DateTime |

### Sheet: Transactions
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | date | DateTime |
| C | cashier | String (user ID) |
| D | items | JSON String |
| E | subtotal | Number |
| F | discount | Number |
| G | total | Number |
| H | paymentMethod | String |
| I | amountPaid | Number |
| J | change | Number |
| K | status | String (completed/void) |
| L | notes | String |

### Sheet: Expenses
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | date | DateTime |
| C | category | String |
| D | description | String |
| E | amount | Number |
| F | createdBy | String (user ID) |
| G | createdAt | DateTime |

### Sheet: StockMovements
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | date | DateTime |
| C | productId | String |
| D | type | String (in/out/adjust) |
| E | quantity | Number |
| F | notes | String |
| G | reference | String (transaction ID / manual) |
| H | createdBy | String (user ID) |

### Sheet: Users
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | email | String |
| C | password | String (hashed) |
| D | name | String |
| E | role | String (admin/cashier) |
| F | createdAt | DateTime |
| G | status | String (active/inactive) |

### Sheet: Settings
| Kolom | Nama | Tipe |
|-------|------|------|
| A | key | String |
| B | value | String |
| C | updatedAt | DateTime |

## Role & Hak Akses

### Admin
- Semua fitur
- Manajemen user
- Void transaksi
- Pengaturan toko
- Laporan lengkap

### Kasir
- Dashboard (view only, data sendiri)
- Transaksi kasir (buat baru)
- Riwayat transaksi (view only, milik sendiri)
- Pengeluaran (tambah)
- Produk (view only)
- Stok (view only)

## Pertanyaan Discovery Khusus POS

1. Jenis produk apa yang dijual? (makanan, pakaian, elektronik, campuran?)
2. Ada variasi produk? (ukuran, warna, rasa?)
3. Berapa rata-rata transaksi per hari?
4. Metode pembayaran apa saja yang diterima?
5. Perlu fitur diskon/promo?
6. Satu outlet atau multi-outlet?
7. Siapa saja yang akan jadi kasir?
8. Perlu cetak struk?
