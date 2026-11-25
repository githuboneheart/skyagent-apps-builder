---
name: skyagent-revision
description: >-
  Skill untuk menangani revisi dari member. Digunakan saat member ingin menambah, mengubah,
  atau menghapus fitur, memperbaiki tampilan, atau memperbaiki error. Menjaga konsistensi
  dengan PRD dan keputusan produk sebelumnya.
---

# SkyAgent Revision — Panduan Revisi Fitur & Tampilan

## Tujuan

Menangani permintaan revisi dari member secara terstruktur, menjaga konsistensi dengan PRD dan keputusan produk sebelumnya, serta memastikan setiap perubahan terdokumentasi.

## Jenis Revisi

### 1. Tambah Fitur Baru

**Alur:**
1. Member menyebutkan fitur yang ingin ditambahkan
2. SkyAgent menganalisis:
   - Apakah fitur ini feasible di Apps Script?
   - Apakah ada dampak ke fitur yang sudah ada?
   - Berapa kompleksitasnya?
   - File mana yang perlu diubah?
3. SkyAgent memberikan analisis dampak
4. Member mengonfirmasi
5. SkyAgent update PRD + generate kode tambahan

**Template respons:**

```
📝 **Analisis Penambahan Fitur**

**Fitur yang diminta:** [nama fitur]
**Deskripsi:** [penjelasan]

**✅ Feasibility:** [Bisa / Bisa dengan batasan / Tidak bisa di Apps Script]

**📊 Dampak Perubahan:**

| File | Perubahan | Kompleksitas |
|------|----------|-------------|
| [file.gs] | [deskripsi perubahan] | [Rendah/Sedang/Tinggi] |
| [file.html] | [deskripsi perubahan] | [Rendah/Sedang/Tinggi] |

**⚠️ Hal yang Perlu Diperhatikan:**
- [dampak ke fitur lain]
- [potensi masalah]
- [batasan]

**📋 Perubahan PRD:**
- Bagian 7 (Fitur Wajib): + [fitur baru]
- Bagian 10 (Struktur Sheet): + [kolom/sheet baru jika ada]
- Bagian 11 (Halaman UI): + [halaman baru jika ada]

Mau lanjut dengan penambahan ini, Kak? 😊
```

### 2. Ubah Fitur yang Sudah Ada

**Alur:**
1. Member menyebutkan fitur yang ingin diubah
2. SkyAgent cek keputusan produk sebelumnya (kenapa fitur ini dibuat seperti ini)
3. SkyAgent menganalisis dampak perubahan
4. Member mengonfirmasi
5. SkyAgent update PRD + modifikasi kode

**Template respons:**

```
📝 **Analisis Perubahan Fitur**

**Fitur yang diubah:** [nama fitur]
**Kondisi saat ini:** [deskripsi fitur saat ini]
**Perubahan yang diminta:** [deskripsi perubahan]

**📋 Keputusan Sebelumnya:**
- [tanggal]: [keputusan terkait fitur ini dan alasannya]

**📊 Dampak Perubahan:**
| Aspek | Sebelum | Sesudah |
|-------|---------|---------|
| [aspek] | [kondisi lama] | [kondisi baru] |

**⚠️ Risiko:**
- [risiko perubahan]

Lanjut dengan perubahan ini, Kak? 😊
```

### 3. Hapus Fitur

**Alur:**
1. Member menyebutkan fitur yang ingin dihapus
2. SkyAgent cek apakah ada fitur lain yang bergantung pada fitur ini
3. Berikan peringatan jika ada dependensi
4. Member mengonfirmasi
5. SkyAgent update PRD + hapus kode terkait

**Template respons:**

```
📝 **Analisis Penghapusan Fitur**

**Fitur yang dihapus:** [nama fitur]

**🔗 Dependensi:**
- [fitur/komponen yang bergantung pada fitur ini]

**📊 File yang Terpengaruh:**
| File | Perubahan |
|------|----------|
| [file] | [apa yang dihapus/diubah] |

**⚠️ Peringatan:**
- [dampak penghapusan]

**Catatan:** Fitur ini akan dipindahkan ke daftar "Fitur Ditolak" di PRD,
supaya kalau nanti Kakak berubah pikiran, kita bisa kembalikan dengan mudah.

Lanjut hapus fitur ini, Kak? 😊
```

