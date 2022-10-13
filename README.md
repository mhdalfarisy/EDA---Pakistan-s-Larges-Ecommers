## PROJECT : Pakistan Large E-Commers

![a1](https://github.com/mhdalfarisy/EDA---Pakistan-s-Larges-Ecommers/blob/main/Images/62253a402fccf.jpg)

### **Problem Statement**
  - Transaksi penjualan Perusahaan E-Commers Pakistan setiap tahunnya mengalami penurunan, hal ini dikarenakan angka pembatalan yang dilakukan konsumen setiap tahunnya terus meningkat. Tahun 2016 pembatalan penjualan terjadi sebanyak 41%, pada tahun 2017 mengalami peningkatan 45% dan pada tahun 2018 mengalami peningkatan menjadi 48% pembatalan penjualan. Jika hal ini dibiarkan, maka Perusahaan E-Commers Pakistan akan mengalami penurunan penjualan yang semakin tinggi dan akan kehilangan konsumen. 

### **Objectives**
  - Memberikan rekomendasi strategi kepada perusahaan E-Commers Pakistan untuk meningkatkan penjualan dan menurunkan angka pembatalan pembelian.

### **Analytical Approach**
  - Pendekatan analisa ini dengan cara melakukan pembagian variabel pada saat dilakukan Exploratory Data Analyst dan Visualisasi Data:
  - Melakukan Exploratory Data Analyst terhadap seluruh variabel yang ada untuk mengetahui karakteristik karyawan yang resign dari kantor (Jupyter NoteBook).
  - Melakukan Visualisasi data dari setiap analisa untuk mendapatkan gambaran secara visual dari hasil Exploratory Data Analyst (Tableau).

### **Definisi Kolom**
#
| **Nama Kolom** | **Deskripsi Kolom** |
| --- | --- |
|Item_Id|Nomor urut product dalam database di website saat barang masuk troli pembelian di marketplace|
|Status|Informasi status pengiriman|
|Created_at|Tanggal dibuat pesanan|
|Stock_Keeping_Unit|Kode stock di gundang|
|Price|Harga produk|
|Ordered_Quantity|Jumlah pembelian|
|Grand_Total|Total pembelian setelah diskon|
|Increment_Id|Kode electronic struck pembelian|
|Category|Kategori Produknya|
|Sales_Commission_Code|Komisi sales untuk product yang terjual|
|Discount_Amount|Jumlah diskon yang diberikan|
|Payment_Method|Jenis pembayaran|
|Payment_Method_Category|Kategori pembayaran|
|Working_Date|Jam kerja pengiriman barang|
|Business_Insight_Status|Status pengiriman berhasil atau tidak|
|Year|Tahun penjualan|
|Month|Bulan penjualan|
|Customer_Since|Tahun konsumen berasal|
|Month-Year|Tahun dan Bulan|
|FY|Tahun fiskal pajak di pakistan|
|Customer_Id|Konsumen Id|

## Penjelasan Data Wrangling :
- **Total baris dan kolom :**
  - Baris 1.048.575
  - Kolom 26
---
- **Nama Kolom** :
  - Banyak nama kolom yang masih menggunakan huruf kapital tidak sesuai, dan ada yang menggunakan kategori '_' ada yang tidak serta ada spasi lebih di nama kolom.
---
- **Tipe data yang harus di ganti:**
  - item_id -> float64 -> int64, dikarenakan item_id nomor urut yang seharusnya menggunakan tipe data diskrit, sehingga akan di ganti ke tipe data diskrit menggunakan `int64` .
  - created_at -> object -> datetime64, dikarenakan created_at merupakan tanggal di buatnya pesanan dimarketplace, sehingga tipe data string akan di ganti menjadi tipe data `datetime64` yang menandakan tanggal.
  - qty_ordered -> float64 -> int64, dikarenakan qty_ordered merupakan jumlah kuantitas/banyaknya produk yang dibeli oleh konsumen. Untuk produk ini berisikan angka satuan yang tidak memiliki angka decimal (bukan tipe data continous) sehingga perlu di ganti tipe data menjadi tipe data angka diskrit dengan menggunakan tipe `int64`.
  - Working Date -> object -> int64, dikarenakan Working Date merupakan tanggal / hari kerja, maka tipe datanya akan diubah menjadi tipe data tanggal `datetime64`.
  -  Year -> float64 -> int64, dikarenakan Year merupakan tahun penjualan, sehingga tipe datanya akan diganti menjadi `datetime64`.
  -  Month -> float64 -> int64, dikarenakan Month merupakan bulan penjualan, sehingga tipe datanya akan diganti menjadi `datetime64`.
  -  Customer ID -> float64 -> int64, dikarenakan Customer ID adalah nomor identitas konsumen sehingga tipe datanya tidak menggunakan decimal / tidak menggunakan tipe data continous sehingga tipe datanya perlu di ubah menjadi distrik / `int64`.
---
- **Kolom Missing Values :**
  - `item_id`, `created_at`, `sku`, `price`, `qty_ordered`, `grand_total`, `increment_id`,`sales_commission_code`, `discount_amount`, `payment_method`, `Working Date`, `MV`, `Year`, `Month`, `Customer Since`, `M-Y`, `FY`, `Customer ID`,`Unnamed: 21`,`Unnamed: 22`,`Unnamed: 23`,`Unnamed: 24`,`Unnamed: 25` berisikan missing values yang memiliki tanda **NaN**.
  -  berisikan missing values yang memiliki tanda **NaN** dan **\N**
  -  berisikan missing values yang memiliki tanda **NaN** dan **#REFF**
---
- **Persentase Missing Values :**
  - `item_id`, `created_at`, `sku`, `price`, `qty_ordered`, `grand_total`, `increment_id`,`sales_commission_code`, `discount_amount`, `payment_method`, `Working Date`, `MV`, `Year`, `Month`, `Customer Since`, `M-Y`, `FY`, `Customer ID`, `status`,`category_name_1` dan `BI Status` memiliki 44,26% missing values.
  - `Unnamed: 21`,`Unnamed: 22`,`Unnamed: 23`,`Unnamed: 24`,`Unnamed: 25` memiliki missing values 100%

## **Kesimpulan Exploratory Data Analyst**
1. `Status :` Pembataln transaksi banyak terjadi dengan status `Cancelled` sebanyak 32,8% dan `Refund` sebanyak 11,8%.
2. `Category :` Produk yang paling banyak pembatalan ada pada category `Mobiles & Tablet :`, dengan total pembatalan `Cancelled` sebanyak 9,8% dan pengembalian barang (`Refund`) sebanyak 2,1%.
3. `Payment_Method_Category :` Cara yang paling banyak digunakan konsumen di pakistan adalah `COD, Debit Card dan Credit Card` namun pembatalan paling banyak ada pada cara pembayaran `Credit Card & Debit Card` sedangkan pembatalan refund paling banyak dengan cara pembayaran `COD`.
4. `Discount_Amount_Category :` Transaksi yang tidak mendapatkan diskon paling banyak pembatalan sekitar 27% dan transaksi yang mendapatkan diskon terjadi pembatalan karena diskon yang diberikan kurang dari 1000 Rupee.
5. `Month :` Bulan yang paling banyak transaksi berhasil ada pada akhir tahun bulan 11, pertengahan tahun bulan 8 dan awal tahun bulan 5 dengan.

## **Saran Exploratory Data Analyst**
1. `Status :` 
   - Untuk mengecilkan angka pembatalan pesanan dan refund, perusahaan dapat melakukan evaluasi seperti berikut :
   - Melakukan pencegah pembatalan :
     -  Menawarkan harga non-refundable
     -  Terima berbagai metode pembayaran
     -  Validasi pembayaran dimuka
     -  Balas pertanyaan customer dengan cepat
     -  Pikat pemesan last minute dari perangkat mobile
     -  Buat promosi / diskon
   - Untuk mengurangi pengembalian barang (refund) :
     - Mengontrol kualitas barang sebelum melakukan pengiriman
     - Mendeskripsikan produk melalui tulisan, gambar dan ukuran packingan
     - Meminta feedback pelanggan
     - Menampilkan informasi pengiriman dan waktu barang akan sampai
     - Menyediakan customer service real time
2. `Category :` 
   - Perusahaan dapat memberikan diskon untuk kategori Mobile & Tablets untuk menarik minat pembeli, terutama pada pembelian yang melebihi 1 unit selain itu perusahaan dapat memberikan garansi pada pembelian barang `Mobile & Tablets`.
3. `Payment_Method_Category :` Perusahaan dapat memfokuskan pembayaran menggunakan media elektronik seperti `Debit Card dan Credit Card` berikan potongan harga jika konsumen melakukan pembelian barang menggunakan pembayaran secara `Debit Card dan Credit Card` , berikan point tambahan untuk pembayaran secara elektronik yang mana point ini nanti dapat di tukarkan dan perusahaan dapat membangun branding awarness tentang keuntungan menggunakan pembayaran dengan elektronik.
4. `Discount_Amount_Category :` Untuk pemberian diskon kepada konsumen, perusahaan dapat memberikan diskon sebesar besar nya namun pada tanggal tertentu saja yang berkaitan dengan hari besar di pakistan dan dikson dapat diberikan berkisaran diatas 50% atau setengah harga dari total pembelian.
5. `Month :` Awal tahun yaitu bulan 5, pertengahan tahun bulan 8 dan akhir tahun bulan 11 dapat perusahaan jadikan sebagai target promo besar besaran selama 1 bulan penuh, berikan promo besar pada bulan itu terhadap produk-produk yang memiliki transaksi paling banyak terjual, berikan diskon tambahan jika pembayaran menggunakan pembayaran elektronik dan berikan garansi untuk setiap pembelian. Selain dari bulan 5,8 dan bulan 11 perusahaan dapat gunakan untuk membangun branding awarness.

**💬 Ask me about anything, I'll be happy to help!** <br>
**💬 My inbox is always open, Contact me**
<br>
<br> 
  </a>
  <a href="mailto:m.alfarisy797@gmail.com">
    <img align="left" alt="Muhammad Al-farisy | Gmail" width="26px" src="https://cdn.worldvectorlogo.com/logos/official-gmail-icon-2020-.svg" />
  </a>
  <a href="https://www.linkedin.com/in/m-alfarisy97/">
    <img align="left" alt="Muhamamd Al-farisy | Instagram" width="26px" src="https://cdn.worldvectorlogo.com/logos/linkedin-icon-2.svg" />
  </a>
  <a href="https://www.instagram.com/inifaris_____/">
    <img align="left" alt="Muhammad Al-farisy | Instagram" width="24px" src="https://cdn.worldvectorlogo.com/logos/instagram-5.svg" />
  </a>
  <a href="https://public.tableau.com/app/profile/muhammad.al.farisy6147">
    <img align="left" alt="Muhammad Al-farisy | Tableau" width="24px" src="https://seeklogo.com/images/T/tableau-software-logo-081AF6D95D-seeklogo.com.png" />
  </a>
  
<br>
<br>

⭐️ From [Muhammad Al-farisy](https://github.com/mhdalfarisy)
