# Laporan Proyek Machine Learning - Muhammad Difagama Ivanka

## Project Overview

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/138017796-b083cf9c-1610-4d14-8287-b3efe152cc73.png">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/138018614-de84c049-e638-49b7-8078-633f68ff3a26.png"><br>
  <sup><sub><a href="https://www.pxfuel.com/en/free-photo-xtdqo"><i>image source</i></a></sub></sup>
  <sup><sub><a href="https://www.flickr.com/photos/levork/4966756896"><i>image source</i></a></sub></sup>
</p>

Penggemar cerita superhero tentu sudah mengenal dengan adanya dua *universe* fiksi populer yaitu [**Marvel *Universe***](https://www.marvel.com/explore) dan [**DC *Universe***](https://www.dccomics.com/). Adanya cerita superhero tersebut terutama bagi seorang yang merupakan warga kebangsaan Amerika Serikat sudah menjadi suatu budaya dan peradaban bagi kehidupan sehari-hari yang tidak dapat dilepaskan. [<sup>1</sup>](https://scholarship.richmond.edu/cgi/viewcontent.cgi?article=2397&context=honors-theses) Perkembangan cerita superhero yang berawal dari komik dan kemudian mulai banyak diadaptasi ke dalam perfilman atau media lainnya lantas menjadikan cerita ini semakin populer bahkan hingga ke seluruh penjuru dunia. [<sup>2</sup>](https://core.ac.uk/download/pdf/61661616.pdf) Dalam perjalanan keduanya telah menjadi perdebatan panjang sebagai rival tentang siapa yang terbaik di antara keduanya baik dalam aspek superhero itu sendiri maupun jalan cerita dalam komik dan atau media lainnya. [<sup>3</sup>](https://www.qualitycomix.com/learn/marvelvdc#:~:text=While%20both%20comics%20publishers%20present,Batman)

Perdebatan tersebut tidak terkecuali juga memiliki pengaruh terhadap orang yang juga menggemari tokoh superhero dalam dua cerita tersebut didalam menentukan *action figures* siapakah yang akan dibeli atau dikumpulkan. Tentu bagi seorang yang memiliki dana besar akan sangat mudah baginya untuk dapat membeli keseluruhan *figures* tersebut tanpa peduli dengan syarat khusus. Namun berdasarkan data dari diantaranya empat *marketplace* populer yaitu [Amazon](https://www.amazon.com/Superhero-figures/s?k=Superhero+figures), [eBay](https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2499334.m570.l1313&_nkw=superhero+action+figures&_sacat=220), [Tokopedia](https://www.tokopedia.com/find/action-figure-super-hero), dan [Shopee](https://shopee.co.id/search?keyword=superhero%20figures) menunjukkan rata-rata hanya superhero populer saja baik itu berdasarkan cerita dalam komik, film, atau media lainnya yang terdapat dalam katalog penjualan, serta semakin populer superhero tersebut akan semakin diminati untuk dibeli. 

Hal ini selain akan menyulitkan bagi penggemar yang akan mengoleksi juga akan dapat mengurangi keuntungan dari pihak pemilik cerita karena penikmat memiliki kecenderungan untuk menyukai hanya karakter superhero yang populer saja walaupun nantinya akan ada superhero dengan jalan cerita jauh lebih bagus dan menarik serta kekuatan yang unik tidak akan dapat menarik minat mereka. Oleh karena itu dibuatkan sebuah sistem rekomendasi yang dapat membantu menyelesaikan permasalahan tersebut. Diharapkan hasil rekomendasi dapat membantu karakter-karakter yang jarang terekspos terutama dikarenakan kurang populer menjadi digemari banyak pihak. Sehingga dapat membantu pihak pemilik cerita dalam meningkatkan keuntungan serta dapat memudahkan bagi seseorang dalam menentukan siapa saja karakter superhero favoritnya terlebih bagi pengoleksi *action figures*nya.

---
<sub><sup>1. Lydia Dubois. (2019). Superheroes and "the American way" : popular culture, national identity, and American notions of heroism and leadership. Honors Theses. 1380.</sup></sub><br>
<sub><sup>2. Alex Brundige. (2015). The Rise of Marvel and DC's Transmedia Superheroes: Comic Book Adaptations, Fanboy Auteurs, and Guiding Fan Reception. Electronic Thesis and Dissertation Repository. 3104.</sup></sub><br>
<sub><sup>3. Brent Moeshlin. (2021). QUALITYCOMIX: What is the difference between Marvel and DC?</sup></sub>

## Business Understanding
Bagian ini menjelaskan proses klarifikasi masalah dengan mengajukan beberapa solusi dalam menyelesaikannya.

### Problem Statements
Berangkat dari *overview* tersebut, maka rincian masalah yang dapat diselesaikan diantaranya:
1. Apa **sistem rekomendasi** yang paling baik dan sesuai untuk diterapkan pada proyek ini?
2. Bagaimana cara membuat **sistem rekomendasi** tersebut agar dapat merekomendasikan karakter superhero terbaik bagi pengoleksi *action figures*?

### Goals
Berikut merupakan tujuan dibuatnya proyek ini:
1. Memilih serta membuat sistem rekomendasi karakter superhero yang baik dan sesuai bagi pengoleksi *action figures*.
2. Merekomendasikan setidaknya lima karakter superhero terbaik yang mungkin juga disukai oleh pengoleksi *action figures*.

### Solution approach
Solusi yang dapat diterapkan untuk mencapai tujuan tersebut diantaranya:
- Memilih sistem rekomendasi [*content-based filtering*](https://codeburst.io/explanation-of-recommender-systems-in-information-retrieval-13077e1d916c) yang memiliki kesesuaian dengan dataset dimana tidak harus memerlukan adanya informasi dari sang pengoleksi *action figures*. Kemudian diajukan tiga algoritma terhadap sistem rekomendasi tersebut.
- Memilih tiga algoritma yang diajukan dalam sistem rekomendasi tersebut, yaitu:
  * Algoritma `Nearest Neighbors` yang menerapkan jarak **Jaccard**. Algoritma ini dipilih mengingat kesederhanaan dalam penggunaan, kemudian karena permasalahan berkaitan dengan *unsupervised learning* serta penggunaan jarak dimaksudkan untuk dataset yang memiliki fitur [*binary*](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.DistanceMetric.html#sklearn.neighbors.DistanceMetric). Cara kerja algoritma adalah dengan menemukan jumlah beberapa *neighbors* terdekat dari suatu titik baru untuk kemudian menentukan termasuk dari kelompok mana titik tersebut. [<sup>4</sup>](https://scikit-learn.org/stable/modules/neighbors.html#unsupervised-neighbors) Sedangkan jarak *jaccard*, membandingkan anggota pada dua set untuk melihat anggota yang terbagi atau yang terdapat perbedaan. Jarak ini memiliki rentang dari 0% hingga 100% dengan semakin tinggi persentasenya, maka semakin mirip kedua populasi tersebut. Meskipun mudah diinterpretasikan, namun penggunaan jarak ini sangat sensitif terhadap ukuran sampel kecil dan dapat memberikan hasil yang salah, terutama pada sampel sangat kecil atau kumpulan data dengan pengamatan yang hilang.  [<sup>5</sup>](https://www.statisticshowto.com/jaccard-index/)
  * Algoritma `Nearest Neighbors` yang menerapkan jarak **RusselRao**.
  * Algoritma `Cosine Similarity`.
- **Collaborative Filtering**. Sama dengan di atas. 

---
<sub><sup>4. sklearn. (2021). "1.6. Nearest Neighbors".</sup></sub>
<sub><sup>5. Stephanie. (2016). statisticshowto: Jaccard Index / Similarity Coefficient.</sup></sub>

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

## Data Preparation
Pada bagian ini Anda menjelaskan teknik yang digunakan pada tahapan Data Preparation. 
- Terapkan minimal satu teknik data preparation dan jelaskan proses yang dilakukan.
- Jelaskan juga alasan mengapa Anda perlu menerapkan teknik tersebut pada tahap Data Preparation. 

## Modeling
Tahapan ini membahas mengenai **pembuatan model sistem rekomendasi** untuk menyelesaikan permasalahan dan **menyajikan top-N recommendation sebagai solusi.**

Untuk menjelaskan mengenai bagian ini, Anda dapat mengikuti panduan: 
- Jelaskan bagaimana Anda melakukan proses modeling dalam proyek. 
- Sajikan top-N recommendation sebagai output model Anda.
- Jelaskan pula hasil rekomendasi dari model Anda.

## Evaluation
Bagian ini menjelaskan mengenai metrik evaluasi yang digunakan untuk mengukur kinerja model.  Penjelasannya meliputi (namun tidak terbatas pada) beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan dan bagaimana formulanya
- Kelebihan dan kekurangan metrik
- Bagaimana cara menerapkannya ke dalam kode.

> **Ini adalah bagian akhir laporan**

_Catatan:_
_Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/) atau [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/). Semangat!_
