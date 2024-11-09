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
- ratings.csv: 22,884,377  baris dan 4 kolom (userId, movieId, rating, timestamp).

### Penjelasan Fitur Dataset
- movieId: ID unik untuk setiap film.
- title: Judul film
- genres: Genre film, yang dapat terdiri dari beberapa genre yang dipisahkan oleh tanda '|'.
- imdbId: ID film di IMDb untuk referensi lebih lanjut.
- userId: ID unik untuk setiap pengguna yang memberikan rating.
- tag: Tag atau label yang diberikan oleh pengguna untuk film tertentu.
- rating: Rating yang diberikan oleh pengguna untuk film, biasanya dari 1 hingga 5.
- timestamp: Waktu ketika rating atau tag diberikan.

### Kondisi Data
- Missing Values: Setelah dilakukan analisis ada nilai yang hilang(null) pada dataset tags, links, dan rating.
- Duplikat: Setelah dilakukan analisis tidak ditemukan duplikat dalam tiap-tiap dataset.

### Exploratory Data Analysis
Pada tahap ini, kita melakukan eksplorasi data untuk mendapatkan wawasan awal mengenai dataset. Beberapa analisis yang dilakukan meliputi:
- Genre Film yang Paling Umum: Mengidentifikasi genre film yang paling banyak ditonton.
![Cuplikan layar 2024-11-09 101428](https://github.com/user-attachments/assets/994903d6-ab6f-4487-a447-cbbc48b33330)
Genre film yang paling umum adalah Drama dan Comedy, yang menunjukkan preferensi pengguna terhadap film-film tersebut.


- Tag yang Sering Digunakan: Menganalisis tag yang sering digunakan oleh pengguna.
![Cuplikan layar 2024-11-09 101547](https://github.com/user-attachments/assets/b97c394c-ab9f-4f0c-a148-d375b9175f4b)
Tag yang sering digunakan memberikan wawasan tentang tema atau elemen yang disukai pengguna dalam film.


- Menganalisis tag yang sering digunakan oleh pengguna.
![Cuplikan layar 2024-11-09 101631](https://github.com/user-attachments/assets/9ea03ecd-0b18-42fd-b0d2-156f71610390)

Dari distribusi rating, terlihat bahwa mayoritas film mendapatkan rating di atas 3, menunjukkan kepuasan pengguna yang relatif tinggi.

## Data Preparation
### 1. Data Preparation Pada Content-Based Filtering:
- Menghapus Nilai Null: menghapus baris dengan nilai null dari dataset untuk memastikan hanya data lengkap yang digunakan dalam analisis. Baris tanpa tag dalam dataset tags dihapus, sedangkan baris tanpa rating dalam dataset ratings juga dihilangkan. Langkah ini menjamin relevansi dan kualitas data yang digunakan.
- Penggabungan Dataset: Menggabungkan dataset ratings.csv dan tags.csv berdasarkan movieId.
- Penghapusan Kolom : Menghapus kolom timestamp dan userId pada data yang telah digabungkan sebelumnya.
- Mengelompokkan Tag untuk Setiap Film: Mengelompokkan tag untuk setiap film berdasarkan movieId, title, dan genres. Ini menyusun tag menjadi list untuk setiap film, sehingga kita dapat melihat semua tag yang terkait dengan film tersebut.
- Menghapus Karakter Khusus: Pada langkah ini, kita akan menggunakan fungsi remove_special_characters untuk menghapus karakter khusus dari kolom tag dan genres. Ini membantu memastikan bahwa data yang kita gunakan tidak mengandung karakter yang tidak diinginkan yang dapat mempengaruhi analisis atau pemodelan.
- Menambahkan Spasi Antar Genre: Dalam beberapa dataset, genre mungkin ditulis tanpa spasi antar kata (misalnya, "ActionAdventure"). Untuk meningkatkan keterbacaan dan konsistensi, kita menambahkan spasi antar genre. Kita menggunakan regex untuk menambahkan spasi sebelum huruf kapital yang tidak berada di awal string.
- ** Membuat kolom description_words yang berisi semua 'tag' dan 'genre' untuk setiap film, yang akan digunakan dalam proses modeling.
- TF-IDF Vectorization: Menggunakan TfidfVectorizer untuk mengubah kolom description_words menjadi representasi numerik. Parameter lowercase=True digunakan untuk mengubah semua teks menjadi huruf kecil.
- Ekstraksi Fitur: Menggabungkan informasi dari file tags.csv dengan movies.csv untuk membuat dataset yang berisi informasi lengkap tentang film. Menghapus karakter khusus dan menggabungkan genre dan tag menjadi satu kolom deskripsi.
### 2. Data Preparation Pada Collaborative Filtering:
- Penggabungan Dataset: Menggabungkan dataset ratings.csv dan movies.csv berdasarkan movieId.
- Pembuatan Pivot Table: Membuat pivot table yang menunjukkan rating yang diberikan oleh pengguna untuk setiap film.
- Mengisi Nilai yang Hilang: Mengisi nilai yang hilang (NaN) dengan 0, yang menunjukkan bahwa pengguna tersebut tidak memberikan rating untuk film tertentu.
- Transposisi Matriks: Untuk keperluan analisis lebih lanjut, matriks transposisi dibuat sehingga baris mewakili pengguna dan kolom mewakili film. Ini mempermudah saat melakukan rekomendasi berbasis pengguna.
- Membagi Data: Data dibagi menjadi data pelatihan (training) dan data pengujian (test) menggunakan train_test_split. Ini bertujuan untuk melatih model pada satu bagian data dan mengujinya pada bagian lain untuk mengevaluasi performa model.
- Ekstraksi Fitur Menggunakan Matriks Sparse: Untuk efisiensi memori dan kecepatan komputasi, matriks sparse digunakan. Matriks sparse menyimpan hanya nilai-nilai yang tidak nol, yang sangat berguna dalam konteks sistem rekomendasi di mana sebagian besar pengguna tidak memberikan rating untuk sebagian besar film.

## Modeling
### 1. Content-Based Filtering:
- TF-IDF Vectorization: Menggunakan TF-IDF Vectorizer untuk mengubah deskripsi film menjadi representasi numerik. Ini memungkinkan kita untuk menghitung kesamaan antar film berdasarkan deskripsi mereka.
- Cosine Similarity: Menghitung cosine similarity untuk menemukan kesamaan antar film berdasarkan fitur yang diekstrak dari genre atau deskripsi film.
- Fungsi Rekomendasi: Membuat fungsi get_recommendation yang akan memberikan rekomendasi film berdasarkan film yang telah ditonton oleh pengguna.
  
### 2. Collaborative Filtering:
Collaborative Filtering: Menggunakan model Nearest Neighbors untuk menemukan film yang mirip berdasarkan rating pengguna. Rekomendasi ditampilkan dengan memvisualisasikan jarak antar film yang direkomendasikan.

1. Menghitung Similarity Antara Item: Dalam pendekatan ini, kita menghitung kesamaan antara film berdasarkan rating yang diberikan oleh pengguna. Metrik yang umum digunakan adalah cosine similarity atau Pearson correlation, mirip dengan pendekatan pengguna. Pada kasus ini saya menggunakan Cosine Similarity.

2. Mencari Item Mirip: Setelah menghitung kesamaan antara film, model akan mencari film lain yang memiliki rating serupa. Film-film ini disebut sebagai "tetangga terdekat" untuk film tertentu.

3. Rekomendasi Film: Rekomendasi diberikan berdasarkan film yang mirip dengan film yang telah ditonton oleh pengguna. Jika pengguna telah menonton dan menyukai film tertentu, maka film-film yang mirip akan direkomendasikan.
#### Parameter:
- n_neighbors=5: Menentukan jumlah tetangga terdekat (film) yang akan dicari.
- metric='cosine': Menggunakan cosine similarity sebagai metode pengukuran kesamaan.
- algorithm='brute': Menentukan algoritma brute-force untuk menemukan tetangga terdekat, cocok untuk dataset kecil atau sedang.

Saya menggunakan Cosine pada kedua pendekatan model diatas. Cosine similarity mengukur seberapa mirip dua vektor dalam ruang multidimensi, dan dihitung menggunakan rumus: di mana (A) dan (B) adalah vektor dari dua film yang dibandingkan.
![cosine-similarity](https://github.com/user-attachments/assets/f80c0851-a4a3-4dda-b7fb-121a45e3b980)


### Hasil Prediksi

#### Rekomendasi Pada Content Based Filtering
  
![Cuplikan layar 2024-11-10 002311](https://github.com/user-attachments/assets/dece123f-03ed-49c3-981a-3f874148db52)

#### Rekomendasi Pada Item Based Filtering

![Cuplikan layar 2024-11-10 002544](https://github.com/user-attachments/assets/b75d7a2e-d2a5-4ac4-8f2c-132ededb8983)

#### Rekomendasi Pasa User Based Filtering

![Cuplikan layar 2024-11-10 004327](https://github.com/user-attachments/assets/fcc1693e-1a16-44cd-9d99-d6d19ce04e15)



## Evaluation
Evaluasi Model Rekomendasi Menggunakan Mean Absolute Error (MAE)

Mean Absolute Error (MAE) adalah salah satu metode evaluasi yang umum digunakan dalam sistem rekomendasi untuk mengukur kesalahan prediksi model. MAE memberikan informasi tentang seberapa dekat prediksi model dengan nilai aktual yang ada, dalam hal ini, rating yang diberikan oleh pengguna.

Definisi MAE
MAE dihitung sebagai rata-rata dari selisih absolut antara nilai yang diprediksi (prediksi rating) dan nilai yang sebenarnya (rating aktual). Rumus untuk menghitung MAE adalah sebagai berikut:

![images](https://github.com/user-attachments/assets/ee92ab2e-5e78-40df-a1b8-0a739ddc4837)

Di mana:

( n ) = jumlah total prediksi (data pengujian).

( yi ) = rating aktual dari item (film) yang ditonton oleh pengguna (data tes).

( ŷ ) = rating yang diprediksi oleh model.

### Hasil Evaluasi Menggunakan MAE
![Cuplikan layar 2024-11-10 004501](https://github.com/user-attachments/assets/ff6c499e-905c-4767-81b6-e11ace953638)

Secara keseluruhan, MAE sebesar 0.20173630200422316 menunjukkan bahwa model rekomendasi film Anda dapat memberikan prediksi rating yang cukup akurat, dan pengguna kemungkinan besar akan merasa puas dengan rekomendasi yang diberikan berdasarkan model tersebut. Namun, selalu penting untuk membandingkan MAE ini dengan nilai MAE dari model lain atau baseline untuk menilai seberapa baik model Anda dibandingkan dengan alternatif yang ada.

## Dampak Model terhadap Pemahaman Bisnis:

Hasil evaluasi sistem rekomendasi film menunjukkan bahwa model dapat menjawab pernyataan masalah yang diajukan di awal. Dengan menggunakan teknik Content-Based Filtering dan Collaborative Filtering, sistem ini berhasil memberikan rekomendasi film yang relevan berdasarkan preferensi pengguna dan perilaku rating pengguna lain.

Sistem rekomendasi ini memiliki dampak signifikan terhadap pengalaman pengguna dalam menemukan film yang sesuai dengan minat mereka. Dengan meningkatkan relevansi rekomendasi, pengguna dapat menghabiskan lebih sedikit waktu untuk mencari film dan lebih banyak waktu untuk menikmati konten yang mereka sukai.

Selain itu, informasi yang dihasilkan dari sistem ini sangat berharga bagi platform streaming dan penyedia konten. Dengan memahami preferensi pengguna melalui analisis data, mereka dapat mengoptimalkan katalog film mereka, meningkatkan kepuasan pengguna, dan pada akhirnya meningkatkan retensi pelanggan.

Secara keseluruhan, model rekomendasi ini tidak hanya memberikan nilai tambah bagi pengguna, tetapi juga berkontribusi pada strategi bisnis yang lebih luas dengan meningkatkan engagement dan loyalitas pengguna terhadap platform.

## Kesimpulan
Proyek ini berhasil membangun sistem rekomendasi film menggunakan teknik Content-Based Filtering dan Collaborative Filtering. Hasil evaluasi menunjukkan bahwa sistem dapat memberikan rekomendasi yang relevan dan membantu pengguna dalam menemukan film yang sesuai dengan preferensi mereka.

## Referensi
1. Dicoding. Diakses pada 10 November 2024 dari https://www.dicoding.com/academies/319-machine-learning-terapan
2. Rodrigo de Menezes Gomes - Kaggle. Diakses pada 10 November 2024 dari https://www.kaggle.com/datasets/kanametov/movies-recomendation-system
3. Rodrigo de Menezes Gomes - Kaggle. Diakses pada 10 November 2024 dari https://www.kaggle.com/code/rodmnzs/movies-recommendation-system
4. Google Colab. Diakses pada 10 November 2024 https://g.co/kgs/tPKUQUM
