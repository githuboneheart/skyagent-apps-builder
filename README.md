# SkyAgent Apps Builder

**AI Agent konsultan produk dan Apps Script builder untuk UMKM Indonesia.**

SkyAgent adalah Antigravity Plugin yang memandu member dari ide bisnis → discovery → PRD → UI Plan → kode Google Apps Script, semuanya dalam bahasa Indonesia yang ramah dan mudah dipahami.

## 🎯 Untuk Siapa?

- Pemilik UMKM Indonesia
- Freelancer
- Pemilik bisnis kecil-menengah
- Mahasiswa
- Calon developer

## 🚀 Cara Pakai

Cukup tag `@skyagent` di Antigravity dan jelaskan kebutuhan bisnis Anda:

```
@skyagent saya mau aplikasi POS untuk toko kelontong, bisa catat penjualan, stok barang, dan pengeluaran.
```

SkyAgent akan memandu Anda melalui proses:

1. **Discovery** — Memahami kebutuhan bisnis Anda
2. **Referensi UI** — Menentukan tampilan aplikasi
3. **UI Plan** — Rancangan detail tampilan
4. **PRD** — Dokumen kebutuhan produk lengkap
5. **Generate Kode** — Membuat kode Google Apps Script
6. **QA** — Memeriksa kualitas kode
7. **Deployment** — Panduan deploy aplikasi

## 📦 Template Bawaan

### 1. POS UMKM
Aplikasi kasir lengkap: produk, stok, transaksi, pengeluaran, laporan laba rugi.

### 2. Absensi & Manajemen Karyawan
Pencatatan kehadiran: check-in/out, izin, cuti, rekap bulanan.

### 3. Booking & Pendaftaran
Sistem pemesanan layanan: jadwal, booking, konfirmasi, laporan.

## 📁 Struktur Plugin

```
skyagent-plugin/
├── plugin.json                    # Manifest plugin
├── README.md                      # Dokumentasi
├── agents/
│   └── skyagent.md                # Definisi agent @skyagent
├── rules/
│   └── AGENTS.md                  # Aturan global
├── skills/
│   ├── skyagent-discovery/        # Skill wawancara & rekomendasi
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── template-pos-umkm.md
│   │       ├── template-absensi-karyawan.md
│   │       └── template-booking-pendaftaran.md
│   ├── skyagent-ui-analysis/      # Skill analisis referensi UI
│   │   └── SKILL.md
│   ├── skyagent-ui-plan/          # Skill pembuatan UI Plan
│   │   └── SKILL.md
│   ├── skyagent-prd-builder/      # Skill pembuatan PRD
│   │   └── SKILL.md
│   ├── skyagent-apps-script-generator/  # Skill generate kode
│   │   ├── SKILL.md
│   │   ├── templates/
│   │   └── references/
│   ├── skyagent-qa/               # Skill Quality Assurance
│   │   └── SKILL.md
│   └── skyagent-revision/         # Skill revisi fitur/tampilan
│       └── SKILL.md
└── assets/
    └── logo.svg                   # Logo plugin
```

## ⚙️ Instalasi

### Opsi 1: Global (untuk semua project)

Copy folder `skyagent-plugin` ke:
```
~/.gemini/config/plugins/skyagent-plugin/
```

### Opsi 2: Per-project (untuk project tertentu)

Copy folder `skyagent-plugin` ke:
```
.agents/plugins/skyagent-plugin/
```

## 📋 Alur Kerja Detail

```
Member menulis ide
        ↓
SkyAgent memahami ide
        ↓
Discovery (3-5 pertanyaan per putaran)
        ↓
Rekomendasi fitur wajib & opsional
        ↓
Member konfirmasi fitur
        ↓
Tanya referensi UI
        ↓
Analisis referensi / pilih gaya desain
        ↓
Buat UI Plan → Konfirmasi member
        ↓
Buat PRD lengkap → Review member
        ↓
Member setujui PRD → Tekan "Proses"
        ↓
Generate kode Apps Script
        ↓
QA (quality check)
        ↓
Pop-up konfirmasi pembuatan
        ↓
Buat Spreadsheet & Apps Script
        ↓
Panduan deployment
        ↓
Aplikasi siap! 🎉
```

## ⚠️ Batasan

- Aplikasi berjalan di Google Apps Script (ada batasan waktu eksekusi, concurrent users, dll)
- Untuk kebutuhan yang lebih besar, SkyAgent akan merekomendasikan Laravel atau solusi lain
- Member tetap perlu melakukan otorisasi Google dan deployment sendiri
- Desain UI dibatasi oleh kemampuan HTML Service di Apps Script

## 📝 Lisensi

MIT License

## 👥 Kontribusi

Kontribusi sangat diterima! Silakan buka issue atau pull request.
