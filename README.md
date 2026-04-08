# dashboard-kependudukan
prototype
# Dashboard Kependudukan Kelurahan

Dashboard interaktif analisis data kependudukan 35 RT periode 2021–2025, dilengkapi hasil pengelompokan K-Means dan proyeksi penduduk 2026–2028.

---

## Tampilan

- Mode gelap dan mode terang
- Warna chart berubah otomatis setiap 10 detik
- Klik kotak RT untuk melihat detail penduduk per RT

---

## Fitur Utama

- **KPI ringkasan** — total jiwa, jumlah laki-laki, perempuan, dan rasio L:P
- **Grafik tren** — total, gender, per kelompok, dan proyeksi 2026–2028
- **Peta sebaran RT** — 35 RT berwarna sesuai kelompok K-Means
- **Top 10 RT** — RT dengan total penduduk terbanyak
- **Profil 7 kelompok** — hasil analisis K-Means lengkap dengan anggota RT dan arah tren
- **Proyeksi 2026–2028** — berdasarkan regresi linear per kelompok
- **Peringatan otomatis** — RT yang membutuhkan perhatian khusus

---

## Data

| Keterangan | Nilai |
|------------|-------|
| Jumlah RT | 35 RT |
| Periode data | 2021 – 2025 |
| Total jiwa tercatat | 76.128 jiwa |
| Total laki-laki | 38.887 (51,1%) |
| Total perempuan | 37.241 (48,9%) |
| Rasio L : P | 1,04 (hampir seimbang) |

---

## Hasil Analisis K-Means (K=7)

| Kelompok | Nama | Jumlah RT | Tren |
|----------|------|-----------|------|
| 0 | Fluktuasi Stabil | 5 RT | +26/tahun |
| 1 | Penurunan Kuat | 5 RT | −166/tahun |
| 2 | Tumbuh Stabil | 7 RT | +13/tahun |
| 3 | Pertumbuhan Sedang | 6 RT | +67/tahun |
| 4 | Populasi Kecil Naik | 7 RT | +45/tahun |
| 5 | Populasi Besar | 3 RT | +81/tahun |
| 6 | Penurunan Kritis | 2 RT | −137/tahun |

**Validasi model:**
- Silhouette Score: **0,295** (moderat — wajar untuk data populasi heterogen)
- Davies-Bouldin Index: **0,865** (cukup baik, makin kecil makin baik)

---

## Metode Analisis

Penelitian ini merupakan bagian dari Tugas Akhir D3. Metode yang digunakan:

1. **K-Means Clustering** — pengelompokan RT berdasarkan pola populasi (rata-rata, slope tren, koefisien variasi, range)
2. **Regresi Linear Tren** — identifikasi arah tren dan proyeksi jangka pendek 2026–2028
3. **StandardScaler** — normalisasi fitur sebelum clustering
4. **Silhouette Score + Davies-Bouldin Index** — validasi kualitas klaster

> Metode seperti ARIMA, Prophet, atau ETS tidak digunakan karena data historis hanya 5 titik waktu, di bawah minimum yang dibutuhkan metode tersebut.

---

## Teknologi

- HTML / CSS / JavaScript (vanilla, tanpa framework)
- [Chart.js 4.4.1](https://www.chartjs.org/) — visualisasi grafik
- Python + scikit-learn — pengolahan data dan K-Means (tidak dijalankan di browser)

---

## Cara Menggunakan

**Buka langsung di browser:**
```
Klik dua kali file index.html
```

**Atau akses online via GitHub Pages:**
```
https://github.com/edityanurpratama/dashboard-kependudukan
```

---

## Struktur File

```
/
├── index.html       # Dashboard utama (semua-dalam-satu)
└── README.md        # Dokumentasi ini
```

---

## Keterbatasan

- Data historis hanya 5 tahun sehingga proyeksi bersifat indikatif
- Proyeksi tidak memperhitungkan faktor eksternal (ekonomi, migrasi, kebijakan)
- Silhouette Score 0,295 mengindikasikan batas antar klaster tidak sepenuhnya tegas

---

## Referensi

- Rousseeuw, P. J. (1987). Silhouettes: A graphical aid to the interpretation and validation of cluster analysis. *Computational and Applied Mathematics*, 20, 53–65.
- Davies, D. L., & Bouldin, D. W. (1979). A cluster separation measure. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, PAMI-1(2), 224–227.
- Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, 12, 2825–2830.

---

## Lisensi

MIT License — bebas digunakan dan dimodifikasi dengan mencantumkan sumber.
