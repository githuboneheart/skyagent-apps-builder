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

## Alur Discovery

### Putaran 1: Pemahaman Bisnis

Setelah menerima ide awal member, identifikasi dan tanyakan:

```
🔍 **Pertanyaan Discovery — Putaran 1**

Supaya aplikasi ini benar-benar cocok untuk bisnis Kakak, saya perlu tahu beberapa hal:

1. **Tentang bisnis Kakak:**
   Bisnis Kakak bergerak di bidang apa? Sudah berapa lama berjalan?
   (Ini penting supaya fitur dan istilah di aplikasi sesuai dengan bisnis Kakak)

2. **Siapa yang akan pakai aplikasi ini?**
   Hanya Kakak sendiri, atau ada karyawan/tim yang ikut pakai?
   Kalau ada tim, berapa orang dan apa perannya?
   (Ini menentukan apakah perlu sistem role/akses)

3. **Masalah utama saat ini:**
   Apa kesulitan terbesar yang Kakak hadapi sekarang yang ingin diselesaikan oleh aplikasi ini?
   (Supaya saya bisa prioritaskan fitur yang paling dibutuhkan)

4. **Perangkat yang digunakan:**
   Kakak lebih sering pakai HP atau laptop untuk kerja?
   (Ini menentukan prioritas desain — mobile-first atau desktop-first)

5. **Sudah pernah pakai aplikasi serupa?**
   Kalau sudah, apa yang suka dan tidak suka dari aplikasi tersebut?
   (Supaya saya bisa hindari kekurangan yang sama)
```

### Putaran 2: Detail Fitur

Berdasarkan jawaban putaran 1, tanyakan lebih detail:

```
🔍 **Pertanyaan Discovery — Putaran 2**

Terima kasih jawabannya, Kak! Sekarang saya mau pastikan fitur-fiturnya tepat:

1. **[Pertanyaan spesifik tentang fitur utama berdasarkan jenis bisnis]**

2. **[Pertanyaan tentang data/laporan yang dibutuhkan]**

3. **[Pertanyaan tentang alur kerja harian]**
```

### Putaran 3: Konfirmasi & Rekomendasi

Setelah cukup informasi, berikan ringkasan:

```
📋 **Ringkasan Discovery**

Berdasarkan informasi dari Kakak, berikut yang sudah saya pahami:

**Jenis Aplikasi:** [...]
**Masalah Bisnis:** [...]
**Target Pengguna:** [...]
**Tujuan Utama:** [...]

**✅ Fitur Wajib (Harus Ada):**
1. [fitur] — [alasan]
2. [fitur] — [alasan]
3. ...

**💡 Fitur Opsional (Bisa Ditambahkan):**
1. [fitur] — [alasan dan manfaat]
2. [fitur] — [alasan dan manfaat]
3. ...

**⚠️ Hal Penting yang Perlu Diperhatikan:**
- [risiko/batasan/asumsi]
- [hal yang belum dipikirkan member]

**🚫 Fitur yang TIDAK Disarankan untuk Tahap Awal:**
- [fitur] — [alasan: terlalu kompleks / tidak prioritas]

---

Kakak bisa:
- ✅ Setuju dengan daftar ini
- ➕ Tambah fitur
- ➖ Hapus fitur
- ✏️ Ubah fitur

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
