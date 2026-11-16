# Laporan Singkat Praktikum Pertemuan 6
## Topik: Activity Diagram (Dari Skenario ke Alur Aktivitas)

### 1. Gambaran Umum
Praktikum ini berfokus pada pembuatan **Activity Diagram** yang diturunkan langsung dari tabel skenario Pertemuan 5. Jika skenario berisi langkah-langkah kegiatan, maka Activity Diagram memvisualisasikan langkah tersebut menjadi sebuah alur kerja (workflow) yang utuh dari awal hingga akhir.

### 2. Konsep Utama yang Dipelajari
Materi ini memperkenalkan sembilan unsur dasar UML yang wajib digunakan:
*   **Initial Node & Activity Final Node:** Titik mulai dan titik akhir alur (tepat satu titik awal, minimal satu titik akhir).
*   **Action:** Satu langkah kegiatan yang diambil dari tabel skenario (ditulis dengan kata kerja + objek).
*   **Control Flow:** Panah yang menghubungkan antar-action.
*   **Decision & Merge:** Titik percabangan keputusan (wajib memiliki *guard* atau syarat, misal `[tersedia]`) dan titik penggabungnya kembali.
*   **Fork & Join:** Digunakan berpasangan untuk membagi alur menjadi proses paralel (berjalan bersamaan) dan menyatukannya kembali.
*   **Swimlane (Partisi):** Kolom yang membatasi tugas berdasarkan aktor (misal: Mahasiswa, Sistem, Petugas).

### 3. Aturan Penting dalam Menggambar
*   Setiap cabang keputusan (Decision) harus memiliki *guard* yang jelas dan saling lepas.
*   Fork harus selalu disatukan dengan Join, bukan dengan Merge.
*   Action aktor manusia diletakkan di swimlane aktor tersebut, sedangkan respon sistem diletakkan di swimlane "Sistem".
*   Alur diagram harus bisa dilacak kembali ke langkah pada tabel skenario Pertemuan 5.

### 4. Tugas dan Deliverables
*   **Studi Kasus LAB:** Membuat **7 Activity Diagram** (Peminjaman, Pengembalian, Lihat Ketersediaan, Kelola Data, Cetak Bukti, Proses Keputusan, dan Lihat Laporan). Diagram Keputusan dikerjakan secara mandiri.
*   **Tugas SIA:** Membuat **1 Activity Diagram** untuk proses Input Nilai sampai Lihat KHS (menggunakan swimlane Dosen, Admin Akademik, Sistem, dan Mahasiswa).
*   **Output:** File sumber `.drawio` beserta hasil ekspor `.png` yang disimpan di folder `04_model_analisis/P06/`.