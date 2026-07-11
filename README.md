# 👩‍💼 Klasifikasi dan Prediksi Indeks Pemberdayaan Gender (IPG) Indonesia

Analisis data **Indeks Pemberdayaan Gender (IPG)** kabupaten/kota di Indonesia periode 2021–2023, menggunakan pendekatan **klasifikasi (KNN)** untuk mengelompokkan wilayah berdasarkan kategori IPG, dan **regresi (Linear Regression)** untuk memproyeksikan nilai IPG tahun 2024.

## 📌 Latar Belakang

Indeks Pemberdayaan Gender (IPG) mengukur sejauh mana perempuan berperan aktif dalam kehidupan ekonomi dan politik di suatu wilayah. Nilai IPG bervariasi cukup signifikan antar kabupaten/kota di Indonesia, dan mengetahui wilayah mana yang tertinggal dapat membantu pemerintah menentukan prioritas kebijakan pemberdayaan perempuan secara lebih terarah.

## 🎯 Rumusan Masalah

1. Wilayah mana saja yang memiliki kategori IPG "Rendah", dan dapatkah kategori ini diprediksi berdasarkan tren nilai historisnya?
2. Bagaimana proyeksi nilai IPG tiap wilayah pada tahun 2024 berdasarkan tren 2021–2023?
3. Wilayah mana yang diproyeksikan memiliki IPG terendah pada 2024, sehingga perlu menjadi prioritas intervensi?

## 🎯 Tujuan Project

- Membangun model klasifikasi kategori IPG (Tinggi/Rendah) menggunakan KNN.
- Membangun model regresi untuk memproyeksikan nilai IPG tahun 2024 tiap wilayah, dengan validasi yang genuine menggunakan data historis yang benar-benar tersedia.
- Mengidentifikasi wilayah dengan IPG terendah sebagai bahan rekomendasi kebijakan.

## 💡 Manfaat

**Untuk Pemerintah/Kementerian PPPA & Pemerintah Daerah:**
- Membantu memetakan wilayah prioritas untuk program pemberdayaan perempuan secara lebih terarah dan berbasis data, bukan hanya berdasarkan asumsi.
- Proyeksi tahun berikutnya dapat menjadi early warning bagi wilayah yang berpotensi mengalami penurunan IPG.

**Untuk Peneliti/Akademisi:**
- Menjadi referensi studi kesenjangan gender antar wilayah di Indonesia, serta contoh penerapan klasifikasi & regresi pada data statistik wilayah.

**Dari Sisi Teknis (Data Science):**
- Studi kasus penerapan klasifikasi dan regresi pada data deret waktu (time-series) singkat berbasis wilayah, termasuk bagaimana menghindari data leakage dan melakukan validasi proyeksi secara jujur.

## 📊 Dataset

Dataset berisi nilai Indeks Pemberdayaan Gender (IPG) untuk ratusan kabupaten/kota di Indonesia pada tahun 2021, 2022, dan 2023, bersumber dari data resmi (BPS/Kementerian PPPA).

## 🔬 Metodologi

1. **Problem Statement** — perumusan masalah dan tujuan analisis
2. **Data Understanding** — eksplorasi struktur data, pengecekan missing value, duplikat, dan baris agregat non-wilayah
3. **Data Preparation** — mengeluarkan baris agregat nasional ("INDONESIA"), menghapus duplikat, menangani nilai kosong/nol
4. **Exploratory Data Analysis (EDA)** — correlation heatmap antar tahun dan distribusi nilai IPG
5. **Klasifikasi (KNN)** — pembuatan label kategori dari nilai 2023, pemilihan fitur yang menghindari data leakage, pemilihan K optimal melalui cross-validation, evaluasi pada data test terpisah
6. **Regresi (Linear Regression)** — validasi metode dengan memprediksi nilai 2023 dari tren 2021–2022 dan membandingkannya dengan nilai 2023 asli, sebelum digunakan untuk memproyeksikan nilai 2024
7. **Kesimpulan & Rekomendasi**

## 📈 Hasil Utama

**Klasifikasi (KNN):**
| Metrik | Nilai |
|---|---|
| K optimal (cross-validation) | 5 |
| Akurasi (data test) | 94.5% |
| F1-Score kategori Rendah / Tinggi | 0.96 / 0.93 |

**Regresi (validasi genuine — prediksi 2023 dari tren 2021–2022, dibanding nilai 2023 asli):**
| Metrik | Nilai |
|---|---|
| RMSE | 4.75 |
| MAE | 2.59 |
| R² | 0.755 |

**Insight utama:**
- Fitur klasifikasi sengaja dibatasi hanya pada nilai 2021 dan 2022 (bukan 2023, yang menjadi sumber label) agar model benar-benar memprediksi berdasarkan tren, bukan "mengintip" jawaban.
- Proyeksi nilai IPG 2024 divalidasi terlebih dahulu menggunakan data historis yang sudah diketahui (2023), sehingga tingkat kepercayaan proyeksi (RMSE ≈ 4.75 poin) dapat dipertanggungjawabkan, bukan sekadar angka tanpa dasar.
- Wilayah dengan IPG terendah relatif konsisten dari tahun ke tahun, menunjukkan bahwa kesenjangan pemberdayaan gender di wilayah tersebut bersifat struktural dan memerlukan intervensi berkelanjutan, bukan sekadar kebijakan jangka pendek.

## 🛠️ Tools & Library

- Python
- Pandas, NumPy — manipulasi data
- Matplotlib, Seaborn — visualisasi data
- Scikit-learn — modeling (KNN, Linear Regression), evaluasi, dan cross-validation

## 📂 Struktur Project

```
├── Classification_and_Regresion_Indeks_Pemberdayaan_Gender_IKG.ipynb   # Notebook analisis lengkap
└── Indeks Pemberdayaan Gender 2021-2023.csv                            # Dataset
```

## 🚀 Cara Menjalankan

```bash
# 1. Clone repository
git clone https://github.com/DanuSetiawan05/Classification-and-Regression-Gender-Empowerment-Index.git
cd Classification-and-Regression-Gender-Empowerment-Index

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# 3. Jalankan notebook
jupyter notebook Classification_and_Regresion_Indeks_Pemberdayaan_Gender_IKG.ipynb
```

## 🔮 Pengembangan Selanjutnya

- Menambahkan data historis lebih dari 3 tahun agar tren yang ditangkap model regresi lebih stabil.
- Mengeksplorasi fitur tambahan (misalnya indikator ekonomi atau pendidikan wilayah) untuk memperkaya model klasifikasi.
- Membandingkan pendekatan regresi per-wilayah ini dengan model time-series lain (misalnya ARIMA) untuk melihat konsistensi hasil proyeksi.

## 👤 Author

**Muhammad Danu Setiawan**
[LinkedIn](https://www.linkedin.com/in/danu-setiawan-98b496348/) · [GitHub](https://github.com/DanuSetiawan05)
