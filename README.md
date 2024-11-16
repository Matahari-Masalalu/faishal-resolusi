# Laporan Proyek Analisis Data - Faishal Anwar Hasyim

## Analisis Data: Dataset Bike Sharing

## Domain Proyek
Proyek ini bertujuan untuk menganalisis data sewa sepeda menggunakan dataset bike sharing yang mencakup informasi mengenai waktu sewa, kondisi cuaca, dan karakteristik pengguna. Dengan meningkatnya popularitas penggunaan sepeda sebagai sarana transportasi, pemahaman tentang faktor-faktor yang mempengaruhi permintaan sepeda menjadi sangat penting. Analisis ini diharapkan dapat memberikan wawasan bagi penyedia layanan bike sharing untuk meningkatkan layanan dan memenuhi kebutuhan pengguna.

## Business Understanding

### Problem Statements

- Pernyataan Masalah: Bagaimana faktor-faktor seperti cuaca, musim, dan hari libur mempengaruhi permintaan sewa sepeda?

### Goals
- Jawaban pernyataan masalah: Menganalisis data untuk mengidentifikasi pola dan tren dalam permintaan sewa sepeda berdasarkan berbagai faktor.

### Solution Statement
- Penggunaan Analisis Data: Menggunakan teknik analisis data eksploratif untuk memahami hubungan antara variabel yang mempengaruhi permintaan sewa sepeda.
- Data Preparation: Proyek ini akan menggunakan teknik data preparation untuk meningkatkan kualitas data dan performa analisis, termasuk pembersihan data dan normalisasi.

## Data Understanding

Sumber/referensi: [Bike Sharing Dataset - Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/bike-sharing-dataset/data)

Dataset yang digunakan pada proyek ini adalah dataset bike sharing yang berisi informasi historis tentang sewa sepeda. Dataset ini memiliki beberapa atribut yang mencakup waktu sewa, kondisi cuaca, dan karakteristik pengguna.

Variabel-variabel pada dataset adalah sebagai berikut:
- **instant**: Indeks tiap entri data.
- **dteday**: Tanggal saat data diambil.
- **season**: Musim (1: Musim Semi, 2: Musim Panas, 3: Musim Gugur, 4: Musim Dingin).
- **yr**: Tahun (0: 2011, 1: 2012).
- **mnth**: Bulan (1 hingga 12).
- **hr**: Jam (0 hingga 23).
- **holiday**: Apakah data diambil ketika hari libur atau tidak.
- **weekday**: Hari dalam seminggu saat data diambil.
- **workingday**: Hari kerja.
- **weathersit**: Kondisi cuaca.
  - 1: Cerah
  - 2: Kabut + Mendung
  - 3: Salju Ringan
  - 4: Hujan Lebat
- **temp**: Suhu yang dinormalisasi dalam derajat Celsius.
- **atemp**: Suhu perasaan yang dinormalisasi dalam derajat Celsius.
- **hum**: Kelembaban yang dinormalisasi.
- **windspeed**: Kecepatan angin yang dinormalisasi.
- **casual**: Jumlah pengguna kasual.
- **registered**: Jumlah pengguna terdaftar.
- **cnt**: Jumlah total sepeda yang disewakan.

## Exploratory Data Analysis

### Total Volume Sewa Sepeda

Analisis jumlah total sewa sepeda berdasarkan faktor waktu, cuaca, dan karakteristik pengguna memberikan wawasan tentang pola dan tren dalam penggunaan sepeda.

![Cuplikan layar 2024-11-16 145947](https://github.com/user-attachments/assets/0f8c30cb-bd6e-46fe-8177-fd37614c6f5b)
![Cuplikan layar 2024-11-16 145938](https://github.com/user-attachments/assets/ef3239e8-8128-4522-bbd7-d143306f3c37)
![Cuplikan layar 2024-11-16 150012](https://github.com/user-attachments/assets/a8ccaefb-8bdc-447f-9b6e-28317a129915)
![Cuplikan layar 2024-11-16 150000](https://github.com/user-attachments/assets/6ef29c80-80a3-4d57-bfc4-554f34a2badd)

### Pengaruh Cuaca terhadap Permintaan Sepeda

Analisis ini menunjukkan bagaimana kondisi cuaca mempengaruhi jumlah permintaan sewa sepeda.

![Cuplikan layar 2024-11-16 145136](https://github.com/user-attachments/assets/9724bbf5-c6fa-4837-add3-028479769dd9)

### Tren Musiman dalam Penggunaan Sepeda

Pola penggunaan sepeda berdasarkan musim memberikan pemahaman tentang kapan permintaan sewa sepeda meningkat atau menurun.

![Cuplikan layar 2024-11-16 145227](https://github.com/user-attachments/assets/105c236c-6430-4e8d-a424-4369e6e44a74)


### Pengaruh Hari Libur

Analisis menunjukkan perbandingan permintaan sewa sepeda pada hari libur dan hari biasa.

![Cuplikan layar 2024-11-16 145301](https://github.com/user-attachments/assets/004aafd6-f54e-456e-af1f-be04f547a33f)

## Data Preparation

Proses data preparation pada proyek ini terdiri dari beberapa tahapan:

### Data Cleaning

1. ** Menghapus duplikat dan nilai yang hilang**: Memastikan tidak ada data yang duplikat atau hilang dalam dataset.
2. **Mengubah tipe data**: Mengonversi kolom `dteday` menjadi format datetime untuk analisis yang lebih baik.

### Data Splitting  
Dataset dibagi menjadi dua bagian: data untuk analisis dan data untuk visualisasi.

## Modeling

Analisis dilakukan untuk menjawab pertanyaan bisnis yang telah ditentukan, menggunakan visualisasi untuk menggambarkan hasil.

## Evaluation

Hasil analisis menunjukkan bahwa faktor cuaca, musim, dan hari libur memiliki pengaruh signifikan terhadap permintaan sewa sepeda. Data yang diperoleh dapat digunakan untuk meningkatkan layanan bike sharing.

## Kesimpulan
Analisis ini memberikan wawasan yang berharga tentang faktor-faktor yang mempengaruhi permintaan sewa sepeda. Dengan memahami pola dan tren ini, penyedia layanan dapat mengoptimalkan operasional dan meningkatkan pengalaman pengguna.

## Download Dataset
Dataset yang telah dibersihkan dapat diunduh melalui [data_hour.csv](data_hour.csv).

## Requirements
Untuk menjalankan proyek ini, Anda perlu menginstal paket-paket berikut:
```bash
pip install numpy pandas matplotlib seaborn
