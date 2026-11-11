# Metadata Artefak - Pertemuan 6

| Elemen | Keterangan |
|---|---|
| Mata kuliah | Praktikum Analisis dan Desain Berorientasi Objek |
| Repository | `IFRWP5149_2406114_LabAlat` |
| Pertemuan | P06 - Activity diagram: dari skenario ke alur aktivitas |
| Versi metadata | v01 |
| Tanggal penyusunan | 11 November 2026 |
| Status | Draf v01; seluruh diagram LAB dan SIA tersedia beserta ekspor PNG. |

## Ringkasan artefak

| No | Artefak (v01) | Tabel skenario sumber | Unsur activity yang digunakan | Unsur proses baru | Catatan |
|---:|---|---|---|---|---|
| 1 | `P06_2406114_LAB_activity_lihat_ketersediaan_v01.drawio/.png` | Tabel 5.3 LAB-UC01 | decision, merge | - | Alur baca tanpa perubahan data; swimlane Peminjam dan Sistem. |
| 2 | `P06_2406114_LAB_activity_kelola_data_v01.drawio/.png` | Tabel 5.6 LAB-UC02; Tabel 5.7 LAB-UC08; Tabel 5.8 LAB-UC09; Tabel 5.9 LAB-UC10 | decision (4), merge | - | Tiga cabang varian `[tambah]`, `[ubah]`, `[hapus]` dengan satu merge bersama. |
| 3 | `P06_2406114_LAB_activity_peminjaman_v01.drawio/.png` | Tabel 5.1 LAB-UC03; Tabel 5.3 LAB-UC04 (include); Tabel 5.5 LAB-UC05 (extend) | decision (2), merge (2) | - | Include `Periksa Ketersediaan` pada alur utama; extend `[ya, memilih cetak]`. |
| 4 | `P06_2406114_LAB_activity_cetak_bukti_v01.drawio/.png` | Tabel 5.5 LAB-UC05 (extend dari Tabel 5.1 LAB-UC03) | decision, merge | - | Dimulai pada extension point `Bukti pengajuan tersedia`; condition `[ya, memilih cetak]`. |
| 5 | `P06_2406114_LAB_activity_keputusan_v01.drawio/.png` | Tabel 5.10 LAB-UC06 | decision (2), merge | - | Tugas mandiri; alur utama dan cabang Alternative tanpa membuka berkas pembanding. |
| 6 | `P06_2406114_LAB_activity_pengembalian_v01.drawio/.png` | Tabel 5.12 LAB-UC11; Tabel 5.13 LAB-UC12 (include) | decision, merge, fork, join | `Periksa kelengkapan aksesori peralatan` (keterangan tertulis pada action) | Fork/join dua pemeriksaan paralel; include `Periksa Kondisi Peralatan`. |
| 7 | `P06_2406114_LAB_activity_laporan_v01.drawio/.png` | Tabel 5.11 LAB-UC07 | decision, merge | - | Satu-satunya activity dengan aktor Kepala Laboratorium; tanpa fitur ekspor/unduh. |
| 8 | `P06_2406114_SIA_activity_v01.drawio/.png` | Tabel 5.15 SIA-UC08; Tabel 5.16 SIA-UC09; langkah pengesahan dan publikasi sesuai P06 Bagian C.3 | decision, merge, fork, join | - | Empat swimlane: Dosen, Sistem, Admin Akademik, Mahasiswa. |

Seluruh berkas sumber berada di `04_model_analisis/P06/LAB/` dan
`04_model_analisis/P06/SIA/`. Setiap berkas `.drawio` v01 memiliki ekspor
`.png` dengan nama dan nomor versi yang sama.

## Catatan pemeriksaan

- Seluruh action pada ketujuh activity LAB ditelusuri ke bunyi langkah tabel
  skenario Pertemuan 5; nama action dipertahankan sama dengan sumbernya.
- Perbaikan berkas: artefak P06 LAB yang sebelumnya ada di repository memiliki
  isi yang tidak sesuai nama berkasnya (misalnya berkas `peminjaman` berisi
  diagram Lihat Ketersediaan dan berkas `kelola_data` berisi Pengembalian).
  Seluruh berkas P06 LAB dibangun ulang agar isi, nama berkas, dan ekspor PNG
  konsisten, lalu diperiksa terhadap checklist Bagian C.4.
- P04 dan dokumen P05 tidak diubah. LAB-UC04 dan LAB-UC12 digambar sebagai
  action include, sedangkan LAB-UC08, LAB-UC09, dan LAB-UC10 digambar sebagai
  cabang varian pada Activity Kelola Data Peralatan.
- Berkas pembanding bertahap pada Lampiran jobsheet tidak tersedia di
  workspace, sehingga perbandingan visual dengan berkas pembanding belum
  dilakukan; pemeriksaan memakai checklist Bagian C.4 dan penelusuran action
  ke tabel skenario.
- Versi dinaikkan ke v02 hanya bila ada perubahan isi hasil review; perubahan
  dicatat pada metadata ini dan logbook tanpa menimpa v01.
