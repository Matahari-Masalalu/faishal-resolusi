# Laporan Proyek Machine Learning - Faishal Anwar Haysim

## Rekomendasi Film dengan Machine Learning

## Domain Proyek
Proyek ini bertujuan untuk membangun sistem rekomendasi film menggunakan teknik machine learning. Sistem ini akan menggunakan dataset film yang mencakup informasi mengenai films, tags, ratings, dan links. Dengan banyaknya pilihan film yang tersedia, sistem rekomendasi diharapkan dapat membantu pengguna menemukan film yang sesuai dengan preferensi mereka, meningkatkan pengalaman menonton, dan mengurangi waktu yang dihabiskan untuk mencari film.

## Business Understanding

### Problem Statements

- Pernyataan Masalah: Bagaimana merancang sistem rekomendasi film yang dapat memberikan rekomendasi akurat berdasarkan preferensi pengguna?

### Goals
- Jawaban pernyataan masalah: Membangun sistem rekomendasi film menggunakan teknik Content-Based Filtering dan Collaborative Filtering untuk memberikan rekomendasi yang relevan kepada pengguna.
### Solution Statement
- Penggunaan Content-Based Filtering: Menggunakan informasi dari deskripsi film, genre, dan tag untuk memberikan rekomendasi film yang mirip.
- Penggunaan Collaborative Filtering: Menggunakan data rating pengguna untuk memberikan rekomendasi berdasarkan perilaku pengguna lain yang memiliki preferensi serupa.

## Data Understanding

### Sumber Data
sumber/referensi :  https://www.kaggle.com/datasets/kanametov/movies-recomendation-system

### Jumlah Data
Dataset yang digunakan dalam proyek ini terdiri dari beberapa file CSV, yaitu:
- movies.csv: 34,208 baris dan 3 kolom (movieId, title, genres).
- links.csv: 34,208 baris dan 2 kolom (movieId, imdbId).
- tags.csv: 34,208 baris dan 4 kolom (userId, movieId, tag, timestamp).
- ratings.csv: 4,144,672 baris dan 4 kolom (userId, movieId, rating, timestamp).

### Kondisi Data
- Missing Values: Setelah dilakukan analisis ada nilai yang hilang(null) pada dataset tags, links, dan rating.
- Duplikat: Setelah dilakukan analisis tidak ditemukan duplikat dalam tiap-tiap dataset.

