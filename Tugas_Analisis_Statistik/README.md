# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** Kadek Julita Widianti
- **NIM:** 2515091010
- **Program Studi:** Sistem Informasi
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

> Dataset yang digunakan dalam proyek ini adalah data_startup_saas.csv, yang berisi informasi mengenai berbagai perusahaan rintisan (startup) berbasis Software as a Service (SaaS). Dataset ini mencakup beberapa variabel penting, antara lain Nama_Startup sebagai identitas perusahaan, Kategori_Layanan yang menunjukkan jenis layanan yang ditawarkan, Pendapatan_Tahunan_Miliar_IDR sebagai ukuran pendapatan perusahaan dalam satu tahun,  Biaya_Akuisisi_Pelanggan_Juta_IDR yang menggambarkan biaya untuk memperoleh pelanggan baru, Nilai_Pelanggan_Juta_IDR yang merepresentasikan nilai ekonomi pelanggan bagi perusahaan (customer value), serta Tingkat_Churn_Persen yang menunjukkan persentase pelanggan yang berhenti menggunakan layanan.

> Meskipun dataset ini memiliki beberapa variabel numerik, analisis mendalam dalam penelitian ini difokuskan pada variabel Pendapatan_Tahunan_Miliar_IDR sebagai variabel kunci atau utama,  karena variabel tersebut berfungsi sebagai ukuran pendapatan perusahaan dalam satu tahun. Sementara itu, Nilai_Pelanggan_Juta_IDR dipilih sebagai variabel kunci kedua karena secara teoritis berperan penting dalam menentukan besarnya pendapatan yang dihasilkan perusahaan. Pemilihan variabel kunci dalam proyek ini ini difokuskan pada variabel numerik, karena metode analisis yang digunakan meliputi statistik deskriptif, uji normalitas, korelasi, dan regresi mensyaratkan data dalam bentuk numerik agar hasil analisis dapat dihitung dan diinterpretasikan secara valid.

> Tujuan utama dari proyek ini adalah untuk memahami karakteristik data melalui analisis statistik deskriptif, menguji distribusi data menggunakan uji normalitas, serta menganalisis hubungan antara Nilai_Pelanggan_Juta_IDR dan Pendapatan_Tahunan_Miliar_IDR menggunakan analisis korelasi guna mengetahui arah dan kekuatan hubungan kedua variabel tersebut. Selanjutnya, proyek ini bertujuan untuk membangun model regresi linear sederhana dengan Pendapatan_Tahunan_Miliar_IDR sebagai variabel dependen dan Nilai_Pelanggan_Juta_IDR sebagai variabel independen, guna mengevaluasi sejauh mana nilai pelanggan mampu menjelaskan variasi pendapatan tahunan startup SaaS.

> Melalui rangkaian analisis ini, diharapkan dapat diperoleh pemahaman yang lebih mendalam mengenai peran nilai pelanggan terhadap pendapatan tahunan startup SaaS, sekaligus memberikan dasar kuantitatif yang kuat dalam mendukung pengambilan keputusan dan perumusan strategi bisnis berbasis data.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

### 5.1. Statistik Deskriptif
> Analisis statistik deskriptif pada bagian ini difokuskan pada variabel Pendapatan_Tahunan_Miliar_IDR sebagai variabel utama penelitian.
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Ringkasan:* Ukuran pemusatan data terhadap variabel Pendapatan_Tahunan_Miliar_IDR dari 650 startup SaaS menunjukkan nilai mean sebesar 31,88 miliar IDR, median 31,3 miliar IDR, dan modus 1,87 miliar IDR.
  - *Interpretasi:*
    Berdasarkan hasil analisis, nilai mean (31,88 miliar IDR) dan median (31,3 miliar IDR) yang relatif berdekatan menunjukkan bahwa pendapatan startup tersebar cukup merata dan tidak didominasi oleh nilai yang sangat kecil atau sangat besar. Namun, nilai modus yang jauh lebih rendah, yaitu 1,87 miliar IDR, mengindikasikan bahwa pendapatan yang paling sering muncul berada pada tingkat rendah.Hal ini mengungkap bahwa mayoritas startup SaaS masih memiliki pendapatan rendah, meskipun terdapat sejumlah startup yang telah mencapai pendapatan menengah hingga tinggi. Perbedaan antara mean, median, dan modus ini mengindikasikan adanya kesenjangan kinerja dalam startup SaaS. Sejumlah kecil startup dengan pendapatan sangat tinggi berkontribusi besar dalam mendorong nilai rata-rata, sementara sebagian besar startup berada pada tingkat pendapatan yang lebih rendah. Pola ini umum terjadi dalam startup, di mana keberhasilan segelintir perusahaan besar dapat memengaruhi statistik agregat (nilai statistik yang mewakili keseluruhan startup dalam dataset) secara signifikan. Dengan demikian, rata-rata pendapatan yang tinggi tidak serta-merta mencerminkan bahwa seluruh startup telah sukses secara finansial, melainkan merupakan hasil dari distribusi pendapatan yang tidak merata. Oleh karena itu, penggunaan mean, median, dan modus secara bersama-sama membantu memahami kondisi pendapatan startup SaaS secara lebih menyeluruh sebelum dilakukan analisis lanjutan.

- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Ringkasan:* Pendapatan startup SaaS menunjukkan variasi yang signifikan dengan standar deviasi sebesar 19,79 miliar IDR dan rentang yang lebar dari 1 hingga 66,89 miliar IDR (selisih 65,89 miliar IDR). Distribusi pendapatan terlihat dari ringkasan lima angka: minimum 1,00 miliar IDR, kuartil pertama 14,31 miliar IDR, median 31,30 miliar IDR, rata-rata 31,88 miliar IDR, kuartil ketiga 49,04 miliar IDR, dan maksimum 66,89 miliar IDR.
  - *Interpretasi:*
     Nilai standar deviasi yang cukup tinggi menunjukkan bahwa pendapatan startup SaaS sangat beragam dan tidak terkumpul pada satu tingkat tertentu. Artinya, terdapat perbedaan yang jelas antara startup dengan pendapatan rendah, menengah, dan tinggi. Rentang pendapatan yang lebar semakin menegaskan adanya kesenjangan pendapatan yang signifikan dalam startup ini. Berdasarkan ringkasan lima angka, sekitar 25% startup memiliki pendapatan di bawah 14,31 miliar rupiah, yang mencerminkan kelompok startup dengan pendapatan relatif rendah. Di sisi lain, sekitar 25% startup memiliki pendapatan di atas 49,04 miliar rupiah, yang menunjukkan kelompok startup dengan pendapatan tinggi. Sementara itu, 50% startup lainnya berada di antara kedua nilai tersebut, dengan pendapatan yang terkonsentrasi di sekitar nilai median, yaitu sekitar 31 miliar rupiah per tahun. Secara keseluruhan, hasil ini menunjukkan bahwa kondisi startup SaaS ini memiliki kesenjangan pendapatan yang cukup besar. Terdapat kelompok startup dengan pendapatan rendah, kelompok menengah yang relatif stabil, dan kelompok kecil startup dengan pendapatan sangat tinggi. Oleh karena itu, meskipun rata-rata pendapatan industri terlihat cukup besar, nilai tersebut tidak sepenuhnya mencerminkan kondisi seluruh startup. Pemahaman terhadap penyebaran data ini penting agar analisis lanjutan tidak hanya bergantung pada nilai rata-rata, tetapi juga mempertimbangkan variasi dan kesenjangan yang ada.
    
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:*
    Berdasarkan boxplot dan histogram, pendapatan tahunan startup SaaS menunjukkan penyebaran yang cukup lebar. Boxplot memperlihatkan bahwa setengah dari data berada pada rentang yang luas, menandakan adanya perbedaan pendapatan yang cukup besar antar startup. Rentang nilai yang panjang ke arah pendapatan tinggi menunjukkan bahwa sebagian startup memiliki pendapatan jauh lebih besar dibandingkan mayoritas lainnya.

    Histogram mendukung temuan tersebut dengan menunjukkan bahwa pendapatan tahunan startup SaaS tersebar dari nilai yang rendah hingga tinggi, tanpa terpusat pada satu nilai tertentu. Garis putus-putus hitam pada grafik menandai nilai mean sebesar 31,88 miliar IDR, yang berada di sekitar tengah sebaran data. Hal ini sejalan dengan nilai median sebesar 31,3 miliar IDR yang hampir sama, menunjukkan bahwa distribusi pendapatan tidak terlalu dipengaruhi oleh nilai ekstrem. Meskipun demikian, nilai modus sebesar 1,87 miliar IDR berada jauh di sisi kiri distribusi, yang mengindikasikan bahwa pendapatan yang paling sering muncul dalam data berada pada tingkat yang relatif rendah. Kondisi ini terlihat pada histogram, di mana frekuensi startup dengan pendapatan rendah hingga menengah lebih banyak dibandingkan startup dengan pendapatan tinggi.Secara keseluruhan, histogram memperlihatkan bahwa pendapatan startup SaaS belum merata. Sebagian besar startup masih berada pada level pendapatan rendah hingga menengah, sementara hanya sebagian kecil startup dengan pendapatan tinggi yang mendorong nilai rata-rata menjadi lebih besar. Pola ini menegaskan adanya kesenjangan pendapatan dalam startup SaaS, meskipun distribusi data secara umum tidak menunjukkan kemiringan yang ekstrem atau sebaran data yang tidak merata.


### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.

---

## 6. Kesimpulan

Berdasarkan rangkaian analisis statistik yang telah dilakukan terhadap dataset startup SaaS, dapat disimpulkan bahwa pendapatan tahunan startup menunjukkan karakteristik distribusi yang tidak merata dengan tingkat variasi yang cukup tinggi. Analisis statistik deskriptif terhadap variabel Pendapatan_Tahunan_Miliar_IDR memperlihatkan bahwa meskipun nilai rata-rata dan median pendapatan berada pada kisaran menengah, nilai modus yang jauh lebih rendah mengindikasikan bahwa sebagian besar startup masih berada pada level pendapatan rendah. Hal ini menunjukkan adanya kesenjangan pendapatan yang cukup signifikan antar startup SaaS, di mana hanya sebagian kecil perusahaan dengan pendapatan tinggi yang mendorong nilai rata-rata keseluruhan menjadi lebih besar. Temuan ini menegaskan bahwa penggunaan ukuran pemusatan saja tidak cukup untuk menggambarkan kondisi finansial startup secara menyeluruh tanpa mempertimbangkan sebaran data.
<Details><Summary>Klik untuk melihat details</Summary>

Hasil uji normalitas menggunakan metode Shapiro-Wilk dan didukung oleh visualisasi Q-Q plot menunjukkan bahwa data pendapatan tahunan tidak terdistribusi normal dan cenderung memiliki kemiringan ke kanan (right-skewed). Ketidaknormalan distribusi ini dipengaruhi oleh keberadaan sejumlah startup dengan pendapatan yang sangat tinggi dibandingkan mayoritas data lainnya. Oleh karena itu, pemilihan metode analisis lanjutan disesuaikan dengan karakteristik data, khususnya dalam analisis korelasi yang menggunakan metode Spearman. Penggunaan korelasi Spearman dinilai lebih tepat karena metode ini tidak mensyaratkan distribusi normal dan mengukur hubungan monotonik berdasarkan peringkat data, sehingga lebih stabil terhadap data yang tidak simetris dan keberadaan nilai ekstrem.

Analisis korelasi Spearman antara Nilai_Pelanggan_Juta_IDR dan Pendapatan_Tahunan_Miliar_IDR menghasilkan koefisien korelasi sebesar 0,997, yang menunjukkan adanya hubungan positif yang sangat kuat antara kedua variabel tersebut. Scatter plot yang dihasilkan memperlihatkan pola titik yang membentuk tren menaik yang jelas dan konsisten, di mana peningkatan nilai pelanggan diikuti oleh peningkatan pendapatan tahunan. Meskipun korelasi Spearman tidak mengukur hubungan linear secara langsung, visualisasi scatter plot dengan garis tren linear digunakan sebagai alat bantu untuk memperjelas arah umum hubungan antarvariabel. Kesesuaian antara pola visual dan nilai koefisien korelasi yang sangat tinggi memperkuat kesimpulan bahwa nilai pelanggan memiliki keterkaitan yang erat dengan pendapatan tahunan startup SaaS.

Selanjutnya, analisis regresi linear sederhana dilakukan untuk mengevaluasi sejauh mana Nilai_Pelanggan_Juta_IDR mampu menjelaskan variasi Pendapatan_Tahunan_Miliar_IDR. Hasil pemodelan menunjukkan persamaan regresi dengan koefisien slope positif, yang mengindikasikan bahwa setiap peningkatan nilai pelanggan diikuti oleh peningkatan pendapatan tahunan. Nilai koefisien determinasi (R-squared) sebesar 0,994 menunjukkan bahwa sekitar 99,4% variasi pendapatan tahunan dapat dijelaskan oleh nilai pelanggan dalam model ini. Visualisasi garis regresi yang memperlihatkan titik-titik data berada sangat dekat dengan garis regresi menandakan bahwa model memiliki tingkat kesesuaian yang sangat tinggi dan kesalahan prediksi yang relatif kecil.

Secara keseluruhan, hasil analisis ini menunjukkan bahwa nilai pelanggan merupakan faktor yang sangat penting dalam menjelaskan pendapatan tahunan startup SaaS. Temuan ini memberikan dasar kuantitatif yang kuat bahwa peningkatan nilai pelanggan berpotensi berkontribusi secara signifikan terhadap pertumbuhan pendapatan perusahaan. Dengan demikian, bagi startup SaaS, strategi bisnis yang berfokus pada peningkatan nilai pelanggan dapat menjadi salah satu pendekatan utama dalam mendorong kinerja finansial secara berkelanjutan. Analisis ini juga menegaskan pentingnya penggunaan metode statistik yang sesuai dengan karakteristik data agar kesimpulan yang dihasilkan lebih akurat dan dapat dipertanggungjawabkan secara ilmiah.
</Details>


