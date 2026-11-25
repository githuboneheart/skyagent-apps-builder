---
name: skyagent-discovery
description: >-
  Skill untuk tahap discovery SkyAgent. Digunakan saat SkyAgent perlu melakukan
  wawancara bertahap dengan member untuk memahami kebutuhan bisnis, mengidentifikasi
  fitur, dan memberikan rekomendasi. Hanya bertanya 3-5 pertanyaan per putaran.
---

# SkyAgent Discovery — Panduan Wawancara & Rekomendasi

## Tujuan

Menggali kebutuhan member secara bertahap dan terstruktur, tanpa membuat member kewalahan. Hasil discovery menjadi fondasi PRD.

## Prinsip Discovery

1. **Bertahap** — Jangan tanya semua sekaligus. Maksimal 3-5 pertanyaan per putaran.
2. **Relevan** — Setiap pertanyaan harus punya alasan jelas dan relevan dengan bisnis member.
3. **Rekomendatif** — Jangan hanya bertanya, berikan juga rekomendasi dan opsi.
4. **Transparan** — Jelaskan mengapa informasi ini penting.
5. **Fleksibel** — Biarkan member menambah, menghapus, atau mengubah jawaban.

## Alur Discovery & Mekanisme Pop-up (WAJIB)

> [!IMPORTANT]
> **JANGAN ketik pertanyaan discovery hanya sebagai teks biasa di chat!**
> SkyAgent **WAJIB** memanggil tool `ask_question` agar pertanyaan muncul sebagai dialog pop-up / kartu pilihan interaktif di antarmuka Antigravity. Member cukup klik pilihan yang tersedia tanpa harus mengetik panjang.

### Putaran 1: Pemahaman Bisnis (Gunakan `ask_question`)

Setelah menerima ide awal, panggil tool `ask_question` dengan 3-5 pertanyaan terstruktur. Contoh payload `ask_question` untuk Template POS UMKM:

```json
{
  "questions": [
    {
      "question": "Bisnis Kakak bergerak di bidang apa & apakah ada variasi produk?",
      "options": [
        "(Recommended) Toko Kelontong / Sembako / Ritel (banyak barang satuan)",
        "Cafe / Resto / Makanan & Minuman (ada varian rasa/porsi)",
        "Toko Pakaian / Fashion / Butik (ada varian ukuran & warna)",
        "Jasa (Salon, Barbershop, Bengkel, Laundry)",
        "Kios Pulsa / Aksesoris / Counter"
      ],
      "is_multi_select": false
    },
    {
      "question": "Siapa yang akan mengoperasikan kasir di toko?",
      "options": [
        "(Recommended) Saya sendiri dibantu karyawan (butuh role Kasir & Admin)",
        "Hanya saya sendiri (single user / pemilik)",
        "Beberapa staf/karyawan dengan shift bergantian"
      ],
      "is_multi_select": false
    },
    {
      "question": "Perangkat utama yang digunakan di meja kasir saat melayani pembeli?",
      "options": [
        "(Recommended) Smartphone / HP Android (layar sentuh, praktis)",
        "Laptop / Komputer PC meja kasir",
        "Tablet / iPad"
      ],
      "is_multi_select": false
    },
    {
      "question": "Metode pembayaran apa saja yang disediakan untuk pembeli?",
      "options": [
        "(Recommended) Tunai & QRIS / Transfer Bank",
        "Hanya pembayaran Tunai",
        "Tunai, QRIS, & Kasbon / Catatan Hutang Pelanggan",
        "Lengkap (Tunai, QRIS, Transfer, Debit/Kredit, Kasbon)"
      ],
      "is_multi_select": false
    },
    {
      "question": "Apa kendala pencatatan terbesar saat ini yang ingin diselesaikan?",
      "options": [
        "(Recommended) Stok sering selisih & sering lupa sisa barang",
        "Rekap omzet harian & laba kotor ribet/manual",
        "Sering lupa harga modal (HPP) & harga jual barang",
        "Catatan kasbon pelanggan sering hilang/tercecer"
      ],
      "is_multi_select": false
    }
  ]
}
```

### Putaran 2: Detail Fitur & Pilihan Stack (Gunakan `ask_question`)

Berdasarkan jawaban putaran 1, panggil tool `ask_question` untuk memperdalam fitur spesifik dan menentukan platform teknologi yang diinginkan member:

