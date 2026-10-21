# LAPORAN SINGKAT REVIEW JOBSHEET PERTEMUAN 3

**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek  
**Kasus:** Sistem Informasi Akademik — Pengajuan dan Persetujuan KRS  
**Fokus Review:** Skenario, identifikasi aktor, katalog use case, relasi UML, deskripsi use case, dan konsistensi model analisis.

## 1. Hasil Review

| No. | Temuan | Perbaikan yang Dilakukan atau Perlu Dipastikan | Alasan |
|---|---|---|---|
| 1 | Kebutuhan dari Pertemuan 2 berbeda dengan cakupan model KRS Pertemuan 3. | SIA-R01 dan SIA-R02 tetap dicatat sebagai kebutuhan terdahulu. Diagram P03 difokuskan pada proses pengajuan dan persetujuan KRS. | Agar cakupan diagram jelas dan tidak tercampur dengan pengelolaan jadwal kuliah. |
| 2 | Aktor harus berada di luar batas sistem. | Letakkan Mahasiswa dan Dosen wali di luar batas sistem Sistem Informasi Akademik — Pengajuan dan Persetujuan KRS. | Aktor merupakan pihak eksternal yang berinteraksi dengan sistem. |
| 3 | Setiap aktor harus memiliki hubungan sesuai tanggung jawabnya. | Hubungkan Mahasiswa dengan SIA-UC03 dan SIA-UC05, serta Dosen wali dengan SIA-UC06. | Hubungan aktor harus sesuai dengan skenario dan tujuan interaksi. |
| 4 | Validasi merupakan bagian wajib dari pengajuan KRS. | Tambahkan relasi `«include»` dari SIA-UC03 — Ajukan KRS menuju SIA-UC04 — Validasi KRS. | Setiap pengajuan harus diperiksa kelengkapan data, prasyarat mata kuliah, dan benturan jadwal. |
| 5 | Pengunduhan bukti bersifat opsional. | Tambahkan relasi `«extend»` dari SIA-UC05 — Unduh bukti pengajuan KRS menuju SIA-UC03 — Ajukan KRS. | Pengunduhan hanya dilakukan jika mahasiswa memilih opsi tersebut setelah pengajuan tersimpan. |
| 6 | Relasi extend memerlukan kondisi dan extension point. | Cantumkan kondisi `[mahasiswa memilih mengunduh bukti]` dan extension point `Konfirmasi penyimpanan tersedia` pada SIA-UC03. | Untuk menjelaskan kapan perilaku tambahan dijalankan dan di bagian mana perilaku tersebut memperluas use case dasar. |
| 7 | Validasi dapat berhasil atau gagal. | Jelaskan alur alternatif ketika data tidak lengkap, prasyarat mata kuliah tidak terpenuhi, atau jadwal bentrok. | Pengajuan yang gagal divalidasi tidak boleh dinyatakan berhasil tersimpan. |
| 8 | Pengajuan yang berhasil belum tentu disetujui dosen wali. | Tetapkan status setelah pengajuan berhasil sebagai `Menunggu persetujuan dosen wali`. | Keberhasilan pengajuan berbeda dari keputusan akhir dosen wali. |
| 9 | Keputusan dosen wali memiliki beberapa kemungkinan hasil. | Pada SIA-UC06, dokumentasikan proses persetujuan dan penolakan beserta catatan keputusan. | Agar deskripsi use case sesuai dengan kebutuhan SIA-R06. |
| 10 | Diagram dan deskripsi harus konsisten. | Samakan ID, nama use case, aktor, relasi, kondisi extend, extension point, dan status KRS pada seluruh artefak. | Untuk memudahkan penelusuran kebutuhan serta menghindari perbedaan informasi. |
| 11 | Berkas diagram perlu memiliki nama dan versi yang konsisten. | Simpan diagram sumber dan hasil ekspor menggunakan nama `P03_2406043_SIA_usecase_v02.drawio` dan `P03_2406043_SIA_usecase_v02.png`. | Agar berkas mudah dikelola dan diperiksa kembali. |

## 2. Pemeriksaan Tiga Situasi Uji

| No. | Situasi Uji | Perilaku yang Diharapkan | Hasil Pemeriksaan |
|---|---|---|---|
| A | Validasi berhasil dan mahasiswa tidak mengunduh bukti. | KRS tersimpan dengan status Menunggu persetujuan dosen wali. SIA-UC05 tidak dijalankan. | Konsisten dengan relasi extend yang opsional. |
| B | Validasi gagal. | Pengajuan tidak berhasil tersimpan. Extension point tidak tercapai dan SIA-UC05 tidak dijalankan. | Konsisten dengan alur alternatif validasi gagal. |
| C | Validasi berhasil dan mahasiswa memilih mengunduh bukti. | KRS tersimpan dengan status Menunggu persetujuan dosen wali. Setelah extension point tercapai, SIA-UC05 dijalankan. | Konsisten dengan kondisi extend dan pascakondisi pengajuan. |

## 3. Kesimpulan

Berdasarkan hasil review, model use case Sistem Informasi Akademik untuk pengajuan dan persetujuan KRS perlu memperlihatkan batas sistem, aktor, katalog use case, serta hubungan antar-use-case secara jelas dan konsisten.

SIA-UC03 — Ajukan KRS menggunakan relasi `«include»` ke SIA-UC04 — Validasi KRS karena validasi merupakan bagian wajib dari proses pengajuan. Sementara itu, SIA-UC05 — Unduh bukti pengajuan KRS menggunakan relasi `«extend»` ke SIA-UC03 karena pengunduhan hanya dilakukan jika mahasiswa memilihnya setelah pengajuan berhasil disimpan.

Validasi yang gagal tidak menghasilkan pengajuan yang berhasil tersimpan. Pengajuan yang berhasil disimpan memiliki status Menunggu persetujuan dosen wali dan tidak otomatis disetujui. Proses keputusan tersebut dimodelkan melalui SIA-UC06 — Proses keputusan KRS yang melibatkan aktor Dosen wali.

Kebutuhan SIA-R01 dan SIA-R02 tetap dipertahankan sebagai konteks Pertemuan 2 dan tidak dimodelkan ulang dalam diagram KRS P03. Dengan demikian, model analisis diharapkan lebih terstruktur, mudah ditelusuri, dan sesuai dengan cakupan praktikum.

## 4. Daftar Artefak

1. `P03_SIA_kebutuhan_v01.md`
2. `P03_2406043_SIA_usecase_v02.drawio`
3. `P03_2406043_SIA_usecase_v02.png`
4. `P03_2406043_SIA_deskripsi_v02.md`
5. `P03_SIA_review_v01.md`

**Catatan:** Pastikan setiap berkas benar-benar sudah dibuat dan diperiksa sebelum dicantumkan sebagai hasil akhir praktikum.