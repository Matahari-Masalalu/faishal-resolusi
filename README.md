# Laporan Proyek Machine Learning - Faishal Anwar Haysim

## Prediksi Harga Bitcoin dengan Machine Learning

## Domain Proyek
Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi harga penutupan (Close) Bitcoin (BTC) menggunakan dataset harga Bitcoin dalam USD, yang mencakup informasi mengenai harga pembukaan (Open), harga tertinggi (High), harga terendah (Low), harga penutupan (Close), harga penutupan yang disesuaikan (Adj Close), dan volume perdagangan (Volume) pada periode waktu tertentu. Dengan meningkatnya permintaan untuk cryptocurrency, terutama Bitcoin, fluktuasi harga menjadi sangat tinggi dan sulit diprediksi, sehingga investor memerlukan alat bantu yang akurat untuk meminimalkan risiko kerugian. Model prediksi yang dihasilkan diharapkan dapat membantu investor membuat keputusan investasi yang lebih baik dan mengoptimalkan keuntungan, serta memberikan dukungan dalam memprediksi pergerakan harga Bitcoin secara lebih akurat.

## Business Understanding

### Problem Statements

- Pernyataan Masalah : Bagaimana merancang model machine learning yang dapat memprediksi harga penutupan (Close) Bitcoin dengan akurasi yang tinggi?

### Goals
- Jawaban pernyataan masalah : Membangun model machine learning yang dapat memprediksi harga penutupan (Close) Bitcoin dengan akurasi yang tinggi, diukur dengan metrik Root Mean Squared Error (rMSE).
### Solution Statement
- Penggunaan Multiple Algoritma Machine Learning: Karakteristik Data: Algoritma LSTM dan GRU dipilih karena kemampuannya dalam menangani data sekuensial yang kompleks, seperti deret waktu, teks, atau data lain yang memiliki struktur temporal. Kedua algoritma ini diharapkan dapat memberikan hasil yang optimal dalam pengolahan data dengan ketergantungan jangka panjang.
- Data Preparation: Proyek ini akan menggunakan teknik data preparation untuk meningkatkan kualitas data dan performa model, seperti:
Normalisasi Data Menggunakan MinMaxScaler untuk menskalakan data dalam rentang (0, 1). Ini membantu dalam mempercepat konvergensi model machine learning dan meningkatkan akurasi.

## Data Understanding

sumber/referensi : https://www.kaggle.com/datasets/gallo33henrique/bitcoin-btc-usd-stock-dataset

Dataset yang digunakan pada proyek ini adalah dataset Bitcoin (BTC-USD) Stock Data yang diunduh dari Kaggle. Dataset ini berisi informasi historis tentang harga Bitcoin dari tahun 2014 hingga 2023. Dataset ini memiliki 2836 baris dan 7 kolom, tidak ada nilai missing value dan data duplikat pada semua kolom atau baris, tetapi pada kolom volume masih terdapat outliner yang dituntukan pada gambar dibawah ini.

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

## Exploratory Data Analysis

### Total Volume Trader by Year
  
"Total Volume Trader by Year" merujuk pada analisis jumlah total volume perdagangan yang dilakukan oleh trader dalam satu tahun tertentu. Volume perdagangan adalah ukuran seberapa banyak aset, dalam hal ini Bitcoin, yang diperdagangkan dalam periode waktu tertentu. 

Analisis ini penting karena memberikan wawasan tentang aktivitas pasar dan minat investor terhadap Bitcoin dari tahun ke tahun. Dengan menghitung total volume perdagangan per tahun, kita dapat mengidentifikasi tren, pola, dan perubahan dalam perilaku trader. 

