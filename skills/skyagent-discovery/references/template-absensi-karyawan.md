# Template Referensi: Absensi & Manajemen Karyawan

## Deskripsi

Aplikasi pencatatan kehadiran dan manajemen karyawan untuk usaha kecil-menengah.

## Fitur Wajib

### 1. Dashboard Admin
- Total karyawan aktif
- Kehadiran hari ini (hadir, izin, cuti, alpha)
- Rekap kehadiran bulan ini
- Karyawan terlambat hari ini
- Grafik kehadiran mingguan

### 2. Data Karyawan
- Tambah, edit, hapus karyawan
- Nama, posisi, departemen, kontak
- Tanggal masuk kerja
- Status aktif/nonaktif
- Foto profil (opsional, link URL)

### 3. Check-in / Check-out
- Tombol check-in saat datang
- Tombol check-out saat pulang
- Catat waktu otomatis
- Lokasi GPS (opsional)
- Foto selfie (opsional)
- Deteksi keterlambatan otomatis

### 4. Izin & Cuti
- Form pengajuan izin/cuti
- Jenis: sakit, izin pribadi, cuti tahunan, dll
- Tanggal mulai & selesai
- Alasan
- Status: menunggu, disetujui, ditolak
- Approval oleh admin

### 5. Rekap Kehadiran
- Rekap per karyawan per bulan
- Total hadir, izin, cuti, alpha, terlambat
- Filter per departemen, periode
- Export rekap

### 6. Pengaturan
- Jam kerja (jam masuk, jam pulang)
- Toleransi keterlambatan (menit)
- Jatah cuti per tahun
- Hari libur

## Struktur Google Sheet

### Sheet: Employees
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | name | String |
| C | position | String |
| D | department | String |
| E | phone | String |
| F | email | String |
| G | joinDate | Date |
| H | photoUrl | String |
| I | status | String (active/inactive) |
| J | createdAt | DateTime |

### Sheet: Attendance
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | employeeId | String |
| C | date | Date |
| D | checkIn | DateTime |
| E | checkOut | DateTime |
| F | status | String (hadir/terlambat/izin/cuti/alpha) |
| G | lateMinutes | Number |
| H | notes | String |

### Sheet: Leaves
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | employeeId | String |
| C | type | String (sakit/izin/cuti) |
| D | startDate | Date |
| E | endDate | Date |
| F | reason | String |
| G | status | String (pending/approved/rejected) |
| H | approvedBy | String |
| I | createdAt | DateTime |

### Sheet: Users
| Kolom | Nama | Tipe |
|-------|------|------|
| A | id | UUID |
| B | email | String |
| C | password | String (hashed) |
| D | name | String |
| E | role | String (admin/employee) |
| F | employeeId | String |
| G | status | String (active/inactive) |

### Sheet: Settings
| Kolom | Nama | Tipe |
|-------|------|------|
| A | key | String |
| B | value | String |

## Role & Hak Akses

### Admin
- Semua fitur
- Approval izin/cuti
- Manajemen karyawan
- Rekap lengkap
- Pengaturan

### Karyawan
- Check-in/check-out sendiri
- Riwayat kehadiran sendiri
- Ajukan izin/cuti
- Lihat status pengajuan
