# P05 — Lembar Skenario Studi Kasus LAB: Peminjaman dan Pengembalian Peralatan Laboratorium

| Metadata | Keterangan |
|---|---|
| Mata kuliah | Praktikum Analisis dan Desain Berorientasi Objek |
| Pertemuan | 5 — Skenario use case: dari diagram ke langkah kegiatan |
| Kasus | Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus |
| Nama / NIM | Muhammad Iqbal Syarief / 2406114 |
| Versi | v01 |
| Tanggal | 30 Oktober 2026 |
| Dokumen acuan | `04_model_analisis/P04/LAB/P04_2406114_LAB_usecase_v01.drawio` (tidak diubah) |
| Kebutuhan acuan | LAB-R01 sampai LAB-R11 (Jobsheet Pertemuan 4, Tabel 4.5) |

Dokumen ini memuat telaah kedua belas tabel skenario studi kasus LAB terhadap
diagram kumulatif Pertemuan 4. Setiap tabel diberi kolom **Penelusuran relasi**
yang menyebut asosiasi, `«include»`, `«extend»`, `generalization`, atau
`realization` yang menjadi dasar langkah tersebut. Tidak ada use case, aktor,
atau kebutuhan baru pada pertemuan ini; format dan isi langkah mengikuti
Jobsheet Pertemuan 5.

## 1. Indeks tabel skenario

| No. | Tabel jobsheet | ID | Nama use case | Aktor |
|---|---|---|---|---|
| 1 | Tabel 5.1 | LAB-UC03 | Ajukan Peminjaman | Peminjam (Mahasiswa, Dosen) |
| 2 | Tabel 5.3 | LAB-UC01 | Lihat Ketersediaan Peralatan | Peminjam (Mahasiswa, Dosen) |
| 3 | Tabel 5.4 | LAB-UC04 | Periksa Ketersediaan | Peminjam (di dalam UC03) |
| 4 | Tabel 5.5 | LAB-UC05 | Cetak Bukti Pengajuan | Mahasiswa |
| 5 | Tabel 5.6 | LAB-UC02 | Kelola Data Peralatan | Petugas Laboratorium |
| 6 | Tabel 5.7 | LAB-UC08 | Tambah Data Peralatan | Petugas Laboratorium |
| 7 | Tabel 5.8 | LAB-UC09 | Ubah Data Peralatan | Petugas Laboratorium |
| 8 | Tabel 5.9 | LAB-UC10 | Hapus Data Peralatan | Petugas Laboratorium |
| 9 | Tabel 5.10 | LAB-UC06 | Proses Keputusan Peminjaman | Petugas Laboratorium |
| 10 | Tabel 5.11 | LAB-UC07 | Lihat Laporan Peminjaman | Kepala Laboratorium |
| 11 | Tabel 5.12 | LAB-UC11 | Catat Pengembalian Peralatan | Petugas Laboratorium |
| 12 | Tabel 5.13 | LAB-UC12 | Periksa Kondisi Peralatan | Petugas Laboratorium (di dalam UC11) |

## 2. Tabel skenario

### Tabel 5.1 — LAB-UC03 Ajukan Peminjaman

