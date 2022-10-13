## PROJECT : Pakistan Large E-Commers

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

#### Penjelasan Data Wrangling :
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
