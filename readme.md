## Analisis Penggunaan Smartphone terhadap Tingkat Stres Menggunakan Machine Learning

## Latar Belakang

Penggunaan smartphone telah menjadi bagian dari kehidupan sehari-hari, terutama pada generasi muda. Aktivitas seperti penggunaan media sosial, gaming, notifikasi berlebih, dan tingginya screen time sering dikaitkan dengan kondisi stres dan kesehatan mental.

Proyek ini bertujuan untuk menganalisis hubungan antara perilaku penggunaan smartphone dan tingkat stres pengguna menggunakan pendekatan machine learning.

Dataset yang digunakan memiliki sekitar 7.500 data pengguna dengan berbagai fitur perilaku penggunaan smartphone.

## Disclimer :

- Saya masih dalam tahap belajar data analis dan machine learning
- Dataset yang digunakan berasal dari kaggle dan kemungnkinan besar adalah data sintetis (data yang dibuat)
- Saya menggunakan bantuan AI untuk membantu saya berpikir dalam menganalisis data
- Dataset bersifat simulasi sehingga hasil tidak bisa merepresentasikan kondisi dunia nyata sepenuhnya

## Tujuan Proyek

Proyek ini bertujuan untuk:

Menganalisis pola penggunaan smartphone terhadap tingkat stres
Membangun model machine learning untuk memprediksi tingkat stres pengguna
Membandingkan performa beberapa model klasifikasi
Mengevaluasi apakah fitur penggunaan smartphone memiliki hubungan yang cukup kuat terhadap tingkat stres

## Dataset

Dataset memiliki beberapa fitur utama seperti:

Kolom :
age	
gender	
daily_screen_time_hours	
social_media_hours	
gaming_hours	
work_study_hours	
sleep_hours	
notifications_per_day	
app_opens_per_day
weekend_screen_time	
academic_work_impact
addiction_level	
stress_level

## Data Preprocessing

Tahapan preprocessing dilakukan untuk memastikan data siap digunakan pada model machine learning.

1. Mengecek Missing Value

Ditemukan missing value pada kolom:

addiction_level

Jumlah missing value sekitar 819 data.

Penanganan dilakukan menggunakan:

Mode Imputation

2. Menghapus Kolom Tidak Relevan

Kolom berikut dihapus karena hanya berupa identifier dan tidak memiliki pengaruh terhadap prediksi:

transaction_id
user_id

3. Encoding Data Kategorikal

Karena model machine learning tidak dapat memproses data string secara langsung, dilakukan encoding pada beberapa fitur.

One Hot Encoding

Digunakan pada:

gender Karena bersifat nominal:

Male
Female
Other

Binary Encoding

Digunakan pada academic_work_impact

Mapping:

Yes → 1
No → 0

Ordinal Encoding

Digunakan pada addiction_level

Mapping:

Mild → 0
Moderate → 1
Severe → 2

Label Encoding

Digunakan pada target stress_level

## Exploratory Data Analysis (EDA)

Distribusi Target :

- Distribusi setiap kelas pada stress_level relatif seimbang,Hal ini mengurangi risiko bias model terhadap salah satu kelas tertentu.

- Visualisasi Hubungan Antar Fitur Dilakukan dengan menggunakan visualisasi Boxplot

Heatmap korelasi :

Fitur yang dianalisis screen time, sleep hours, social media hours dan notifications per day

## Insight dari EDA

Hasil visualisasi menunjukkan bahwa:

- Distribusi antar kelas stres sangat overlap
- Tidak terdapat pemisahan yang jelas antar kelas
- Perbedaan antar kelas cenderung tipis

Hal ini mengindikasikan bahwa:

- Tingkat stres kemungkinan dipengaruhi oleh kombinasi banyak faktor, bukan oleh satu variabel tunggal.

## Modeling

Model pertama yang digunakan adalah:

- Logistic Regression

Tujuannya sebagai baseline model

Hasil :
- Metric	Nilai
- Accuracy	~35%
- Macro F1-Score	~34%
- Analisis Logistic Regression

Model mengalami kesulitan membedakan setiap kelas stres.

Beberapa penyebab yang teridentifikasi:

- Hubungan antar fitur dan target tidak linear
- Distribusi antar kelas terlalu overlap
- Tidak terdapat feature dominan yang kuat

## Model 2 — Random Forest

Model kedua:

- Random Forest Classifier

Tujuannya untuk menguji apakah pola nonlinear dapat meningkatkan performa model

Hasil :

- Performa Random Forest ternyata hampir sama dengan Logistic Regression.

Metric	Nilai :

- Accuracy	~34%
- Macro F1-Score	~34%

## Insight Penting dari Modeling

Hasil kedua model menunjukkan performa yang relatif mirip.

Hal ini mengindikasikan bahwa:

Dataset kemungkinan tidak memiliki pola yang cukup kuat
Tingkat stres sulit diprediksi hanya berdasarkan perilaku penggunaan smartphone
Fitur yang tersedia belum cukup representatif untuk menjelaskan kondisi stres manusia secara menyeluruh

## Pelajaran Penting dari Proyek

Proyek ini memberikan pelajaran bahwa:

- Dalam machine learning, kualitas dan relevansi data sering kali lebih penting dibanding sekadar mengganti model.

Meskipun menggunakan model berbeda:

performa tetap rendah
pola antar kelas tetap sulit dipisahkan

Hal ini menjadi contoh nyata bahwa:

perilaku manusia bersifat kompleks
tidak semua permasalahan memiliki pola prediksi yang kuat

## Keterbatasan Dataset

Beberapa kemungkinan keterbatasan dataset:

- Dataset memiliki pola yang terlalu acak atau sintetis
- Faktor penyebab stres belum cukup lengkap
- Tidak terdapat fitur psikologis atau sosial lain yang relevan

🛠️ Tools & Library yang saya gunakan

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Kesimpulan

Proyek ini berhasil menunjukkan proses end-to-end machine learning mulai dari:

preprocessing
exploratory data analysis
modeling
evaluasi model
interpretasi hasil

Meskipun performa model belum tinggi, proyek ini memberikan insight penting bahwa:

- hubungan antara penggunaan smartphone dan tingkat stres tidak sederhana
- machine learning tidak selalu menghasilkan akurasi tinggi jika data tidak memiliki pola yang kuat

Proyek ini lebih berfokus pada:

- proses analisis
- interpretasi data
- evaluasi kritis terhadap dataset

dibanding sekadar mengejar nilai akurasi tinggi.
