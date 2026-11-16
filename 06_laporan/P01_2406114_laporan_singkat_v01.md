# LAPORAN SINGKAT PRAKTIKUM PERTEMUAN 1

**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek  
**Pertemuan:** 1 — Pengenalan Lingkungan Praktikum dan Kakas Pemodelan UML  
**Nama / NIM:** Muhammad Iqbal Syarief / 2406114  
**Kasus:** Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus  
**Kakas:** draw.io (diagrams.net)  
**Tanggal:** 2 Oktober 2026  
**Status artefak:** LATIHAN — belum divalidasi sebagai model analisis

## 1. Hasil yang Dicapai

| No. | Kegiatan | Hasil |
|---|---|---|
| 1 | Penyiapan workspace | Folder proyek `IFRWP5149_2406114_LabAlat` dengan subfolder `00_administrasi`, `01_skenario`, `02_template`, `03_latihan_tools`, `04_model_analisis`, `05_model_desain`, dan `06_laporan`; dilengkapi `README.md`. |
| 2 | Orientasi kakas | draw.io dibuka, kanvas baru dibuat, pustaka bentuk UML diaktifkan, dan lokasi penyimpanan lokal dipastikan dapat diakses. |
| 3 | Latihan diagram aktivitas | Diagram aktivitas S-ORI-01 dibuat dengan empat elemen berurutan dan tiga alur kontrol. |
| 4 | Simpan dan ekspor | Berkas sumber `.drawio` disimpan, lalu diekspor menjadi `.png` dengan nama dasar dan nomor versi yang sama. |
| 5 | Uji buka ulang | Berkas `.drawio` ditutup dan dibuka kembali, satu elemen digeser, disimpan ulang, lalu diekspor ulang agar sumber dan gambar sesuai. |

## 2. Artefak yang Dihasilkan

| Artefak | Lokasi | Keterangan |
|---|---|---|
| `README.md` | akar proyek | Identitas mahasiswa, kasus, kakas, daftar folder, dan status pekerjaan. |
| `S-ORI-01_orientasi_v01.md` | `01_skenario/` | Skenario latihan: mahasiswa membuka daftar peralatan dan melihat informasi ketersediaan. |
| `template_metadata_artefak_v01.md` | `02_template/` | Template identitas artefak untuk pertemuan berikutnya. |
| `P01_2406114_latihan_activity_v01.drawio` | `03_latihan_tools/` | Sumber diagram aktivitas latihan. |
| `P01_2406114_latihan_activity_v01.png` | `03_latihan_tools/` | Hasil ekspor diagram latihan. |
| `P01_2406114_logbook_v01.md` | `00_administrasi/` | Logbook dan checklist Pertemuan 1. |

## 3. Struktur Diagram Latihan

Alur yang dimodelkan sesuai jobsheet, tanpa percabangan, swimlane, autentikasi, atau aturan bisnis tambahan:

node awal → aktivitas “Buka daftar peralatan” → aktivitas “Lihat informasi ketersediaan” → node akhir aktivitas

Kanvas diberi judul latihan dan catatan bahwa diagram **belum divalidasi sebagai model proses**, sehingga tidak diklaim sebagai hasil analisis kebutuhan.

## 4. Pemeriksaan yang Dilakukan

| No. | Butir Pemeriksaan | Hasil |
|---|---|---|
| 1 | Empat elemen latihan dan tiga alur penghubung tersedia | Sesuai |
| 2 | Label aktivitas terbaca dan garis benar-benar terhubung ke elemen | Sesuai |
| 3 | Berkas sumber dapat dibuka kembali dan disunting | Berhasil |
| 4 | Gambar ekspor sesuai versi terakhir berkas sumber | Sesuai, diekspor ulang setelah perubahan |
| 5 | Nama dan nomor versi sumber serta ekspor konsisten | Sesuai (`v01`) |
| 6 | Tidak ada kredensial atau data pribadi nyata pada arsip | Sesuai |

## 5. Kendala dan Tindak Lanjut

| Kendala | Penanganan |
|---|---|
| Bentuk node awal dan node akhir tidak langsung ditemukan pada pustaka bentuk standar. | Pustaka UML diaktifkan melalui **More Shapes**, lalu bentuk node awal dan *end state* dipilih dari pustaka tersebut. |
| Posisi penghubung sempat tampak menempel tetapi tidak terhubung ke elemen. | Ujung garis ditarik ulang sampai titik sambung aktif, lalu diagram diperiksa satu per satu. |

Tindak lanjut: ketepatan notasi use case, batas sistem, dan penamaan aktor akan diperiksa pada Pertemuan 2; latihan ini hanya menguji operasional kakas.

## 6. Kesimpulan

Workspace praktikum telah tersusun sesuai SOP, kakas draw.io dapat dioperasikan untuk membuat, menyimpan, membuka kembali, dan mengekspor diagram, serta seluruh artefak Pertemuan 1 tersedia dan dapat dibaca. Diagram latihan bersifat uji kakas dan belum merupakan model analisis tervalidasi, sehingga pemeriksaan notasi dilakukan pada pertemuan berikutnya.