| Nama use case | LAB-UC03 Ajukan Peminjaman |
|---|---|
| Aktor | Peminjam (berlaku untuk Mahasiswa dan Dosen) |
| Tujuan | Pengajuan peminjaman tercatat dan dapat diproses oleh petugas |
| Deskripsi | Peminjam memilih peralatan yang tersedia, mengisi data peminjaman, dan mengirim pengajuan |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Peminjam memilih peralatan yang akan dipinjam | | Asosiasi Peminjam — LAB-UC03 |
| | 2. Sistem menjalankan Periksa Ketersediaan (lihat Tabel 5.4 LAB-UC04) | `«include»` LAB-UC03 → LAB-UC04 |
| 3. Peminjam mengisi tanggal pinjam, tanggal rencana kembali, dan keperluan peminjaman | | Langkah alur utama UC03 |
| | 4. Sistem memeriksa kelengkapan isian dan menampilkan ringkasan pengajuan | Langkah alur utama UC03 |
| 5. Peminjam mengirim pengajuan | | Langkah alur utama UC03 |
| | 6. Sistem menyimpan pengajuan dengan status Menunggu Keputusan dan menampilkan nomor pengajuan | Pascakondisi berhasil UC03 |
| **Skenario Alternative** | | |
| 7. Peralatan yang dipilih tidak tersedia (cabang dari langkah 2) | | Hasil gagal `«include»` LAB-UC04 |
| | 8. Sistem menampilkan pesan peralatan tidak tersedia dan pengajuan tidak dilanjutkan | Alur alternatif UC03 |
| 9. Isian pengajuan tidak lengkap (cabang dari langkah 4) | | Langkah pemeriksaan kelengkapan |
| | 10. Sistem menampilkan pesan isian belum lengkap dan meminta peminjam melengkapi isian | Alur alternatif UC03 |
| 11. Peminjam memilih cetak bukti, condition `[mahasiswa memilih cetak]`, extension point Bukti pengajuan tersedia (lihat Tabel 5.5 LAB-UC05) | | `«extend»` LAB-UC05 → LAB-UC03 |
| | 12. Sistem menampilkan bukti pengajuan dengan nomor pengajuan sesuai Tabel 5.5 LAB-UC05 | `«extend»` LAB-UC05 → LAB-UC03 |
| **Skenario Akhir** | Use case selesai jika pengajuan tersimpan dengan status Menunggu Keputusan; jika peralatan tidak tersedia atau isian tidak lengkap, pengajuan tidak tersimpan dan peminjam kembali ke daftar peralatan atau melengkapi isian. | — |

Keterangan: use case ini direalisasikan oleh collaboration **LAB-CO01 Ajukan
Peminjaman**; collaboration tidak diberi langkah kegiatan pada tabel ini.

### Tabel 5.3 — LAB-UC01 Lihat Ketersediaan Peralatan

| Nama use case | LAB-UC01 Lihat Ketersediaan Peralatan |
|---|---|
| Aktor | Peminjam (berlaku untuk Mahasiswa dan Dosen) |
| Tujuan | Peminjam dapat mengetahui peralatan yang tersedia sebelum mengajukan peminjaman |
| Deskripsi | Peminjam membuka fungsi ketersediaan dan melihat daftar peralatan beserta status ketersediaannya |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Peminjam membuka fungsi Lihat Ketersediaan Peralatan | | Asosiasi Peminjam — LAB-UC01 (diwarisi Mahasiswa dan Dosen) |
| | 2. Sistem menampilkan daftar peralatan beserta status ketersediaannya | Asosiasi Peminjam — LAB-UC01 |
| **Skenario Alternative** | | |
| 3. Tidak ada peralatan yang tersedia pada daftar (cabang dari langkah 2) | | Alur alternatif UC01 |
| | 4. Sistem menampilkan pesan tidak ada peralatan yang tersedia | Alur alternatif UC01 |
| **Skenario Akhir** | Use case selesai jika daftar peralatan beserta status ketersediaannya ditampilkan; jika tidak ada peralatan yang tersedia, use case selesai dengan pesan tersebut. | — |

### Tabel 5.4 — LAB-UC04 Periksa Ketersediaan

