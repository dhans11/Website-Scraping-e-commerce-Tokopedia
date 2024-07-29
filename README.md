# 🚩 Project Name: Web Scraping E-Commerce Tokopedia

🙋🏻‍♂️ Project Owner: Ahmad Dani Rifai  
🏁 Date Finished: May 2024  
📞 Contact: [LinkedIn](https://www.linkedin.com/in/ahmad-dhani-0b8b6a22b/); [E-mail](adhani866@gmail.com)

#### Tujuan

Mengembangkan sistem web scraping otomatis untuk Tokopedia, dengan tujuan mengekstraksi data komprehensif tentang daftar produk, harga, ulasan, dan informasi penjual. Tujuannya termasuk memastikan keakuratan data, menerapkan penanganan kesalahan yang kuat, dan menyediakan analisis yang mendalam untuk mendukung kecerdasan bisnis dan riset pasar.

Kamu ingin menambah pendapatanmu dengan berjualan. Namun, kamu tidak punya cukup modal untuk produksi barang dan hanya cukup untuk promosi, sehingga kamu memutuskan untuk menjalanan skema dropship di platform Tokopedia.

Kamu masih bingung akan berjualan apa dan teringat bahwa saat ini sedang viral seblak. Namun, kamu tidak yakin apakah benar bahwa masyarakat memiliki animo yang besar terhadap seblak.

Karena kamu lulusan bootcamp Data Science Hacktiv8, dengan kemampuan dan pengetahuan kamu, kamu ingin menganalisis bagaimana penjualan produk seblak di Tokopedia. Apakah orang suka, apakah banyak yang beli, dsb.

Tantangannya, kamu tidak punya data sama sekali selain yang terpampang pada website e-commerce Tokopedia. Oleh karena itu, perjalanan kamu dimulai dari pengambilan data menggunakan Web Scraping!

#### A. Web Scraping

1. Lakukan pengambilan data dari halaman pencarian kata kunci produk "seblak". Kamu bisa langsung akses link ini:
   https://www.tokopedia.com/search?navsource=&page=1&q=seblak&srp_component_id=02.01.00.00&srp_page_id=&srp_page_title=&st=

   Berikut tampilan halaman link di atas:
   ![img](https://github.com/FTDS-learning-materials/phase-0/blob/main/img/p0gc3_1.png?raw=true)

2. Ambil data `Nama Produk`, `Harga Produk`, `Penjual`, `Kota Toko`, `Banyaknya Terjual`, dan `Rating Produk`.

3. Tokopedia memiliki skema promosi sehingga pada panel teratas merupakan info produk suatu merchant yang membayar iklan. Kita akan ambil produk di dalam box yang reguler dengan elemen `<div class="css-974ipl">`.

   **Tambahan:** untuk produk baru, belum ada informasi berapa produk yang terjual dan rating sehingga hasil akhir akan berbeda jumlah data yang diperoleh untuk kolom `Banyaknya Terjual` dan `Rating Produk` seperti contoh gambar di bawah:

   ![img](https://github.com/FTDS-learning-materials/phase-0/blob/main/img/p0gc3_2.png?raw=true)

   Sehingga kamu perlu mengatasi hal ini dengan cara, jika menemukan bahwa tidak ada informasi `Banyaknya Terjual` dan `Rating Produk`, kamu hanya perlu mengisi data dengan `None` (tanpa string) dan pandas akan langsung mendeteksi sebagai missing value.

4. Untuk memudahkan kamu, sudah disediakan list elemen salah satu produk:

   ```html
   <div class="prd_link-product-name css-3um8ox" data-testid="spnSRPProdName">
     SEBLAK JUARA INSTAN MASAK BASAH ASLI BANDUNG ENAK MANTAP
   </div>
   <div
     class="prd_link-product-price css-1ksb19c"
     data-testid="spnSRPProdPrice"
   >
     Rp22.000
   </div>
   <div class="css-1rn0irl">
     <span
       class="prd_link-shop-loc css-1kdc32b flip"
       data-testid="spnSRPProdTabShopLoc"
       >Bandung</span
     ><span class="prd_link-shop-name css-1kdc32b flip" data-testid=""
       >Rasa Juara Indonesia</span
     >
   </div>
   <span class="prd_label-integrity css-1duhs3e" data-testid=""
     >Terjual 750+</span
   >
   <span class="prd_rating-average-text css-t70v7i" data-testid="">4.9</span>
   ```

   **WARNING:** Kamu harus mengecek lagi kebenaran dari elemen tersebut karena Tokopedia merupakan website dinamis yang bisa saja berubah lagi attribute dan attribute value nya. Perlu diingat juga, Tokopedia senantiasa ingin melakukan improvisasi khususnya UI website sehingga bisa jadi sedang dilakukan A/B Testing dan kamu mendapatkan tampilan web yang berbeda. Tampilan web berbeda, maka elemennya juga berbeda.

   Pastikan seluruh attribute dan values digunakan dalam positioning di Beautifulsoup-nya.

5. Ambil informasi produk minimal dari 10 halaman pencarian (perhatikan format url linknya dan eksplorasi terlebih dahulu halaman web nya).

6. Perlu diingat bahwa setiap orang dan setiap waktu akan menghasilkan hasil data yang berbeda, hal ini tidak masalah, yang paling penting jumlah data yang diperoleh minimal 50 data dari minimal 10 halaman yang diakses.

7. Simpan hasil scrape ke pandas data frame dan kemudian diolah. Kamu dibebaskan memberikan nama kolom yang memudahkan kamu.

#### B. Data Preparation

1. Lakukan eksplorasi data sederhana:
   - Tampilkan beberapa baris data - tuliskan insight
   - Tampilkan informasi rangkuman data - tuliskan insight dan berikan penjelasan langkah apa yang akan kamu lakukan
   - Cek missing value - tuliskan insight dari temuan yang kamu dapatkan
2. Lakukan data cleaning:
   Kamu bisa handle missing value bila ada, mengubah bentuk data menjadi konsisten dan menyesuaikan tipe data. Perlu diingat bahwa data ini akan digunakan untuk perhitungan statisik dan membutuhkan angka.
3. Catatan:
   Pada kolom "Banyaknya Terjual", jumlah produk yang terjual dituliskan sebagai `Terjual 750+`, `Terjual 1 rb`. Ambil angkanya saja. Misal `Terjual 750+` -> `750` dan `Terjual 1 rb` -> `1000`.

#### C. Business Understanding/Problem Statement

Buat problem statement menggunakan SMART framework berikut dengan penjabaran Specific, Measurable, Achievable, Relevant, dan Time-bound. Jangan lupa merangkup dalam satu kalimat problem statement serta gunakan metrik yang tepat dari kasus ini.

#### D. Analysis

Dalam melakukan analisa data untuk mencapai tujuan yang diinginkan, kamu perlu mengikuti soal/pertanyaan/instruksi berikut ini:

1. Hitung rata-rata, median, standar deviasi, skewness, dan kurtosis dari kolom harga, banyak produk terjual, dan rating. Dari hasil perhitungan, insight apa saja yang bisa kamu dapatkan khususnya terkait dengan produk seblak dan datanya (distribusi dan kecenderungan ada/tidaknya outlier)?
   **Note:** Jika menemukan adanya indikasi outlier dari perhitungan ini, tidak perlu dihandle karena sifatnya alami. Dibiarkan saja.

2. Kamu memikirkan berapa potensi minimum dan maksimum pendapatan jika kamu menjual produk seblak?(Gunakan confidence interval untuk mendapatkan lower value dan upper value dari distribusi populasi pendapatan).

   Anggap data terdistribusi normal dan informasi produk terjual merupakan penjualan produk per bulan. Ambil confidence level 95%.

3. Apakah harga barang di Jabodetabek dan di luar Jabodetabek berbeda? mengingat biaya bahan baku di kedua lokasi berbeda. (Gunakan uji hipotesis yang diawali dengan menuliskan hipotesis null dan alternatifnya serta tentukan jenis hipotesis yang digunakan).

4. Apakah orang lebih cenderung suka dengan produk yang harganya murah?

   Kamu dapat jawab pertanyaan ini dengan uji korelasi. Gunakan library scipy jangan pandas. Analisis nilai korelasi dan p-value nya. Gunakan teknik yang sesuai dengan kondisi data!

   Kamu dilarang untuk copy-paste pertanyaan soal. Buat lah cerita yang runut dari persoalan dan jawaban nomor 1 sampai 4 sebagai ganti kalimat soal.

#### E. Conclusion

Penjualan seblak di Tokopedia masih menunjukkan banyak produk yang belum terjual, sehingga pendapatan dari penjualan ini sangat minimum. Hal ini dapat disebabkan oleh preferensi konsumen yang cenderung memilih barang dengan rating tinggi daripada harga murah. Konsumen mungkin menganggap bahwa produk dengan harga murah memiliki kualitas yang kurang memuaskan atau kurang layak dibeli.

Selain itu, penjualan seblak juga bervariasi antara wilayah Jabodetabek dan luar Jabodetabek. Perbedaan ini dapat disebabkan oleh variasi bahan baku yang digunakan dalam pembuatan produk, yang mempengaruhi selera dan preferensi konsumen di masing-masing wilayah. Oleh karena itu, strategi pemasaran dan penawaran produk perlu disesuaikan dengan karakteristik dan preferensi pasar di berbagai wilayah untuk meningkatkan penjualan dan pendapatan secara keseluruhan.

---
