@part 1 | Kerangka Halaman | Struktur bab, penomoran, dan batas antar halaman | Kerangka Halaman

:::goals
- Memahami urutan halaman dalam sebuah buku
- Membedakan bab, bagian inti, dan subjudul
- Mengendalikan penomoran dan judul daftar isi
:::

## 1. Urutan Halaman

Sebuah buku tersusun dari lima jenis halaman, dan urutannya bisa dikendalikan lewat
`book.yaml`.

{widths=24,76}
| Jenis | Kapan muncul | Kendali |
|---|---|---|
| Sampul | Selalu di awal | `cover: {motif: none}` untuk sampul polos |
| Daftar isi | Tepat setelah sampul | `toc: false` untuk menghilangkan |
| Pembuka bagian | Setelah setiap `@part` | Ditulis eksplisit di naskah |
| Isi bab | Setelah pembuka atau bab sebelumnya | Ditulis eksplisit di naskah |
| Sampul belakang | Selalu di akhir | Hapus blok `back_cover` |

Posisi daftar isi diatur lewat `toc_after: NamaBab`. Tanpa itu, daftar isi muncul tepat
setelah sampul.

:::tip Kalau daftar isi terasa terlalu awal
Kalau pengantarmu panjang dan daftar isi muncul sebelum pembaca belum tahu apa yang akan
dibaca, pindahkan dengan `toc_after: Pengantar`. Nilai yang dipakai adalah judul bab
persisnya, bukan nomor halaman.
:::

## 2. Tiga Tingkat Struktur

Struktur sederhana yang tersedia adalah tiga tingkat, dan masing-masing punya perilaku berbeda.

{widths=20,34,46}
| Tulis | Hasil | Perilaku |
|---|---|---|
| `# Judul` | Bab | Selalu halaman baru |
| `@part` | Bagian inti | Dapat halaman pembuka penuh |
| `##` dan `###` | Subjudul | Mengikuti alur teks |

Bab selalu memulai halaman baru kecuali diberi atribut `{nobreak}`. Bagian inti boleh tanpa
bab pengantar, dan buku tanpa bagian inti juga sah — banyak panduan pendek tidak memerlukannya.

## 3. Atribut Bab

Empat atribut yang mengubah perilaku bab tanpa mengubah teksnya.

{.dodont widths=24,38,38}
| Atribut | Efek | Ketika dipakai |
|---|---|---|
| `nobreak` | Tidak pindah halaman | Bab pendek sebelum bab utama |
| `notoc` | Tidak masuk daftar isi | Catatan internal |
| `kicker` | Label di atas judul | Memberi konteks tambahan |
| Judul `Lampiran X` | Kicker otomatis | Lampiran bernomor |

Kicker otomatisnya dua: "Bagian Awal" sebelum bagian inti pertama, dan "Penutup & Lampiran"
setelah bagian terakhir. Jadi buku yang benar tanpa `@part` tetap punya pengarah untuk
pembacanya.

@figure ../figures/tiga-tingkat.html | Gambar 1.1 Tiga tingkat struktur dan tempat masing-masing berdiri

## 4. Penomoran Subjudul

Nomor pada `## 1. Judul` otomatis jadi lencana berwarna aksen. Kamu cukup mengetik angkanya;
formatter yang memberi warna, posisi, dan proporsinya.

Menulis `## Tanpa Nomor` memberi subjudul biasa tanpa lencana — berguna untuk subbagian
pelengkap yang bukan bagian dari urutan.

## 5. Kendali Halaman

Ada satu perintah yang memaksa pindah halaman.

```markdown
@pagebreak
```

Gunakan hemat. Hampir semua halaman baru sudah tercipta otomatis oleh `#` dan `@part`, jadi
perintah ini biasanya hanya perlu di satu atau dua tempat.

:::limits Di mana `{nobreak}` justru merusak
Atribut `nobreak` berguna untuk bab pendek. Tapi kalau dipakai pada bab panjang, ia bisa
mendorong bab itu ke halaman yang sebagian besar kosong. Kalau setelah build kamu melihat
halaman nyaris kosong, periksa dulu apakah ada `{nobreak}` di dekatnya.
:::

## 6. Daftar Isi

Daftar isi dihasilkan dua kali pass, sehingga nomor halamannya bukan perkiraan melainkan hasil
sebenarnya. Karena itu daftar isi baru benar setelah seluruh naskah selesai ditulis.

Setiap subjudul tidak masuk daftar isi — yang masuk adalah bab dan bagian. Kalau butuh daftar isi
yang lebih detail, tambahkan bab, jangan subjudul.

## 7. Latihan

:::exercise Susun kerangka minimal
Tulis satu `book.yaml` dengan tiga bab, tanpa daftar isi, dan sampul polos. Lalu tulis satu
bab yang hanya berisi paragraf dan satu subjudul. Build, dan perhatikan hasilnya: halaman
tidak akan pernah kosong, tapi juga tidak akan pernah terasa seperti buku.
:::

Latihan ini sengaja dibuat membosankan. Hasilnya membuktikan justru hal yang paling
penting: komponen tidak muncul kalau tidak dipakai.

## 8. Intisari

:::summary Inti bagian ini
Kerangka halaman ditentukan oleh `book.yaml` untuk empat komponen pertama, dan oleh naskah
untuk sisanya.

Bab selalu memulai halaman baru, bagian inti selalu punya pembuka, dan daftar isi bisa dipindah
atau dihilangkan tanpa menyentuh naskah.
:::