| Nama use case | LAB-UC04 Periksa Ketersediaan |
|---|---|
| Aktor | Peminjam (berjalan di dalam LAB-UC03 Ajukan Peminjaman) |
| Tujuan | Ketersediaan peralatan yang dipilih terperiksa sebelum pengajuan disimpan |
| Deskripsi | Sistem memeriksa jumlah dan status peralatan yang dipilih peminjam dan menyampaikan hasilnya kepada alur pengajuan; tidak mempunyai interaksi langsung dengan aktor |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Alur pengajuan memanggil Periksa Ketersediaan dengan peralatan yang dipilih | | `«include»` LAB-UC03 → LAB-UC04 |
| | 2. Sistem memeriksa jumlah dan status peralatan tersebut | `«include»` LAB-UC03 → LAB-UC04 |
| | 3. Sistem menyatakan peralatan tersedia | Hasil include |
| | 4. Alur pengajuan melanjutkan penyimpanan pengajuan | Kembali ke Tabel 5.1 langkah 3 |
| **Skenario Alternative** | | |
| 5. Peralatan tidak tersedia atau jumlah tidak mencukupi (cabang dari langkah 2) | | Alur alternatif UC04 |
| | 6. Sistem menyampaikan hasil tidak tersedia sehingga alur pengajuan berhenti | Kembali ke Tabel 5.1 langkah 7 |
| **Skenario Akhir** | Use case selesai jika hasil pemeriksaan tersampaikan kepada alur pengajuan; hasil tersedia melanjutkan pengajuan, hasil tidak tersedia menghentikan pengajuan. | — |

### Tabel 5.5 — LAB-UC05 Cetak Bukti Pengajuan

| Nama use case | LAB-UC05 Cetak Bukti Pengajuan |
|---|---|
| Aktor | Mahasiswa (asosiasi khusus) |
| Tujuan | Bukti pengajuan tercetak sebagai tambahan bersyarat pada pengajuan |
| Deskripsi | Mahasiswa yang memilih cetak pada konfirmasi pengajuan menerima bukti pengajuan dengan nomor pengajuan; berlaku dengan condition `[mahasiswa memilih cetak]` dan extension point Bukti pengajuan tersedia pada LAB-UC03 |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Mahasiswa memilih cetak bukti pada konfirmasi pengajuan | | Asosiasi khusus Mahasiswa — LAB-UC05 |
| | 2. Sistem menampilkan bukti pengajuan dengan nomor pengajuan dan status Menunggu Keputusan | `«extend»` LAB-UC05 → LAB-UC03 |
| 3. Mahasiswa mengonfirmasi pencetakan | | Langkah alur utama UC05 |
| | 4. Sistem mencetak bukti pengajuan | Langkah alur utama UC05 |
| **Skenario Alternative** | | |
| 5. Mahasiswa tidak memilih cetak (cabang dari langkah 1) | | Condition tidak terpenuhi |
| | 6. Sistem menutup konfirmasi tanpa mencetak bukti dan pengajuan tetap tersimpan | Use case dasar tetap berhasil |
| **Skenario Akhir** | Use case selesai jika bukti pengajuan tercetak; jika mahasiswa tidak memilih cetak, pengajuan tetap selesai tanpa bukti cetak. | — |

### Tabel 5.6 — LAB-UC02 Kelola Data Peralatan

| Nama use case | LAB-UC02 Kelola Data Peralatan |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Data peralatan terkelola melalui satu fungsi pengelolaan bersama |
| Deskripsi | Petugas membuka fungsi pengelolaan data peralatan, memilih bentuk pengelolaan, dan menyimpan perubahan; bentuk tambah, ubah, dan hapus dijabarkan pada tabel khususnya |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas membuka fungsi Kelola Data Peralatan | | Asosiasi Petugas Laboratorium — LAB-UC02 |
| | 2. Sistem menampilkan daftar data peralatan | Asosiasi Petugas Laboratorium — LAB-UC02 |
| 3. Petugas memilih bentuk pengelolaan, yaitu tambah, ubah, atau hapus | | Use case umum bagi LAB-UC08, LAB-UC09, LAB-UC10 |
| | 4. Sistem menampilkan formulir sesuai bentuk pengelolaan yang dipilih | Generalization use case |
| 5. Petugas mengisi atau mengonfirmasi data | | Langkah alur utama UC02 |
| | 6. Sistem memeriksa kelengkapan dan keabsahan data | Langkah alur utama UC02 |
| 7. Petugas menyimpan perubahan | | Langkah alur utama UC02 |
| | 8. Sistem menyimpan perubahan dan menampilkan konfirmasi | Pascakondisi berhasil UC02 |
| **Skenario Alternative** | | |
| 9. Data tidak lengkap atau tidak sah (cabang dari langkah 6) | | Alur alternatif UC02 |
| | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data | Alur alternatif UC02 |
| **Skenario Akhir** | Use case selesai jika perubahan data peralatan tersimpan; jika data tidak lengkap atau tidak sah, perubahan tidak tersimpan. | — |

