# Panduan Layout Buku

Dokumentasi sebuah sistem tata letak buku: komponen apa saja yang tersedia, sintaksnya, dan
bagaimana mengaturnya.

## Hasil

| Berkas | Isi |
|---|---|
| `out/Panduan-Layout-Buku.pdf` | 22 halaman, A4, tema teknologi |

Versi DOCX belum dibangun. Untuk menambahkannya:

```bash
python scripts/build.py book.yaml --formats pdf,docx --out out
```

## Struktur

- **Bagian 1 — Kerangka Halaman**: urutan halaman, tiga tingkat struktur, atribut bab,
  penomoran subjudul, daftar isi
- **Bagian 2 — Tipografi dan Warna**: pasangan huruf, skala tipografi, peran warna, kontras
  WCAG, panduan cetak
- **Bagian 3 — Komponen Visual**: 13 jenis callout, kartu angka, 9 gaya tabel, kotak template,
  7 bentuk diagram
- **Bagian 4 — Tema dan Build**: memilih tema, membuat tema sendiri, kunci `book.yaml`, opsi
  build
- **Lampiran**: daftar periksa sebelum dan sesudah build, tabel sintaks, masalah yang sering
  muncul

## Sumber

- `book.yaml` — konfigurasi buku, tema, dan metadata sampul
- `chapters/*.md` — naskah dalam dialek markdown buku
- `figures/*` — diagram HTML yang warnanya mengikuti tema

## Build ulang

```bash
python scripts/build.py book.yaml --formats pdf --out out
```

Tema tersedia: `edukasi`, `korporat`, `akademik`, `teknologi`, `alam`, `premium`, `ceria`.
Ganti satu baris di `book.yaml` untuk berpindah tema.

## Catatan

Nomor halaman daftar isi di DOCX diisi oleh Word saat file dibuka (pilih *update fields*), karena
LibreOffice tidak tersedia di lingkungan build ini.