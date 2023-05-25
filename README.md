# E-Commerce Shipping Data Analysis and Prediction Model
Final Project DS Rakamin Batch 31 - Kelompok 4 (Cobra)

## Data
Dataset yang digunakan dalam proyek ini berasal dari Kaggle, [E-Commerce Shipping Data](https://www.kaggle.com/datasets/prachi13/customer-analytics).

## Latar Belakang
Sebuah perusahaan e-commerce skala internasional seringkali mengalami masalah keterlambatan dalam proses pengiriman barang. Berdasarkan data yang dimiliki, rasio pengiriman yang mengalami keterlambatan mencapai hampir 60% dari keseluruhan pengiriman. Hal ini dapat berdampak kepada tingkat kepuasan pelanggan (customer satisfaction) dan memungkinkan terjadinya penurunan laba akibat churning maupun tambahan biaya operasional yang perlu dikeluarkan, seperti biaya sewa gudang dan logistik. Perusahaan dapat menggunakan sebuah model machine learning yang dapat memprediksi apakah suatu pengiriman akan terlambat atau tidak sebagai upaya untuk meningkatkan rasio pengiriman tepat waktu.

## Stage 1: EDA, Insights & Visualization
1. Pada discount offered terhadap weight, pada umumnya barang-barang yang beratnya di atas 4000 gram tidak diberikan diskon lebih besar dari 10% (kecuali untuk beberapa outlier).
2. Barang yang diberikan diskon lebih dari 10% tidak ada yang pengirimannya tepat waktu
3. Barang dengan berat di antara 2000-4000 gram harganya ada di kisaran ~200 sampai ~300 dollar, dan tidak ada yang pengirimannya tepat waktu
4. Terdapat beberapa data outlier jika dilihat berdasarkan berat barang (`Weight_in_gms`), yaitu barang-barang yang beratnya melebihi 6000 gram, namun untuk barang-barang tersebut tidak ada satupun yang tidak mengalami keterlambatan
5. Barang yang pengirimannya tepat waktu hanya terjadi pada barang yang beratnya ada di bawah 2000 gram atau di antara 4000-6000 gram.
6. Karena pada fitur `Weight_in_gms`, `Discount_offered`, dan `Cost_of_the_products` data cukup tersegmentasi dengan sangat jelas, maka dapat dibentuk suatu fitur kategorikal baru berdasarkan fitur-fitur tersebut.

## Stage 2: Data Pre-processing
Beberapa tahapan yang dilakukan pada pre-processing:
1. Missing values and duplicate data - tidak ada nilai kosong dan data duplikat
2. Train - test split, dibagi dengan rasio 80:20 sehingga diperoleh 8799 data train dan 2200 data test
3. Outliers - ditentukan menggunakan z-score, karena jumlah outlier tidak banyak maka data outlier dihilangkan dari train data
4. Feature Transformation - dengan Normalizer, Log Transformation, dan MinMaxScaler
5. Feature Encoding - dengan OHE, Ordinal, dan Label Encoder
6. Class Imbalance - tidak perlu penanganan khusus karena rasio target masih sekitar 60:40

Untuk Feature Transformation dan Feature Encoding, digunakan pipeline untuk mencegah terjadinya data leakage.

## Stage 3: Machine Learning Modeling & Evaluation
Target merupakan data dengan tipe kategorik (0 dan 1), sehingga pada bagian modeling dipilih metode-metode dari supervised learning berjenis klasifikasi, dimana tujuan dari model yang dibentuk adalah untuk memprediksi apakah suatu pengiriman akan mengalami keterlambatan (nilai 1) atau tidak (nilai 0). Model-model yang digunakan pada studi kasus ini adalah:

- Decision Tree
- Random Forest
- Logistic Regression
- K-Nearest Neighbor
- XGBoost
- SVM

Berdasarkan hasil cross validation dengan menggunakan skor recall, dipilih model Decision Tree sebagai model yang terbaik, walaupun masih terjadi overfit pada model dasar. Setelah dilakukan tuning hyperparameter,  model akhir memiliki nilai recall sebesar 64.343 % pada data train dan 62.833 % pada data test, sehingga model tidak lagi mengalami overfitting yang signifikan.

Beberapa rekomendasi yang dapat dilakukan sebagai tindak lanjut:
1. Perlu pengumpulan data yang lebih banyak dan lengkap untuk memperkuat kekuatan prediksi model, contohnya dengan menambah fitur data terkait dengan:
    - Waktu Keterlambatan: supaya model tidak hanya dapat memprediksi apakah pengiriman terlambat atau tidak, namun juga estimasi durasi keterlambatan
    - Tanggal Pengiriman: apakah pengiriman terlambat terjadi pada rentang waktu tertentu, seperti hari libur?
    - Wilayah Pengiriman: apakah pengiriman terlambat terjadi pada wilayah-wilayah tertentu saja?
    - Jenis/Jasa Kurir: apakah pengiriman yang terlambat memiliki keterkaitan terhadap jasa kurir yang digunakan?
    - Jenis promo/diskon yang ditawarkan: apakah diskon di atas 10% diberikan sebagai bentuk cuci gudang terhadap barang-barang yang tidak terlalu diminati?
    - Tipe/kategori barang elektronik yang dijual (TV, Gadget, dll): apakah barang-barang pada rentang berat yang dibentuk merupakan tipe barang yang sejenis, dan apakah ada keterkaitannya terhadap keterlambatan pengiriman?
2. Model dapat digunakan/di-deploy dalam sistem e-commerce untuk menyaring pesanan yang diduga akan mengalami keterlambatan, sehingga pengiriman tersebut dapat diprioritaskan dan/atau pelanggan dapat diberikan notifikasi terhadap dugaan keterlambatan tersebut.

## Kontributor
- [Mezky Matthew Yandito](https://github.com/mezkymy)
- [Fariyatul Ainiyah](https://github.com/uniainiyah)
- [Ariella Arima Aniendra](https://github.com/arllarima)
- [Dicky Maulana Rozi](https://github.com/dickymrz)
- [Mufid Habiburrahman](https://github.com/hrmufid)
- [Muhamad Fariduddin Syafiq](https://github.com/MFSyafiq)
- [Muhammad Raffi Yudhistira](https://github.com/Mraffiy33)