### Tabel 5.7 — LAB-UC08 Tambah Data Peralatan

| Nama use case | LAB-UC08 Tambah Data Peralatan |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Data peralatan baru tersimpan sebagai bentuk khusus dari pengelolaan data peralatan |
| Deskripsi | Petugas mengisi data peralatan baru dan menyimpan data tersebut; langkah bersama mengikuti Tabel 5.6 LAB-UC02 |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas membuka fungsi Tambah Data Peralatan | | Generalization LAB-UC08 → LAB-UC02 |
| | 2. Sistem menampilkan formulir data peralatan baru | Generalization LAB-UC08 → LAB-UC02 |
| 3. Petugas mengisi data peralatan baru | | Perilaku pembeda: data baru |
| | 4. Sistem memeriksa kelengkapan data | Langkah bersama Tabel 5.6 |
| 5. Petugas menyimpan data | | Langkah bersama Tabel 5.6 |
| | 6. Sistem menyimpan data peralatan baru dan menampilkan konfirmasi | Perilaku pembeda: data baru tersimpan |
| **Skenario Alternative** | | |
| 7. Data tidak lengkap (cabang dari langkah 4) | | Alur alternatif UC08 |
| | 8. Sistem menolak penyimpanan dan meminta petugas melengkapi data | Alur alternatif UC08 |
| **Skenario Akhir** | Use case selesai jika data peralatan baru tersimpan; jika data tidak lengkap, data tidak tersimpan. | — |

Keterangan: use case khusus dari **LAB-UC02 Kelola Data Peralatan**. Perilaku
pembeda: data baru tersimpan. Langkah bersama mengikuti Tabel 5.6 LAB-UC02.

### Tabel 5.8 — LAB-UC09 Ubah Data Peralatan

| Nama use case | LAB-UC09 Ubah Data Peralatan |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Data peralatan berubah sebagai bentuk khusus dari pengelolaan data peralatan |
| Deskripsi | Petugas memilih data peralatan, mengubah datanya, dan menyimpan perubahan; langkah bersama mengikuti Tabel 5.6 LAB-UC02 |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas memilih data peralatan yang akan diubah | | Generalization LAB-UC09 → LAB-UC02 |
| | 2. Sistem menampilkan data peralatan saat ini | Generalization LAB-UC09 → LAB-UC02 |
| 3. Petugas mengubah data peralatan | | Perilaku pembeda: data berubah |
| | 4. Sistem memeriksa perubahan data | Langkah bersama Tabel 5.6 |
| 5. Petugas menyimpan perubahan | | Langkah bersama Tabel 5.6 |
| | 6. Sistem menyimpan data yang diubah dan menampilkan konfirmasi | Perilaku pembeda: data berubah |
| **Skenario Alternative** | | |
| 7. Data peralatan tidak ditemukan (cabang dari langkah 2) | | Alur alternatif UC09 |
| | 8. Sistem menampilkan pesan data peralatan tidak ditemukan | Alur alternatif UC09 |
| **Skenario Akhir** | Use case selesai jika perubahan data peralatan tersimpan; jika data tidak ditemukan, perubahan tidak tersimpan. | — |

Keterangan: use case khusus dari **LAB-UC02 Kelola Data Peralatan**. Perilaku
pembeda: data peralatan berubah. Langkah bersama mengikuti Tabel 5.6.

