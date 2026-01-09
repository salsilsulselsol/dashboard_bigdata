# 📈 Dashboard Analitik Saham (Big Data)

![Laravel](https://img.shields.io/badge/Laravel-12.0-red) ![PHP](https://img.shields.io/badge/PHP-8.2-blue) ![TailwindCSS](https://img.shields.io/badge/Tailwind-v4-38B2AC)

Aplikasi web ini berfungsi sebagai **Frontend** untuk menyajikan data analitik saham, laporan keuangan, dan berita emiten kepada investor. Proyek ini dibangun untuk memenuhi visi *Single Source of Truth*, mengintegrasikan berbagai data fundamental yang biasanya terpisah-pisah.

Repository ini adalah bagian antarmuka dari sistem Big Data. Backend pengolahan data ("Dapur") dapat ditemukan di:
🔗 **[salsilsulselsol/Full-Docker-ETL](https://github.com/salsilsulselsol/Full-Docker-ETL)**

## 🚀 Fitur Utama

Berdasarkan arsitektur *decoupled*, aplikasi ini berfokus pada pengalaman pengguna dan interaktivitas:

* **Grafik Saham Interaktif:** Visualisasi pergerakan harga historis menggunakan library charting dinamis.
* **Laporan Keuangan Dinamis:** Filter data fundamental berdasarkan Tahun dan Periode Triwulan (Q1-Q4) yang terhubung langsung ke *Data Warehouse* MongoDB via API.
* **Portal Berita (Iqplus):** Tampilan berita dengan layout *masonry* dan pencarian *real-time* tanpa refresh halaman (AJAX).
* **Daftar Emiten Terintegrasi:** Membaca dan menampilkan data emiten dari file Excel/CSV menggunakan `PhpSpreadsheet`.

## 🏗️ Arsitektur Sistem

Sistem ini menggunakan pendekatan **Decoupled Architecture**:

1.  **Frontend (Repo ini):** Laravel 12 bertindak sebagai klien yang meminta data.
2.  **API Layer:** Python Flask (berjalan di repo [Full-Docker-ETL](https://github.com/salsilsulselsol/Full-Docker-ETL)).
3.  **Database:** MongoDB (menyimpan hasil olahan ETL: `Yfinance_Load`, `idx_financial_data`, `Iqplus`).

**Alur Data:**
`Browser (User/AJAX)` ➡️ `Laravel Controller` ➡️ `Flask API` ➡️ `MongoDB`

## 🛠️ Teknologi yang Digunakan

* **Framework:** Laravel 12 (PHP 8.2)
* **Styling:** Tailwind CSS v4
* **Build Tool:** Vite
* **Interaktivitas:** jQuery / Axios (AJAX Request)
* **Libraries:** `phpoffice/phpspreadsheet` (Excel Parsing)

## ⚙️ Cara Instalasi & Menjalankan

Pastikan backend [Full-Docker-ETL](https://github.com/salsilsulselsol/Full-Docker-ETL) (API Flask & MongoDB) sudah berjalan agar data dapat tampil.

1.  **Clone Repository**
    ```bash
    git clone https://github.com/salsilsulselsol/dashboard_bigdata.git
    cd dashboard_bigdata
    ```

2.  **Install Dependencies**
    ```bash
    composer install
    npm install
    ```

3.  **Konfigurasi Environment**
    Salin file `.env` dan sesuaikan konfigurasi (terutama URL API Flask jika berbeda dari default).
    ```bash
    cp .env.example .env
    php artisan key:generate
    ```

4.  **Jalankan Server**
    ```bash
    npm run dev
    # Buka terminal baru
    php artisan serve
    ```

5.  **Akses Aplikasi**
    Buka `http://localhost:8000` di browser Anda.

## 📂 Struktur Folder Penting

* `app/Http/Controllers/`: Logika penghubung ke API Flask (`FinancialReportController`, `NewsController`, `GrafikController`).
* `resources/views/`: Antarmuka pengguna (Blade Templates).
* `routes/web.php`: Definisi endpoint aplikasi.

## 👥 Tim Pengembang

Proyek ini dikerjakan untuk memenuhi tugas akhir mata kuliah Big Data.
* **Backend & DevOps:** [Lihat Repo ETL](https://github.com/salsilsulselsol/Full-Docker-ETL)

---
*Catatan: Proyek ini dikembangkan sebagai demonstrasi integrasi sistem end-to-end dari ETL hingga visualisasi data.*
