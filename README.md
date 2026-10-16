# Amazon Data Manipulation & Outlier Treatment (Log Transformation)

## Ringkasan
Melakukan eksplorasi data, pembersihan data (*data cleaning*), penanganan nilai kosong dan duplikasi, serta penerapan teknik **Transformasi Log (Log Transformation)** untuk mengatasi *outlier* dan mengurangi kemiringan data (*skewness*) pada dataset transaksi penjualan Amazon.

## Problem Statement
Menganalisis data mentah (*raw data*) ritel sering kali terkendala oleh adanya *error*, nilai yang hilang, duplikasi, inkonsistensi format, hingga *outlier* ekstrem pada kolom *Sales*, *Quantity*, dan *Profit*[cite: 92]. Jika dibiarkan, anomali ini dapat mendistorsi hasil analisis statistik dan merugikan pengambilan keputusan perusahaan[cite: 92].

## Data Understanding & Exploration
- **Sumber Data:** Dataset transaksi penjualan Amazon (diambil dari Google Drive)[cite: 93].
- **Format File:** Excel / CSV[cite: 93].
- **Ukuran Dataset:** 3.203 baris × 10 kolom[cite: 93].
- **Kolom Utama:** `Order ID`, `Order Date`, `Ship Date`, `EmailID`, `Geography`, `Category`, `Product Name`, `Sales`, `Quantity`, `Profit`[cite: 93].
- **Identifikasi Masalah:** Ditemukan adanya *outlier* yang cukup signifikan pada kolom *Sales*, *Quantity*, dan *Profit*[cite: 93].

## Data Preparation & Cleaning
- **Missing Value:** Pengecekan menggunakan metode `.isnull().sum()` menunjukkan **tidak ada missing value (0)** pada seluruh kolom[cite: 94].
- **Duplikasi:** Pengecekan menggunakan metode `.duplicated().sum()` menunjukkan **tidak ada data terduplikasi (0%)**[cite: 95].
- **Konsistensi Format:** Berhasil memeriksa keunikan nilai (*unique*) pada kolom *Order ID*, tanggal pesanan/pengiriman, *EmailID*, wilayah (*Geography*), kategori, hingga nama produk; tidak ditemukan adanya kesalahan ketik (*typo*)[cite: 96, 97, 98, 99, 100, 101, 102].
- **Deteksi Outlier (Z-Score > 2):**
  - **Sales:** 106 outlier (3.31%), didominasi oleh kategori *Tables* (20 item)[cite: 104].
  - **Quantity:** 145 outlier (4.53%), didominasi oleh kategori *Binders* (23 item)[cite: 106].
  - **Profit:** 59 outlier (1.84%), didominasi oleh kategori *Copiers* (13 item)[cite: 108].

## Outlier Treatment (Log Transformation)
Untuk mengatasi *outlier* dan menormalkan distribusi data yang memiliki *skewness* tinggi, dilakukan pembuatan kolom baru menggunakan fungsi **Transformasi Log (`np.log`)**:
- **`Sales_Log`**: Menstabilkan distribusi nilai penjualan yang memiliki rentang ekstrem[cite: 109].
- **`Quantity_Log`**: Menormalkan variasi jumlah kuantitas produk yang terjual[cite: 110].
- **`Profit_Log`**: Menangani anomali keuntungan/kerugian ekstrem agar lebih seimbang untuk analisis lanjutan[cite: 111].

## Visualization & Output
- Tabel hasil transformasi log membuktikan bahwa data *Sales*, *Quantity*, dan *Profit* kini menjadi jauh lebih stabil[cite: 112].
- Data yang dinormalisasi siap digunakan untuk pemodelan statistik tingkat lanjut seperti analisis regresi atau *clustering*[cite: 112].

## Conclusion
- Pembersihan data dan penanganan *outlier* melalui transformasi log sangat krusial agar data penjualan yang bervariasi ekstrem tidak menyesatkan analisis bisnis[cite: 92, 112].
- Produk yang terlihat laris namun mendatangkan kerugian harus dipantau ketat terkait struktur harga dan biaya operasionalnya[cite: 113].

## Recommendation
- Melakukan pemantauan rutin terhadap metrik *Sales*, *Profit*, dan *Outlier* untuk mengevaluasi produk yang bermasalah (laris tapi merugikan) secara berkala[cite: 113].
- Mengimplementasikan dasbor interaktif untuk memantau performa penjualan dan anomali data secara real-time guna mendukung pengambilan keputusan berbasis data (*data-driven decision making*)[cite: 113].

## Tools yang Digunakan
Python (Pandas, NumPy, Z-Score, Matplotlib, Seaborn) · Log Transformation · Data Cleaning & Exploratory Data Analysis (EDA)

---
*Bagian dari Portofolio Graphic Design & Data Analytics Career Accelerator — Tempat Belajar (2026)*  
*Disusun oleh: Raka Dewa Dipa Mahesa Arsandy*