### Tabel 5.9 — LAB-UC10 Hapus Data Peralatan

| Nama use case | LAB-UC10 Hapus Data Peralatan |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Data peralatan terhapus sebagai bentuk khusus dari pengelolaan data peralatan |
| Deskripsi | Petugas memilih data peralatan, mengonfirmasi penghapusan, dan sistem menghapus data tersebut; langkah bersama mengikuti Tabel 5.6 LAB-UC02 |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas memilih data peralatan yang akan dihapus | | Generalization LAB-UC10 → LAB-UC02 |
| | 2. Sistem memeriksa peralatan tidak sedang dipinjam dan tidak memiliki pengajuan aktif | Syarat hapus (LAB-R08) |
| 3. Petugas mengonfirmasi penghapusan | | Perilaku pembeda: data terhapus |
| | 4. Sistem menghapus data peralatan dan menampilkan konfirmasi penghapusan | Perilaku pembeda: data terhapus |
| **Skenario Alternative** | | |
| 5. Peralatan sedang dipinjam atau memiliki pengajuan aktif (cabang dari langkah 2) | | Alur alternatif UC10 |
| | 6. Sistem menolak penghapusan dan menampilkan pesan peralatan masih terpakai | Alur alternatif UC10 |
| **Skenario Akhir** | Use case selesai jika data peralatan terhapus; jika peralatan sedang dipinjam atau memiliki pengajuan aktif, data tidak terhapus. | — |

Keterangan: use case khusus dari **LAB-UC02 Kelola Data Peralatan**. Perilaku
pembeda: data peralatan terhapus dengan syarat peralatan tidak sedang dipinjam
dan tidak memiliki pengajuan aktif. Langkah bersama mengikuti Tabel 5.6.

### Tabel 5.10 — LAB-UC06 Proses Keputusan Peminjaman

| Nama use case | LAB-UC06 Proses Keputusan Peminjaman |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Pengajuan peminjaman mendapat keputusan setuju atau tolak |
| Deskripsi | Petugas memeriksa pengajuan berstatus Menunggu Keputusan, menetapkan persetujuan atau penolakan, dan sistem menyampaikan keputusan |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas membuka daftar pengajuan yang berstatus Menunggu Keputusan | | Asosiasi Petugas Laboratorium — LAB-UC06 |
| | 2. Sistem menampilkan daftar pengajuan tersebut | Asosiasi Petugas Laboratorium — LAB-UC06 |
| 3. Petugas memilih pengajuan dan menetapkan persetujuan | | Langkah alur utama UC06 |
| | 4. Sistem mengubah status pengajuan menjadi Disetujui dan menampilkan konfirmasi | Pascakondisi berhasil UC06 |
| **Skenario Alternative** | | |
| 5. Petugas menetapkan penolakan (cabang dari langkah 4) | | Alur alternatif UC06 |
| | 6. Sistem mengubah status pengajuan menjadi Ditolak dan menampilkan konfirmasi penolakan | Alur alternatif UC06 |
| 7. Pengajuan tidak ditemukan atau statusnya sudah berubah (cabang dari langkah 2) | | Alur alternatif UC06 |
| | 8. Sistem menampilkan pesan pengajuan tidak dapat diproses | Alur alternatif UC06 |
| **Skenario Akhir** | Use case selesai jika pengajuan berstatus Disetujui atau Ditolak; jika pengajuan tidak dapat diproses, status tidak berubah. | — |

### Tabel 5.11 — LAB-UC07 Lihat Laporan Peminjaman

