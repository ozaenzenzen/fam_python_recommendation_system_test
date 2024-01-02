# Recommendation System - Cosmetic Datasets - Fauzan Akmal Mahdi

## Domain Proyek
***
### Latar Belakang

Perkembangan kosmetik tidak berhenti dan terus berkembang. Berdasarkan penelitian *Overview of Cosmetic Regulatory Frameworks around the World* [1] penjualan kosmetik pada tahun 2020 menyentuh 341,1 juta dollar amerika dan diprediksikan akan menyentuk 560,50 juta dollar pada tahun 2030, dengan kenaikan tahunan sebesar 5,1% dari 2021 sampai 2030. Kosmetik merupakan zat atau campuran apa pun dimaksudkan untuk ditempatkan bersentuhan dengan bagian luar tubuh manusia (epidermis, sistem rambut, kuku, bibir dan alat kelamin luar organ) atau dengan gigi dan selaput lendir mulut rongga dengan tujuan khusus atau terutama untuk membersihkannya, mengharumkan mereka, mengubah penampilan mereka, melindungi mereka, menjaganya dalam kondisi baik atau memperbaiki bau badan [2]. 

Banyak faktor yang memengaruhi pemilihan kosmetik oleh setiap orang. Dengan banyaknya jenis dan merk kosmetik yang beredar, tentunya hal ini akan mempersulit seseorang untuk memilih jenis dan merk kosmetik yang cocok. Tidak jarang juga pemilihan kosmetik seseorang berdasarkan pengalaman orang lain yang telah menggunakan kosmetik.

Teknologi ditujukan untuk membantu persoalan manusia. Pada saat ini sebuah teknologi berkembang pesat dalam bidang dunia teknologi informasi yaitu *Machine Learning*.[3] *Machine learning* adalah sebuah teknologi yang dikembangkan agar mesin / komputer dapat bisa belajar dengan sendirinya tanpa arahan dari penggunanya. Tentunya teknologi *machine learning* dapat digunakan untuk membantu manusia dalam mengolah data dan menarik informasi dari sebuah data sehingga manusia bisa lebih fokus dalam pengembangan bisnisnya.

Pada penelitian ini akan dibuat suatu model sistem rekomendasi menggunkaan *content-based filtering* untuk merekomendasikan kosmetik-kosmetik yang mungkin akan digunakan oleh pengguna. *Content-based filtering* merupakan metode yang digunakan untuk merekomendasikan *item* atau barang berdasarkan "fitur" dari *item* berdasarkan dari aksi atau pengalaman sebelumnya. Contohnya yaitu merekomendasikan suatu buku berdasarkan kategori. Dengan adanya sistem rekomendasi ini diharapkan dapat membantu orang untuk menentukan jenis kosmetik yang akan dipilih.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang yang telah diuraikan, terdapat *problem statements* yang akan dibahas sebagai berikut: 
- Bagaimana cara membuat sistem rekomendasi kosmetik yang disukai pengguna lain dapat direkomendasikan kepada pengguna lainnya juga ?
- Bagaimana membuat daftar top rekomendasi berdasarkan *input* nama kosmetik dari pengguna?


### Goals

Berdasarkan *Problem Statements* yang telah diuraikan, terdapat *Goals* yang akan dicapai sebagai berikut: 
- Dapat membuat sistem rekomendasi kosmetik berdasarkan ratings dan aktivitas pengguna pada masa lalu.
- Dapat menampilkan daftar top rekomendasi kosmetik untuk pengguna baru berdasarkan *input* dari pengguna.


### Solution statements

Berdasarkan *Goals* yang telah diuraikan, terdapat *Solution Statements* yang akan dicapai sebagai berikut: 
- Menyiapkan data agar bisa digunakan dalam membangun sistem rekomendasi
- Menggunakan teknik EDA (*Exploratory Data Analysis*) seperti Pendeskripsian Dataset, Penanganan *Missing Value*, *Univariate Analysis* dan *Multivariate Analysis*
- Membuat sistem rekomendasi menggunakan teknik *Content Based Filtering*. *Content Based Filtering* adalah algoritma yang merekomendasikan item serupa dengan apa yang disukai pengguna, berdasarkan tindakan mereka sebelumnya atau umpan balik eksplisit.
- Mengevaluasi hasil rekomendasi menggunakan *precision*

