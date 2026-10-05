# Deep Work vs Shallow Work

Artikel berbentuk buku (PDF + DOCX) tentang memisahkan pekerjaan yang mengubah sesuatu dari
pekerjaan yang hanya menjaga, lalu menjadikannya sistem yang bisa diukur.

## Hasil

| Berkas | Isi |
|---|---|
| `out/Deep-Work-vs-Shallow-Work.pdf` | 21 halaman, A4, tema korporat |
| `out/Deep-Work-vs-Shallow-Work.docx` | Versi yang bisa disunting di Word |

## Struktur

- **Bagian 1 — Anatomi Dua Mode Kerja**: dua kategori pekerjaan (bukan dua sifat orang), lima
  ciri deep work yang bisa diuji, dan biaya tersembunyi shallow work.
- **Bagian 2 — Mengubah Kebiasaan**: blok berkedalaman, aturan main, lingkungan kerja,
  Template 2.1 (Perencana Blok Mingguan).
- **Bagian 3 — Sistem dan Audit**: audit empat angka, penanganan hari buruk, Template 3.1
  (Audit Mingguan).
- **Lampiran**: glosarium, ringkasan argumentasi, dan daftar hal yang belum terbukti.

## Sumber

- `book.yaml` — konfigurasi buku, tema, dan metadata sampul
- `chapters/*.md` — naskah dalam dialek markdown buku
- `figures/*` — diagram HTML/SVG yang warnanya mengikuti tema

## Build ulang

Dibangun dengan skill `book-layout-designer`:

```bash
python scripts/build.py book.yaml --formats pdf,docx --out out
```

Tema bisa diganti satu baris di `book.yaml`: `korporat`, `edukasi`, `akademik`, `teknologi`,
`alam`, `premium`, atau `ceria`.

## Catatan

Nomor halaman pada daftar isi di DOCX diisi oleh Word saat file dibuka (pilih *update fields*).
Font sudah tertanam di DOCX, tetapi Google Docs mengabaikan font tertanam.