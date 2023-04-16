# ecommerce-ds
Final Project DS Rakamin Batch 31 - Kelompok 4 (Cobra)

## Data
Dataset yang digunakan dalam proyek ini berasal dari Kaggle, [E-Commerce Shipping Data](https://www.kaggle.com/datasets/prachi13/customer-analytics).

## Tahapan
Berikut adalah tahapan dan ringkasan dari kegiatan yang dilakukan dalam proyek ini:

### Stage 0: Preparation

### Stage 1: EDA, Insights & Visualization
1. Berdasarkan data yang tersedia, rasio keterlambatan pengiriman berada di 40.3% dari total pengiriman
2. Beberapa fitur yang diduga memiliki korelasi dengan keterlambatan pengiriman adalah Berat barang (Weight_in_gms) dan Diskon (Discount_offered), namun keduanya mengalami multikolinearitas karena juga saling berkorelasi
3. Terdapat beberapa data outlier jika dilihat berdasarkan berat barang (Weight_in_gms), yaitu barang-barang yang beratnya melebihi 6000 gram, namun untuk barang-barang tersebut tidak ada satupun yang mengalami keterlambatan
4. Nilai Customer rating tidak memiliki korelasi dengan keterlambatan (Reached_on_time) bahkan juga dengan feature-feature lain.

### Stage 2: Data Pre-processing
Beberapa tahapan yang dilakukan pada pre-processing:
1. Missing values and duplicate data - tidak ada nilai kosong dan data duplikat
2. Train - test split, menghasilkan 8799 data train dan 2200 data test
3. Outliers - ditentukan menggunakan z-score dan IQR modifikasi
4. Feature Transformation - dengan Normalizer, Log Transformation, dan MinMaxScaler
5. Feature Encoding - dengan OHE, Ordinal, dan Label Encoder
6. Class Imbalance - tidak perlu penanganan khusus karena rasio target masih sekitar 60:40
7. Feature Selection - terdapat 5 fitur yang memiliki korelasi yang terlihat dengan target, dengan 2 fitur mendominasi 3 lainnya
8. Feature Extraction - belum dirasa diperlukan, karena hanya ada 5 atau 2 fitur yang mungkin akan digunakan pada model nantinya dan bentuk model sendiri belum ditetapkan

### Stage 3: Machine Learning Modelling & Evaluation

### Stage 4: Final Preparation & Simulation

### Final Stage: The Day for Final Presentation


## Kontributor
- [Mezky Matthew Yandito](https://github.com/mezkymy)
- Fariyatul Ainiyah
- Ariella Arima Aniendra
- Dicky Maulana Rozi
- Mufid Habiburrahman
- Muhamad Fariduddin Syafiq
- Muhammad Raffi Yudhistira
- Een Subaeni
