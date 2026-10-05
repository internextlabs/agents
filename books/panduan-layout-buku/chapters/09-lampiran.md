# Lampiran · Rujukan Cepat

Daftar periksa, kamus, dan tabel sintaks yang paling sering dibuka saat menulis naskah.

## 1. Daftar Periksa Sebelum Build

{.checklist widths=8,68,24}
| | Yang diperiksa | Selesai |
|---|---|---|
| 1 | Tiap bab punya judul yang menggambarkan isinya, bukan label kosong | |
| 2 | Dinding teks lebih dari tujuh baris sudah dipecah | |
| 3 | Tiap halaman punya minimal satu jangkar visual | |
| 4 | Satu istilah untuk satu konsep di seluruh buku | |
| 5 | Tidak ada callout sebagai hiasan | |
| 6 | Semua `@figure` memakai path yang benar | |
| 7 | Tabel punya lebar kolom yang sesuai | |

## 2. Daftar Periksa Setelah Build

{.checklist widths=8,68,24}
| | Yang diperiksa | Selesai |
|---|---|---|
| 1 | Daftar isi punya nomor halaman | |
| 2 | Tidak ada halaman nyaris kosong | |
| 3 | Diagram tidak terbelah antar halaman | |
| 4 | Tabel tidak meluap | |
| 5 | Label callout tidak terpisah dari isinya | |
| 6 | Teks besar di DOCX tidak terpotong | |
| 7 | Fakta dan angka sudah diperiksa | |

Baris terakhir sering dilupakan. Layout yang rapi tidak menolong isi yang keliru.

## 3. Kamus Sindaks

{.glossary widths=24,76}
| Sintaks | Hasil |
|---|---|
| `# Judul` | Bab baru |
| `# Judul {nobreak}` | Bab tanpa pindah halaman |
| `# Judul {notoc}` | Bab tersembunyi dari daftar isi |
| `@part` | Bagian inti dengan pembuka |
| `## 1. Judul` | Subjudul dengan lencana angka |
| `:::tip` | Callout hijau |
| `:::summary` | Kotak intisari gelap |
| `:::stats` | Kartu angka |
| `{.dodont}` | Gaya tabel lakukan-hindari |
| `{.steps}` | Garis waktu langkah |
| `{.glossary}` | Gaya tabel istilah |
| ` ```prompt ` | Kotak template |
| `@figure` | Diagram anti-terbelah |
| `@pagebreak` | Pindah halaman paksa |

## 4. Masalah yang Sering Muncul

{widths=30,70}
| Gejala | Penyebab dan perbaikan |
|---|---|
| Diagram tidak tampil | Path relatif terhadap file markdown; fragmen tanpa tag `html` |
| Nomor daftar isi kosong | Bangun ulang; judul bab jangan mengandung markdown |
| Nomor halaman kosong di DOCX | Normal — Word mengisinya saat pembuka meng-update fields |
| Teks besar terpotong di DOCX | Sudah ditangani otomatis; jangan menyunting ulang dengan alat lain |
| Halaman nyaris kosong | Persingkat teks sebelumnya, atau periksa `{nobreak}` |
| Kolom pertama tabel sempit | Tambahkan `{widths=20,40,40}` |
| Warna aksen sulit dibaca | Jalankan pemeriksa kontras pada tema |
| Chromium tidak ditemukan | Jalankan `npx playwright install chromium` |

## 5. Glosarium Istilah

{.glossary widths=26,74}
| Istilah | Arti |
|---|---|
| Anti-terbelah | Aturan yang mencegah elemen pecah antar halaman |
| Opt-in | Komponen muncul hanya jika ditulis di naskah |
| Lencana | Nomor berwarna aksen di depan subjudul |
| Kicker | Label kecil di atas judul |
| Chip | Label kecil berbentuk kapsul pada sampul dan template |
| Seri warna | Palet berurutan untuk diagram dan kartu |
| Track | Jumlah pemisahan antar huruf pada label |
| Indent | Ruang kosong sebelum paragraf atau judul |

## 6. Satu Catatan Penutup

Sistem ini tidak menggantikan penilaianmu. Ia menyelesaikan bagian yang membosankan
dan mudah salah — gambar yang terbelah, nomor halaman yang meleset, baris yang terpotong — supaya
perhatianmu habis untuk isi.

Sisanya tetap milikmu.

:::summary Pesan penutup
Kuasai kerangka, pilih komponen yang memang dipakai, dan periksa hasilnya secara visual.
Tiga langkah itu sudah cukup untuk menghasilkan dokumen yang layak dibaca.
:::