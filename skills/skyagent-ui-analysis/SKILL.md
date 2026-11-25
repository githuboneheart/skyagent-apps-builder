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

### Langkah 1: Terima Referensi

Member bisa memberikan referensi dalam 3 cara:

#### Opsi A: Screenshot / Foto
Jika member melampirkan gambar, analisis aspek berikut:

```
🎨 **Analisis Referensi UI**

Saya sudah melihat referensi yang Kakak kirim. Berikut yang saya tangkap:

**📐 Layout & Struktur:**
- Tipe layout: [sidebar + content / tab navigation / single page / dll]
- Grid system: [card grid / list / tabel / dll]
- Navigasi utama: [top bar / sidebar / bottom nav / dll]
- Responsive hint: [terlihat mobile-friendly / desktop-focused / dll]

**🎨 Warna:**
- Warna utama (primary): [warna + hex jika bisa diidentifikasi]
- Warna aksen (accent): [warna]
- Warna background: [warna]
- Skema keseluruhan: [light mode / dark mode / mixed]
- Kontras: [tinggi / sedang / rendah]

**🔤 Tipografi:**
- Heading: [style — bold, besar, sans-serif / dll]
- Body text: [style]
- Kesan umum: [modern / klasik / playful / dll]

**🧩 Komponen UI yang Terlihat:**
- [ ] Dashboard/overview card
- [ ] Form input
- [ ] Tabel data
- [ ] Tombol aksi (CTA)
- [ ] Modal/dialog
- [ ] Chart/grafik
- [ ] Sidebar menu
- [ ] Search bar
- [ ] Status badge/tag
- [ ] Avatar/profile
- [ ] Notification
- [ ] Tab navigation

**🔄 Alur Pengguna yang Terlihat:**
- [deskripsi alur yang bisa diidentifikasi dari screenshot]

**📱 Kesesuaian Mobile/Desktop:**
- [analisis responsivitas]

**✨ Fitur yang Terlihat dari Referensi:**
- [fitur-fitur yang teridentifikasi dari tampilan]

**💡 Yang Bisa Kita Adopsi (sebagai inspirasi):**
- [elemen yang cocok untuk aplikasi member]

**⚠️ Yang TIDAK Akan Kita Salin:**
- Logo, brand identity, dan warna exact dari referensi
- Konten dan data dari referensi
- Layout yang terlalu kompleks untuk Apps Script
```

#### Opsi B: Link Pinterest / Dribbble / Behance
Jika member mengirim link:
1. Buka dan analisis halaman referensi tersebut.
2. Jika tidak bisa diakses, minta member mengirim screenshot.
3. Lakukan analisis yang sama seperti Opsi A.
4. Catat URL sumber sebagai referensi.

#### Opsi C: Tidak Punya Referensi
Jika member tidak punya referensi, tawarkan 3 pilihan gaya:

```
🎨 **3 Pilihan Gaya Desain**

Karena Kakak belum punya referensi, saya siapkan 3 pilihan gaya. Pilih yang paling cocok dengan bisnis Kakak:

---

**1️⃣ Minimalis & Bersih**
- Warna: Putih, abu-abu lembut, aksen biru atau hijau
- Gaya: Banyak ruang kosong (white space), clean, fokus ke konten
- Navigasi: Sederhana dan intuitif
- Cocok untuk: Bisnis yang ingin kesan profesional dan rapi
- Inspirasi: Seperti tampilan Google Workspace / Notion

**2️⃣ Modern Profesional**
- Warna: Dark sidebar, konten terang, aksen warna brand
- Gaya: Dashboard dengan card, grafik, dan statistik
- Navigasi: Sidebar dengan icon dan label
- Cocok untuk: Bisnis yang butuh banyak data dan monitoring
- Inspirasi: Seperti tampilan admin panel modern

**3️⃣ Ramah & Colorful untuk UMKM**
- Warna: Warna-warni cerah tapi harmonis, background terang
- Gaya: Rounded corners, icon besar, tombol jelas
- Navigasi: Bottom tab (mobile) atau top tab (desktop)
- Cocok untuk: Bisnis yang tim-nya tidak terlalu melek teknologi
- Inspirasi: Seperti tampilan aplikasi kasir mobile

---

Kakak suka yang mana? Atau mau kombinasi dari beberapa gaya? 😊
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