| Nama use case | LAB-UC07 Lihat Laporan Peminjaman |
|---|---|
| Aktor | Kepala Laboratorium |
| Tujuan | Laporan peminjaman dapat dilihat oleh kepala laboratorium |
| Deskripsi | Kepala Laboratorium membuka fungsi laporan dan melihat laporan peminjaman pada periode yang dipilih |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Kepala Laboratorium membuka fungsi Lihat Laporan Peminjaman | | Asosiasi Kepala Laboratorium — LAB-UC07 |
| | 2. Sistem menampilkan daftar periode laporan | Asosiasi Kepala Laboratorium — LAB-UC07 |
| 3. Kepala Laboratorium memilih periode | | Langkah alur utama UC07 |
| | 4. Sistem menampilkan laporan peminjaman periode tersebut | Pascakondisi berhasil UC07 |
| **Skenario Alternative** | | |
| 5. Tidak ada data peminjaman pada periode yang dipilih (cabang dari langkah 4) | | Alur alternatif UC07 |
| | 6. Sistem menampilkan pesan tidak ada data peminjaman pada periode tersebut | Alur alternatif UC07 |
| **Skenario Akhir** | Use case selesai jika laporan periode yang dipilih ditampilkan; jika tidak ada data, use case selesai dengan pesan tersebut. | — |

Keterangan: satu-satunya use case aktor Kepala Laboratorium. Tabel ini berdiri
sendiri dan tidak memuat langkah `«include»`, `«extend»`, `generalization`,
maupun `realization`.

### Tabel 5.12 — LAB-UC11 Catat Pengembalian Peralatan

| Nama use case | LAB-UC11 Catat Pengembalian Peralatan |
|---|---|
| Aktor | Petugas Laboratorium |
| Tujuan | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui |
| Deskripsi | Petugas memilih peminjaman yang akan dikembalikan, mengonfirmasi alat yang kembali, dan menyimpan pencatatan. Prasyarat: peminjaman berstatus Dipinjam |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas memilih peminjaman yang akan dikembalikan | | Asosiasi Petugas Laboratorium — LAB-UC11 |
| | 2. Sistem menampilkan data peminjaman terpilih dan statusnya | Asosiasi Petugas Laboratorium — LAB-UC11 |
| 3. Petugas mengonfirmasi alat yang kembali dan jumlahnya | | Langkah alur utama UC11 |
| | 4. Sistem menampung konfirmasi petugas | Langkah alur utama UC11 |
| | 5. Sistem memeriksa status peminjaman harus Dipinjam | Prasyarat UC11 (LAB-R09) |
| | 6. Sistem menjalankan Periksa Kondisi Peralatan (lihat Tabel 5.13 LAB-UC12) | `«include»` LAB-UC11 → LAB-UC12 |
| 7. Petugas menyimpan pencatatan pengembalian | | Langkah alur utama UC11 |
| | 8. Sistem menyimpan tanggal kembali dan kondisi serta mengubah status peminjaman menjadi Selesai | Pascakondisi berhasil UC11 |
| 9. Petugas melihat konfirmasi | | Langkah alur utama UC11 |
| | 10. Sistem menampilkan ringkasan pengembalian | Langkah alur utama UC11 |
| **Skenario Alternative** | | |
| 11. Status bukan Dipinjam (cabang dari langkah 5) | | Alur alternatif UC11 |
| | 12. Sistem menolak pencatatan dan menampilkan status peminjaman saat ini | Pascakondisi gagal UC11 |
| 13. Kondisi Rusak Ringan atau Rusak Berat dicatat pada langkah 6 (cabang dari langkah 6) | | Hasil `«include»` LAB-UC12 |
| | 14. Sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan, dan pengembalian tetap tercatat tanpa denda | Alur alternatif UC11 (LAB-R10) |
| 15. Jumlah alat yang kembali tidak sesuai (cabang dari langkah 3) | | Alur alternatif UC11 |
| | 16. Sistem meminta petugas memeriksa kembali isian sebelum penyimpanan | Alur alternatif UC11 |
| **Skenario Akhir** | Use case selesai jika pengembalian tercatat dengan tanggal kembali dan kondisi peralatan serta status peminjaman menjadi Selesai; jika status bukan Dipinjam, tidak ada pengembalian baru yang tercatat dan status peminjaman tidak berubah. | — |

