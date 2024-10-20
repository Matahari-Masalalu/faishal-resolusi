# Laporan Proyek Machine Learning - Faishal Anwar Haysim

## Domain Proyek
Proyek ini bertujuan untuk membangun model machine learning untuk memprediksi harga penutupan (Close) Bitcoin (BTC) dengan menggunakan dataset harga Bitcoin (BTC) dalam USD. Dataset ini memuat informasi mengenai harga pembukaan (Open), harga tertinggi (High), harga terendah (Low), harga penutupan (Close), harga penutupan yang disesuaikan (Adj Close), dan volume perdagangan (Volume) pada periode waktu tertentu. Model prediksi yang dihasilkan diharapkan dapat membantu investor untuk membuat keputusan investasi yang lebih baik dan mengoptimalkan keuntungan.

- Permintaan yang semakin tinggi untuk cryptocurrency, khususnya Bitcoin, menyebabkan fluktuasi harga yang sangat tinggi dan sulit diprediksi. Untuk meminimalkan risiko kerugian, para investor membutuhkan alat bantu yang akurat untuk memprediksi pergerakan harga Bitcoin. Model machine learning yang akurat dapat membantu investor untuk memprediksi pergerakan harga Bitcoin dan meminimalkan risiko kerugian.

## Business Understanding

### Problem Statements

- Pernyataan Masalah 1: Bagaimana merancang model machine learning yang dapat memprediksi harga penutupan (Close) Bitcoin dengan akurasi yang tinggi?
- Pernyataan Masalah 2: Bagaimana mengoptimalkan performa model machine learning dengan teknik data preparation dan hyperparameter tuning?

### Goals
- Jawaban pernyataan masalah 1: Membangun model machine learning yang dapat memprediksi harga penutupan (Close) Bitcoin dengan akurasi yang tinggi, diukur dengan metrik Mean Squared Error (MSE).
- Jawaban pernyataan masalah 2: Mengoptimalkan performa model machine learning dengan teknik data preparation dan hyperparameter tuning sehingga nilai MSE pada data testing lebih kecil.
### Solution Statement
Penggunaan Multiple Algoritma Machine Learning: Proyek ini akan menggunakan tiga algoritma machine learning, yaitu K-Nearest Neighbors (KNN), Random Forest, dan Boosting (AdaBoost). Ketiga algoritma ini dipilih karena kemampuannya yang berbeda dalam menangani data dengan karakteristik yang kompleks, sehingga diharapkan dapat memberikan hasil yang optimal.
Data Preparation: Proyek ini akan menggunakan teknik data preparation untuk meningkatkan kualitas data dan performa model, seperti:
Encoding Fitur Kategori: Mengubah kolom tanggal (Date) menjadi fitur numerik dengan mengekstrak informasi tahun, bulan, hari, dan hari dalam seminggu.

## Data Understanding

Dataset yang digunakan pada proyek ini adalah dataset Bitcoin (BTC-USD) Stock Data yang diunduh dari Kaggle atau Google Drive. Dataset ini berisi informasi historis tentang harga Bitcoin dari tahun 2014 hingga 2023.

- Variabel-variabel pada Bitcoin dataset adalah sebagai berikut:
- Date: Tanggal data yang direkam (dalam format YYYY-MM-DD).
- Open: Harga pembukaan Bitcoin pada hari tersebut.
- High: Harga tertinggi Bitcoin pada hari tersebut.
- Low: Harga terendah Bitcoin pada hari tersebut.
- Close: Harga penutupan Bitcoin pada hari tersebut.
- Adj Close: Harga penutupan yang disesuaikan untuk peristiwa seperti dividen atau pemisahan saham.
- Volume: Volume perdagangan Bitcoin pada hari tersebut.

Dataset ini dapat divisualisasikan untuk mendapatkan wawasan awal tentang tren harga Bitcoin, seperti pola harian, bulanan, atau tahunan, serta analisis hubungan antar variabel seperti harga dan volume perdagangan.

## Data Preparation
Proses data preparation pada proyek ini terdiri dari beberapa tahapan:

Data Cleaning: Pada tahap ini, dilakukan pengecekan terhadap data yang tidak valid seperti nilai 0 pada kolom Open, High, Low, Close, dan Volume. Dataset juga dicek untuk keberadaan data duplikat dan nilai yang hilang (NaN).

Data Transformation: Kolom Date diubah menjadi format datetime untuk analisis waktu dan dipecah menjadi kolom Year, Month, Day, dan DayOfWeek untuk mendapatkan fitur-fitur waktu yang dapat digunakan dalam model machine learning.

Data Scaling: Fitur numerik yang akan digunakan untuk pelatihan model seperti Open, High, Low, Adj Close, dan Volume diskalakan menggunakan StandardScaler untuk menormalkan nilai fitur dan meningkatkan performa model.

Tahapan data preparation ini penting untuk memastikan kualitas data dan meningkatkan akurasi model machine learning.
