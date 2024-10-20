# Laporan Proyek Machine Learning - Faishal Anwar Haysim

## Prediksi Harga Bitcoin dengan Machine Learning

## Domain Proyek
Proyek ini bertujuan untuk membangun model machine learning untuk memprediksi harga penutupan (Close) Bitcoin (BTC) dengan menggunakan dataset harga Bitcoin (BTC) dalam USD. Dataset ini memuat informasi mengenai harga pembukaan (Open), harga tertinggi (High), harga terendah (Low), harga penutupan (Close), harga penutupan yang disesuaikan (Adj Close), dan volume perdagangan (Volume) pada periode waktu tertentu. Model prediksi yang dihasilkan diharapkan dapat membantu investor untuk membuat keputusan investasi yang lebih baik dan mengoptimalkan keuntungan.

Permintaan yang semakin tinggi untuk cryptocurrency, khususnya Bitcoin, menyebabkan fluktuasi harga yang sangat tinggi dan sulit diprediksi. Untuk meminimalkan risiko kerugian, para investor membutuhkan alat bantu yang akurat untuk memprediksi pergerakan harga Bitcoin. Model machine learning yang akurat dapat membantu investor untuk memprediksi pergerakan harga Bitcoin dan meminimalkan risiko kerugian.

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

sumber/referensi : https://www.kaggle.com/datasets/gallo33henrique/bitcoin-btc-usd-stock-dataset
sumber/referensi : https://www.kaggle.com/code/njugushedit/btc-usd-market-analysis

Dataset yang digunakan pada proyek ini adalah dataset Bitcoin (BTC-USD) Stock Data yang diunduh dari Kaggle atau Google Drive. Dataset ini berisi informasi historis tentang harga Bitcoin dari tahun 2014 hingga 2023. Dataset ini memiliki 2.991 baris dan 7 kolom, tidak ada nilai missing value dan data duplikat pada semua kolom atau baris, tetapi pada kolom volume masih terdapat outliner yang dituntukan pada gambar dibawah ini.

