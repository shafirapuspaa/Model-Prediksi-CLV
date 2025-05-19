# Prediksi Premi Asuransi (Insurance Charges Prediction)


## 1. Project Overview

### Latar Belakang
Proyek ini dikembangkan untuk memprediksi **Customer Lifetime Value (CLV)** pada perusahaan asuransi non-jiwa dengan akurasi tinggi. CLV menjadi metrik krusial dalam mengoptimalkan strategi bisnis berbasis data di industri yang sangat kompetitif ini.

### Data Utama
Model menggunakan 8 fitur kunci:
1. Demografi (`usia`, `jenis_kelamin`)
2. Polis (`jumlah_polis`, `premi_bulanan`)
3. Ekonomi (`pendapatan`)
4. Perilaku (`status_merokok`, `region`, `lama_berlangganan`)


---

## 2. Data Sources

- **Dataset:** Customer Lifetime Value

### Deskripsi Kolom:


| **Kolom**                  | **Deskripsi** |
|---------------------------|---------------|
| `Vehicle Class`           | Kategori kendaraan yang dimiliki oleh pelanggan, seperti `Two-Door Car`, `Four-Door Car`, `SUV`, `Luxury SUV`, dan `Luxury Car` |
| `Coverage`                | Jenis cakupan asuransi yang dipilih oleh pelanggan. Contoh nilai: `Basic`, `Extended`, `Premium` |
| `Renew Offer Type`        | Jenis penawaran yang diberikan saat pembaruan polis. Contoh nilai: `Offer 1`, `Offer 2`, dst.|
| `Employment Status`       | Status pekerjaan pelanggan, seperti `Employed`, `Unemployed`, `Medical Leave`, atau `Retired`|
| `Marital Status`          | Status pernikahan pelanggan, misalnya `Married`, `Single`, `Divorced` |
| `Education`               | Tingkat pendidikan pelanggan, seperti `High School`, `Bachelor`, `Master`, `Doctor` |
| `Number of Policies`      | Jumlah polis asuransi aktif yang dimiliki oleh pelanggan.|
| `Monthly Premium Auto`    | Jumlah premi bulanan yang dibayarkan oleh pelanggan untuk asuransi kendaraan|
| `Total Claim Amount`      | Jumlah total klaim yang diajukan pelanggan|
| `Income`                  | Pendapatan tahunan pelanggan|
| `Customer Lifetime Value` | Total nilai yang diperkirakan akan dihasilkan pelanggan selama masa hubungan mereka dengan perusahaan. Ini adalah target utama dalam analisis CLV. |
---

## 3. Technologies Used

- **Bahasa Pemrograman:** Python
- **Library Machine Learning:**  
  - Scikit-learn  
  - XGBoost  
  - CatBoost  
  - Gradient Boosting  
- **Visualisasi:** Seaborn, Matplotlib
- **Pengelolaan Proyek:** Jupyter Notebook, Git

---

## 4. Summary of Findings

### 4.1 Business Insight

**Rekomendasi Strategis untuk Perusahaan Asuransi**
1. Fokuskan upaya retensi, upselling, dan cross-selling pada segmen dengan CLV tinggi.

2. Optimalkan Penawaran Berdasarkan Fitur Penting
Berdasarkan hasil SHAP dan feature importance, fitur-fitur seperti Number of Policies, Monthly Premium Auto, dan Income. Penawaran dapat berupa:
- Menawarkan bundling produk atau insentif kepada pelanggan dengan jumlah polis lebih banyak.
- Meninjau kembali struktur premi agar tetap menarik untuk pelanggan berpotensi tinggi.
- Menyesuaikan penawaran produk berdasarkan daya beli pelanggan (Income).

3. Bangun Strategi Khusus untuk Pelanggan CLV Tinggi. Model saat ini memiliki akurasi yang menurun pada nilai CLV ekstrem (>15.000).
- Lakukan analisis tambahan atau pendekatan manual untuk segmen ini.
- Pertimbangkan membangun model terpisah khusus untuk high-value clients.

---

## 5. Models Used & Evaluation

### Model Regresi yang Digunakan:

- Linear Regression  
- K-Nearest Neighbors Regressor  
- Decision Tree Regressor  
- CatBoost Regressor  
- XGBoost Regressor  
- Gradient Boosting Regressor  
- Lasso Regression  
- Ridge Regression

Model akhir yang digunakan adalah Gradient Boosting Regressor  karena memiliki nilai MAE atau eror terkecil dibanding model lainnya

---
### Metrik Evaluasi:

- Mean absolute error (MAE) 
- Mean absolute percentage error(MAPE)

Model fokus melihat niali MAE dan MAPE untuk mempermudah interpretasi

---
**Performa Model**

Model Gradient Boosting menunjukkan hasil terbaik dari seluruh metrik evaluasi:

| Metric       | Train         | Test          |
|--------------|---------------|---------------|
| MAE          | $1,649.55     | $1,636.25     |
| MAPE         | 13.07%        | 13.55%        |

Evaluasi ini menunjukkan bahwa model memiliki **akurasi yang baik dan stabil**, dengan perbedaan performa antara data latih dan uji yang kecil. Hal ini menandakan bahwa **model mampu melakukan generalisasi dengan baik dan minim overfitting**.  Prediksi kesalahan model sekitar $1,636–1,649 dari nilai asli atau sekitar 13% dari nilai aktual.

**Limitasi model**

Meskipun model menunjukkan performa yang baik secara umum, terdapat **penurunan akurasi** pada prediksi **CLV ekstrem tinggi** (di atas $15.000). Error pada segmen ini cenderung lebih besar dan tidak konsisten.

>*Implikasinya*: Diperlukan pendekatan tambahan—seperti segmentasi pelanggan atau model khusus untuk outlier—agar prediksi pada pelanggan bernilai sangat tinggi menjadi lebih andal