![Cuplikan layar 2024-10-20 161335](https://github.com/user-attachments/assets/3a115df8-8f77-4c58-964c-9c860e53c5e1)

### Total Volume Trader by Month for Each Year

"Total Volume Trader by Month for Each Year" merujuk pada pengukuran total volume perdagangan yang dilakukan oleh trader dalam setiap bulan selama satu tahun tertentu. Ini biasanya digunakan untuk menganalisis aktivitas perdagangan, tren pasar, dan performa trader dari waktu ke waktu.

Dengan melihat data ini, kita bisa mendapatkan wawasan tentang kapan volume perdagangan meningkat atau menurun, yang bisa dipengaruhi oleh berbagai faktor seperti berita ekonomi, peristiwa pasar, atau perubahan dalam kebijakan. Data ini sering kali disajikan dalam bentuk grafik atau tabel untuk memudahkan analisis.

![Cuplikan layar 2024-10-20 161422](https://github.com/user-attachments/assets/454289a1-df2b-48e5-b9cb-e9a98aaa76ed)

### High and Low Value Over time

High and Low Value Over Time" dalam konteks Bitcoin merujuk pada fluktuasi harga Bitcoin dari waktu ke waktu. Bitcoin, sebagai mata uang kripto, mengalami perubahan nilai yang signifikan, dipengaruhi oleh berbagai faktor seperti permintaan pasar, berita ekonomi, regulasi, dan sentimen investor.

Ketika harga Bitcoin mencapai titik tertinggi (high), ini biasanya menunjukkan minat yang tinggi dari investor dan mungkin juga adanya berita positif yang mendukung. Sebaliknya, saat harga turun ke titik terendah (low), ini bisa disebabkan oleh faktor negatif seperti berita buruk, penjualan besar-besaran, atau ketidakpastian pasar.

Memahami pola "high and low value over time" sangat penting bagi para investor dan trader untuk membuat keputusan yang lebih baik dalam berinvestasi di Bitcoin.

![Cuplikan layar 2024-10-20 161701](https://github.com/user-attachments/assets/d7b7567c-b536-4a4f-8cae-107e9ff0f6d8)

### High and Low Value for 2023

![Cuplikan layar 2024-10-20 161608](https://github.com/user-attachments/assets/0179068c-ceee-4743-a1dd-70ac9c614b16)

### High and Low Value for October 2023

![Cuplikan layar 2024-10-20 161640](https://github.com/user-attachments/assets/10219937-c3dd-43be-8fce-bb5ee0b62740)

### Correlation Matrik untuk Fitur Numerik

Dalam konteks fitur numerik, matriks ini membantu kita memahami seberapa kuat dan dalam arah mana variabel-variabel tersebut saling berhubungan.

Setiap elemen dalam matriks korelasi menunjukkan koefisien korelasi, yang biasanya berkisar antara -1 hingga 1. Nilai 1 menunjukkan hubungan positif sempurna, di mana ketika satu variabel meningkat, variabel lainnya juga meningkat. Nilai -1 menunjukkan hubungan negatif sempurna, di mana ketika satu variabel meningkat, variabel lainnya menurun. Nilai 0 menunjukkan tidak ada hubungan linear antara variabel-variabel tersebut.

Matriks korelasi sangat berguna dalam analisis data, karena dapat membantu kita mengidentifikasi fitur-fitur yang mungkin saling mempengaruhi, yang pada gilirannya dapat memandu kita dalam pemodelan dan pengambilan keputusan.

![Cuplikan layar 2024-10-20 161935](https://github.com/user-attachments/assets/e38793d6-7a24-4348-8a84-1db8400b2cba)

- Berdasarkan hasil korelasi numerik, korelasi antara fitur-fitur pada dataset tersebut berkorelasi sangat kuat. Dapat dilihat bahwa korelasi positif dan mendekati 1. Hal ini menunjukkan bahwa fitur-fitur tersebut cenderung bergerak searah.

- Contohnya, korelasi antara kolom 'Open' dan 'High' mendekati 1, yang berarti harga pembukaan dan harga tertinggi cenderung bergerak bersamaan.

- Hubungan antara volume dengan fitur lain seperti open, high, low, close dan adj close adalah positif dan lemah.

- Volume memiliki korelasi yang rendah dengan fitur lain seperti open, high, low, close dan adj close. Ini menunjukkan bahwa volume tidak secara langsung terkait dengan harga saham.

- Volume cenderung lebih terkait dengan sentimen pasar atau aktivitas perdagangan daripada dengan harga itu sendiri. Seiring dengan meningkatnya volume, harga saham mungkin cenderung naik atau turun, tetapi hubungan ini tidak selalu konsisten.

## Data visualization

![Cuplikan layar 2024-10-20 161127](https://github.com/user-attachments/assets/28cce4a0-8db3-43df-8b5f-8ce8b65c0fce)


## Data Preparation

Proses data preparation pada proyek ini terdiri dari beberapa tahapan:

### Data Cleaning

#### 1. Menghapus duplikat dan nan
untuk mengecek kemabli data duplikat dan data kosong, pada tahap ini data yang duplikat dan nan akan dihapus

#### 2. Menghapus outilner
karena pada penjelasan data understanding sebelumnya terdapat outliner pada kolom 'Volume', maka kita bisa menghapusnya dengan metode IQR.

Interquartile range (IQR) adalah rentang data antara kuartil pertama (Q1) dan kuartil ketiga (Q3). Kuartil adalah tiga nilai yang membagi distribusi data menjadi empat bagian sama besar. Q1 adalah nilai yang memisahkan 25% data terendah dari 75% data lainnya, Q2 (yang juga merupakan median) memisahkan 50% data terendah dari 50% data lainnya, dan Q3 memisahkan 75% data terendah dari 25% data lainnya. Dengan kata lain, IQR adalah rentang tengah 50% data.

### Data Splitting  
Set pelatihan (train_set) diambil dari data Bitcoin hingga tahun 2020, dengan hanya kolom harga penutupan (Close) yang digunakan. Kode:
python

Set pengujian (test_set) diambil dari data Bitcoin mulai tahun 2021, juga hanya menggunakan kolom harga penutupan.

### Creating Data Structures
Karena LSTM menyimpan status memori jangka panjang, kita membuat struktur data dengan 60 langkah waktu (time steps) dan 1 keluaran (output). Untuk setiap elemen dalam set pelatihan, kita menggunakan 60 elemen sebelumnya. Kode untuk membuat struktur data ini adalah sebagai berikut:

### Data Standarization  
Fitur numerik yang akan digunakan untuk pelatihan model seperti Open, High, Low, Adj Close, dan Volume diskalakan menggunakan MinMaxScaler, MinMaxScaler mengubah rentang fitur menjadi antara 0 dan 1, yang membantu model dalam proses pembelajaran dengan mengurangi skala variabel yang berbeda untuk menormalkan nilai fitur dan meningkatkan performa model.

### Reshaping Shape x_train
Setelah menyiapkan struktur data dengan 60 langkah waktu, kita perlu membentuk ulang x_train agar sesuai dengan input yang diharapkan oleh model LSTM.

Di sini, x_train diubah menjadi tiga dimensi dengan bentuk (jumlah sampel, jumlah langkah waktu, jumlah fitur). Ini penting karena LSTM membutuhkan input dalam format tiga dimensi.

### Preparing the Test Set
Untuk mempersiapkan set pengujian, kita perlu melakukan beberapa langkah agar set pengujian memiliki struktur yang sama dengan set pelatihan.

#### 1. Menggabungkan Data:
Kita menggabungkan data Bitcoin hingga tahun 2020 dan mulai tahun 2021 ke dalam satu dataframe untuk memudahkan proses pemrosesan.

#### 2. Membuat Input untuk Set Pengujian
Kita membuat input untuk set pengujian dengan mengambil 60 nilai sebelumnya dari data atribut 'Close' yang telah digabungkan.

Kemudian, kita reshape input menjadi bentuk yang sesuai untuk proses normalisasi.

#### 3. Normalisasi Input
Kita melakukan normalisasi pada input menggunakan MinMaxScaler yang telah digunakan sebelumnya untuk set pelatihan.

## Modeling

Pada proyek ini, dua algoritma machine learning digunakan untuk memprediksi harga penutupan Bitcoin (BTC), yaitu:

Model LSTM adalah model jaringan saraf rekursi yang digunakan untuk memprediksi nilai masa depan berdasarkan data deret waktu. Model ini bekerja dengan mempelajari pola dan tren dalam data masa lalu dan menggunakannya untuk membuat prediksi untuk masa depan. Model LSTM memiliki beberapa lapisan LSTM yang saling berhubungan. Setiap lapisan LSTM mengambil input dari lapisan sebelumnya dan menghasilkan output yang merupakan prediksi untuk langkah waktu selanjutnya.

Parameter yang digunakan dalam Model LSTM adalah sebagai berikut:

- units: Jumlah unit dalam setiap lapisan LSTM.
- return_sequences: Menentukan apakah setiap lapisan LSTM menghasilkan output untuk setiap langkah waktu atau hanya menghasilkan output untuk langkah waktu terakhir.
- input_shape: Bentuk input data.
- dropout: Persentase neuron yang diabaikan selama pelatihan untuk mencegah overfitting.
- optimizer: Algoritma optimisasi yang digunakan untuk melatih model.
- loss: Fungsi loss yang digunakan untuk menghitung kesalahan model.
- epochs: Jumlah iterasi pelatihan.
- batch_size: Jumlah sampel yang digunakan dalam setiap iterasi pelatihan.


Model GRU adalah model jaringan saraf rekursi yang mirip dengan Model LSTM, tetapi memiliki struktur yang lebih sederhana. Model GRU memiliki dua gerbang, yaitu gerbang pembaruan dan gerbang penataan, yang mengontrol aliran informasi dalam model.

Parameter yang digunakan dalam Model GRU adalah sebagai berikut:

- units: Jumlah unit dalam setiap lapisan GRU.
- return_sequences: Menentukan apakah setiap lapisan GRU menghasilkan output untuk setiap langkah waktu atau hanya menghasilkan output untuk langkah waktu terakhir.
- input_shape: Bentuk input data.
- dropout: Persentase neuron yang diabaikan selama pelatihan untuk mencegah overfitting.
- optimizer: Algoritma optimisasi yang digunakan untuk melatih model.
- loss: Fungsi loss yang digunakan untuk menghitung kesalahan model.
- epochs: Jumlah iterasi pelatihan.
- batch_size: Jumlah sampel yang digunakan dalam setiap iterasi pelatihan.

## Evaluation

Pada proyek ini, metrik yang digunakan untuk mengevaluasi performa model adalah Mean Squared Error (rMSE). MSE merupakan metrik yang umum digunakan untuk mengevaluasi model regresi.

Penjelassan mengenai metrik yang digunakan:

rMSE menghitung akar rata-rata kuadrat dari perbedaan antara nilai sebenarnya dan nilai prediksi. Rumus MSE adalah sebagai berikut:

![rmse-1](https://github.com/user-attachments/assets/196f7b57-446f-41ff-800a-6fd204729256)

Dimana:

N = jumlah dataset

yi = nilai sebenarnya

y_pred = nilai prediksi

RMSE memberikan ukuran kesalahan prediksi model. Nilai MSE yang rendah menandakan bahwa model memiliki kesalahan prediksi yang kecil dan performa yang baik. Sebaliknya, nilai MSE yang tinggi menandakan bahwa model memiliki kesalahan prediksi yang besar dan performa yang buruk.

Hasil proyek berdasarkan metrik MSE: Berikut adalah hasil MSE dari ketiga model yang telah dilatih:

![Cuplikan layar 2024-10-20 231344](https://github.com/user-attachments/assets/221ce827-812d-4c20-af26-b08095dbeade)

Grafik menunjukkan skor rMSE untuk berbagai model time series. Model dengan skor RMSE tertinggi adalah model yang paling tidak akurat, sedangkan model dengan skor rMSE terendah adalah model yang paling akurat. Berdasarkan grafik, model "linear" adalah yang paling akurat, sedangkan model "polynomial" adalah yang paling tidak akurat.

Berdasarkan hasil rMSE, dapat disimpulkan bahwa:

- Model LSTM memiliki nilai rMSE yang relatif rendah, menunjukkan bahwa model ini memiliki performa yang baik dalam memprediksi harga Bitcoin.

- Model GRU memiliki nilai rMSE yang sedikit lebih tinggi dibandingkan dengan model LSTM, menunjukkan bahwa model ini memiliki performa yang baik namun tidak sebaik model LSTM.

### Prediksi harga bitcoin menggunakan model LSTM

![Cuplikan layar 2024-10-20 232735](https://github.com/user-attachments/assets/26416bba-5b5d-4415-9c9a-ee9da6423a8c)

### Prediksi harga bitcoin menggunakan model GRU

![Cuplikan layar 2024-10-20 232746](https://github.com/user-attachments/assets/be5e81d4-96e9-480f-9e01-7e72fa8227e1)

Secara keseluruhan, model LSTM memiliki performa yang paling baik berdasarkan metrik RMSE. Hal ini karena model LSTM memiliki Kemampuan untuk menangani deret waktu, Model LSTM dirancang khusus untuk bekerja dengan data deret waktu. Mereka dapat mengingat informasi dari langkah waktu sebelumnya, yang memungkinkan mereka untuk belajar pola temporal yang rumit.

## Dampak Model terhadap Pemahaman Bisnis:

Hasil evaluasi model menggunakan Root Mean Squared Error (RMSE) menunjukkan bahwa model dapat menjawab pernyataan masalah yang diajukan di awal. Tujuan penelitian ini telah tercapai, karena LSTM, yang menunjukkan performa terbaik, memberikan akurasi prediksi yang memadai untuk harga penutupan Bitcoin. Informasi ini sangat berharga bagi investor yang ingin memprediksi pergerakan harga Bitcoin di masa depan.

## Kesimpulan

Di buku catatan ini, kami menjelajahi kumpulan data saham Bitcoin (BTC-USD), memvisualisasikan tren utama, dan membuat model prediktif untuk memperkirakan harga penutupan Bitcoin. Model Random Forest memberikan akurasi prediksi yang wajar, namun selalu ada ruang untuk perbaikan. Analisis di masa depan dapat mengeksplorasi model yang lebih canggih atau menggabungkan sumber data tambahan untuk meningkatkan akurasi prediksi. Jika menurut Anda buku catatan ini berwawasan luas, suara positif akan sangat dihargai.
