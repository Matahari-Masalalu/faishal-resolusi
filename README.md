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

![Total Volume Sewa Sepeda](https://github.com/user-attachments/assets/3a115df8-8f77-4c58-964c-9c860e53c5e1)

### Pengaruh Cuaca terhadap Permintaan Sepeda

Analisis ini menunjukkan bagaimana kondisi cuaca mempengaruhi jumlah permintaan sewa sepeda.

![Pengaruh Cuaca](https://github.com/user-attachments/assets/d7b7567c-b536-4a4f-8cae-107e9ff0f6d8)

### Tren Musiman dalam Penggunaan Sepeda

Pola penggunaan sepeda berdasarkan musim memberikan pemahaman tentang kapan permintaan sewa sepeda meningkat atau menurun.

![Tren Musiman](https://github.com/user-attachments/assets/454289a1-df2b-48e5-b9cb-e9a98aaa76ed)

### Pengaruh Hari Libur

Analisis menunjukkan perbandingan permintaan sewa sepeda pada hari libur dan hari biasa.

![Pengaruh Hari Libur](https://github.com/user-attachments/assets/0179068c-ceee-4743-a1dd-70ac9c614b16)

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
