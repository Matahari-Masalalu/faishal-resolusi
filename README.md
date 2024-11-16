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

## Data Preparation

Tahap **Data Preparation** adalah langkah penting dalam proses analisis data, di mana data yang telah dikumpulkan disiapkan untuk analisis lebih lanjut. Berikut adalah langkah-langkah yang dilakukan dalam tahap ini:

- Data dikumpulkan dari dua file CSV, yaitu `hour.csv` dan `day.csv`, yang berisi informasi tentang penyewaan sepeda per jam dan per hari. Data dibaca menggunakan pustaka Pandas dan dimasukkan ke dalam DataFrame.
- Data dibersihkan dengan memperbaiki tipe data untuk atribut dteday, yang awalnya bertipe object, menjadi datetime64. Ini dilakukan untuk memudahkan analisis waktu.
- Untuk memudahkan analisis dan visualisasi, beberapa kolom diubah menjadi nilai yang lebih deskriptif. Misalnya, nilai numerik untuk season, yr, holiday, dan weathersit diubah menjadi nama yang lebih mudah dipahami.

## Exploratory Data Analysis

### Total Volume Sewa Sepeda

Analisis jumlah total sewa sepeda berdasarkan faktor waktu, cuaca, dan karakteristik pengguna memberikan wawasan tentang pola dan tren dalam penggunaan sepeda.