### 4. Perbaiki Tampilan / UI

**Alur:**
1. Member menyebutkan bagian tampilan yang ingin diubah
2. SkyAgent identifikasi file dan komponen yang terkait
3. SkyAgent berikan opsi perubahan
4. Member pilih
5. SkyAgent modifikasi Style.html, [Page].html, atau Components.html

**Template respons:**

```
🎨 **Analisis Perubahan Tampilan**

**Halaman/Komponen:** [nama]
**Perubahan yang diminta:** [deskripsi]

**🔧 Opsi Perubahan:**

1️⃣ [Opsi 1] — [deskripsi + preview]
2️⃣ [Opsi 2] — [deskripsi + preview]
3️⃣ [Opsi kustom] — Kakak jelaskan lebih detail apa yang diinginkan

Pilih yang mana, Kak? 😊
```

### 5. Perbaiki Error / Bug

**Alur:**
1. Member melaporkan error (screenshot, pesan error, atau deskripsi)
2. SkyAgent menganalisis kemungkinan penyebab
3. SkyAgent memperbaiki kode
4. SkyAgent jalankan QA pada bagian yang diperbaiki

**Template respons:**

```
🔧 **Analisis Error**

**Error yang dilaporkan:** [deskripsi]
**Kemungkinan penyebab:** [analisis]

**📍 Lokasi Masalah:**
- File: [nama file]
- Fungsi: [nama fungsi]
- Baris: [estimasi baris]

**🔧 Perbaikan:**
[deskripsi perbaikan yang dilakukan]

**Kode sebelum:**
```javascript
[kode lama]
```

**Kode sesudah:**
```javascript
[kode baru]
```

**✅ QA pada bagian yang diperbaiki:**
- [checklist item] — ✅ PASS

Error sudah diperbaiki, Kak! 😊
```

## Aturan Revisi

### WAJIB:
1. **Selalu cek keputusan produk sebelumnya** sebelum melakukan revisi
2. **Analisis dampak** ke fitur dan file lain
3. **Update PRD** setelah revisi disetujui (buat versi baru: 1.1, 1.2, dst)
4. **Dokumentasikan perubahan** dalam log revisi
5. **Jalankan QA** pada bagian yang direvisi
6. **Jaga konsistensi** — perubahan di satu tempat harus konsisten di tempat lain

### JANGAN:
1. Jangan ubah fitur tanpa konfirmasi member
2. Jangan hapus keputusan produk sebelumnya — tandai sebagai "direvisi"
3. Jangan tambah fitur baru tanpa analisis dampak
4. Jangan ubah struktur sheet tanpa migrasi data (jika sudah ada data)

## Log Revisi

Simpan setiap revisi dalam format:

```
REVISI LOG:
- [tanggal] v1.1: [deskripsi perubahan] — Diminta oleh member
  - File diubah: [daftar file]
  - PRD bagian diupdate: [bagian yang berubah]
  - Status QA: PASS/FAIL
```

## Prompt Revisi untuk Member

Berikan prompt ini ke member untuk mempermudah permintaan revisi:

```
💡 **Cara Minta Revisi:**

Kakak bisa kirim pesan seperti ini:

➕ "Tambah fitur diskon per produk"
✏️ "Ubah warna tombol utama jadi biru tua"
➖ "Hapus fitur export ke PDF, tidak diperlukan"
🎨 "Ubah tampilan dashboard, tambahin grafik penjualan"
🐛 "Ada error saat simpan transaksi, muncul pesan [pesan error]"
📱 "Tampilan di HP berantakan di halaman kasir"

Saya akan analisis dulu dampaknya, lalu minta konfirmasi sebelum mengubah ya! 😊
```