```json
{
  "questions": [
    {
      "question": "Platform teknologi mana yang paling sesuai dengan rencana bisnis Kakak?",
      "options": [
        "(Recommended) Google Apps Script (100% Gratis tanpa sewa hosting, simpel di Spreadsheet, cocok untuk 1 toko & UMKM)",
        "Laravel (PHP + MySQL di Laragon/cPanel) (Untuk bisnis berkembang, multi-cabang, jutaan data, performa tinggi)",
        "Migrasi / Upgrade Projek Google Apps Script yang sudah ada ke Laravel"
      ],
      "is_multi_select": false
    },
    {
      "question": "Jika memilih Laravel, arsitektur frontend mana yang Kakak sukai?",
      "options": [
        "(Recommended) Blade + Tailwind CSS (Paling ramah member, ringan, cepat dijalankan di Laragon & cPanel)",
        "Laravel Livewire + Alpine.js (Modern & reaktif tanpa reload halaman, tetap berbasis Blade)",
        "Inertia.js + Vue.js (Single Page Application interaktif untuk dashboard enterprise)",
        "REST API Backend Only (Untuk dihubungkan ke Mobile App Flutter/React)"
      ],
      "is_multi_select": false
    },
    {
      "question": "Bagaimana kebutuhan cetak struk nota belanja di kasir?",
      "options": [
        "(Recommended) Cetak thermal Bluetooth 58mm/80mm & Cetak standar printer",
        "Hanya kirim struk digital via WhatsApp (tanpa kertas)",
        "Cetak thermal Bluetooth, standar printer, & kirim WhatsApp",
        "Tidak perlu cetak struk (cukup simpan data riwayat)"
      ],
      "is_multi_select": false
    }
  ]
}
```

### Putaran 3: Konfirmasi Ringkasan & Rekomendasi

Tampilkan ringkasan teks di chat, lalu panggil tool `ask_question` untuk konfirmasi:

```json
{
  "questions": [
    {
      "question": "Apakah Kakak setuju dengan ringkasan fitur wajib & opsional di atas?",
      "options": [
        "(Recommended) Setuju semua, lanjut ke tahap Referensi UI!",
        "Mau tambah fitur baru",
        "Mau kurangi/hapus beberapa fitur",
        "Ada fitur yang perlu disesuaikan"
      ],
      "is_multi_select": false
    }
  ]
}
```

Silakan beri tahu pendapat Kakak! 😊
```

## Pertanyaan Discovery per Template

### Template POS UMKM

Fokus pertanyaan pada:
- Jenis produk yang dijual (makanan, barang, jasa?)
- Variasi produk (ukuran, warna, varian?)
- Metode pembayaran (tunai, transfer, e-wallet?)
- Kebutuhan stok (ada supplier tetap? perlu notifikasi stok menipis?)
- Laporan yang dibutuhkan (harian, mingguan, bulanan?)
- Jumlah transaksi per hari (menentukan kompleksitas)
- Diskon/promo (perlu fitur diskon per produk atau per transaksi?)
- Multi-outlet atau single outlet?

### Template Absensi Karyawan

Fokus pertanyaan pada:
- Jumlah karyawan
- Jam kerja (tetap atau shift?)
- Jenis absensi (finger print, foto, GPS, manual?)
- Kebijakan izin dan cuti
- Keterlambatan dan penalti
- Laporan yang dibutuhkan HR/owner
- Integrasi dengan penggajian?

### Template Booking & Pendaftaran

Fokus pertanyaan pada:
- Jenis layanan yang di-booking
- Durasi layanan
- Kapasitas per slot
- Pembatalan dan reschedule
- Pembayaran DP atau full?
- Notifikasi reminder?
- Multi-staff/provider?

## Aturan Penting

1. **Jangan bertanya lebih dari 5 pertanyaan per putaran.**
2. **Selalu berikan opsi/contoh jawaban** untuk memudahkan member.
3. **Jika member menjawab singkat, jangan minta detail yang belum relevan.**
4. **Simpan setiap jawaban sebagai keputusan produk.**
5. **Jika informasi sudah cukup (minimal 2 putaran), lanjut ke ringkasan.**
6. **Jangan buat member merasa diwawancarai — ini percakapan, bukan interogasi.**

## Transisi ke Fase Berikutnya

Setelah member mengonfirmasi ringkasan discovery, lanjut ke pertanyaan referensi UI:

```
✅ Bagus, Kak! Kebutuhan fiturnya sudah jelas.

Sekarang kita masuk ke tampilan aplikasinya. Kakak punya referensi tampilan yang disukai?

1️⃣ **Lampirkan screenshot/foto** — tampilan aplikasi yang Kakak suka
2️⃣ **Kirim link** — dari Pinterest, Dribbble, Behance, atau situs lain
3️⃣ **Tidak punya referensi** — Nanti saya buatkan 3 pilihan gaya desain

Pilih yang mana, Kak? 😊
```
