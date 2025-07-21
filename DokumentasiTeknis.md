# 📋 Panduan Deployment dan Penggunaan Aplikasi Ekstraksi Data Kartu Keluarga

## 🚀 Cara Deploy Aplikasi

### 1. Persiapan Google Apps Script

#### Langkah 1: Buat Project Baru
1. Buka [Google Apps Script](https://script.google.com)
2. Klik **"New Project"**
3. Ubah nama project menjadi **"Ekstraksi Data KK"**

#### Langkah 2: Setup File Structure
1. **Rename** file `Code.gs` yang sudah ada
2. **Tambahkan** 3 file HTML baru:
   - `Index.html`
   - `JavaScript.html` 
   - `CSS.html`

#### Langkah 3: Copy-Paste Kode
1. **Code.gs**: Copy seluruh kode dari file Code.gs yang sudah dimodifikasi
2. **Index.html**: Copy seluruh kode dari file Index.html yang sudah dimodifikasi
3. **JavaScript.html**: Copy seluruh kode dari file JavaScript.html yang sudah dimodifikasi
4. **CSS.html**: Copy seluruh kode dari file CSS.html yang sudah dimodifikasi

### 2. Konfigurasi Izin & Deployment

#### Langkah 1: Set Izin Akses
1. Klik **"Review permissions"** jika muncul
2. Pilih akun Google Anda
3. Klik **"Advanced"** → **"Go to [Project Name] (unsafe)"**
4. Klik **"Allow"**

#### Langkah 2: Deploy sebagai Web App
1. Klik tombol **"Deploy"** → **"New deployment"**
2. Pilih type: **"Web app"**
3. **Description**: "Aplikasi Ekstraksi Data Kartu Keluarga v1.0"
4. **Execute as**: "Me"
5. **Who has access**: "Anyone" (untuk akses publik) atau "Anyone with Google account" (untuk akses terbatas)
6. Klik **"Deploy"**
7. **Copy URL** yang diberikan untuk akses aplikasi

#### Langkah 3: Update URL API (Optional)
1. Jika Anda memiliki API ekstraksi KK terpisah, update `CONFIG.API_URL` di Code.gs
2. Save dan deploy ulang

### 3. Setup Google Spreadsheet

#### Langkah 1: Buat Spreadsheet Baru
1. Buka [Google Sheets](https://sheets.google.com)
2. Buat spreadsheet baru
3. Berikan nama: **"Database Kartu Keluarga [Nama Desa/Kelurahan]"**

#### Langkah 2: Dapatkan Spreadsheet ID
1. Dari URL spreadsheet: `https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit`
2. Copy bagian `SPREADSHEET_ID`
3. Simpan ID ini untuk konfigurasi aplikasi

#### Langkah 3: Set Izin Akses Spreadsheet
1. Klik **"Share"** di spreadsheet
2. Tambahkan email akun yang menjalankan Apps Script
3. Berikan permission **"Editor"**

---

## 📱 Alur Penggunaan Aplikasi

### 1. Konfigurasi Awal

#### Step 1: Akses Aplikasi
1. Buka URL deployment aplikasi
2. Tunggu hingga aplikasi ter-load sempurna

#### Step 2: Setup Spreadsheet
1. Klik tab **"Pengaturan"**
2. Masukkan **Spreadsheet ID** yang sudah didapat
3. Klik **"Simpan"**
4. Aplikasi akan otomatis membuat sheet yang diperlukan:
   - `Data_KK` (Data master)
   - `Anggota_Keluarga` (Data anggota)
   - `Status_Hubungan` (Status hubungan keluarga)
   - `Orang_Tua` (Data orang tua)
   - `Data_Sosial` (Data perumahan)
   - `Log` (Log aktivitas)
   - `Metadata` (Metadata file)

### 2. Proses Ekstraksi Data KK

#### Step 1: Upload Kartu Keluarga
1. Klik tab **"Beranda"**
2. **Drag & drop** atau **klik "Pilih File"** untuk upload gambar KK
3. Format yang didukung: JPG, PNG, JPEG (Max 5MB)
4. Tunggu proses upload dan ekstraksi data

#### Step 2: Verifikasi Data Terekstrak
1. Periksa data yang berhasil diekstrak:
   - Nomor KK
   - Data Kepala Keluarga
   - Anggota Keluarga
   - Alamat lengkap
2. Jika data tidak akurat, lakukan koreksi manual di spreadsheet

#### Step 3: Isi Data Perumahan Tambahan
1. Scroll ke bagian **"Data Tambahan Perumahan"**
2. Isi field yang tersedia:
   - **RT**: Pilih RT 1-4 (required)
   - **RW**: Pilih RW 1-5 (required)  
   - **Blok**: Isi jika ada (optional)
   - **No Rumah**: Masukkan nomor rumah (required)
   - **Anggota Rukem Fasilitas**: Ya/Tidak
   - **Anggota Rukem Laham Pemakaman**: WNI/WNA
3. Klik **"Simpan Data Perumahan"**

### 3. Monitoring & Analisis

#### Lihat Statistik
1. Klik tab **"Statistik"**
2. Review data dashboard:
   - Total anggota keluarga
   - Distribusi gender
   - Status perkawinan
   - Agama
   - Pekerjaan
   - Sebaran kecamatan

#### Pencarian Data
1. Klik tab **"Cari Data"**
2. Masukkan kata kunci:
   - Nomor KK
   - NIK
   - Nama anggota keluarga
3. Klik **"Cari"** untuk melihat hasil

---

## 🔍 Alur Pengisian Form Detail

### Form Data Perumahan

#### Field Wajib (Required):
- **RT**: Pilihan radio button RT 1, RT 2, RT 3, atau RT 4
- **RW**: Dropdown pilihan angka 1-5
- **No Rumah**: Input text untuk nomor rumah

#### Field Opsional:
- **Blok**: Input text untuk kode blok (jika ada)
- **Anggota Rukem Fasilitas**: Radio button Ya/Tidak
- **Anggota Rukem Laham Pemakaman**: Radio button WNI/WNA

#### Validasi Form:
- Sistem akan menampilkan error jika field wajib kosong
- Data akan tersimpan ke sheet `Data_Sosial` di spreadsheet
- Jika data untuk KK tersebut sudah ada, akan diupdate otomatis

### Contoh Pengisian:
```
RT: [•] RT 1 [ ] RT 2 [ ] RT 3 [ ] RT 4
RW: [Dropdown: 3]
Blok: A (opsional)
No Rumah: 15
Anggota Rukem Fasilitas: [•] Ya [ ] Tidak
Anggota Rukem Laham: [•] WNI [ ] WNA
```

---

## 📊 Structure Data di Spreadsheet

### Sheet `Data_KK` (Master Data):
| Timestamp | Nomor KK | Nama Kepala KK | NIK Kepala KK | Alamat | RT/RW | Desa | Kecamatan | ... |

### Sheet `Data_Sosial` (Data Perumahan):
| Timestamp | Nomor KK | Nama Kepala KK | RT | RW | Blok | No Rumah | Anggota Rukem Fasilitas | Anggota Rukem Laham |

### Sheet `Anggota_Keluarga`:
| Timestamp | Nomor KK | NIK | Nama | Jenis Kelamin | Tempat Lahir | Tanggal Lahir | Agama | Pendidikan | Pekerjaan |

---

## 🔧 Troubleshooting

### Error Umum:

#### 1. "ID Spreadsheet tidak ditemukan"
- **Solusi**: Pastikan ID spreadsheet benar dan akun memiliki akses editor

#### 2. "Gagal terhubung ke API ekstraksi"
- **Solusi**: Periksa URL API di pengaturan atau gunakan mode manual

#### 3. "File terlalu besar"
- **Solusi**: Compress gambar atau gunakan format yang lebih ringan

#### 4. "Data tidak tersimpan"
- **Solusi**: Periksa koneksi internet dan izin akses spreadsheet

### Tips Optimasi:
- Gunakan gambar KK dengan resolusi yang jelas
- Pastikan koneksi internet stabil saat upload
- Backup data spreadsheet secara berkala
- Monitor log aktivitas untuk debugging
