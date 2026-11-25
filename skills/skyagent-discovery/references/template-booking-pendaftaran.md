# Template Referensi: Booking & Pendaftaran

## Deskripsi

Aplikasi pemesanan/booking layanan dan pendaftaran untuk bisnis jasa (salon, klinik, kursus, dll).

## Fitur Wajib

### 1. Halaman Info (Landing Page)
- Informasi bisnis (nama, alamat, kontak)
- Daftar layanan yang tersedia
- Harga layanan
- Jam operasional
- Tombol "Book Now"

### 2. Form Booking
- Pilih layanan
- Pilih tanggal
- Pilih jam/slot yang tersedia
- Isi data diri (nama, HP, email)
- Catatan tambahan
- Konfirmasi booking

### 3. Dashboard Admin
- Booking hari ini
- Booking mendatang
- Total booking bulan ini
- Status booking (menunggu, dikonfirmasi, selesai, batal)

### 4. Kelola Jadwal
- Atur hari dan jam operasional
- Atur kapasitas per slot
- Blokir tanggal tertentu (libur)
- Atur durasi per layanan

### 5. Daftar Booking
- Semua booking dengan filter
- Filter per tanggal, status, layanan
- Detail booking
- Ubah status (konfirmasi, selesai, batal)

### 6. Konfirmasi & Status
- Status booking real-time untuk pelanggan
- Halaman cek status booking (via kode booking)

### 7. Laporan
- Laporan booking per periode
- Layanan terpopuler
- Revenue per layanan
- Filter per tanggal

## Struktur Google Sheet

### Sheet: Services
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | name | String |
| C | description | String |
| D | duration | Number (menit) |
| E | price | Number |
| F | category | String |
| G | status | String (active/inactive) |

### Sheet: Bookings
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | bookingCode | String |
| C | customerName | String |
| D | customerPhone | String |
| E | customerEmail | String |
| F | serviceId | String |
| G | date | Date |
| H | timeSlot | String |
| I | status | String (pending/confirmed/completed/cancelled) |
| J | notes | String |
| K | createdAt | DateTime |

### Sheet: Schedule
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | dayOfWeek | String (Senin-Minggu) |
| C | startTime | String (HH:mm) |
| D | endTime | String (HH:mm) |
| E | slotDuration | Number (menit) |
| F | maxCapacity | Number |
| G | isActive | Boolean |

### Sheet: BlockedDates
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | date | Date |
| C | reason | String |

### Sheet: Users
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | email | String |
| C | password | String (hashed) |
| D | name | String |
| E | role | String (admin/staff) |
| F | status | String (active/inactive) |

### Sheet: Settings
| Kolom | Nama | Tipe |
|-------|------|------|
| A | key | String |
| B | value | String |

## Role & Hak Akses

### Admin
- Semua fitur
- Kelola jadwal dan layanan
- Konfirmasi/batalkan booking
- Laporan lengkap
- Pengaturan

### Staff
- Lihat booking hari ini
- Update status booking (konfirmasi, selesai)
- Lihat jadwal

### Pelanggan (tanpa login)
- Lihat info dan layanan
- Buat booking baru
- Cek status booking via kode