Keterangan: use case ini direalisasikan oleh collaboration **LAB-CO02 Catat
Pengembalian Peralatan**, tanpa langkah kegiatan sendiri. Keterlambatan dan denda
belum dimodelkan dan tidak menimbulkan aturan tambahan pada tabel ini.

### Tabel 5.13 — LAB-UC12 Periksa Kondisi Peralatan

| Nama use case | LAB-UC12 Periksa Kondisi Peralatan |
|---|---|
| Aktor | Petugas Laboratorium (berjalan di dalam LAB-UC11) |
| Tujuan | Kondisi peralatan yang dikembalikan tercatat pada data peralatan |
| Deskripsi | Petugas memeriksa kondisi fisik peralatan yang baru dikembalikan dan menetapkan status kondisinya. Use case ini dipanggil dari LAB-UC11 melalui relasi `«include»` sehingga tidak memiliki aktor pemicu sendiri |

| Kegiatan | Respon sistem | Penelusuran relasi |
|---|---|---|
| **Skenario Normal** | | |
| 1. Petugas mengamati kondisi fisik peralatan yang dikembalikan | | `«include»` LAB-UC11 → LAB-UC12 (langkah 6 Tabel 5.12) |
| 2. Petugas memeriksa kelengkapan aksesori dan jumlah alat | | Langkah alur utama UC12 |
| 3. Petugas menetapkan kondisi peralatan sebagai Baik, Rusak Ringan, atau Rusak Berat | | Langkah alur utama UC12 (LAB-R10) |
| | 4. Sistem menampung hasil pemeriksaan dan meneruskannya kembali ke LAB-UC11 | `«include»` LAB-UC11 → LAB-UC12 |
| **Skenario Alternative** | | |
| 5. Kondisi ditetapkan Rusak Ringan atau Rusak Berat (cabang dari langkah 3) | | Alur alternatif UC12 |
| | 6. Sistem menandai kondisi tersebut pada data peralatan sebagai dasar tindak lanjut Kepala Laboratorium | Pascakondisi UC12 (LAB-R10) |
| **Skenario Akhir** | Use case selesai jika kondisi peralatan tersimpan pada data peralatan dan hasilnya dikembalikan ke LAB-UC11 sebagai masukan langkah 8 Tabel 5.12. | — |

Keterangan: LAB-UC12 tidak berdiri sendiri. Karena relasinya `«include»`, use
case ini selalu dijalankan sebagai bagian dari LAB-UC11 dan bukan sebagai
skenario terpisah yang dipicu aktor. Sesuai Jobsheet Pertemuan 5, tabel ini
tidak memiliki `realization` tersendiri.

## 3. Rekap penelusuran relasi