![Cuplikan layar 2024-11-16 145947](https://github.com/user-attachments/assets/0f8c30cb-bd6e-46fe-8177-fd37614c6f5b)
![Cuplikan layar 2024-11-16 145938](https://github.com/user-attachments/assets/ef3239e8-8128-4522-bbd7-d143306f3c37)
![Cuplikan layar 2024-11-16 150012](https://github.com/user-attachments/assets/a8ccaefb-8bdc-447f-9b6e-28317a129915)
![Cuplikan layar 2024-11-16 150000](https://github.com/user-attachments/assets/6ef29c80-80a3-4d57-bfc4-554f34a2badd)

### Pengaruh Cuaca terhadap Permintaan Sepeda

![Cuplikan layar 2024-11-16 145136](https://github.com/user-attachments/assets/9724bbf5-c6fa-4837-add3-028479769dd9)

Analisis menunjukkan bahwa rata-rata permintaan sepeda mengalami peningkatan yang signifikan pada hari-hari dengan cuaca cerah. Hal ini dapat dijelaskan oleh kenyataan bahwa cuaca yang baik, seperti sinar matahari dan suhu yang nyaman, mendorong orang untuk beraktivitas di luar ruangan. Ketika cuaca cerah, banyak individu merasa lebih termotivasi untuk menggunakan sepeda sebagai sarana transportasi atau rekreasi. Selain itu, kondisi cuaca yang baik juga meningkatkan pengalaman berkendara, menjadikannya lebih menyenangkan dan nyaman. Sebaliknya, pada hari-hari dengan cuaca buruk, seperti hujan atau suhu yang sangat dingin, permintaan sewa sepeda cenderung menurun. Hal ini menunjukkan bahwa penyedia layanan bike sharing perlu mempertimbangkan faktor cuaca dalam perencanaan dan pengelolaan armada sepeda mereka, serta dalam penawaran promosi untuk menarik pengguna saat cuaca baik.

### Tren Musiman dalam Penggunaan Sepeda

![Cuplikan layar 2024-11-16 145227](https://github.com/user-attachments/assets/105c236c-6430-4e8d-a424-4369e6e44a74)

Dalam analisis musiman, ditemukan bahwa permintaan sepeda tidak menunjukkan pola yang signifikan berdasarkan musim. Meskipun ada kecenderungan untuk bersepeda lebih banyak pada musim tertentu, data menunjukkan bahwa variasi dalam permintaan sewa sepeda antara musim semi, panas, gugur, dan dingin tidak cukup mencolok untuk diidentifikasi sebagai pengaruh yang signifikan.


### Pengaruh Hari Libur

![Cuplikan layar 2024-11-16 145301](https://github.com/user-attachments/assets/004aafd6-f54e-456e-af1f-be04f547a33f)

Hasil analisis menunjukkan bahwa penggunaan sepeda cenderung lebih tinggi pada hari-hari yang bukan hari libur. Ini mungkin disebabkan oleh fakta bahwa pada hari kerja, banyak orang yang menggunakan sepeda sebagai sarana transportasi untuk pergi ke tempat kerja atau sekolah. Dalam konteks ini, sepeda menjadi pilihan yang efisien dan ramah lingkungan. Sebaliknya, pada hari libur, meskipun ada kemungkinan untuk bersepeda sebagai kegiatan rekreasi, banyak orang memilih untuk melakukan aktivitas lain, seperti berkumpul dengan keluarga atau berlibur, yang dapat mengurangi minat mereka untuk menyewa sepeda. Oleh karena itu, penyedia layanan sepeda dapat mempertimbangkan untuk menawarkan promosi khusus pada hari kerja atau mengembangkan program yang mendorong penggunaan sepeda selama hari libur, seperti acara komunitas atau perlombaan sepeda, untuk meningkatkan partisipasi.

### Perbandingan Penggunaan Sepeda oleh Pengguna Terdaftar dan Kasual

![Cuplikan layar 2024-11-16 145342](https://github.com/user-attachments/assets/e78e45ff-ba7b-4619-90bd-1a1c11946a4e)


Dalam analisis perbandingan antara pengguna terdaftar dan pengguna kasual, ditemukan bahwa pengguna terdaftar lebih aktif dan konsisten dalam menyewa sepeda. Pengguna terdaftar, yang biasanya merupakan individu yang telah mendaftar untuk menggunakan layanan secara rutin, menunjukkan pola penggunaan yang lebih teratur dan terjadwal. Mereka cenderung menggunakan sepeda untuk perjalanan harian mereka, baik untuk bekerja, berolahraga, maupun aktivitas sehari-hari lainnya. Di sisi lain, pengguna kasual sering kali menggunakan sepeda secara sporadis, mungkin hanya saat mereka berlibur atau dalam situasi tertentu. Hal ini menunjukkan bahwa penyedia layanan sepeda perlu mengembangkan strategi yang berbeda untuk menarik kedua jenis pengguna ini. Misalnya, untuk pengguna terdaftar, mereka dapat menawarkan program loyalitas atau diskon untuk penyewaan jangka panjang, sementara untuk pengguna kasual, mereka bisa menawarkan paket promosi atau pengalaman unik yang mendorong mereka untuk mencoba layanan sepeda lebih sering.

## Kesimpulan
Analisis ini memberikan wawasan yang berharga tentang berbagai faktor yang mempengaruhi permintaan sewa sepeda. Melalui eksplorasi data yang mendalam, kami telah mengidentifikasi bahwa cuaca, hari kerja, dan karakteristik pengguna berperan penting dalam menentukan pola penggunaan sepeda.

Meskipun terdapat beberapa asumsi awal tentang pengaruh signifikan dari faktor-faktor musiman, analisis menunjukkan bahwa variasi permintaan sewa sepeda tidak selalu berkorelasi langsung dengan perubahan musim. Ini menunjukkan bahwa pengguna sepeda mungkin lebih fleksibel dan adaptif terhadap kondisi cuaca, serta mengindikasikan bahwa penyedia layanan harus mempertimbangkan faktor-faktor lain yang lebih mempengaruhi keputusan pengguna untuk menyewa sepeda.

Selain itu, temuan mengenai perbedaan antara pengguna terdaftar dan pengguna kasual memberikan wawasan penting bagi penyedia layanan. Pengguna terdaftar, yang menunjukkan pola penggunaan yang lebih konsisten, dapat menjadi fokus utama untuk program loyalitas dan penawaran khusus, sementara pengguna kasual dapat dijangkau melalui promosi yang menarik dan acara komunitas yang mendorong partisipasi.

Dengan memahami pola dan tren ini, penyedia layanan sepeda dapat mengoptimalkan operasional mereka dengan lebih baik. Misalnya, mereka dapat menyesuaikan jumlah armada sepeda yang tersedia berdasarkan analisis permintaan yang telah diidentifikasi, serta merencanakan promosi atau acara yang sesuai dengan kebiasaan pengguna.

Selain itu, analisis ini juga menyoroti pentingnya meningkatkan pengalaman pengguna melalui layanan yang lebih responsif dan inovatif. Penyedia layanan dapat mempertimbangkan untuk memperkenalkan fitur-fitur baru, seperti aplikasi mobile yang lebih baik untuk pemesanan dan pelacakan, atau program pendidikan yang mengedukasi pengguna tentang manfaat bersepeda dan cara aman bersepeda di berbagai kondisi.

Secara keseluruhan, hasil dari analisis ini tidak hanya memberikan pemahaman yang lebih dalam tentang faktor-faktor yang mempengaruhi permintaan sewa sepeda, tetapi juga membuka peluang untuk inovasi dan peningkatan layanan yang dapat meningkatkan kepuasan pengguna dan mendorong lebih banyak orang untuk memilih sepeda sebagai pilihan transportasi yang berkelanjutan. Dengan pendekatan yang tepat, penyedia layanan dapat berkontribusi pada pengembangan kota yang lebih ramah lingkungan dan berkelanjutan, sekaligus meningkatkan kesehatan dan kesejahteraan masyarakat.

## Referensi
1. Lakshmipathi N  - Kagle. Diakses pada 16 November 2024 dari (https://www.kaggle.com/datasets/lakshmi25npathi/bike-sharing-dataset/data)
2. Eslam Mohamed  - Kagle. Diakses pada 16 November 2024 dari (https://www.kaggle.com/code/eslammohamed100/bike-sharing-prediction)


