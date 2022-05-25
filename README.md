# Laporan Proyek Machine Learning: System Recomendation Movie - Riezki Maisyar
---
### Domain Project

> **Domain proyek yang dipilih dalam proyek machine learning ini adalah mengenai industri perfilman dengan judul proyek "Movie System Recomendation"**.

* Latar belakang
Pertumbuhan pasar industri dari bidang perfilman di luar negeri hingga dalam negeri kian menjanjikan. Dilihat dari banyaknya jumlah penonton bioskop yang terus meningkat dari tahun ke tahun. Per 2018 angka jumlah penonton bioskop di Indonesia saja telah mencapai lebih dari 50 juta penonton dengan jumlah produksi film luar negeri hingga dalam negeri sebanyak hampir 200 judul film yang telah tayang di seluruh Indonesia [[1](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/)] (Tren Positif Film Indonesia | Indonesia.go.id, 2019).
![img](https://cdn.dribbble.com/users/6337227/screenshots/17230478/media/e4379e3065e4ba2bea8c4767a2dbf599.png)
Dari sekian banyaknya film yang diproduksi membuat calon penonton kesulitan dalam menentukan film yang akan ditontonnya. Untuk mencari film tentunya akan memakan waktu, selain itu film yang sudah ditentukan untuk ditonton belum tentu sesuai dengan keinginan calon penonton setelah menontonnya, sehingga akan menghabiskan waktu lebih banyak lagi. Menonton film melalui bioskop, platform penyedia layanan streaming, maupun penyewaan dan pembelian kaset DVD juga diperlukan biaya, akan terbuang sia-sia apabila film yang ditonton tidak sesuai keinginan. [[2](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/)]
Mereka yang kesulitan untuk memilih menonton film apa memutuskan untuk mengunjungi beberapa situs seperti suggestmemovie.com yang memberikan saran film kepada pengguna atau situs StayIn app yang memberikan kuesioner secara umum untuk mencari tahu suasana hati pengunjung situs dengan beberapa pertanyaan. Dari semua solusi berikut pengunjung situs mengaku terkadang harus mencoba beberapa kali untuk mendapat film yang dianggap bagus (Mihir, 2019) [[3](https://www.makeuseof.com/tag/fastest%20-ways-good-movie-film-watching/)]. Pada salah satu platform penyedia layanan streaming digital terbesar saat ini, Netflix sering kali membuat kebingungan penggunanya karena banyaknya pilihan film atau serial yang bisa ditonton. Hal ini mendorong Netflix untuk mengeluarkan fitur untuk menjadi solusi permasalahan berikut yang disebut dengan shuffle play yang akan memutar film atau serial yang dipilihkan oleh sistem [[4](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/)].
Dalam mencari kemiripan dapat menggunakan metode cosine similarity yang digunakan dalam penelitian sistem temu kembali buku berbahasa Arab yang ditulis oleh (Fauzi, Arifin and Yuniarti, 2017) [[5](https://pdfs.semanticscholar.org/4cba/7c655cf843fe703211f385259ac082cb2b00.pdf)]. Dengan memadukan frekuensi kata, inverse frekuensi dokumen, inverse frekuensi kelas, dan inverse frekuensi buku yang menjadi nilai hitung pembobotan term. Hasil pembobotan akan dicari kemiripannya pada setiap dokumen menggunakan metode cosine similarity. Proyek yang dirancang kali ini merupakan proyek membuat sistem rekomendasi judul film berdasarkan genre menggunakan data dari metadata movies yang didownload dari kaggle. Oleh sebab itu, dibuatlah sistem rekomendasi yang dapat menyelasaikan permasalahan pelanggan, dan dapat dengan mudah mendapatkan rekomendasi film berdasarkan genre dari judul film yang dicari atau yang telah diinput sebelumnya. Metode untuk sistem rekomendasi judul film berdasarkan genre ini menggunakan teknik content-based filtering.
___
# Business Understanding
---
#### Problem Statements
berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:

- Bagaimana cara melakukan pra-pemrosesan pada data movie recomendation yang akan digunakan agar dapat membuat model yang baik menggunakan teknik content-base filtering?
- Bagaimana memberikan rekomendasi judul film berdasarkan genre pada setiap judul film yang pelanggan input sehingga dapat memberikan preferensi yang sesuai pelanggan inginkan?
 
#### Goals
- Melakukan pra-pemrosesan dengan baik agar dapat digunakan dalam pembuatan model.
- Membuat pelanggan lebih mudah menemukan judul film yang tepat dengan bantuan sistem rekomendasi judul film berdasarkan genre yang dibuat.

#### Solution Statements
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya :
* Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, diantaranya :
    * Mengecek masalah data yang kosong dengan melakukan pengecekan terlebih dahulu.
    * Menghitung besar/panjang data pada dataset terlebih dahulu kemudian mencoba untuk menguraikan jenis-jenis fitur pada kolom genre
    * mengurutkan data movieId dan menghapus data yg sama
    * Membuang judul film yg duplikat dengan method ``` drop_duplicats()``` 
* Metode yang digunakan pada projek ini adalah Content Based Filtering. Content Based Filtering adalah rekomendasi berbasis konten yang merekomendasikan item yang memiliki kemiripan dengan item yang disukai/diinput pengguna sebelumnya. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna [[6](http://103.23.20.161/index.php/semnasif/article/view/1148)]. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna. Kelebihan dan Kekurangan dari Content-based Filtering adalah sebagai berikut:
    * Kelebihan
        * User Independence
        Tidak bergantung kepada user lain dalam memberikan rekomendasi yang ada. New Item Mampu merekomendasikan item yang belum dinilai oleh setiap pengguna.
    * Kekurangan
        * New User
        Sistem tidak dapat memberikan rekomendasi yang dapat diandalkan pada pengguna baru, karena membutuhkan penelusuran terlebih dahulu pada preferensi pengguna.

# Data Understanding
---
![kaggle](https://i.postimg.cc/Y92XtJf4/image.png)
Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut menyajikan data-data daftar film dari yg terlama hingga ke yg terbaru serta memberikan korelasi dengan data rating yg disediakan pada dataset (tidak terlalu banyak digunakan pada studi kasus projek ini).
Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset : Movie recomendation pjct](https://www.kaggle.com/datasets/sayan0211/movie-recomendation-pjct)
Lisensi | Unknown
Kategori | Movies, TV Shows, Recomendations movie Dataset
Jenis dan Ukuran Berkas | Zip (866 kB)

Pada berkas yang diunduh yakni movies.csv berisi 9743 rows × 3 columns dan ratings.csv berisi 100k++ baris dan 4 columns. Kolom-kolom tersebut terdiri dari 2 buah kolom bertipe objek dan 1 buah kolom bertipe numerik (tipe data int64) pada file movies.csv dan pada files ratings.csv terdiri dari 4 buah kolom bertipe numerik (int64 dan float64). Untuk penjelasan mengenai variabel-variable pada dataset movies recomendation ini dapat dilihat sebagai berikut:
- **movieId** merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap film.
- **userId** merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap pengguna.
- **rating** merupakan parameter berisi nilai rating film yg diberikan pengguna
- **genre** merupakan parameter yg menyimpan tiap-tiap kategori film
- **title** merupakan parameter yg menyimpan judul masing-masing film

Berikut beberapa tahapan Data Understanding diantaranya sebagai berikut:
- Meload Dataset ke dalam sebuah Dataframe menggunakan pandas
- ``` df.info()``` digunakan untuk mengecek tipe kolom pada dataset
- ```df.isna().sum()``` digunakan untuk mengecek apakah ada kolom yg kosong, pada dataset ini nilai kosong tidak ditemukan
- ```df.describe()``` digunakan utk mendapatkan info mengenai dataset terhadap nilai rata-rata, median, banyaknya data, nilai Q1 hingga Q3 dan lain-lain.
- ``` len(nama_variable.unique()) ```menghitung panjang data unique dari variable tertentu
- Mengurutkan dataset dan menghapus data movieId yg sama
![img](https://i.ibb.co/HqPgGQk/image.png)
- Menampilkan rata-rata genre yg paling banyak muncul pada dataset
![img](https://i.ibb.co/k91yqBN/image.png)

# Data Preparation
---
Berikut adalah tahapan-tahapan dalam melakukan Persiapan data:
1. Menghitung jumlah data pada genre
![img](https://i.ibb.co/304YRwv/image.png)
2. Men-drop judul yg duplikat (membersihkan data)
![img](https://i.ibb.co/ScBTNMm/image.png)
3. Mereset ulang penomoran index data (tranformasi data)
![img](https://i.ibb.co/BjFJbsR/image.png)

Teknik yang digunakan pada tahapan Proses Data adalah vektorisasi fungsi CountVectorizer dari library scikit-learn. CountVectorizer digunakan untuk mengubah teks yang diberikan menjadi vektor berdasarkan frekuensi (jumlah) setiap kata yang muncul di seluruh teks. 
CountVectorizer membuat matriks di mana setiap kata unik diwakili oleh kolom matriks, dan setiap sampel teks dari dokumen adalah baris dalam matriks. Nilai setiap sel tidak lain adalah jumlah kata dalam sampel teks tertentu.

Pada proses vektorisasi ini, digunakan metode sebagai berikut. 
1. ```fit``` metode berfungsi untuk melakukan perhitungan idf pada data
![img](https://i.ibb.co/DwGCM0q/image.png)
2. ```get_feature_names_out()``` berfungsi untuk melakukan mapping array dari fitur index integer ke fitur nama
3. ```fit_transform()``` berfungsi untuk mempelajari kosa kata dan Inverse Document Frequency (IDF) dengan memberikan nilai return berupa *document-term matrix*
![img](https://i.ibb.co/0G4dCDN/image.png)
4. ```todense()``` berfungsi untuk mengubah vektor tf-idf dalam bentuk matriks
![omg](https://i.ibb.co/JzbgH87/image.png)

# Modeling
---
Setelah dilakukan pra-pemrosesan pada dataset, langkah selanjutnya adalah *modeling* terhadap data. Pada tahap ini Model machine learning yang digunakan pada sistem rekomendasi ini adalah model _content-based filtering_ dengan _simlarty measure_ yang digunakan adalah _Cosine Similarity_.. 
Model _content-based filtering_ ini bekerja dengan mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna dengan menggunakan _similarity_ tertentu.

Sedangkan _cosine similarity_ adalah salah satu teknik mengukur kesamaan yang bekerja dengan mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama dengan menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai _cosine similarity_.
cara kerja dari fungsi *cosine similiraty* yaitu dengan melakukan perhitungan yang sering digunakan untuk menghitung kemiripan diantara item-item [[7]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748). Secara umum, fungsi similarity adalah fungsi yang menerima dua buah obyek berupa bilangan riil (0 dan 1) dan mengembalikan nilai kemiripan (similarity) antara kedua obyek tersebut berupa bilangan riil. Cosine similarity merupakan salah satu metode pengukuran kemiripan yang populer. Metode ini digunakan untuk menghitung nilai kosinus sudut antara dua vektor dan biasanya digunakan untuk mengukur kemiripan antara dua teks/dokumen. Fungsi cosine similarity antara item A dan item B ditunjukkan sebagai berikut [[8]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748). 
![img](https://i.ibb.co/tJXFZXB/image.png)
Keterangan:
```
𝑠𝑖𝑚(𝐴, 𝐵) = nilai similaritas dari item A dan item B
𝑛(𝐴) = banyaknya fitur konten item A 
𝑛(𝐵) = banyaknya fitur konten item B 
𝑛(𝐴 ∩ 𝐵)  = banyaknya fitur konten yang terdapat pada item A dan juga terdapat pada item B
```
Jika kedua objek memiliki nilai similaritas 1, maka kedua objek dikatakan identik dan sebaliknya. Semakin besar hasil dari fungsi similarity, maka kedua objek yang dievaluasi dianggap semakin mirip dan sebaliknya. 

* Berikut cara melatih model dengan menggunakan *consine similarity* yg dapat dilihat pada gambar dibawah brikut ini:
![img](https://i.ibb.co/sPrnF84/image.png)
* Pada tahapan ini menampilkan matriks kesamaan setiap judul dengan menampilkan judul film dalam 10 sampel kolom (axis = 1) dan 10 sampel baris (axis=0).
![img](https://i.ibb.co/z86Jh8T/image.png)

Dalam pemanggilan rekomendasi judul film menggunakan function yang dibuat dengan code seperti yg terlihat pada dibawah berikut ini:
![img](https://i.ibb.co/27Bbwhg/image.png)

Tahapan yang dilakukan pada fungsi tersebut ialah sebagai berikut.
1. Mengambil indeks dari judul film yang telah didefinisikan sebelumnnya
2. Mengambil skor kemiripan dengan semua film
3. Mengurutkan film berdasarkan skor kemiripan
4. Mengambil 19 judul berdasarkan kemiripan dari 1-20 karena urutan 0 memberikan indeks yang sama dengan judul film yang diinput
5. Mengambil judul film dari skor kemiripan
6. Mengembalikan 19 rekomendasi judul film dari kemiripan skor yang telah diurutkan dan menampilkan genre dari 19 rekomendasi film tersebut

Berikut _top_-20 _recommemdation_ berdasarkan genre dari judul film "*Jhonny English Reborn (2011)*"
judul | genre
---|---
Jhonny English Reborn (2011) | Adventure, Comedy, Thriller
![img](https://i.ibb.co/bWv2ht5/image.png)
Dengan hasil yang diberikan di atas berdasarkan judul film "Jhonny English Reborn (2011)" dengan genre Adventure, Comedy, Thriller maka didapatkan 19 rekomendasi judul film dengan genre yang serupa ataupun mirip.

# Evaluation
---
Pada proyek ini, Metric yang digunakan pada sistem rekomendasi judul film berdasarkan genre adalah accuracy precision. Precision adalah metrik yang membandingkan rasio prediksi benar atau positif dengan keseluruhan hasil yang diprediksi positif dengan rumus

$$\ Precission=TP/(TP+FP)$$
~~~
keterangan:
TP = True Positif (prediksi positif dan hal tersebut benar)
FP = False Positif (prediksi positif dan hal tersebut salah)
~~~
Alasan accuracy Precision dipilih adalah karena metrik ini dapat membandingkan rasio prediksi benar atau positif dengan keseluruhan hasil yang diprediksi positif. Dalam hal ini adalah rasio item yang direkomendasikan memiliki genre yang mirip atau serupa dibandingkan dengan genre dari judul film yang diinput.

Code yang digunakan untuk melihat jumlah genre yang mirip atau serupa adalah sebagai berikut.
~~~
# menghitung banyaknya data genre pada hasil rekomendasi yg dilakukan 
value = pd.DataFrame(recomendation['genre'].value_counts().reset_index().values, columns = ['genre', 'count'])
value.head()
~~~
Output:
~~~

        genre   	                        count
0	    Comedy|Thriller	                    7
1	    Adventure|Comedy	                6
2	    Action|Adventure|Comedy|Thriller	3
3	    Adventure|Comedy|Thriller	        2
4	    Adventure|Comedy|Crime|Thriller	    1
~~~
Dari output tersebut dihitung accuracy precision nya adalah
```
TP = 19 #jumlah prediksi benar untuk genre yang mirip atau serupa
FP = 0 #jumlah prediksi salah untuk genre yang mirip atau serupa

Precision = TP/(TP+FP)
print("{0:.0%}".format(Precision))
```
Dipilih nya nilai True Positif 19 karna ia merupakan nilai atau jumlah yg diduga memiliki kemiripan/identik dengan genre yg dipilih yaitu 19 (7+6+3+2+1). hasil rekomendasi yg dihasilkan model menunjukan kemiripan dengan genre film yg dinput yaitu Adventure|comedy|thriller
sedangkan utk nilai False Positif tidak teridentifikasi pada hasil output dari genre yg diinput maka nilai nya 0 
Output:
```
100%
```
Kesimpulan dari output yang dihasilkan bahwa prediksi rekomendasi yang diberikan 100% presisi sesuai genre yang mirip atau serupa dengan genre dari judul yang diinput.
## Referensi
---
[[1]](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/) Tren Positif Film Indonesia | Indonesia.go.id (2019). Available at: https://indonesia.go.id/ragam/seni/sosial/tren-positif-film-indonesia (Accessed: 28 August 2020).
[[2, 4]](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/)  Fajriansyah, Muhammad, Putra Pandu Adikara, & Agus Wahyu Widodo. " Sistem Rekomendasi Film Menggunakan Content Based Filtering." Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer [Online], 5.6 (2021): 2188-2199. Web. 9 Mei. 2022
https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/
[[3]](https://www.makeuseof.com/tag/fastest%20-ways-good-movie-film-watching/) Mihir, P. (2019) 5 Fastest Ways to Find a Good Movie or Film Worth Watching, makeuseof.com. Available at: https://www.makeuseof.com/tag/fastest -ways-good-movie-film-watching/ (Accessed: 22 December 2020).
[[5]](https://pdfs.semanticscholar.org/4cba/7c655cf843fe703211f385259ac082cb2b00.pdf) Fauzi, M. A., Arifin, A. Z. and Yuniarti, A. (2017) ‘Arabic book retrieval using class and book index based term weighting’, International Journal of Electrical and Computer Engineering, 7(6), pp. 3705–3710. doi: 10.11591/ijece.v7i6.pp3705-3711. 
[[6]](http://103.23.20.161/index.php/semnasif/article/view/1148) Badriyah, T., Fernando, R., & Syarif, I. (2018). Sistem Rekomendasi Content Based Filtering Menggunakan Algoritma Apriori. Konferensi Nasional Sistem Informasi (KNSI) 2018.
http://103.23.20.161/index.php/semnasif/article/view/1148
[[7]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748) D. Jannach, M. Zanker, A. Felfernig, and G. Friedrich, Recommender systems: an introduction, vol. 40. 2011. 
[[8]](https://jurnal.uns.ac.id/itsmart/article/download/35008/27748) L. Djumiroh and R. Saptono, “Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD,” J. ITSMART, vol. 1, no. 2, pp. 54–59, 2012. 
---Ini adalah bagian akhir laporan---