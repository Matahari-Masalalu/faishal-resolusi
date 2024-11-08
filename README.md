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

sumber/referensi :  https://www.kaggle.com/datasets/kanametov/movies-recomendation-system

Dataset yang digunakan dalam proyek ini terdiri dari beberapa file CSV, yaitu:
- movies.csv: Berisi informasi tentang film, seperti judul, tahun rilis, dan genre.
- links.csv: Berisi informasi tentang link film, kemungkinan ke platform IMDb.
- tags.csv: Berisi tag atau label yang diberikan oleh pengguna untuk film tertentu.
- ratings.csv: Berisi data rating yang diberikan oleh pengguna untuk film.

## Exploratory Data Analysis
Pada tahap ini, kita melakukan eksplorasi data untuk mendapatkan wawasan awal mengenai dataset. Beberapa analisis yang dilakukan meliputi:
- Memeriksa distribusi rating film.
- Melihat genre film yang paling umum.
- Menganalisis tag yang sering digunakan oleh pengguna.

## Content-Based Filtering

### Data Preparation
Data dari file tags.csv digabungkan dengan movies.csv untuk membuat dataset yang berisi informasi lengkap tentang film. Setelah itu, kita melakukan pembersihan data, termasuk menghapus karakter khusus dan menggabungkan genre dan tag menjadi satu kolom deskripsi.

### Modeling
Modeling dilakukan dengan menggunakan TF-IDF Vectorizer untuk mengubah deskripsi film menjadi representasi numerik. Kemudian, cosine similarity digunakan untuk menghitung kesamaan antar film. Fungsi rekomendasi dibuat untuk memberikan rekomendasi berdasarkan film yang telah ditonton pengguna.

## Item-Based Collaborative Filtering

### Data Preparation
Dataset digabungkan antara ratings.csv dan movies.csv untuk mendapatkan informasi rating lengkap. Setelah itu, pivot table dibuat untuk mendapatkan matriks film versus pengguna.

### Modeling
Model Nearest Neighbors digunakan untuk menemukan film yang mirip berdasarkan rating pengguna. Rekomendasi ditampilkan dengan memvisualisasikan jarak antar film yang direkomendasikan.

## User-Based Collaborative Filtering

### Data Preparation
Matriks rating pengguna ditransposisi untuk memudahkan analisis berdasarkan pengguna.

### Modeling
Model Nearest Neighbors digunakan kembali untuk menemukan pengguna lain yang memiliki perilaku rating serupa. Rekomendasi film diberikan berdasarkan film yang telah ditonton oleh pengguna yang mirip.

## Evaluation
Sistem rekomendasi dievaluasi berdasarkan akurasi dan relevansi rekomendasi yang diberikan. Metrik evaluasi dapat mencakup precision, recall, dan user satisfaction.

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

