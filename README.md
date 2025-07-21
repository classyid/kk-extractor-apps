## 🏠 Aplikasi Ekstraksi Data Kartu Keluarga

[![Google Apps Script](https://img.shields.io/badge/Google%20Apps%20Script-4285F4?style=flat-square&logo=google&logoColor=white)](https://script.google.com)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

Aplikasi web modern untuk ekstraksi dan manajemen data Kartu Keluarga (KK) dengan fitur form data perumahan terintegrasi. Dibangun menggunakan Google Apps Script untuk kemudahan deployment dan maintenance.

## ✨ Fitur Utama

### 🔍 **Ekstraksi Data Otomatis**
- Upload gambar Kartu Keluarga (JPG/PNG/JPEG)
- Ekstraksi data otomatis menggunakan OCR/API
- Validasi format dokumen Kartu Keluarga
- Preview hasil ekstraksi real-time

### 🏘️ **Form Data Perumahan**
- Input data RT/RW
- Pencatatan nomor rumah dan blok
- Data keanggotaan Rukem Fasilitas
- Data keanggotaan Rukem Laham Pemakaman
- Validasi form dan penyimpanan otomatis

### 📊 **Dashboard & Statistik**
- Statistik demografis real-time
- Chart distribusi gender, agama, pekerjaan
- Analisis sebaran kecamatan
- Grafik status perkawinan

### 🔎 **Pencarian & Filter**
- Pencarian berdasarkan Nomor KK, NIK, atau Nama
- Filter data dengan multiple criteria
- Export hasil pencarian
- Preview detail data keluarga

### 💾 **Penyimpanan Terintegrasi**
- Auto-sync ke Google Spreadsheet
- Multiple sheet organization
- Backup data otomatis
- Log aktivitas lengkap

## 🚀 Quick Start

### 1. **Clone Repository**
```bash
git clone https://github.com/classyid/kk-extractor-apps.git
cd kk-extractor-apps
```

### 2. **Setup Google Apps Script**
1. Buka [Google Apps Script](https://script.google.com)
2. Buat project baru: "Ekstraksi Data KK"
3. Copy-paste code dari folder `/src`:
   - `Code.gs` → Google Apps Script editor
   - `Index.html` → Buat file HTML baru
   - `JavaScript.html` → Buat file HTML baru  
   - `CSS.html` → Buat file HTML baru

### 3. **Deploy Web App**
1. Klik **Deploy** → **New deployment**
2. Type: **Web app**
3. Execute as: **Me**
4. Access: **Anyone** (atau sesuai kebutuhan)
5. Klik **Deploy**

### 4. **Setup Google Spreadsheet**
1. Buat [Google Spreadsheet](https://sheets.google.com) baru
2. Copy Spreadsheet ID dari URL
3. Paste di pengaturan aplikasi

## 📁 Struktur File

```
kk-extractor-apps/
├── src/
│   ├── Code.gs              # Backend logic Google Apps Script
│   ├── Index.html           # Main UI interface
│   ├── JavaScript.html      # Frontend JavaScript logic
│   └── CSS.html            # Styling dan responsive design
├── README.md
```

## 🛠️ Konfigurasi

### Environment Variables (di Code.gs):
```javascript
const CONFIG = {
  API_URL: "YOUR_OCR_API_URL",                    // URL API OCR
  DEFAULT_SPREADSHEET_ID: "YOUR_SPREADSHEET_ID", // ID Google Spreadsheet
  UPLOAD_FOLDER_NAME: "KK_Uploads"               // Nama folder Google Drive
};
```

### Required Permissions:
- Google Sheets API
- Google Drive API  
- External API calls (untuk OCR)

## 📊 Struktur Data

### Sheet `Data_KK`:
| Field | Type | Description |
|-------|------|-------------|
| Timestamp | DateTime | Waktu input data |
| Nomor KK | String | Nomor Kartu Keluarga |
| Nama Kepala KK | String | Nama kepala keluarga |
| NIK Kepala KK | String | NIK kepala keluarga |
| Alamat | String | Alamat lengkap |

### Sheet `Data_Sosial`:
| Field | Type | Description |
|-------|------|-------------|
| RT | String | RT 1-4 |
| RW | String | RW 1-5 |
| Blok | String | Kode blok (opsional) |
| No Rumah | String | Nomor rumah |
| Anggota Rukem Fasilitas | String | Ya/Tidak |
| Anggota Rukem Laham | String | WNI/WNA |

## 🎯 Penggunaan

### 1. **Upload Kartu Keluarga**
```javascript
// Drag & drop atau klik untuk upload
// Format: JPG, PNG, JPEG (Max 5MB)
// Hasil ekstraksi akan ditampilkan otomatis
```

### 2. **Isi Form Perumahan**
```javascript
// Field wajib: RT, RW, No Rumah
// Field opsional: Blok, Rukem data
// Auto-save setelah submit
```

### 3. **Monitor Dashboard**
```javascript
// Real-time statistics
// Interactive charts
// Export capabilities
```

## 🤝 Contributing

1. **Fork** repository ini
2. **Create** feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** Pull Request

### Development Guidelines:
- Follow JavaScript ES6+ standards
- Use meaningful commit messages
- Add comments for complex logic
- Test on multiple browsers
- Update documentation

## 📝 Changelog

### v1.0.0 (2024-01-XX)
- ✨ Initial release
- 🔍 OCR-based KK data extraction
- 🏠 Housing data form integration
- 📊 Statistical dashboard
- 🔎 Advanced search functionality
- 💾 Google Spreadsheet auto-sync

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Google Apps Script** - Platform deployment
- **Chart.js** - Data visualization
- **Tailwind CSS** - UI framework
- **Font Awesome** - Icon library

## 📞 Support

- 📧 **Email**: [kontak@classy.id](mailto:kontak@classy.id)

---

<div align="center">

**[⭐ Star Repository](https://github.com/classyid/kk-extractor-apps)** • **[🐛 Report Bug](https://github.com/classyid/kk-extractor-apps/issues)** • **[💡 Request Feature](https://github.com/classyid/kk-extractor-apps/issues)**

Made with ❤️ for Indonesian Government Data Management

</div>
