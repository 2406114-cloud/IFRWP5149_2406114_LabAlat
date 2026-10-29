# LAPORAN SINGKAT REVIEW JOBSHEET PERTEMUAN 4

**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek  
**Kasus:** Sistem Informasi Akademik — Layanan Hasil Studi  
**Fokus Review:** Generalization aktor, generalization use case, collaboration/realization, konsistensi diagram kumulatif, batas sistem, dan tiga situasi uji konsistensi.

## 1. Hasil Review

| No. | Temuan | Perbaikan yang Dilakukan atau Perlu Dipastikan | Alasan |
|---|---|---|---|
| 1 | Diagram Pertemuan 4 bersifat kumulatif. | Pastikan diagram memuat SIA-UC01 sampai SIA-UC13 tanpa mengubah nama/arti use case lama. | Fungsi jadwal kuliah P02 dan KRS P03 harus tetap ada, sedangkan elemen baru P04 ditambahkan. |
| 2 | Aktor harus berada di luar batas sistem. | Letakkan Civitas Akademika, Mahasiswa, Dosen, Admin Akademik, dan Dosen Wali di luar batas sistem. Use case dan collaboration berada di dalam batas sistem. | Aktor adalah pihak eksternal; use case dan collaboration merupakan bagian internal model sistem. |
| 3 | Mahasiswa dan Dosen sama-sama dapat melihat kalender akademik. | Jadikan Mahasiswa dan Dosen sebagai aktor khusus dari Civitas Akademika. Gambar asosiasi ke SIA-UC07 hanya dari Civitas Akademika. | Mahasiswa dan Dosen mewarisi asosiasi SIA-UC07 melalui generalization aktor. |
| 4 | Tidak boleh ada asosiasi langsung Mahasiswa–SIA-UC07 atau Dosen–SIA-UC07. | Hapus/cegah garis langsung dari Mahasiswa maupun Dosen ke SIA-UC07. | Asosiasi tersebut sudah diwariskan dari aktor umum Civitas Akademika. |
| 5 | Dosen Wali tetap aktor terpisah. | Pertahankan Dosen Wali sebagai aktor P03 dan hubungkan langsung ke SIA-UC06. Jangan membuat Dosen Wali sebagai specialization dari Dosen. | Tugas hanya menetapkan Civitas Akademika sebagai aktor umum dengan Mahasiswa dan Dosen sebagai specialization. |
| 6 | SIA-UC11, SIA-UC12, dan SIA-UC13 adalah bentuk khusus SIA-UC10. | Gambar panah generalization dari SIA-UC11, SIA-UC12, dan SIA-UC13 menuju SIA-UC10. Hubungkan Admin Akademik cukup ke SIA-UC10. | Tambah, ubah, dan hapus data mahasiswa merupakan bentuk khusus dari Kelola Data Mahasiswa. |
| 7 | Relasi lama `«include»` dan `«extend»` harus dipertahankan. | Pastikan SIA-UC03 `«include»` SIA-UC04; SIA-UC05 `«extend»` SIA-UC03 dengan kondisi `[Mahasiswa memilih mengunduh bukti]` dan extension point `Konfirmasi penyimpanan tersedia`. | Validasi wajib pada pengajuan KRS; unduh bukti bersifat opsional. |
| 8 | Collaboration harus merealisasikan use case dengan nama yang sama persis. | SIA-CO01 — Input Nilai Mata Kuliah merealisasikan SIA-UC08 — Input Nilai Mata Kuliah. SIA-CO02 — Lihat KHS merealisasikan SIA-UC09 — Lihat KHS. | Nama collaboration harus sama dengan use case yang direalisasikan dan tidak terhubung langsung ke aktor. |
| 9 | Panah realization harus konsisten. | Gambar garis putus-putus dengan segitiga kosong dari collaboration menuju use case yang direalisasikan. | Menunjukkan hubungan realization, bukan asosiasi aktor. |
| 10 | SIA-UC08 hanya untuk Dosen pengampu. | Pastikan deskripsi/alur alternatif menyatakan Dosen yang bukan pengampu ditolak; nilai baru tidak tersimpan dan data lama tidak berubah. | Sesuai batas perilaku dan situasi uji B. |
| 11 | Nilai baru belum otomatis dipublikasikan. | SIA-UC09 hanya menampilkan nilai yang statusnya sudah dipublikasikan. Jangan menambahkan rentang angka atau alur publikasi yang tidak diberikan jobsheet. | Menghindari tafsiran berlebihan di luar sumber tugas. |
| 12 | Hapus data mahasiswa memiliki guard. | SIA-UC13 harus menolak penghapusan jika mahasiswa masih memiliki data akademik aktif dan mempertahankan data tersebut. | Sesuai kebutuhan SIA-R11 dan situasi uji C. |
| 13 | ID dan nama harus konsisten di seluruh artefak. | Samakan ID, nama use case, aktor, relasi, kondisi extend, extension point, dan nama collaboration pada katalog, deskripsi, diagram Draw.io, dan PNG. | Memudahkan penelusuran kebutuhan dan menghindari perbedaan informasi. |
| 14 | Berkas P02/P03 asli tidak boleh ditimpa. | Simpan diagram P04 sebagai `P04_2406043_SIA_usecase_v01.drawio` dan `P04_2406043_SIA_usecase_v01.png`. Jika hasil review mengubah isi, simpan sebagai v02 dan catat perubahan. | Menjaga riwayat artefak dan versi. |