| No. | Tabel | ID | Relasi yang ditelusur | Hasil penelusuran |
|---|---|---|---|---|
| 1 | Tabel 5.1 | LAB-UC03 | Asosiasi Peminjam (Mahasiswa, Dosen) — UC03; `«include»` UC03 → UC04 | Konsisten: kedua aktor Peminjam terhubung ke UC03, dan langkah 6 memanggil UC04 |
| 2 | Tabel 5.3 | LAB-UC01 | Asosiasi Peminjam — UC01 | Konsisten: UC01 hanya memiliki satu aktor, tanpa `«include»` |
| 3 | Tabel 5.4 | LAB-UC04 | `«include»` UC03 → UC04 | Konsisten: tabel tidak memberi aktor sendiri karena dipanggil dari UC03 |
| 4 | Tabel 5.5 | LAB-UC05 | Asosiasi Mahasiswa — UC05; `«extend»` UC05 → UC03 | Konsisten: UC05 memperluas UC03 dan hanya dimiliki Mahasiswa |
| 5 | Tabel 5.6 | LAB-UC02 | Asosiasi Petugas Laboratorium — UC02; `generalization` UC08, UC09, UC10 → UC02 | Konsisten: tiga use case khusus mewarisi langkah umum UC02 |
| 6 | Tabel 5.7 | LAB-UC08 | `generalization` UC08 → UC02 | Konsisten: tabel hanya memuat langkah tambah data |
| 7 | Tabel 5.8 | LAB-UC09 | `generalization` UC09 → UC02 | Konsisten: tabel hanya memuat langkah ubah data |
| 8 | Tabel 5.9 | LAB-UC10 | `generalization` UC10 → UC02 | Konsisten: tabel hanya memuat langkah hapus data |
| 9 | Tabel 5.10 | LAB-UC06 | Asosiasi Petugas Laboratorium — UC06 | Konsisten: UC06 tidak memiliki relasi `«include»` maupun `generalization` |
| 10 | Tabel 5.11 | LAB-UC07 | Asosiasi Kepala Laboratorium — UC07 | Konsisten: UC07 satu-satunya use case aktor Kepala Laboratorium |
| 11 | Tabel 5.12 | LAB-UC11 | Asosiasi Petugas Laboratorium — UC11; `«include»` UC11 → UC12; `realization` LAB-CO02 | Konsisten: langkah 6 memanggil UC12 dan seluruh langkah direalisasikan LAB-CO02 |
| 12 | Tabel 5.13 | LAB-UC12 | `«include»` UC11 → UC12 | Konsisten: UC12 tanpa aktor sendiri, hasilnya kembali ke UC11 |

Tidak ditemukan relasi pada diagram Pertemuan 4 yang belum terwakili di tabel,
dan tidak ada langkah tabel yang tidak memiliki dasar relasi. Use case UC13 pada
kasus SIA tidak termasuk lingkup dokumen LAB ini.

## 4. Checklist penilaian

| No. | Butir yang diperiksa | Status | Bukti |
|---|---|---|---|
| 1 | Kedua belas tabel skenario tersedia dan diberi nomor sesuai jobsheet | Terpenuhi | Tabel 5.1 serta 5.3 sampai 5.13 pada Bagian 2 |
| 2 | Setiap tabel memuat nama use case, aktor, tujuan, deskripsi, skenario normal, alternatif, dan skenario akhir | Terpenuhi | Format seragam pada 12 tabel |
| 3 | Langkah normal ditulis sebagai pasangan kegiatan aktor dan respon sistem | Terpenuhi | Kolom Kegiatan dan Respon sistem terisi bergantian |
| 4 | Langkah alternatif menyebut nomor langkah asal cabangnya | Terpenuhi | Contoh: langkah 11 Tabel 5.12 bercabang dari langkah 5 |
| 5 | Setiap tabel menyebut relasi diagram yang mendasari langkahnya | Terpenuhi | Kolom Penelusuran relasi pada 12 tabel dan Bagian 3 |
| 6 | Use case hasil `«include»` tidak diberi aktor pemicu sendiri | Terpenuhi | LAB-UC04 dan LAB-UC12 |
| 7 | Use case hasil `generalization` tidak mengulang langkah use case induk | Terpenuhi | LAB-UC08, LAB-UC09, LAB-UC10 terhadap LAB-UC02 |
| 8 | `«extend»` dijelaskan sebagai perluasan kondisional, bukan langkah wajib | Terpenuhi | Tabel 5.5 terhadap LAB-UC03 |
| 9 | Tidak ada use case, aktor, atau kebutuhan baru di luar Pertemuan 4 | Terpenuhi | Bagian 1 dan penutup Bagian 3 |
| 10 | Rujukan berkas acuan ditulis dengan nama berkas yang benar | Terpenuhi | Metadata dokumen menunjuk `P04_2406114_LAB_usecase_v01.drawio` |

Catatan: seluruh isi dokumen ini diturunkan dari Jobsheet Pertemuan 5 dan
diagram kumulatif Pertemuan 4. Berkas diagram tidak diubah pada pertemuan ini.
Dua hal belum dicakup karena tidak diminta jobsheet: aturan denda keterlambatan
pengembalian dan penanganan peralatan yang hilang.
