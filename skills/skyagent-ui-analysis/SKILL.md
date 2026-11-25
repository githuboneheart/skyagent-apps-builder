---
name: skyagent-ui-analysis
description: >-
  Skill untuk menganalisis referensi UI yang dilampirkan member (screenshot, foto,
  atau link Pinterest/Dribbble/Behance). SkyAgent mengidentifikasi layout, warna,
  tipografi, komponen, dan alur pengguna dari referensi, lalu menggunakannya sebagai
  inspirasi untuk desain original. Jika member tidak punya referensi, buat 3 pilihan gaya.
---

# SkyAgent UI Analysis — Analisis Referensi Visual

## Tujuan

Menganalisis referensi tampilan UI dari member dan mengekstrak elemen desain yang bisa dijadikan inspirasi. Referensi digunakan sebagai panduan, **BUKAN untuk disalin identik**.

## Alur Analisis

### Langkah 1: Tanyakan Referensi UI (Gunakan `ask_question`)

Panggil tool `ask_question` untuk menanyakan referensi tampilan kepada member:

```json
{
  "questions": [
    {
      "question": "Apakah Kakak memiliki referensi tampilan UI yang disukai?",
      "options": [
        "(Recommended) Belum punya referensi (SkyAgent buatkan 3 pilihan gaya UI)",
        "Saya punya screenshot/foto UI yang disukai (akan saya lampirkan)",
        "Saya punya link referensi (Pinterest / Dribbble / Behance / Web lain)"
      ],
      "is_multi_select": false
    }
  ]
}
```

### Langkah 2: Analisis atau Pemilihan Gaya UI

#### Opsi A: Screenshot / Foto
Jika member melampirkan gambar, analisis aspek layout, warna, tipografi, dan komponen.

#### Opsi B: Link Pinterest / Dribbble / Behance
Jika member mengirim link, buka dan analisis referensi tersebut.

#### Opsi C: Tidak Punya Referensi (Tampilkan 3 Gaya via `ask_question`)
Jika member memilih tidak punya referensi, tampilkan ringkasan gaya di teks dan panggil tool `ask_question`:

```json
{
  "questions": [
    {
      "question": "Pilih gaya desain yang paling cocok untuk bisnis Kakak:",
      "options": [
        "(Recommended) Ramah & Colorful untuk UMKM (rounded, cerah, tombol besar, cocok untuk kasir)",
        "Minimalis & Bersih (putih, rapi, banyak white space, gaya Notion/Google)",
        "Modern Profesional (sidebar gelap, statistik card, dashboard admin)"
      ],
      "is_multi_select": false
    }
  ]
}
```

## Aturan Analisis

### JANGAN:
- Menyalin warna exact dari referensi (buat variasi sendiri)
- Menyalin logo atau brand identity
- Menyalin layout pixel-perfect
- Mengasumsikan semua fitur di referensi dibutuhkan member
- Merekomendasikan komponen yang terlalu kompleks untuk Apps Script

### SELALU:
- Gunakan referensi sebagai **inspirasi**
- Buat desain original yang sesuai kebutuhan member
- Sederhanakan komponen agar feasible di Google Apps Script + HTML Service
- Prioritaskan fungsi daripada estetika
- Pertimbangkan batasan rendering HTML Service di Apps Script

## Batasan Teknis Apps Script untuk UI

Ingatkan member tentang batasan ini saat analisis:

1. **Tidak ada framework CSS/JS modern** — Semua CSS dan JS harus inline atau dalam file .html terpisah.
2. **Tidak ada routing SPA** — Navigasi antar halaman menggunakan parameter URL atau show/hide section.
3. **Rendering lambat untuk komponen kompleks** — Hindari terlalu banyak animasi.
4. **Ukuran file terbatas** — Total file tidak boleh terlalu besar.
5. **Tidak ada real-time update** — Perlu polling atau refresh manual.
6. **Responsive harus custom** — Tidak ada Bootstrap/Tailwind, perlu CSS media query manual.

## Transisi ke UI Plan

Setelah analisis selesai dan member mengonfirmasi gaya yang dipilih:

```
✅ Referensi UI sudah saya pahami!

Sekarang saya akan buatkan **UI Plan** — rancangan detail tampilan aplikasi Kakak.
UI Plan ini berisi daftar halaman, komponen, navigasi, dan warna.

Kakak bisa review dan minta perubahan sebelum kita lanjut ke PRD. Siap? 😊
```
