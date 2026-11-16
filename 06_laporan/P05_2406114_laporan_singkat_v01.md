# Laporan Singkat Jobsheet Praktikum Pertemuan 5

**Topik:** Skenario Use Case: Dari Diagram ke Langkah Kegiatan  
**Mata Praktikum:** IFRWP5149 Analisis dan Desain Berorientasi Objek  
**Sumber:** Jobsheet Praktikum Pertemuan 5  
**Sifat laporan:** Ringkasan dokumen jobsheet, bukan laporan hasil pengerjaan mahasiswa.

---

## 1. Tujuan Pembelajaran

Praktikum Pertemuan 5 bertujuan agar mahasiswa mampu:

1. Menyusun tabel skenario use case secara lengkap, meliputi Nama use case, Aktor, Tujuan, Deskripsi, kolom Kegiatan dan Respon sistem, Skenario Normal, Skenario Alternative, dan Skenario Akhir.
2. Menulis langkah skenario secara berurutan dengan satu aksi per langkah serta memisahkan aksi aktor dan tanggapan sistem pada kolom yang benar.
3. Memetakan relasi `include` menjadi langkah wajib pada Skenario Normal dan relasi `extend` menjadi cabang bersyarat pada Skenario Alternative lengkap dengan `condition` dan `extension point`.
4. Menerapkan `generalization` aktor dan `generalization` use case dalam penulisan skenario.
5. Menelaah 12 tabel skenario studi kasus Laboratorium dari diagram kumulatif Pertemuan 4 dan menyusun 7 tabel skenario tugas Sistem Informasi Akademik (SIA).

Produk yang dihasilkan berupa lembar skenario untuk 12 tabel studi kasus LAB dan 7 tabel tugas SIA.

---

## 2. Konsep Inti

### 2.1 Pengertian Skenario Use Case

Skenario use case adalah uraian langkah demi langkah interaksi antara aktor dan sistem untuk satu use case. Skenario menjawab bagaimana use case berjalan dari awal sampai selesai, kapan alur bercabang, dan kapan use case dinyatakan selesai.

Skenario ditulis dalam tabel dua kolom:

- **Kegiatan:** berisi aksi aktor.
- **Respon sistem:** berisi tanggapan sistem.

Skenario berbeda dari `use case description` dan `use case diagram`. Diagram menunjukkan use case dan relasinya, sedangkan skenario merinci urutan langkahnya. Pada Pertemuan 5 tidak ada diagram baru; diagram acuan tetap diagram kumulatif Pertemuan 4.

### 2.2 Struktur Tabel Skenario

Urutan struktur tabel skenario:

1. Nama use case.
2. Aktor.
3. Tujuan.
4. Deskripsi.
5. Kolom Kegiatan dan Respon sistem.
6. Skenario Normal.
7. Skenario Alternative dengan penomoran yang **melanjutkan** Skenario Normal.
8. Skenario Akhir sebagai kalimat kondisi selesai, bukan langkah bernomor baru.

### 2.3 Kaidah Penulisan Langkah

- Satu langkah berisi satu aksi.
- Kolom Kegiatan hanya untuk aksi aktor; kolom Respon sistem hanya untuk tanggapan sistem.
- Gunakan kalimat aktif singkat yang diawali kata kerja.
- Data yang dimasukkan/ditampilkan disebut eksplisit, misalnya tanggal pinjam, status Menunggu Keputusan.
- Cabang Alternative merujuk ke langkah tempat cabang terjadi.
- Penomoran langkah berlanjut dari Normal ke Alternative.
- Nama, ID, aktor, `condition`, dan `extension point` harus sama persis dengan diagram Pertemuan 4.


### 3.3 Tugas SIA

Tugas melanjutkan kasus SIA Pertemuan 4 dengan 7 tabel skenario:

| ID | Nama Use Case | Aktor |
|---|---|---|
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen |
| SIA-UC09 | Lihat KHS | Mahasiswa |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik |

Aturan khusus:

- SIA-UC07 ditulis satu kali atas nama Civitas Akademika dan berlaku untuk Mahasiswa dan Dosen.
- SIA-UC10 adalah skenario umum; SIA-UC11, UC12, dan UC13 hanya memuat perilaku pembeda.
- Nilai hanya dapat diinput oleh dosen pengampu.
- KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa tanpa data akademik aktif.
- Collaboration SIA-CO01 disebut pada keterangan UC08; SIA-CO02 pada keterangan UC09.

---

## 5. Checklist Ringkas

- [ ] Seluruh field tabel terisi.
- [ ] Langkah berurutan, satu aksi per langkah.
- [ ] Penomoran berlanjut dari Skenario Normal ke Skenario Alternative.
- [ ] Kolom Kegiatan dan Respon sistem tidak tertukar.
- [ ] Data yang dimasukkan/ditampilkan disebut eksplisit.
- [ ] Include ditulis sebagai langkah rujukan pada Skenario Normal.
- [ ] Extend ditulis sebagai cabang bersyarat dengan `condition` dan `extension point`.
- [ ] Generalization aktor diterapkan satu tabel atas nama aktor umum.
- [ ] Generalization use case diterapkan dengan skenario umum dan skenario khusus.
- [ ] Collaboration hanya disebut pada keterangan tabel.
- [ ] Setiap tabel memiliki Skenario Alternative dan Skenario Akhir.
- [ ] Nama, ID, aktor, `condition`, dan `extension point` sama persis dengan diagram Pertemuan 4.
- [ ] Berkas diagram P04 tidak diubah.
- [ ] Nama dan lokasi file deliverable sesuai ketentuan.

---

## 6. Deliverable

1. `P05_<NIM>_LAB_skenario_v01.md`  
   Berisi hasil telaah 12 tabel skenario studi kasus LAB, checklist, dan kolom penelusuran singkat per tabel.

2. `P05_<NIM>_SIA_skenario_v01.drawio`  
   Berisi 7 tabel skenario tugas SIA.

3. Logbook singkat  
   Mencatat tabel studi kasus yang sudah dicek dan kemajuan penulisan tabel tugas SIA.

Diagram P04 tetap menjadi acuan dan tidak dikumpulkan ulang sebagai produk baru.

---

## 7. Kesimpulan

Pertemuan 5 menekankan penulisan skenario use case yang lengkap, konsisten dengan diagram kumulatif Pertemuan 4, serta tepat dalam memetakan relasi `include`, `extend`, `generalization`, dan `collaboration`. Produk utama praktikum adalah 12 tabel skenario studi kasus LAB dan 7 tabel skenario tugas SIA yang diperiksa menggunakan checklist dan rubrik praktik RPS.