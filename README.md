# Laporan Proyek Analisis Data - Faishal Anwar Hasyim

## Analisis Data: Dataset Bike Sharing

- **Nama:** Faishal Anwar Hasyim
- **Email:** anwarfaishal86@gmail.com
- **ID Dicoding:** anwarfaishal86

---

Data yang digunakan dapat diakses pada link [Bike Sharing Dataset - Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/bike-sharing-dataset/data).

## Deskripsi Dataset
Dataset ini memiliki beberapa atribut sebagai berikut:
* **instant:** Indeks tiap entri data.
* **dteday:** Tanggal saat data diambil.
* **season:** Musim (1: Musim Semi, 2: Musim Panas, 3: Musim Gugur, 4: Musim Dingin).
* **yr:** Tahun (0: 2011, 1: 2012).
* **mnth:** Bulan (1 hingga 12).
* **hr:** Jam (0 hingga 23).
* **holiday:** Apakah data diambil pada hari libur atau tidak.
* **weekday:** Hari dalam seminggu saat data diambil.
* **workingday:** Hari kerja.
* **weathersit:** Kondisi cuaca.
  * 1: Cerah.
  * 2: Kabut + Mendung.
  * 3: Salju Ringan.
  * 4: Hujan Lebat.
* **temp:** Suhu yang dinormalisasi dalam derajat Celsius.
* **atemp:** Suhu perasaan yang dinormalisasi dalam derajat Celsius.
* **hum:** Kelembaban yang dinormalisasi.
* **windspeed:** Kecepatan angin yang dinormalisasi.
* **casual:** Jumlah pengguna kasual.
* **registered:** Jumlah pengguna terdaftar.
* **cnt:** Jumlah total sepeda yang disewakan.

## Menentukan Pertanyaan Bisnis
1. Apa dampak cuaca terhadap permintaan sepeda?
2. Bagaimana pola penggunaan sepeda berubah seiring dengan musim?
3. Apa pengaruh hari libur terhadap frekuensi penggunaan sepeda?
4. Bagaimana perbandingan antara pengguna sepeda terdaftar dan pengguna kasual dalam hal penggunaan sepeda?

## Import Semua Packages/Library yang Digunakan
- **NumPy:** Pustaka untuk operasi matematika dan manipulasi array multidimensi.
- **Pandas:** Pustaka untuk manipulasi dan analisis data.
- **Matplotlib:** Pustaka untuk membuat visualisasi data.
- **Seaborn:** Pustaka untuk visualisasi statistik yang dibangun di atas Matplotlib.

## Data Wrangling

### Gathering Data
Data diambil dari file CSV "hour.csv" dan "day.csv" menggunakan Pandas.

### Assessing Data
Informasi tentang struktur dan isi data diperoleh melalui metode `info()` dan `describe()`.

### Cek Missing Value dan Duplikat
Tidak ditemukan missing value atau duplikat dalam dataset.

### Cleaning Data
Proses cleaning dilakukan untuk memperbaiki tipe data dari atribut `dteday` menjadi `datetime64`.

## Exploratory Data Analysis (EDA)
Melakukan analisis eksplorasi untuk memahami karakteristik data dan visualisasi distribusi data.

## Visualization & Explanatory Analysis
Mengganti nilai-nilai dalam DataFrame untuk analisis yang lebih deskriptif dan memeriksa nilai unik dari kolom tertentu.

## Pertanyaan Analisis
### 1. Berapa banyak orang yang menyewa sepeda, per jam, hari, bulan, dan tahun?
### 2. Apakah cuaca buruk mengurangi jumlah peminjaman?
### 3. Apakah ada peningkatan yang konsisten pada musim tertentu?
### 4. Apakah ada peningkatan atau penurunan yang signifikan selama hari libur?
### 5. Apa perbandingan antara pengguna terdaftar dan pengguna kasual dalam penggunaan sepeda?

## Kesimpulan
### Pengaruh Cuaca terhadap Permintaan Sepeda
Rata-rata permintaan sepeda lebih tinggi pada hari-hari dengan cuaca cerah.

### Variasi Musiman dalam Penggunaan Sepeda
Permintaan sepeda paling tinggi terjadi selama musim gugur.

### Pengaruh Hari Libur terhadap Penggunaan Sepeda
Penggunaan sepeda cenderung lebih tinggi pada hari-hari bukan libur.

### Perbandingan Penggunaan Sepeda oleh Pengguna Terdaftar dan Kasual
Pengguna terdaftar lebih aktif dan konsisten dalam menyewa sepeda.

### Hubungan antara Suhu dan Penggunaan Sepeda
Terdapat hubungan positif antara suhu dan jumlah penggunaan sepeda, serta kelembapan dan kecepatan angin yang mempengaruhi permintaan sepeda dalam rentang tertentu.

## Download Dataset
Dataset yang telah dibersihkan dapat diunduh melalui [data_hour.csv](data_hour.csv).

## Requirements
Untuk menjalankan proyek ini, Anda perlu menginstal paket-paket berikut:
```bash
pip install numpy pandas matplotlib seaborn
