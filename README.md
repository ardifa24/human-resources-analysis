# Proyek Akhir: Menyelesaikan Permasalahan Human Resource

## Business Understanding

Jaya Jaya Maju merupakan salah satu perusahaan multinasional yang telah berdiri sejak tahun 2000 dan memiliki lebih dari 1000 karyawan. Meskipun telah menjadi perusahaan yang cukup besar, departemen HR memiliki permasalahan dalam mengelola karyawan, sehingga berimbas pada tingginya attrition rate lebih dari 10%. Permasalahan ini dapat mempengaruhi produktivitas perusahaan dan biaya yang dikeluarkan untuk rekrutmen serta pelatihan karyawan baru.

### Permasalahan Bisnis
Tingkat attrition rate Jaya Jaya Maju saat ini berada di angka 16,9%, sebuah kondisi yang tidak dapat diabaikan mengingat dampaknya terhadap tiga aspek utama, yaitu aspek finansial, produktivitas, dan jangka panjang.
Dari aspek finansial, setiap karyawan yang resign menambah beban biaya rekrutmen, seleksi, dan pelatihan karyawan baru, yang secara akumulatif membebani anggaran operasional. Dari aspek produktivitas, turnover yang terus menerus mengganggu kestabilan tim, memperlambat penyelesaian proyek, serta membebani karyawan yang tersisa dengan beban kerja tambahan selama masa transisi pencarian pengganti. Serta dari aspek jangka panjang berisiko hilangnya institutional knowledge dari karyawan berpengalaman,serta menurunkan moral dan engagement karyawan yang bertahan.
Apabila permasalahan ini tidak segera ditangani, attrition rate berisiko terus meningkat dan berdampak pada menurunnya stabilitas operasional serta daya saing perusahaan secara berkelanjutan.

### Cakupan Proyek

- **Data Understanding & Cleaning:** Eksplorasi struktur data karyawan dan pembersihan data agar siap dianalisis.
- **Exploratory Data Analysis (EDA):** Analisis distribusi variabel numerik dan kategorikal, serta hubungan masing-masing variabel terhadap attrition.
- **Machine Learning Modeling:** Membangun model klasifikasi (Logistic Regression, Random Forest, Gradient Boosting, XGBoost) untuk memprediksi risiko attrition karyawan, dilengkapi feature importance untuk mengidentifikasi faktor paling berpengaruh.
- **Business Dashboard:** Menyusun dashboard visual interaktif yang dapat digunakan tim HR untuk memonitor kondisi attrition secara berkelanjutan.

### Persiapan

Sumber data: Dataset yang digunakan dalam proyek ini adalah **[Dataset Karyawan Jaya Jaya Maju](https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee)**, sesuai dengan instruksi dari submission proyek ini.

Setup environment:

1. Buat Python Virtual Environment
   ```bash
   virtualenv venv
   ```

2. Aktifkan virtual Environment
   ```bash
   venv\Scripts\activate
   ```

4. Install semua requirements di dalam file "requirements.txt"
   ```bash
   pip install -r requirements.txt
   ```

5. Eksekusi Script Prediksi :
    ```bash
    python prediction.py
    ```

## Business Dashboard

Dashboard HR Analytics ini dirancang menggunakan Looker Studio untuk memberikan gambaran menyeluruh mengenai kondisi attrition karyawan secara visual dan interaktif, sehingga tim HR dapat memantau serta menganalisis pola turnover tanpa perlu membuka data mentah atau notebook analisis.

![Dashboard](Human-Resorces-Dashboard.png)

**Fitur Filter Interaktif**
Dashboard dilengkapi filter *Department* dan *Job Role* di bagian kiri atas, memungkinkan pengguna memfokuskan analisis pada departemen atau posisi pekerjaan tertentu secara dinamis.

**Ringkasan Metrik Utama (Summary Cards)**
Bagian atas dashboard menampilkan lima metrik kunci: Total Employees (1.058), Attrition Rate (16,9%), Resigned Employees (179), Active Employees (879), dan Average Age (37,06), memberikan gambaran cepat kondisi keseluruhan tenaga kerja.

**Analisis Attrition Berdasarkan Profil Karyawan**
- **Attrition by Age Group:** Menampilkan distribusi resign berdasarkan kelompok usia (18-25 hingga 56+)
- **Attrition Rate by Job Level:** Membandingkan tingkat attrition antar level jabatan (1-5)
- **Attrition Rate by Overtime:** Menunjukkan perbedaan signifikan attrition antara karyawan yang lembur dan tidak

**Analisis Mendalam per Job Role**
- **Attrition Rate by Job Role:** Bar chart horizontal yang menampilkan tingkat attrition di setiap posisi pekerjaan
- **Attrition by Job Role & Income Group:** Tabel heatmap yang memetakan jumlah karyawan resign berdasarkan kombinasi job role dan kelompok penghasilan (<3k, 3k-6k, 6k-10k, >10k)
- **Attrition by Job Role & Tenure Group:** Tabel heatmap serupa yang memetakan resign berdasarkan job role dan Kelompok Masa Kerja (0-2 th, 3-5 th, 6-10 th, >10 th)

