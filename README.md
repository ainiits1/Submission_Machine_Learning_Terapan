# Laporan Proyek Machine Learning - Nurul Itsnaini MC229D5X0883

## Domain Proyek
Pendidikan merupakan sebuah hal untuk mengangkat harkat dan martabat seseorang, menuju pemahaman pengetahuan, serta keterampilan yang ada dalam dirinya. Pendidikan dapat juga dikatakan suatu kegiatan dalam proses pemberian ilmu pengetahuan, mengarahkan, dan masukan agar dapat keluar dari bentuk kebodohan. 
Pendidikan menjadi faktor penting untuk meningkatkan kualitas sumber daya manusia, oleh karena itu semua warga Negara Indonesia harus terdidik melalui lembaga pendidikan formal dan nonformal, maupun secara informal.

Di balik pentingnya peran pendidikan tersebut, masih ditemukan berbagai permasalahan yang menghambat pencapaian prestasi belajar siswa. Banyak siswa yang masih memperoleh hasil ujian yang rendah. Kondisi ini diduga disebabkan oleh beberapa faktor, seperti kurangnya jam belajar, rendahnya tingkat kehadiran di sekolah, latar belakang pendidikan orang tua, keterbatasan akses internet, serta keterlibatan dalam kegiatan ekstrakurikuler yang berpotensi mengganggu waktu belajar. Oleh karena itu, diperlukan adanya semangat belajar yang tinggi dari siswa, baik di rumah maupun di sekolah, serta kemampuan untuk mengatur waktu secara efektif, terutama jika terlibat dalam kegiatan di luar pembelajaran atau kegiatan ekstrakurikuler.