![image](https://github.com/user-attachments/assets/2f31a20d-b31f-4d80-83b4-9e0fdce20103)


Variabel-variabel pada Bitcoin dataset adalah sebagai berikut:
- Date: Tanggal data yang direkam (dalam format YYYY-MM-DD).
- Open: Harga pembukaan Bitcoin pada hari tersebut.
- High: Harga tertinggi Bitcoin pada hari tersebut.
- Low: Harga terendah Bitcoin pada hari tersebut.
- Close: Harga penutupan Bitcoin pada hari tersebut.
- Adj Close: Harga penutupan yang disesuaikan untuk peristiwa seperti dividen atau pemisahan saham.
- Volume: Volume perdagangan Bitcoin pada hari tersebut.

Dataset ini dapat divisualisasikan untuk mendapatkan wawasan awal tentang tren harga Bitcoin, seperti pola harian, bulanan, atau tahunan, serta analisis hubungan antar variabel seperti harga dan volume perdagangan.

## Data visualization

![Cuplikan layar 2024-10-20 161127](https://github.com/user-attachments/assets/28cce4a0-8db3-43df-8b5f-8ce8b65c0fce)

## Exploratory Data Analysis

Total Volume Trader by Year

![Cuplikan layar 2024-10-20 161335](https://github.com/user-attachments/assets/3a115df8-8f77-4c58-964c-9c860e53c5e1)

Total Volume Trader by Month for Each Year

![Cuplikan layar 2024-10-20 161422](https://github.com/user-attachments/assets/454289a1-df2b-48e5-b9cb-e9a98aaa76ed)

High and Low Value Over time

![Cuplikan layar 2024-10-20 161701](https://github.com/user-attachments/assets/d7b7567c-b536-4a4f-8cae-107e9ff0f6d8)

High and Low Value for 2023

![Cuplikan layar 2024-10-20 161608](https://github.com/user-attachments/assets/0179068c-ceee-4743-a1dd-70ac9c614b16)

High and Low Value for October 2023

![Cuplikan layar 2024-10-20 161640](https://github.com/user-attachments/assets/10219937-c3dd-43be-8fce-bb5ee0b62740)

Correlation Matrik untuk Fitur Numerik

![Cuplikan layar 2024-10-20 161935](https://github.com/user-attachments/assets/e38793d6-7a24-4348-8a84-1db8400b2cba)

- Berdasarkan hasil korelasi numerik, korelasi antara fitur-fitur pada dataset tersebut berkorelasi sangat kuat. Dapat dilihat bahwa korelasi positif dan mendekati 1. Hal ini menunjukkan bahwa fitur-fitur tersebut cenderung bergerak searah.

- Contohnya, korelasi antara kolom 'Open' dan 'High' mendekati 1, yang berarti harga pembukaan dan harga tertinggi cenderung bergerak bersamaan.

- Hubungan antara volume dengan fitur lain seperti open, high, low, close dan adj close adalah positif dan lemah.

- Volume memiliki korelasi yang rendah dengan fitur lain seperti open, high, low, close dan adj close. Ini menunjukkan bahwa volume tidak secara langsung terkait dengan harga saham.

- Volume cenderung lebih terkait dengan sentimen pasar atau aktivitas perdagangan daripada dengan harga itu sendiri. Seiring dengan meningkatnya volume, harga saham mungkin cenderung naik atau turun, tetapi hubungan ini tidak selalu konsisten.


## Data Preparation

Proses data preparation pada proyek ini terdiri dari beberapa tahapan:

- Data Cleaning: Pada tahap ini, dilakukan pengecekan terhadap data yang tidak valid seperti nilai 0 pada kolom Open, High, Low, Close, dan Volume. Dataset juga dicek untuk keberadaan data duplikat dan nilai yang hilang (NaN).

- Data Transformation: Kolom Date diubah menjadi format datetime untuk analisis waktu dan dipecah menjadi kolom Year, Month, Day, dan DayOfWeek untuk mendapatkan fitur-fitur waktu yang dapat digunakan dalam model machine learning.

- Data Scaling: Fitur numerik yang akan digunakan untuk pelatihan model seperti Open, High, Low, Adj Close, dan Volume diskalakan menggunakan StandardScaler untuk menormalkan nilai fitur dan meningkatkan performa model.

Tahapan data preparation ini penting untuk memastikan kualitas data dan meningkatkan akurasi model machine learning.

## Modeling

Pada proyek ini, tiga algoritma machine learning digunakan untuk memprediksi harga penutupan Bitcoin (BTC), yaitu:

- K-Nearest Neighbors (KNN): Model KNN bekerja dengan mencari k data terdekat dari data yang ingin diprediksi. Prediksi kemudian didasarkan pada rata-rata dari k data terdekat tersebut. Model ini mudah dipahami dan diterapkan, tetapi dapat menjadi tidak efisien untuk dataset yang besar.

- Random Forest: Model Random Forest merupakan ensemble learning yang terdiri dari banyak pohon keputusan. Setiap pohon dilatih dengan subset data dan variabel acak. Prediksi akhir dilakukan dengan menggabungkan prediksi dari setiap pohon. Model ini memiliki akurasi yang tinggi dan mampu menangani data yang kompleks, tetapi membutuhkan waktu yang lebih lama untuk dilatih.

- AdaBoost (Adaptive Boosting): Model AdaBoost merupakan algoritma boosting yang menggabungkan banyak model yang lemah untuk membentuk model yang kuat. Model yang lemah diberi bobot lebih tinggi jika prediksinya benar. Model ini memiliki akurasi yang tinggi dan mampu menangani data yang kompleks, tetapi dapat mengalami overfitting jika tidak diatur dengan baik.

Pada proses pelatihan model, parameter yang digunakan adalah sebagai berikut:

- KNN: n_neighbors=10. Parameter ini menentukan jumlah tetangga terdekat yang digunakan untuk memprediksi nilai target.

- Random Forest: n_estimators=50, max_depth=16, random_state=55, n_jobs=-1. Parameter n_estimators menentukan jumlah pohon dalam Random Forest, max_depth menentukan kedalaman maksimal pohon, random_state digunakan untuk inisialisasi random number generator, dan n_jobs menentukan jumlah core CPU yang digunakan untuk pelatihan.

- AdaBoost: learning_rate=0.05, random_state=55. Parameter learning_rate menentukan besarnya pengaruh setiap model yang lemah pada model akhir, dan random_state digunakan untuk inisialisasi random number generator.

## Evaluation

Pada proyek ini, metrik yang digunakan untuk mengevaluasi performa model adalah Mean Squared Error (MSE). MSE merupakan metrik yang umum digunakan untuk mengevaluasi model regresi.

Penjelassan mengenai metrik yang digunakan:

MSE menghitung rata-rata kuadrat dari perbedaan antara nilai sebenarnya dan nilai prediksi. Rumus MSE adalah sebagai berikut:

![Cuplikan layar 2024-10-20 155611](https://github.com/user-attachments/assets/636a0d1b-a371-45f1-af31-b05a962d3e74)

Dimana:

N = jumlah dataset

yi = nilai sebenarnya

y_pred = nilai prediksi

MSE memberikan ukuran kesalahan prediksi model. Nilai MSE yang rendah menandakan bahwa model memiliki kesalahan prediksi yang kecil dan performa yang baik. Sebaliknya, nilai MSE yang tinggi menandakan bahwa model memiliki kesalahan prediksi yang besar dan performa yang buruk.

Hasil proyek berdasarkan metrik MSE: Berikut adalah hasil MSE dari ketiga model yang telah dilatih:

![Cuplikan layar 2024-10-20 163337](https://github.com/user-attachments/assets/1770f22f-fedb-4c04-aaa2-56c69ae01979)

![Cuplikan layar 2024-10-20 155841](https://github.com/user-attachments/assets/2882be6b-3c61-4136-9818-468fec90f31a)

Grafik menunjukkan skor MSE untuk berbagai model regresi. Model dengan skor MSE tertinggi adalah model yang paling tidak akurat, sedangkan model dengan skor MSE terendah adalah model yang paling akurat. Berdasarkan grafik, model "linear" adalah yang paling akurat, sedangkan model "polynomial" adalah yang paling tidak akurat.

Grafik juga menunjukkan bahwa sebagian besar model memiliki performa yang lebih baik pada data training daripada data testing. Ini menunjukkan bahwa beberapa model mungkin mengalami overfitting.

Berdasarkan hasil MSE, dapat disimpulkan bahwa:

- Model KNN memiliki performa yang baik pada data pelatihan, namun performanya menurun pada data pengujian.

- Model Random Forest memiliki performa yang baik pada data pelatihan dan pengujian, dengan nilai MSE yang relatif rendah pada data pengujian.

- Model Boosting memiliki performa yang baik pada data pelatihan, namun performanya menurun pada data pengujian.

Secara keseluruhan, model Random Forest memiliki performa yang paling baik berdasarkan metrik MSE. Hal ini karena model Random Forest mampu menangkap pola yang kompleks dalam data dan menghasilkan prediksi yang lebih akurat dibandingkan dengan model KNN dan Boosting.

## Kesimpulan

Di buku catatan ini, kami menjelajahi kumpulan data saham Bitcoin (BTC-USD), memvisualisasikan tren utama, dan membuat model prediktif untuk memperkirakan harga penutupan Bitcoin. Model Random Forest memberikan akurasi prediksi yang wajar, namun selalu ada ruang untuk perbaikan. Analisis di masa depan dapat mengeksplorasi model yang lebih canggih atau menggabungkan sumber data tambahan untuk meningkatkan akurasi prediksi. Jika menurut Anda buku catatan ini berwawasan luas, suara positif akan sangat dihargai.