**Perbandingan Karyawan Aktif vs Resign**
- **Resigned vs Active Employee by Department:** Horizontal bar chart perbandingan jumlah karyawan aktif dan resign per departemen (Research & Development, Sales, Human Resources)
- **Resigned vs Active Employees by Marital Status:** Perbandingan berdasarkan status pernikahan (Single, Married, Divorced)
- **Resigned vs Active Employees by Gender:** Perbandingan berdasarkan gender (Male, Female)

Dengan kombinasi filter interaktif, ringkasan metrik, dan berbagai breakdown visual ini, dashboard memungkinkan tim HR melakukan monitoring attrition secara mandiri dan berkelanjutan, sekaligus mengidentifikasi segmen karyawan berisiko tinggi untuk ditindaklanjuti lebih cepat.

🔗 Link akses dashboard: *[HR Analytics Dashboard](https://datastudio.google.com/reporting/93541d95-eb4d-4d19-88b3-a0b3b038a579)*

## Conclusion

Berdasarkan hasil analisis, tingginya attrition rate (16,9%) pada perusahaan dapat dijelaskan melalui tiga kategori akar masalah utama:

- **Beban Kerja & Tekanan Keseimbangan Kerja**, OverTime menjadi prediktor paling dominan di seluruh metode analisis (Cramér's V=0,253; feature importance tertinggi), dengan attrition rate karyawan lembur mencapai 31,9% dibanding 10,8% pada yang tidak lembur. Faktor ini diperkuat oleh BusinessTravel (24,9% vs 10,3%) dan WorkLifeBalance rendah (32,1%), yang secara konsisten menunjukkan bahwa tekanan kerja berlebih menjadi pemicu resign yang paling cepat berdampak.

- **Kesenjangan Tahap Karier & Struktur Posisi**, Kelompok ini memiliki sinyal statistik terbanyak dan terkuat, ditandai dengan korelasi point-biserial tertinggi pada Age, TotalWorkingYears, dan JobLevel, serta Cramér's V tinggi pada JobRole (0,251) dan MaritalStatus (0,189). Karyawan muda, junior, dan berada di posisi entry-level/operasional (seperti Sales Representative, 43,1%) jauh lebih rentan keluar dibanding posisi senior/manajerial (Research Director, 3,2%), mengindikasikan adanya kesenjangan struktural dalam jenjang karier yang perlu ditangani.

- **Kompensasi & Pengakuan Finansial**, MonthlyIncome dan StockOptionLevel terbukti signifikan secara statistik, meski dengan magnitude korelasi yang lebih moderat dibanding dua kategori sebelumnya. Rendahnya kompensasi dan insentif finansial pada level bawah mengindikasikan adanya gap antara kontribusi dan pengakuan yang diterima karyawan, yang berpotensi memperkuat risiko attrition di kategori Career Stage.

Ketiga faktor ini saling terkait dan saling memperkuat, karyawan pada tahap karier awal cenderung menerima kompensasi lebih rendah dan lebih rentan terhadap tekanan kerja, sehingga strategi retensi yang efektif perlu menyasar ketiganya secara bersamaan, bukan secara terpisah.

### Rekomendasi Action Items (Optional)

**1. Kontrol Lembur & Penambahan Headcount:** Berdasarkan analisis, OverTime merupakan variabel dengan feature importance tertinggi (39,56% berbasis impurity; 15,82% berbasis permutation) dan signifikan secara statistik (Cramér's V=0,253). Karyawan yang lembur memiliki attrition rate 31,9%, hampir tiga kali lipat dibanding yang tidak lembur (10,8%), dengan konsentrasi tertinggi pada Sales Representative (43,1%) dan Laboratory Technician (26,1%). Oleh karena itu, perusahaan perlu melakukan audit headcount pada kedua role tersebut dalam 1 bulan ke depan untuk menentukan kebutuhan tambahan tenaga kerja minimal 15–20% dari jumlah saat ini, menerapkan batas maksimal lembur 10 jam/minggu dengan kompensasi lembur atau cuti pengganti wajib, serta memantau rate lembur bulanan sebagai KPI tim People Operations.

**2. Percepatan Jalur Karier untuk Karyawan Entry-Level:** Berdasarkan Analisis, Karyawan pada JobLevel 1 (entry-level) dan berusia di bawah 30 tahun jauh lebih rentan resign dibanding level manajerial ke atas (Research Director hanya 3,2%). Oleh karena itu, perusahaan dapat membangun jalur promosi terstruktur dengan milestone yang jelas pada bulan ke-12, 24, dan 36 masa kerja untuk JobLevel 1–2, mengalokasikan budget mentoring/coaching khusus untuk karyawan berusia di bawah 30 tahun, serta mewajibkan stay interview pada bulan ke-6 dan ke-18 masa kerja untuk mendeteksi risiko resign secara dini.