## Data Understanding
Data yang digunakan bersumber dari [kaggle](https://www.kaggle.com/datasets/kingabzpro/cosmetics-datasets)

Spesifikasi dataset yang digunakan pada Table 1

Table 1. Informasi Dataset
| Jenis | Keterangan |
| --- | --- |
| Sumber Dataset | [Cosmetic Datasets](https://www.kaggle.com/datasets/kingabzpro/cosmetics-datasets) |
| Kategori Dataset | Open Dataset |
| Lisensi Dataset | [GPL](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html) |
| Jenis Dataset | Comma-Separated Values  (CSV) |
| Ukuran Dataset |  1.15 MB |

Dataset merupakan koleksi data yang berfokus kepada *rating* kosmetik. Dataset berisi berbagai fitur yang menggambarkan setiap kosmetik yang dijual, seperti  **'Label', 'Brand', 'Name', 'Price', 'Rank', 'Ingredients', 'Combination','Dry', 'Normal', 'Oily', 'Sensitive'**.  Dataset berisi 11 kolom dan 1472 baris. Dengan 4 variabel bersifat kategorikal dan 7 variabel bersifat numerik. Tujuannya adalah untuk membuat sistem rekomendasi kosmetik berdasarkan label dan nama kosmetik. Berikut penjelasan lebih lengkap terhadap variabel dalam dataset

### Data Info:
#### 1. Variabel-variabel pada Cosmetic Dataset adalah sebagai berikut:
- Label: Merupakan jenis kosmetik 
- Brand: Merupakan nama *brand* atau merek kosmetik
- Name: Merupakan nama produk kosmetik 
- Price: Merupakan harga kosmetik
- Rank: Merupakan deskripsi penilaian kosmetik
- Ingredients: Merupakan deskripsi komponen-komponen bahan kosmetik
- Combination: Merupakan *identifier* kosmetik campuran atau bukan
- Dry: Merupakan *identifier* kosmetik kering atau bukan
- Normal: Merupakan *identifier* kosmetik normal atau bukan
- Oily: Merupakan *identifier* kosmetik berminyak atau bukan
- Sensitive: Merupakan *identifier* kosmetik sensitif atau bukan

#### 2. Deskripsi Dataset:
##### Didapatkan informasi dataset sebagai berikut: 
- 1472 baris, 11 kolom. 
- Tipe data: float64(1), int64(6), object(4)
- Size dataset: 1.15 MB

Table 2. Informasi Dataset

<table><thead><tr><th>#</th><th>Column</th><th>Non-Null Count</th><th>Dtype</th></tr></thead><tbody><tr><td>---</td><td>------</td><td>--------------</td><td>-----</td></tr><tr><td>0</td><td>Label</td><td>1472 non-null</td><td>object</td></tr><tr><td>1</td><td>Brand</td><td>1472 non-null</td><td>object</td></tr><tr><td>2</td><td>Name</td><td>1472 non-null</td><td>object</td></tr><tr><td>3</td><td>Price</td><td>1472 non-null</td><td>int64</td></tr><tr><td>4</td><td>Rank</td><td>1472 non-null</td><td>float64</td></tr><tr><td>5</td><td>Ingredients</td><td>1472 non-null</td><td>object</td></tr><tr><td>6</td><td>Combination</td><td>1472 non-null</td><td>int64</td></tr><tr><td>7</td><td>Dry</td><td>1472 non-null</td><td>int64</td></tr><tr><td>8</td><td>Normal</td><td>1472 non-null</td><td>int64</td></tr><tr><td>9</td><td>Oily</td><td>1472 non-null</td><td>int64</td></tr><tr><td>10</td><td>Sensitive</td><td>1472 non-null</td><td>int64</td></tr></tbody></table>

#### 3. *Univariate Analysis*:
*Univariate Analysis* adalah tahap untuk mengeksplorasi dan menjelaskan setiap variabel dalam kumpulan data secara terpisah untuk 1 jenis variabel / kolom. Tahap ini dilakukan dengan tujuan untuk mengetahui persebaran dan informasi nilai pada data per 1 kolom sehingga dapat dilakukan proses persiapan data yang sesuai.
##### Kolom Kategorik

- Kolom Label

    Persebaran kolom Label terdapat 6 nilai yang berbeda. Nilai tertinggi didapatkan pada value `Moisturizer` sebanyak 298 dengan persentase 20.2% dan terendah pada value `Puzzle` sebanyak 170 dengan persentase 11.5%
    
    Didapatkan hasil pada kolom `Label` pada Table 3

    Table 3. hasil univariate analysis pada kolom kategorik `Label`

    <table><thead><tr><th>Data</th><th>jumlah sampel</th><th>persentase</th></tr></thead><tbody><tr><td>Moisturizer</td><td>298</td><td>20.2</td></tr><tr><td>Cleanser</td><td>281</td><td>19.1</td></tr><tr><td>Face Mask</td><td>266</td><td>18.1</td></tr><tr><td>Treatment</td><td>248</td><td>16.8</td></tr><tr><td>Eye cream</td><td>209</td><td>14.2</td></tr><tr><td>Sun protect</td><td>170</td><td>11.5</td></tr></tbody></table>
    
    Image 1. Pesebaran Kolom Label

    ![Kolom Genre](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/43cb8e46-ab40-4662-959b-30ef024840f7)

- Kolom Brand

    Persebaran kolom Brand terdapat 116 nilai yang berbeda. Nilai tertinggi didapatkan pada value `CLINIQUE` sebanyak 79 dengan persentase 5.4% dan nilai terendah pada beberapa value sebanyak 1. Berikut divisualisasikan 10 nilai tertinggi dari kolom `Brand` dan 10 nilai terendah
    
    Didapatkan hasil pada kolom `Brand` pada Table 4

    Table 4. hasil univariate analysis pada kolom kategorik `Brand`. Ditampilkan 5 teratas dan 5 terbawah karena terdapat 116 kategori

    <table><thead><tr><th>Data</th><th>jumlah sampel</th><th>persentase</th></tr></thead><tbody><tr><td>CLINIQUE</td><td>79</td><td>5.4</td></tr><tr><td>SEPHORA COLLECTION</td><td>66</td><td>4.5</td></tr><tr><td>SHISEIDO</td><td>63</td><td>4.3</td></tr><tr><td>ORIGINS</td><td>54</td><td>3.7</td></tr><tr><td>MURAD</td><td>47</td><td>3.2</td></tr><tr><td>...</td><td>...</td><td>...</td></tr><tr><td>SON &amp; PARK</td><td>1</td><td>0.1</td></tr><tr><td>MAKEUP ERASER</td><td>1</td><td>0.1</td></tr><tr><td>KAT VON D</td><td>1</td><td>0.1</td></tr><tr><td>NURSE JAMIE</td><td>1</td><td>0.1</td></tr><tr><td>DERMAFLASH</td><td>1</td><td>0.1</td></tr><tr><td></td><td></td><td></td></tr><tr><td>[116 rows x 2 columns]</td><td></td><td></td></tr></tbody></table>

    Image 2. Pesebaran Kolom Publisher (10 Highest)

    ![download (1)](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/e2771ead-09cc-4da0-8698-104e77992333)

    Image 3. Pesebaran Kolom Publisher (10 Lowest)

    ![download (2)](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/a98e5d07-67d2-4701-8560-c2251e45b4c6)


##### Kolom Numerik
Persebaran kolom numerik terdapat pada 7 kolom yaitu **'Price', 'Rank', 'Combination','Dry', 'Normal', 'Oily', 'Sensitive'**. 
- Pada kolom `Price` merupakan sebuah kolom yang berisi harga kosmetik pada dataset. 
- Pada kolom `Price` nilai terendah yaitu 5 dan untuk nilai tertinggi 260
- Pada kolom `Rank` nilai terendah 0 dan untuk nilai tertinggi 5
- Pada kolom `'Combination','Dry', 'Normal', 'Oily', 'Sensitive'` memilki nilai antara 0 dan 1 

Image 5. Pesebaran Kolom Numerik
![Kolom Numerik](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/cfadab17-5a90-4201-a024-b3e650e494ea)

#### 4. *Multivariate Analysis*:
*Multivariate Analysis* yaitu tahap mengeksplorasi dan menjelaskan setiap variabel dalam kumpulan data secara terpisah untuk 2 atau lebih jenis variabel / kolom. Tahap ini dilakukan dengan tujuan untuk mengetahui persebaran dan informasi nilai pada data antara kolom dengan kolom lainnya sehingga dapat dilakukan proses persiapan data yang sesuai.

- Pada tahap ini divisualisasikan persebaran kolom `Price` terhadap kolom kategorik `Label` dan `Brand`

    Pada Image 6 disajikan visualisasi persebaran kolom `Price` terhadap kolom kategorik `Label` dan `Brand`. Didapatkan informasi sebagai berikut
    - Antara kolom `Price` dengan kolom `Label` didapatkan persebaran nilai terbesar pada `Treatment` sedangkan persebaran nilai terendah pada `Cleanser`
    - Antara kolom `Price` dengan kolom `Brand` didapatkan persebaran nilai yang terhadap 116 nilai yang berbeda

    Image 6. Persebaran kolom `Price` terhadap kolom kategorik `Label` dan `Brand`

    ![gbrx1](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/244a0241-a887-4ba1-8890-06638ebb2615)
    ![gbrx2](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/65ccc352-8daf-4170-9587-afe466beae6d)
    
- Pada tahap ini divisualisasikan persebaran kolom `Rank` terhadap kolom kategorik `Label` dan `Brand`

    Pada Image 7 disajikan visualisasi persebaran kolom `Rank` terhadap kolom kategorik `Label` dan `Brand`. Didapatkan informasi sebagai berikut
    - Antara kolom `Rank` dengan kolom `Label` didapatkan persebaran nilai terbesar pada `Cleanser` sedangkan persebaran nilai terendah pada `Eye Cream`
    - Antara kolom `Rank` dengan kolom `Brand` didapatkan persebaran nilai yang terhadap 116 nilai yang berbeda

    Image 7. Persebaran kolom `Rank` terhadap kolom kategorik `Label` dan `Brand`

    ![gbry1](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/9dda0d1e-1992-42b3-839f-3e94e9a55307)
    ![gbry2](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/6aa5672f-7b4b-48e4-948d-a25d600f37f2)


Pada Image 8 disajikan visualisasi *multivariate analysis* atau persebaran antar kolom numerik. Didapatkan beberapa informasi sebagai berikut
- Kolom `Price` dengan kolom `Rank` memiliki korelasi negatif ditunjukkan visualisasi semakin tinggi variabel X, maka semakin rendah variabel Y
- Antar Kolom `'Combination','Dry', 'Normal', 'Oily', dan 'Sensitive'` saling memiliki korelasi positif. Ini ditunjukkan visualisasi semakin tinggi variabel X, maka semakin tinggi variabel Y
- Kolom `'Combination','Dry', 'Normal', 'Oily', dan 'Sensitive'` dengan kolom `Price` dan `Rank` hampir tidak memiliki korelasi. Ini ditunjukkan visualisasi persebaran data sejajar dengan sumbu X atau sumbu Y

Image 8. Visualisasi persebaran antar kolom numerik
![Visualisasi persebaran antar kolom numerik](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/fa7ee75e-b86e-496e-a29d-fcb980fd3928)


## Data Preparation
Langkah dalam persiapan data dijabarkan dalam beberapa poin
1. Mendownload dataset dari kaggle
    - Proses: Mengambil dataset dari website kaggle 
    - Alasan: Dataset akan digunakan untuk pengolahan dan pemodelan pada penelitian
2. Menyimpan dataset ke dalam Google Drive
    - Proses: Menyimpan dataset ke dalam penyimpanan cloud Google Drive
    - Alasan: Penyimpanan dataset dalam Google Drive agar mempermudah proses pemanggilan data dalam proses penelitian
3. Melakukan pemanggilan library pendukung
    - Proses: Melakukan pengimporan beberapa library dari numpy, matplotlib, pandas, dan seaborn dengan `import`
    - Alasan: Ditujukan untuk mendukung proses pengolahan, pelatihan, dan evaluasi data seperti pengolahan, visualisasi, dan proses matematis
4. Melakukan mounting Google Colab dengan Google Drive 
    - Proses: Melakukan koneksi antar platform Google Colab sebagai media pengolahan data dan Google Drive sebagai media penyimpanan data. Menggunakan library `from google.colab import drive` dan menggunakan kode `drive.mount('/content/drive')`
    - Alasan: Agar proses persiapan data dan pengolahan model bisa dilakukan dari data yang disimpan dalam Google Drive dan media pengolahan data di Google Colab
5. Memanggil dataset 
    - Proses: Melakukan pemanggilan dataset dengan library pandas `pd.read_csv(url)`
    - Alasan: Agar dataset siap digunakan pada proses pengolahan dalam Google Colab
6. Melakukan pengecekan informasi dataset
    - Proses: Pengecekan informasi dataset terbagi menjadi sub tahap seperti
        - menggunakan `dataset.info()` untuk menampilkan jumlah baris, missing value, dan tipe data dari dataset
        - menggunakan `dataset.describe()` untuk mendeskripsikan parameter singkat pada dataset
            - Count atau jumlah baris dari setiap kolom
            - Mean atau rata-rata dari setiap kolom
            - Standar deviasi dari setiap kolom
            - Nilai minimum / terkecil dari setiap kolom
            - Nilai kuartil pertama atau 25% dari setiap kolom
            - Nilai kuartil kedua atau 50% atau median dari setiap kolom
            - Nilai kuartil ketiga atau 75% dari setiap kolom
            - Nilai maximum / terbesar dari setiap kolom
        - menggunakan `dataset.column` untuk mengetahui kolom yang tersedia pada dataset
    - Alasan: Untuk mengetahui informasi dasar dari dataset yang akan digunakan sehingga dapat ditentukan langkah selanjutnya dalam melakukan persiapan data
7. Melakukan pengecekan missing value dalam data (bisa NULL atau 0) 
    - Proses: Menggunakan `dataset.isnull().sum()` untuk mendapatkan informasi apakah terdapat data yang bersifat null, hasil:
        - Tidak didapatkan *missing value* seluruh kolom fitur

            Table 6. Informasi Missing Value

            <table><thead><tr><th>Column</th><th>Count Null Value</th></tr></thead><tbody><tr><td>Label</td><td>0</td></tr><tr><td>Brand</td><td>0</td></tr><tr><td>Name</td><td>0</td></tr><tr><td>Price</td><td>0</td></tr><tr><td>Rank</td><td>0</td></tr><tr><td>Ingredients</td><td>0</td></tr><tr><td>Combination</td><td>0</td></tr><tr><td>Dry</td><td>0</td></tr><tr><td>Normal</td><td>0</td></tr><tr><td>Oily</td><td>0</td></tr><tr><td>Sensitive</td><td>0</td></tr></tbody></table>

    - Alasan: Untuk mengetahui informasi missing value dari dataset yang akan digunakan sehingga dapat ditentukan langkah selanjutnya dalam melakukan persiapan data

8. Melakukan univariate analysis yaitu mengeksplorasi dan menjelaskan setiap variabel dalam kumpulan data secara terpisah untuk 1 jenis variabel / kolom
    - Proses: Proses dalam tahap ini ditujukan untuk mengeksplorasi dan menjelaskan setiap variabel dalam kumpulan data secara terpisah untuk 1 jenis variabel / kolom. Tahap ini terbagi menjadi sub tahap seperti berikut
        - Membagi kolom yang bersifat numerk dan kategorikal 
        - Menyimpan kolom ke dalam masing-masing variabel yaitu `numerical_features` dan `categorical_features`
        - Melakukan visualisasi untuk menginformasikan data pada kolom kategorik yaitu `Label`, `Brand`. Untuk kolom `Name` dan `Ingredients` tidak dipilih karena bersifat unique pada setiap datanya
        - Melakukan visualisasi persebaran nilai dalam bentuk grafik untuk menginformasikan data pada kolom numerik yaitu **'Price', 'Rank', 'Combination','Dry', 'Normal', 'Oily', 'Sensitive'**
    - Alasan: Untuk mengetahui informasi persebaran nilai pada kolom kategorikal dan numerikal secara spesifik univariate per kolom pada dataset yang digunakan sehingga dapat ditentukan langkah selanjutnya dalam melakukan persiapan data
9. Melakukan multivariate analysis yaitu mengeksplorasi dan menjelaskan setiap variabel dalam kumpulan data secara terpisah untuk 2 atau lebih jenis variabel / kolom
    - Proses: Pada tahap ini terbagi menjadi beberapa sub tahap sebagai berikut
        - Visualisasi data kategorik `Label` dan `Brand` terhadap data numerik yang dipilih `Price` dan `Rank` menggunakan fungsi `pairplot()`
        - Visualisasi antar data kolom numerik menggunakan fungsi `pairplot()`
        - Visualisasi matriks korelasi antar data kolom numerik untuk mendapatkan nilai koefisien korelasi
    - Alasan: Untuk mengetahui informasi persebaran nilai antar kolom kategorikal dan numerikal dan kolom numerik dengan kolom numerik lainnya  pada dataset yang digunakan sehingga dapat ditentukan langkah selanjutnya dalam melakukan persiapan data. 


## Modeling
Pada penelitian ini akan dilakukan proses pembuatan model sistem rekomendasi menggunakan metode *Content Based Filtering*. 

Sistem *Content Based Filtering* adalah sistem yang merekomendasikan konten yang mirip dengan konten yang disukai pengguna sebelumnya. Jika suatu konten memiliki karakteristik yang sama atau hampir sama dengan konten lainnya, maka kedua konten tersebut dapat dikatakan mirip.

Misalkan dalam sistem rekomendasi kosmetik, jika pengguna menyukai kosmetik `'The Eye Balm Intense'`, sistem dapat merekomendasikan kosmetik dengan label `'Eye Cream'` lainnya.

- Tahap Vektorisasi dengan TF-IDF (*Term Frequency - Inverse Document Frequency*)

    Tahap ini akan dilakukan proses vektorisasi dengan metode yang digunakan untuk menentukan nilai frekuensi sebuah kata di dalam sebuah dokumen atau artikel dan juga frekuensi di dalam banyak dokumen. Sistem rekomendasi berdasarkan `Label` yang dimiliki kosmetik. Teknik ini digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap `Label` kosmetik. Sample dari hasil tf-idf dapat dilihat pada Image 9.

    Image 9. Sample vektorisasi
    <img width="1275" alt="Screenshot 2024-01-02 at 16 48 35" src="https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/512d94da-f645-4894-a8dd-0526456b5fdb">

    Ditunjukkan pada Image 9 bahwa nilai `Tonique Radiance Clarifying Refining Toner` bertipe label `cleanser` Hal ini terlihat pada kolom `cleanser` baris ke-3

- Tahap *Cosine Similarity*

    Tahap *Cosine Similarity* ditujukan untuk mengukur derajat kesamaan antara dua vektor dan menentukan apakah kedua vektor menunjuk ke arah yang sama. Cara kerja teknik ini dengan menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus antara dua vektor, semakin besar nilai kemiripan cosinusnya.

    Image 10. Sample hasil consine similarity
    <img width="1275" alt="Screenshot 2024-01-02 at 17 02 59" src="https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/9078d154-d4f5-436c-91dd-d409f4af013a">

    Pada Image 10 dituntukkan kesamaan antara satu nama kosmetik dengan nama kosmetik lainnya. Pada nama kosmetik `Mist & Fix Setting Spray` memiliki Label yang sama dengan nama kosmetik `Secret Sauce Clinically Advanced Miraculous Anti-Aging Moisturizer`, kesamaan ini ditandai dengan nilai 1 pada matriks. Kedua kosmetik tersebut termasuk ke dalam Label `Moisturizer`

- Tahap Get Recommendation 

    Pada tahap ini dilakukan pengujian untuk mengetahui seberapa baik model dalam memberikan sebuah daftar rekomendasi dari sebuah fungsi yang akan menerima beberapa sebuah *input* dalam `nama_kosmetik, similarity_data, items, k` dengan definisi masing-masing parameter sebagai berikut:

    - nama_komsetik: Parameter masukkan nama kosmetik yang ingin diketahui rekomendasinya
    - similarity_data: Parameter yang berisi mengenai similarity yang telah dibuat 
    - items: Parameter yang berisi Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah `Name` dan `Label`
    - k: Parameter untuk menentukan jumlah rekomendasi yang ingin diberikan

    Table 9. Hasil Rekomendasi kosmetik dengan nama `Help Me` yang termasuk label `Treatment`

    <table><thead><tr><th align="right">No</th><th align="right">Name</th><th align="right">Label</th></tr></thead><tbody><tr><td align="right">0</td><td align="right">Ferulic + Retinol Wrinkle Recovery Peel</td><td align="right">Treatment</td></tr><tr><td align="right">1</td><td align="right">Concentrated Reconstructing Serum</td><td align="right">Treatment</td></tr><tr><td align="right">2</td><td align="right">High Potency Classics: Hyaluronic Intensive Mo...</td><td align="right">Treatment</td></tr><tr><td align="right">3</td><td align="right">EradiKate™ Mask Foam-Activated Acne Treatment</td><td align="right">Treatment</td></tr><tr><td align="right">4</td><td align="right">Crème Ancienne® Supreme Face Serum</td><td align="right">Treatment</td></tr><tr><td align="right">5</td><td align="right">FIRMx Growth Factor Extreme Neuropeptide Serum</td><td align="right">Treatment</td></tr><tr><td align="right">6</td><td align="right">Power Dose Vitamin C</td><td align="right">Treatment</td></tr><tr><td align="right">7</td><td align="right">Kakadu C™ Intensive Vitamin C Peel Pads with F...</td><td align="right">Treatment</td></tr><tr><td align="right">8</td><td align="right">Intensive-C® Radiance Peel</td><td align="right">Treatment</td></tr><tr><td align="right">9</td><td align="right">REVEAL Concentrated Color Correcting Drops</td><td align="right">Treatment</td></tr></tbody></table>
    
    Table 10. Hasil Rekomendasi kosmetik dengan nama `Acne Solutions BB Cream Broad Spectrum SPF 40` yang termasuk label `Moisturizer`

    <table><thead><tr><th align="right">No</th><th align="right">Name</th><th align="right">Label</th></tr></thead><tbody><tr><td align="right">0</td><td align="right">Crème de la Mer</td><td align="right">Moisturizer</td></tr><tr><td align="right">1</td><td align="right">Truth Revealed™ Brightening Broad Spectrum SPF...</td><td align="right">Moisturizer</td></tr><tr><td align="right">2</td><td align="right">Resilience Lift Night Lifting/Firming Face and...</td><td align="right">Moisturizer</td></tr><tr><td align="right">3</td><td align="right">Resilience Lift Firming/Sculpting Face and Nec...</td><td align="right">Moisturizer</td></tr><tr><td align="right">4</td><td align="right">Cooling Water</td><td align="right">Moisturizer</td></tr><tr><td align="right">5</td><td align="right">100 percent Pure Argan Oil Light</td><td align="right">Moisturizer</td></tr><tr><td align="right">6</td><td align="right">Hungarian Water Essence</td><td align="right">Moisturizer</td></tr><tr><td align="right">7</td><td align="right">Capture Totale Multi-Perfection Creme</td><td align="right">Moisturizer</td></tr><tr><td align="right">8</td><td align="right">Premier Cru Cream</td><td align="right">Moisturizer</td></tr><tr><td align="right">9</td><td align="right">Waterfall Glacier Water Cream</td><td align="right">Moisturizer</td></tr></tbody></table>

## Evaluation
Pada tahap evaluasi akan digunakan *Precision* untuk mengevaluasi hasil dari rekomendasi pada tabel 9 dan tabel 10. *Precision* dapat didefinisikan sebagai berikut:

![dos_819311f78d87da1e0fd8660171fa58e620211012160253 (1)](https://github.com/ozaenzenzen/project_vehicle_log/assets/67274784/c6401bdc-4825-408a-aecc-5f92ec1ac6e7)

Parameter *precision*
- r = total rekomendasi yang relevan
- i = jumlah rekomendasi yang diberikan

Hasil: 
1. Dari hasil rekomendasi di tabel 9, diketahui bahwa `Help Me` masuk ke dalam label `Treatment`. Dari 10 item yang direkomendasikan, 10 item memiliki label `Treatment` (*similar*)
2. Untuk hasil rekomendasi di tabel 10, diketahui bahwa `Acne Solutions BB Cream Broad Spectrum SPF 40` masuk ke dalam label `Moisturizer`. Dari 10 item yang direkomendasikan, 10 item memiliki label `Moisturizer` (*similar*)


Artinya, nilai *precision* dari sistem rekomendasi yang telah dibuat sebesar 10/10 atau 100%


### Kesimpulan

Pada evaluasi hasil 2 pengujian sistem rekomendasi dengan parameter *Precision* didapatkan nilai 100%. Untuk hasil rekomendasi di tabel 9, diketahui bahwa kosmetik `Help Me` masuk ke dalam label `Treatment`. Dari 10 item yang direkomendasikan dihasilkan 10 item memiliki label `Treatment` dan
untuk hasil rekomendasi di tabel 10, diketahui bahwa `Acne Solutions BB Cream Broad Spectrum SPF 40` masuk ke dalam label `Moisturizer`. Dari 10 item yang direkomendasikan dihasilkan 10 item memiliki label `Moisturizer` 

Penelitian ini telah  menerapkan langkah persiapan data *Video Game Sales* menggunakan teknik EDA (*Exploratory Data Analysis*) seperti Pendeskripsian Dataset, Penanganan *Missing Value*, *Univariate Analysis* dan *Multivariate Analysis*.

Mengacu kepada *business understanding* yang ditulis pada awal laporan, penelitian ini telah berhasil membuat sistem rekomendasi kosmetik yang disukai pengguna dengan menerapkan tahap vektorisasi TF-IDF dan menghitung *Cosine Similarity*. Kemudian telah dilakukan pembuatan daftar top rekomendasi berdasarkan *input* atau masukkan yaitu nama kosmetik

Dari penlitian ini, sudah dilakukan pembangunan sistem rekmendasi kosmetik yang dapat membantu orang untuk menentukan kosmetik dari pengalaman pengguna lainnya 


## Referensi
[1] [Ferreira, M., Matos, A., Couras, A., Marto, J. and Ribeiro, H., 2022. Overview of cosmetic regulatory frameworks around the world. Cosmetics, 9(4), p.72.](https://www.mdpi.com/2079-9284/9/4/72) 

[2] [Bom, S., Jorge, J., Ribeiro, H.M. and Marto, J.O.A.N.A., 2019. A step forward on sustainability in the cosmetics industry: A review. Journal of Cleaner Production, 225, pp.270-290.](https://www.sciencedirect.com/science/article/abs/pii/S0959652619309655)

[3] [Jalil, N.A., Hwang, H.J. and Dawi, N.M., 2019, July. Machines learning trends, perspectives and prospects in education sector. In Proceedings of the 3rd International Conference on Education and Multimedia Technology (pp. 201-205).](https://github.com/ozaenzenzen/fam_python_predictive_analytics_test2/files/13662300/Machines.Learning.Trends.Perspectives.and.Prospects.in.Education.Sector.pdf)