### Data Cleaning
#### Menghilangkan Nilai Null
Setelah mengidentifikasi bahwa terdapat nilai null dalam dataset, langkah pertama yang kami ambil adalah menghapus nilai-nilai tersebut. 
#### Hasil
![Cuplikan layar 2024-11-09 101112](https://github.com/user-attachments/assets/8b3e9be7-512c-4c5c-af5a-2483620eaf1b)

## Exploratory Data Analysis
Pada tahap ini, kita melakukan eksplorasi data untuk mendapatkan wawasan awal mengenai dataset. Beberapa analisis yang dilakukan meliputi:
- Genre Film yang Paling Umum: Mengidentifikasi genre film yang paling banyak ditonton.
![Cuplikan layar 2024-11-09 101428](https://github.com/user-attachments/assets/994903d6-ab6f-4487-a447-cbbc48b33330)
- Tag yang Sering Digunakan: Menganalisis tag yang sering digunakan oleh pengguna.
![Cuplikan layar 2024-11-09 101547](https://github.com/user-attachments/assets/b97c394c-ab9f-4f0c-a148-d375b9175f4b)
- Menganalisis tag yang sering digunakan oleh pengguna.
![Cuplikan layar 2024-11-09 101631](https://github.com/user-attachments/assets/9ea03ecd-0b18-42fd-b0d2-156f71610390)

### Insight dari EDA
- Genre film yang paling umum adalah Drama dan Comedy, yang menunjukkan preferensi pengguna terhadap film-film tersebut.
- Tag yang sering digunakan memberikan wawasan tentang tema atau elemen yang disukai pengguna dalam film.
- Dari distribusi rating, terlihat bahwa mayoritas film mendapatkan rating di atas 3, menunjukkan kepuasan pengguna yang relatif tinggi.

## Content-Based Filtering

### Data Preparation
#### Ekstraksi Fitur
- Data dari file tags.csv digabungkan dengan movies.csv untuk membuat dataset yang berisi informasi lengkap tentang film. Setelah itu, kita melakukan pembersihan data, termasuk menghapus karakter khusus dan menggabungkan genre dan tag menjadi satu kolom deskripsi.
- Kolom description_words dibuat dengan menggabungkan genre dan tag untuk setiap film, yang akan digunakan dalam proses modeling.
-  Menggunakan TF-IDF Vectorizer untuk mengubah deskripsi film menjadi representasi numerik. Ini memungkinkan kita untuk menghitung kesamaan antar film berdasarkan deskripsi mereka.

### Modeling

- Pada pendekatan Content-Based Filtering, saya menghitung cosine similarity untuk menemukan kesamaan antar film berdasarkan fitur yang diekstrak dari genre atau deskripsi film. Cosine similarity mengukur seberapa mirip dua vektor dalam ruang multidimensi, dan dihitung menggunakan rumus: di mana (A) dan (B) adalah vektor dari dua film yang dibandingkan.
![cosine-similarity](https://github.com/user-attachments/assets/f80c0851-a4a3-4dda-b7fb-121a45e3b980)

- Kemudian Membuat fungsi get_recommendation yang akan memberikan rekomendasi film berdasarkan film yang telah ditonton oleh pengguna. Fungsi ini akan mengambil judul film sebagai input dan mengembalikan daftar film yang mirip.

## Item-Based Collaborative Filtering

### Data Preparation
#### 1. Penggabungan Dataset
- Dataset ratings.csv berisi informasi tentang rating yang diberikan oleh pengguna untuk film tertentu, sedangkan movies.csv berisi informasi tentang film itu sendiri, seperti judul dan genre.
- Untuk analisis yang lebih komprehensif, kedua dataset ini perlu digabungkan berdasarkan kolom movieId, yang merupakan kunci yang menghubungkan kedua dataset.

#### 2. Membuat Pivot Table
- Pivot table dibuat untuk menyusun data dalam format yang lebih mudah dianalisis. Dalam hal ini, kita ingin membuat matriks di mana barisnya adalah pengguna dan kolomnya adalah film, dengan nilai yang menunjukkan rating yang diberikan oleh pengguna untuk film tersebut.

#### Mengisi Nilai yang Hilang atau nan
- Dalam pivot table, tidak semua pengguna akan memberikan rating untuk semua film. Oleh karena itu, nilai yang hilang (NaN) akan dihasilkan. Untuk analisis lebih lanjut, kita perlu mengisi nilai-nilai ini, biasanya dengan 0, yang menunjukkan bahwa pengguna tersebut tidak memberikan rating untuk film tersebut.

### Modeling
Model Nearest Neighbors digunakan untuk menemukan film yang mirip berdasarkan rating pengguna. Rekomendasi ditampilkan dengan memvisualisasikan jarak antar film yang direkomendasikan.

## User-Based Collaborative Filtering

### Data Preparation
Matriks rating pengguna ditransposisi untuk memudahkan analisis berdasarkan pengguna.

### Modeling
Model Nearest Neighbors digunakan kembali untuk menemukan pengguna lain yang memiliki perilaku rating serupa. Rekomendasi film diberikan berdasarkan film yang telah ditonton oleh pengguna yang mirip.

## Evaluation
Sistem rekomendasi dievaluasi berdasarkan akurasi dan relevansi rekomendasi yang diberikan.
### Evaluasi Untuk Collaborative Filtering dengan melihat Tetangga Terdekat
![Cuplikan layar 2024-11-09 014726](https://github.com/user-attachments/assets/9d1982e9-55ff-49d2-9a4f-85fee5622e39)
### Rekomendasi Berdasarkan Item (Item-Based Collaborative Filtering)
![Cuplikan layar 2024-11-09 014753](https://github.com/user-attachments/assets/fc739f5d-2b55-486a-a5a7-269fbe1974a3)
### Rekomendasi Berdasarkan Item (User-Based Collaborative Filtering)
![Cuplikan layar 2024-11-09 014827](https://github.com/user-attachments/assets/b8b218d1-b4f9-47d5-a390-16ae935f4768)

## Dampak Model terhadap Pemahaman Bisnis:

Hasil evaluasi sistem rekomendasi film menunjukkan bahwa model dapat menjawab pernyataan masalah yang diajukan di awal. Dengan menggunakan teknik Content-Based Filtering dan Collaborative Filtering, sistem ini berhasil memberikan rekomendasi film yang relevan berdasarkan preferensi pengguna dan perilaku rating pengguna lain.

Sistem rekomendasi ini memiliki dampak signifikan terhadap pengalaman pengguna dalam menemukan film yang sesuai dengan minat mereka. Dengan meningkatkan relevansi rekomendasi, pengguna dapat menghabiskan lebih sedikit waktu untuk mencari film dan lebih banyak waktu untuk menikmati konten yang mereka sukai.

Selain itu, informasi yang dihasilkan dari sistem ini sangat berharga bagi platform streaming dan penyedia konten. Dengan memahami preferensi pengguna melalui analisis data, mereka dapat mengoptimalkan katalog film mereka, meningkatkan kepuasan pengguna, dan pada akhirnya meningkatkan retensi pelanggan.

Secara keseluruhan, model rekomendasi ini tidak hanya memberikan nilai tambah bagi pengguna, tetapi juga berkontribusi pada strategi bisnis yang lebih luas dengan meningkatkan engagement dan loyalitas pengguna terhadap platform.

## Kesimpulan
Proyek ini berhasil membangun sistem rekomendasi film menggunakan teknik Content-Based Filtering dan Collaborative Filtering. Hasil evaluasi menunjukkan bahwa sistem dapat memberikan rekomendasi yang relevan dan membantu pengguna dalam menemukan film yang sesuai dengan preferensi mereka.