## 2. Pemeriksaan Tiga Situasi Uji

| No. | Situasi Uji | Perilaku yang Diharapkan | Hasil Pemeriksaan |
|---|---|---|---|
| A | Mahasiswa melihat kalender akademik tanpa asosiasi langsung dari aktor Mahasiswa ke SIA-UC07. | Mahasiswa mewarisi asosiasi SIA-UC07 dari aktor umum Civitas Akademika melalui generalization; asosiasi tidak digambar ulang dari Mahasiswa. | Konsisten. Asosiasi SIA-UC07 hanya berasal dari Civitas Akademika. |
| B | Dosen yang bukan pengampu mata kuliah mencoba menginput nilai. | Sistem menolak operasi untuk mata kuliah tersebut. Tidak ada nilai baru yang tersimpan dan data yang sudah ada tidak berubah. | Konsisten dengan batas perilaku SIA-UC08; perlu dipastikan alur alternatif/deskripsi menyebut penolakan tersebut. |
| C | Admin Akademik menghapus data mahasiswa yang masih memiliki data akademik aktif. | Sistem menolak penghapusan dan mempertahankan data mahasiswa. | Konsisten dengan guard SIA-UC13 dan kebutuhan SIA-R11. |

## 3. Kesimpulan

Berdasarkan hasil review, model use case Sistem Informasi Akademik untuk Layanan Hasil Studi perlu mempertahankan fungsi jadwal kuliah P02 dan fungsi KRS P03, lalu menambahkan layanan kalender akademik, input nilai, lihat KHS, serta pengelolaan data mahasiswa pada P04.

SIA-UC07 — Lihat Kalender Akademik dihubungkan hanya ke aktor umum Civitas Akademika. Mahasiswa dan Dosen menjadi aktor khusus dari Civitas Akademika sehingga mewarisi akses tersebut tanpa garis asosiasi langsung. SIA-UC11, SIA-UC12, dan SIA-UC13 merupakan bentuk khusus dari SIA-UC10 — Kelola Data Mahasiswa, dengan panah generalization dari use case khusus menuju use case umum.

Relasi lama tetap dipertahankan: SIA-UC03 — Ajukan KRS `«include»` SIA-UC04 — Validasi KRS, sedangkan SIA-UC05 — Unduh Bukti Pengajuan KRS `«extend»` SIA-UC03 dengan kondisi dan extension point yang tetap dicantumkan. Collaboration SIA-CO01 — Input Nilai Mata Kuliah merealisasikan SIA-UC08, dan SIA-CO02 — Lihat KHS merealisasikan SIA-UC09. Collaboration tidak dihubungkan langsung ke aktor.

Tiga situasi uji konsistensi menunjukkan hasil yang sesuai: pewarisan akses kalender akademik melalui generalization aktor, penolakan input nilai oleh Dosen bukan pengampu, dan penolakan hapus data mahasiswa yang masih memiliki data akademik aktif. Dengan demikian, model analisis diharapkan konsisten, mudah ditelusuri, dan tidak menambahkan aturan di luar sumber tugas.

## 4. Daftar Artefak

1. `P04_SIA_kebutuhan_v01.md`
2. `P04_2406043_SIA_usecase_v01.drawio`
3. `P04_2406043_SIA_usecase_v01.png`
4. `P04_2406043_SIA_deskripsi_v01.md`
5. `P04_SIA_review_v01.md`

**Catatan:** Pastikan setiap berkas benar-benar sudah dibuat dan diperiksa sebelum dicantumkan sebagai hasil akhir praktikum.