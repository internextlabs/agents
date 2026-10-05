# Menulis yang Menggambar

Buku saku untuk belajar menulis prompt yang menghasilkan gambar. Fokusnya bukan trik,
tapi cara mengomunikasikan visual ke model, dan di mana batas etikanya.

29 halaman, A5, PDF dan DOCX dari satu sumber.

## Isi

- `verify.md` - 11 klaim mayor dengan 7 sumber, plus daftar yang sengaja tidak diverifikasi
- `book.yaml` - konfigurasi build
- `chapters/` - naskah, 8 file
- `out/` - PDF, DOCX, dan satu lembar pratinjau

## Struktur bab

1. Cara model membaca prompt Anda (dua tahap parsing dan generation)
2. Anatomi prompt yang bekerja (subjek, komposisi, cahaya, gaya, batasan)
3. Mengunci konsistensi lintas beberapa gambar
4. Gaya sebagai bahasa, bukan daftar kata
5. Debugging: ketika hasilnya salah, dan kenapa
6. Etika: watermark, AI Act, likeness, bias
7. Workflow produksi dari ide sampai file jadi

## Catatan etika

Buku ini memuat klaim yang sudah diverifikasi per 5-7 Oktober 2026, termasuk bahwa
watermark SynthID dan metadata C2PA tetap tertanam meski watermark tampilan Gemini
dimatikan, dan bahwa kewajiban pengungkapan AI Act Pasal 50 ada di pihak penerbit.

Buku ini bukan nasihat hukum. Kalau Anda mengirim konten ke yurisdiksi tertentu,
periksa sendiri persyaratannya.

## Build ulang

Butuh venv dengan `pypdf`, `pdfplumber`, `pillow`, `pyyaml`, plus Node dan Playwright.

```bash
uv venv ~/.venvs/pocket
uv pip install --python ~/.venvs/pocket/bin/python pypdf pdfplumber pillow pyyaml

~/.venvs/pocket/bin/python \
  ~/.hermes/skills/productivity/book-layout-designer/scripts/build.py \
  book.yaml --preview --formats pdf,docx
```

Dibuat dengan skill `pocket-book`, tata letak dari `book-layout-designer`.