Pada proyek ini dilakukan analisis regresi untuk menganalisis faktor-faktor yang mempengaruhi hasil ujian siswa serta memprediksi hasil ujian siswa. Adapun variabel-variabel yang digunakan dalam penelitian ini adalah Jenis kelamin, Jam belajar siswa, Kehadiran siswa, Nilai ujian sebelumnya, Tingkat pendidikan Orang tua, Akses internet dirumah, Kegiatan Ekstrakurikuler dan variabel terikatnya yaitu Nilai ujian akhir. Terdapat penelitian terdahulu yaitu [Simamora et al.,2020](https://drive.google.com/file/d/1xdcdVOny5kGI1IryKU5o-WoArsr5DC6D/view?usp=sharing) yakni membahas tentang faktor-faktor determinan yang mempengaruhi prestari belajar siswa. Adapun variabel yang digunakan dalam penelitian tersebut yaitu Motivasi belajar, Minat belajar, Keadaan ekonomi keluarga, serta Tingkat pendidikan orang tua. 

## Business Understanding
Institusi pendidikan memiliki peran penting dalam memastikan bahwa setiap siswa memperoleh hasil akademik yang optimal. Namun kenyataannya, banyak siswa yang mengalami kesulitan belajar atau kurangnya waktu belajar hingga akhirnya mendapatkan nilai yang rendah dalam ujian akhir.
### Problem Statements
Berdasarkan kondisi yang telah diuraikan, akan dikembangkan sebuah sistem prediksi nilai ujian akhir siswa untuk menjawab permasalahan berikut ini:
  1. Dari beberapa variabel yang ada, Apa variabel yang paling berpengaruh terhadap hasil ujian akhir siswa?
  2. Berapa hasil nilai akhir ujian siswa dengan variabel-variabel yang ada?
### Goals
Berdasarkan pertanyaan yang telah diuraikan, akan dibuat sebuah program _predictive modelling_ dengan tujuan sebagai berikut:
  1. Mengetahui faktor-faktor yang paling berpengaruh dengan hasil nilai ujian akhir siswa.
  2. Membuat model machine learning yang dapat memprediksi hasil ujian akhir siswa seakurat mungkin berdasarkan variabel-variabel yang ada.
### Solution Statements
Berdasarkan tujuan yang ada, pendekatan dengan dua algoritma machine learning akan digunakan untuk mencapai tujuan tersebut, yakni akan digunakan **algoritma KNN** dan **Random Forest**, serta evalusi model menggunakan **_Mean Squared Error_ (MSE)**.

## Data Understanding
Data yang digunakan pada proyek ini adalah student performance dataset yang di unduh dari tautan berikut https://www.kaggle.com/datasets/amrmaree/student-performance-prediction). Dataset ini memiliki **708 baris** hasil nilai ujian akhir siswa serta **10 kolom** variabel/fitur.
Adapun variabel-variabel pada [student performance dataset](https://www.kaggle.com/datasets/amrmaree/student-performance-prediction) adalah sebagai berikut:
  1. **ID_Siswa** : merupakan pengenal unik untuk setiap siswa
  2. **Jenis Kelamin** : merupakan jenis kelamin siswa (Laki-laki atau Perempuan)
  3. **Jam belajar per-minggu** : merupakan rata-rata jumlah jam belajar siswa  per minggu
  4. **Tingkat kehadiran** : merupakan persentase kehadiran siswa (50% - 100%)
  5. **Nilai ujian sebelumnya** : merupakan nilai rata-rata ujian siswa sebelumnya (50 - 100)
  6. **Tingkat pendidikan orang tua** : merupakan tingkat pendidikan orang tua siswa (SMA, Sarjana, Magister, dan Doktor)
  7. **Akses internet di rumah** : merupakan pernyataan apakah siswa memiliki akses internet di rumah (Ya/Tidak)
  8. **Kegiatan ekstrakurikuler** : merupakan pernyataan apakah siswa berpartisipasi dalam kegiatan ekstrakurikuler (Ya/Tidak)
  9. **Nilai ujian akhir** : merupakan hasil nilai ujian akhir siswa (50 - 77)
  10. **Lulus/Gagal** : merupakan status siswa berdasarkan nilai ujian akhir (Lulus/Gagal)

Adapun tahapan yang diperlukan untuk memahami data yaitu:
1. **Data loading**
2. **Exploratory Data Analysis** - Menampilkan Informasi umum dataset, ringkasan statistik dataset, mengecek data duplikat, missing value dan outlier 
3. **Exploratory Data Analysis** - Univariate Analysis (visualisasi fitur kategorik dan numerik)
4. **Exploratory Data Analysis** - Multivariate Analysis (mengecek pengaruh fitur kategorik dan numerik terhadap variabel dependen yakni Final_Exam_Score serta menampilkan matriks korelasinya)

Setelah proses EDA, diperoleh output:


## Data Preparation
Adapun tahapan persiapan data yang dilakukan yaitu:
  1. **Menghapus variabel yang tidak digunakan**, yaitu Student_ID dan Pass_Fail.
  2. **Encoding fitur kategori menggunakan OneHotEncoding**. Hal ini dilakukan agar data bisa diproses oleh algoritma machine learning karena sebagian besar algoritma machine learning hanya dapat menerima input berupa nilai numerik.
  3. **Membagi data Train dan data Test menggunakan fungsi train_test_split dari library sklearn**. Hal ini dilakukan untuk mengukur performa model secara objektif, yakni data training digunakan untuk melatih model dan data testing digunakan untuk mengevaluasi kinerja model pada data yang belum pernah dilihat sebelumnya.
  4. **Standarisasi menggunakan StandardScaler**. Hal ini dilakukan untuk menyamakan skala antar fitur karena tanpa standarisasi, fitur dengan nilai besar bisa mendominasi proses pembelajaran model. Selain itu juga untuk mencegah biar karena skala yang berbeda.

## Modeling
Adapun tahapan dalam membuat model yaitu:
  1. **Menyiapkan dataframe untuk analisis model**. Tahapan bertujuan untuk membuat struktur tabel yang akan digunakan untuk menyimpan dan membandingkan nilai error dari masing-masing model pada data train dan test.
  2. **Membuat model KNN** -> melatih model menggunakan ```knn.fit(X_train, y_train)```
     ```
     a. Parameter : n_neighbors = 5
     b. Kelebihan :
         - Sederhana dan mudah dipahami
         - Tidak membutuhkan pelatihan model yang kompleks
     c. Kekurangan :
         - Sensitif terhadap skala dan outlier
         - Tidak efisien untuk data besar
         - Kinerja turun pada dimensi tinggi
     ```
     **Cara Kerja KNN:**
     KNN bekerja dengan membandingkan jarak satu sampel ke sampel pelatihan      lain dengan memilih sejumlah k tetangga terdekat (dengan k adalah
     sebuah angka positif). 
     
  4. **Membuat model Random Forest** -> melatih model menggunakan ```Random_Forest.fit(X_train, y_train)```
     ```
     a. Parameter :
         - n_estimators = 100
         - max_depth = 7
         - min_samples_split = 2, min_samples_leaf = 2
         - max_features = 'sqrt'
         - random_state = 55
         - n_jobs = -1
     b. Kelebihan :
         - Kuat terhadap overfitting
         - Cocok untuk data kompleks dan besar
         - Dapat menangani data yang tidak linear dengan baik
     c. Kekurangan:
         - Interpretasi lebih sulit daripada KNN
         - Waktu training lebih lama
     ```
     **Cara kerja Random Forest:**
     Random forest bekerja dengan membangun banyak pohon keputusan               (decision trees) dan menggabungkan hasilnya untuk membuat prediksi          yang lebih akurat dan stabil. Algoritma ini bekerja dengan membangun        banyak pohon keputusan dari subset data yang diambil secara acak            (bootstrap). Saat membagi node, hanya sebagian fitur yang dipilih           secara acak untuk mengurangi korelasi antar pohon. Hasil prediksi           diperoleh melalui voting (untuk klasifikasi) atau rata-rata (untuk          regresi)

     
**Model terbaik** yang dipilih yaitu **Random Forest** karena memberikan performa yang lebih akurat secara konsisten, baik di data train maupun data test dan juga berdasarkan nilai MSE terkecil.

## Evaluation
Adapun metrik yang digunakan dalam proyek ini adalah **Mean Squared Error (MSE)**. MSE adalah rata-rata kuadrat selisih antara nilai prediksi dan nilai aktual. MSE digunakan untuk mengukur seberapa dekat prediksi model terhadap nilai sebenarnya. Nilai MSE yang lebih rendah menunjukkan bahwa model memiliki performa yang lebih baik.

**Hasil evaluasi model**
```
  1. **KNN**
     a. MSE (Train) : 0.010937
     b. MSE (Test) : 0.019178
  3. **Random Forest**
     a. MSE (Train) : 0.007687
     b. MSE (Test) : 0.015682
```
Berdasarkan hasil analisis, variabel yang paling berpengaruh terhadap hasil nilai ujian akhir siswa yaitu variabel Jam belajar perminggu (Study_Hourse_per_Week), Tingkat kehadiran (Attendace_Rate) dan Hasil nilai ujian sebelumnya (Past_Exam_Scores), akan tetapi ketiga variabel tersebut menunjukkan skor korelasi dibawah 0.5, yang artinya korelasi positif sedang.

Model juga dapat memprediksi hasil nilai ujian akhir siswa, yakni seperti contoh sebagai berikut:


Dalam proyek ini berhasil membuat serta membandingkan antara 2 algoritma model machine learning. Model Random Forest (RF) memiliki nilai MSE yang lebih rendah baik pada data training maupun testing dibandingkan KNN, yang menunjukkan bahwa RF memiliki performa yang lebih baik dalam mempelajari pola dari data dan melakukan generalisasi. Kemudian penggunaan matriks evaluasi MSE (Mean Squared Eror) juga sangat berdampak untuk mengetahui sebaik mana model yang dihasilkan. Selisih antara MSE training dan testing untuk kedua model juga relatif kecil, yang berarti tidak terjadi overfitting yang signifikan.
