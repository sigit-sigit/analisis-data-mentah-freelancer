# analisis-data-mentah-freelancer

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

## 📁 Keterangan Dataset & Folder Hasil Preprocessing

Selain menyediakan dataset mentah, repositori ini juga menyediakan data hasil tahapan pemrosesan agar dapat langsung ditinjau tanpa harus menjalankan ulang keseluruhan notebook:

### 1. Data Mentah (*Raw Data*)
* `global_freelancers_raw.csv`: Dataset asli yang diunduh langsung dari Kaggle sebelum dilakukan pembersihan.

### 2. Folder Data Hasil Preprocessing (`udah di preprocess/`)
Folder ini memuat *output* dari masing-masing tahapan data wrangling:

* **`global_freelancers_preprocessing.csv`**:
  Data hasil pembersihan tahap pertama[cite: 1]. Format mata uang (`$` dan `USD`) serta persentase (`%`) telah dikonversi ke numerik, label `gender` dan status aktif `is_active` telah diseragamkan, baris dengan target kosong dihapus, dan *missing value* pada fitur numerik telah diimputasi menggunakan nilai median.
  
* **`global_freelancers_normalisasi.csv`**:
  Data bersih yang seluruh variabel numerik kontinunya (`age`, `years_of_experience`, `hourly_rate_usd`, `rating`, `client_satisfaction`) telah diskalakan ke rentang `[0, 1]` menggunakan metode **Min-Max Scaling** agar bobot antarfitur seragam saat digunakan untuk pemodelan.

* **`global_freelancers_no_outliers.csv`**:
  Data yang telah melalui tahap deteksi dan penanganan nilai pencilan (*outlier removal*), sehingga data yang ekstrem telah difilter.

* **`global_freelancers_no_outliers_nilai_asli.csv`**:
  Data yang telah bersih dari pencilan (*outliers*), namun nilainya dikembalikan ke skala/satuan aslinya (bukan rentang 0–1) agar mudah dibaca dan diinterpretasikan secara statistik.
