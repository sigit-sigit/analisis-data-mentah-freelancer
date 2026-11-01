# analisis-data-mentah-freelancer

# Analisis Data Wrangling: Global Freelancers Dataset

Proyek ini merupakan tugas kelompok Data Wrangling yang mencakup tahapan pembersihan data (*data cleaning*), normalisasi fitur, evaluasi awal klasterisasi (*baseline clustering*), serta analisis univariat terhadap dataset *Global Freelancers*.

## 📁 Sumber Data
Dataset mentah yang digunakan diperoleh dari Kaggle:
* **Dataset:** [Global Freelancers Raw Dataset](https://www.kaggle.com/datasets/urvishahir/global-freelancers-raw-dataset)
* **File Mentah:** `global_freelancers_raw.csv` (1.000 baris, 12 kolom)

## 🛠️ Alur Analisis & Metodologi
1. **Data Preprocessing & Cleaning:**
   * Standarisasi nama kolom ke format *lowercase_with_underscore*.
   * Ekstraksi dan konversi tipe data numerik pada kolom tarif (`hourly_rate_usd`) dan kepuasan klien (`client_satisfaction`).
   * Penyeragaman kategori string pada `gender` dan binerisasi status keaktifan (`is_active` ke nilai `0` dan `1`).
   * Penghapusan baris dengan label `is_active` kosong serta imputasi nilai median untuk atribut numerik yang memiliki *missing value*.
2. **Normalisasi:**
   * Penskalaan fitur-fitur numerik kontinu (`age`, `years_of_experience`, `hourly_rate_usd`, `rating`, `client_satisfaction`) ke rentang `[0, 1]` menggunakan **MinMaxScaler**.
3. **Evaluasi Klasterisasi (Silhouette Score):**
   * Pengujian pembentukan klaster dengan algoritma K-Means untuk nilai $k = 2$ hingga $k = 8$ sebagai *baseline* evaluasi kerapatan struktur data.
4. **Analisis Univariat:**
   * Perhitungan statistik deskriptif (mean, median, IQR, standar deviasi) untuk variabel numerik.
   * Distribusi frekuensi variabel kategorikal.
   * Uji redundansi antara kolom `country` dan `language`.
   * Visualisasi distribusi menggunakan histogram dan boxplot.

## 📂 Struktur Repositori
```text
├── data/
│   └── raw/
│       └── global_freelancers_raw.csv
├── notebooks/
│   └── Data_Wrangling_Kel_4_Final.ipynb
├── .gitignore
├── README.md
└── requirements.txt
