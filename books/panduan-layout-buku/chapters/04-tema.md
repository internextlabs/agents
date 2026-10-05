@part 4 | Tema dan Build | Memilih tema, membuat sendiri, dan kendali keluaran | Tema dan Build

:::goals
- Memilih tema yang tepat untuk isi dan pembacanya
- Membuat tema sendiri dengan kontras yang lolos uji
- Mengendalikan format, ukuran halaman, dan bahasa
:::

## 1. Tujuh Tema

Tiap tema adalah satu set lengkap: sepasang huruf, skala, dan palet yang sudah lolos kontras.

{.dodont widths=24,38,38}
| Tema | Cocok untuk | Hindari untuk |
|---|---|---|
| `edukasi` | Modul pelatihan, bahan ajar | Dokumentasi teknis |
| `korporat` | Laporan, SOP, proposal | Buku anak |
| `akademik` | Buku ajar, monograf | Materi ringan |
| `teknologi` | Dokumentasi teknis, koding | Buku sastra |
| `alam` | Lingkungan, kesehatan | Buku anak |
| `premium` | Kepemimpinan, katalog | Materi formal |
| `ceria` | Buku anak, LKPD | Laporan formal |

Kalau pengguna tidak menyebut preferensi, pilih yang paling sesuai isi dan sebutkan pilihan itu
dalam satu kalimat. Mengganti tema cuma mengubah satu baris di `book.yaml`.

## 2. Tema Buatan Sendiri

Salin tema terdekat, ubah warnanya, lalu jalankan pemeriksa kontras.

```bash
python scripts/check_contrast.py path/tema.json
```

Semua pasangan yang gagal dilaporkan satu per satu. Jangan skipping langkah ini — kontras yang
buruk adalah kesalahan yang paling sering terlewat dan paling sulit terlihat saat membaca.

## 3. Font Tambahan

Taruh berkas TTF berlisensi terbuka di `assets/fonts/`, lalu daftarkan di
`assets/fonts/fonts.json`. Nama di daftar itu harus sama persis dengan nama berkas.

## 4. Kendali book.yaml

Kunci yang paling sering dipakai, dan efeknya.

{widths=26,74}
| Kunci | Efek |
|---|---|
| `page_size` | A4, B5, A5, atau Letter |
| `lang` | Semua label mengikuti bahasa ini |
| `part_label` | Label di halaman pembuka bagian |
| `toc_after` | Posisi daftar isi relatif terhadap bab |
| `theme_overrides` | Ganti satu warna tanpa membuat tema baru |
| `highlight_placeholders` | Matikan sorotan kuning pada variabel |

`theme_overrides` adalah cara paling murah untuk menyesuaikan warna merek: tema tetap resmi,
warna aksen ditimpa.

## 5. Opsi Build

```bash
python scripts/build.py path/book.yaml --formats pdf,docx --theme NAMA --out DIR
```

{widths=24,76}
| Opsi | Fungsi |
|---|---|
| `--formats` | Pilih keluaran: pdf, docx, atau keduanya |
| `--theme` | Timpa tema dari baris perintah |
| `--out` | Folder keluaran |
| `--no-embed` | Jangan tertapkan font ke DOCX |
| `--preview` | Tulis lembar kontak halaman |

Build berjalan dua kali pass supaya daftar isi mendapat nomor halaman yang benar, mengambil
snapshot sampul dan diagram untuk DOCX, lalu tertapkan font tema.

## 6. Periksa Hasilnya

Langkah ini tidak boleh dilewati: build yang berhasil belum tentu buku yang benar.

Periksa setiap halaman: daftar isi bernomor, diagram tidak terbelah, tabel tidak meluap,
tidak ada halaman nyaris kosong, label callout tidak terpisah dari isinya.

:::limits Kendala lingkungan
Beberapa komponen butuh program eksternal: LibreOffice untuk mengisi nomor halaman daftar
isi di DOCX, dan poppler untuk membuat lembar pratinjau. Keduanya opsional — kalau tidak ada,
build tetap berhasil, hanya dua fitur itu yang dilewati.
:::

## 7. Intisari

:::summary Inti bagian ini
Tema menentukan tampilan, `book.yaml` menentukan perilaku, dan build menghasilkan dua format
dari satu sumber.

Semua koreksi visual dilakukan lewat satu file konfigurasi, bukan dengan mengedit hasil.
:::