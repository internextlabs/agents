@part 3 | Komponen Visual | Callout, tabel, template, dan diagram | Komponen Visual

:::goals
- Mengenal 13 jenis callout dan kapan masing-masing dipakai
- Memilih gaya tabel yang tepat untuk jenis datanya
- Menulis diagram tanpa menulis HTML dari nol
:::

## 1. Callout

Callout adalah komponen paling sering dipakai dan paling mudah disalahgunakan. Aturannya
sederhana: satu jenis callout, satu fungsi.

{widths=22,20,58}
| Jenis | Warna | Untuk |
|---|---|---|
| `note` (catatan) | Primer | Informasi tambahan |
| `tip` (tips) | Hijau | Saran praktis |
| `analogy` (analogi) | Aksen | Metafora penjelas |
| `policy` (kebijakan) | Biru | Rujukan resmi |
| `warning` (perhatian) | Merah | Risiko dan larangan |
| `limits` (uji) | Merah | Keterbatasan pendekatan |
| `check` (koreksi) | Hijau | Praktik baik |
| `privacy` (privasi) | Netral | Data pribadi |
| `exercise` (latihan) | Aksen | Tugas praktik |
| `question` (refleksi) | Ungu | Pertanyaan diskusi |
| `example` (contoh) | Biru | Contoh kasus |
| `summary` (intisari) | Kotak gelap | Ringkasan akhir |
| `card` (kartu) | Garis putus | Kartu ringkas |

Semua nama punya padanan bahasa Indonesia, jadi naskah bisa ditulis sepenuhnya dalam bahasa
tanpa perlu mengingat nama aslinya.

```markdown
:::tip Mulai dari asesmen
Tentukan bukti keberhasilan lebih dulu.
:::
```

Aturan praktisnya: maksimal dua callout berturut-turut, dan callout lebih dari dua belas baris
lebih baik dipecah menjadi subbagian biasa.

:::limits Kesalahan yang paling sering terjadi
Menggunakan callout sebagai hiasan. Kalau semua paragraf dibungkus callout, tidak ada lagi
yang menonjol — dan komponen yang paling terlihat justru kehilangan tugasnya. Callout untuk
pengecualian, bukan untuk emphasises.
:::

## 2. Kartu Angka

Kartu angka dipakai untuk fakta kunci, maksimal dua sampai empat kartu dengan nilai pendek.

```markdown
:::stats
- 4 | Prasyarat
- 50 | Menit minimum
- 1 | Tugas per blok
:::
```

## 3. Tabel

Sembilan gaya tabel, dipilih lewat baris atribut tepat sebelum tabel.

{widths=16,34,50}
| Gaya | Efek | Gunakan saat |
|---|---|---|
| Tanpa atribut | Header primer, baris zebra | Tabel data biasa |
| `.dodont` | Kolom hijau dan merah | Ada pasangan lakukan-hindari |
| `.compare` | Dua kolom sebelum-sesudah | Menunjukkan perubahan |
| `.matrix` | Kolom pertama 20% | Perbandingan lintas kategori |
| `.key` | Kolom pertama tebal | Istilah dan definisi |
| `.glossary` | Lebar 26 dan 74 | Daftar istilah |
| `.checklist` | Kotak centang | Daftar periksa |
| `.numbered` | Nomor berwarna aksen | Langkah berurutan |

Lebar kolom diatur terpisah dengan `widths=20,40,40`. Nilai bebas dan dinormalkan otomatis.

Sel sebaiknya maksimal dua puluh lima kata. Lebih dari itu, isi sebaiknya dipindah ke subbagian.

## 4. Kotak Template

Blok kode dengan bahasa `prompt` berubah menjadi kotak template siap salin. Variabel
[seperti ini] otomatis disorot, dan `### LABEL` menjadi subjudul kecil.

````markdown
```prompt Template 2.1 · Nama Template
### KONTEKS
- Peran: [Sebut peran]
```
````

Bahasa lain seperti `python` atau `bash` tetap jadi blok kode biasa dengan chip nama bahasa.

## 5. Diagram

Tujuh bentuk tersedia, dan warnanya otomatis mengikuti tema.

@figure ../figures/diagram-kit.html | Gambar 3.1 Bentuk diagram yang tersedia

Cara menulisnya cukup satu baris:

```markdown
@figure figures/alur.html | Gambar 3.1 Alur proses
```

Path-nya relatif terhadap file markdown, bukan terhadap naskah. Berkas HTML dan SVG dirender
sebagai vektor di PDF dan di-snapshot menjadi PNG untuk DOCX.

:::tip Kalau diagrammu tidak muncul
Periksa dua hal: path-nya relatif terhadap file markdown, dan fragmennya tidak boleh memuat
tag `html` atau `body`. Buka `out/_build/book.html` di browser untuk melihat hasilnya.
:::

## 6. Langkah Bertahap

Daftar bernomor bisa diubah menjadi garis waktu dengan satu baris atribut:

```markdown
{.steps}
1. **Baca** tujuan bagian.
2. **Kerjakan** langkah pertama.
3. **Periksa** hasilnya.
```

Di DOCX, bentuk ini tetap tampil sebagai daftar bernomor biasa.

## 7. Intisari

:::summary Inti bagian ini
Komponen visual bekerja karena dipilih, bukan karena selalu ada.

Satu jenis callout untuk satu fungsi, gaya tabel sesuai bentuk datanya, dan diagram hanya
ketika benar-benar membantu — itulah aturan yang membuat hasilnya terlihat rapi.
:::