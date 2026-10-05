@part 2 | Tipografi dan Warna | Angka di balik setiap keputusan visual | Tipografi dan Warna

:::goals
- Memahami skala tipografi dan alasan di balik angkanya
- Mengetahui peran setiap warna, bukan hanya nama warnanya
- Menerapkan aturan kontras WCAG pada tema sendiri
:::

## 1. Pasangan Huruf

Sistem ini memakai dua keluarga huruf: satu untuk judul, satu untuk isi. Peran yang berbeda
membuat hierarki terlihat tanpa perlu banyak warna.

{widths=18,26,26,30}
| Tema | Judul | Isi | Karakter |
|---|---|---|---|
| edukasi | Poppins | Lora | Ramah dan hangat |
| korporat | Outfit | Work Sans | Bersih dan netral |
| akademik | Crimson Pro | Crimson Pro | Serif klasik, satu keluarga |
| teknologi | Bricolage | Instrument Sans | Modern dan rapat |
| alam | Work Sans | IBM Plex Serif | Humanis dan lugas |
| premium | Young Serif | Lora | Elegan untuk judul |
| ceria | Poppins | Work Sans | Bulat dan ramah |

Aturan praktisnya: jangan pernah menambah keluarga huruf ketiga. Tiga keluarga sudah menjadi
batas wajar; empat membuat dokumen terlihat berantakan.

## 2. Skala Tipografi

Semua ukuran diturunkan dari satu angka dasar, bukan dipilih satu per satu.

{widths=30,26,44}
| Elemen | Rasio | Catatan |
|---|---|---|
| Isi | 1,0 | 9,8 sampai 11,3 pt |
| Subjudul tingkat 3 | 1,1 | Skala kecil |
| Subjudul tingkat 2 | 1,42 | Dapat lencana angka |
| Judul bab | 2,45 | Paling besar setelah sampul |
| Judul sampul | 44 pt | Mengikuti motif sampul |

Ukuran dasar berbeda antar tema karena huruf berbeda secara optis. Crimson Pro terlihat lebih
kecil pada ukuran sama, sehingga dasarnya dinaikkan.

:::note Angka yang perlu dijaga
Spasi baris 1,5 sampai 1,62. Huruf dengan x-height besar seperti Poppins dan Work Sans butuh
ruang lebih lega. Panjang baris ideal 60 sampai 80 karakter; untuk bacaan sangat panjang,
ukuran B5 memberi sekitar 70 karakter dan terasa lebih nyaman.
:::

## 3. Peran Warna

Warna bukan daftar pilihan, tapi sistem peran. Setiap komponen selalu punya warna yang sama
karena perannya sama.

{widths=28,72}
| Peran | Dipakai untuk |
|---|---|
| `primary` | Sampul, judul, header tabel, kotak intisari |
| `accent` | Nomor besar, lencana subjudul, chip template |
| `success` dan `danger` | Callout praktik dan kolom lakukan-hindari |
| `info`, `violet`, `neutral` | Callout lain yang butuh makna berbeda |
| `ink`, `muted`, `line`, `zebra` | Teks dan permukaan tabel |

Proporsi 60-30-10 menjaga keseimbangan: sekitar 60% putih, 30% warna primer, 10% aksen. Aksen
yang terlalu banyak kehilangan tugasnya sebagai sorotan.

## 4. Kontras

Semua pasangan warna di setiap tema sudah lolos uji WCAG. Standarnya: teks isi minimal 7:1,
teks kecil minimal 4,5:1, teks besar di atas warna gelap minimal 3:1.

Kalau kamu membuat tema sendiri, jalankan pemeriksa kontras sebelum build:

```bash
python scripts/check_contrast.py path/tema.json
```

Semua pasangan yang gagal akan diberi tahu satu per satu, jadi tidak ada cara untuk
tidaknya tahu.

:::warning Makna tidak boleh hanya lewat warna
Tabel lakukan-hindari selalu mendapat simbol dan label teks, bukan hanya warna hijau dan
merah. Callout mendapat ikon dan label. Ini bukan hiasan: sekitar satu dari dua belas pria
wanita memiliki sebagian bentuk buta warna, dan dokumenmu dibaca juga oleh orang yang buta warna.
:::

## 5. Tipografi untuk Cetak

Untuk cetak hitam-putih, latar berwarna penuh hanya dipakai di sampul dan halaman pembuka bagian.
Semua callout memakai versi terang yang tetap terbaca tanpa warna.

Kuncinya begini: dokumen yang enak dibaca di layar harus tetap terbaca dalam keadaan
cetak paling buruk.

## 6. Intisari

:::summary Inti bagian ini
Tipografi dan warna bukan pilihan selera, tapi sistem angka dan peran.

Skala diturunkan dari satu angka dasar, warna punya peran tetap, dan kontras diverifikasi
otomatis — sehingga keputusan visual bisa diambil dengan sadar.
:::