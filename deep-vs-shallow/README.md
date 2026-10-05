# Deep Work vs Shallow Work

Artikel berbentuk buku (PDF + DOCX) tentang memisahkan pekerjaan yang mengubah sesuatu dari
pekerjaan yang hanya menjaga, lalu menjadikannya sistem yang bisa diukur.

Versi kedua: naskah lebih panjang dan deskriptif, tanpa callout di dalam bab. Setiap bab
ditutup satu kotak intisari.

## Hasil

| Berkas | Isi |
|---|---|
| `out/Deep-Work-vs-Shallow-Work.pdf` | 26 halaman, B5, tema premium (plum & emas, Young Serif/Lora) |
| `out/Deep-Work-vs-Shallow-Work.docx` | Versi yang bisa disunting di Word |

## Struktur

- **Pengantar**: dua kategori kerja, biaya yang tidak tampak, dan dua pertanyaan pemeriksaan
  singkat.
- **Bagian 1 — Anatomi Dua Mode Kerja**: deep work dan shallow work sebagai kategori pekerjaan
  (bukan sifat orang), lima ciri deep work yang bisa diuji, batas sehat shallow work, dan biaya
  tersembunyi.
- **Bagian 2 — Mengubah Kebiasaan**: blok berkedalaman, aturan jadwal, lingkungan kerja,
  contoh sebelum-sesudah, uji batas.
- **Bagian 3 — Sistem dan Audit**: empat angka mingguan, template audit, penanganan hari buruk,
  ukuran nyata.
- **Lampiran**: glosarium, ringkasan argumentasi, apa yang belum terbukti, penutup.

## Sumber

- `book.yaml` — konfigurasi buku, tema, dan metadata sampul
- `chapters/*.md` — naskah dalam dialek markdown buku
- `figures/*` — diagram HTML/SVG yang warnanya mengikuti tema

## Build ulang

```bash
python scripts/build.py book.yaml --formats pdf,docx --out out
```

Tema bisa diganti satu baris di `book.yaml`: `korporat`, `edukasi`, `akademik`, `teknologi`,
`alam`, `premium`, atau `ceria`.

## Catatan

Nomor halaman pada daftar isi di DOCX diisi oleh Word saat file dibuka (pilih *update fields*).
Font sudah tertanam di DOCX, tetapi Google Docs mengabaikan font tertanam.