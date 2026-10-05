# Membaca yang Menggugah

Buku saku untuk belajar pribadi. Topik: analisis tematik atas persepsi guru tentang
penggunaan AI oleh siswa, dengan fokus pada perubahan dari melarang ke memfasilitasi.

35 halaman, A5, PDF dan DOCX dari satu sumber.

## Isi

- `verify.md` — 7 klaim mayor, 6 sumber, plus daftar klaim yang sengaja tidak diverifikasi
- `book.yaml` — konfigurasi build
- `chapters/` — naskah, 8 file
- `out/` — PDF, DOCX, dan satu lembar pratinjau

## Struktur bab

1. Analisis tematik itu apa, dan kenapa bukan "baca lalu tulis"
2. Mengenal data tanpa coding dulu
3. Open coding: membuat kode dari data, bukan dari teori
4. Dari kode ke tema: mengelompokkan tanpa memaksa
5. Tema mayor, tabel analisis, dan soal reliabilitas
6. Interpretasi: dari tema ke klaim
7. Batasnya di mana, dan apa yang tidak boleh diklaim

## Build ulang

Butuh venv dengan `pypdf`, `pdfplumber`, `pillow`, `pyyaml`, plus Node dan Playwright.

```bash
uv venv ~/.venvs/pocket
uv pip install --python ~/.venvs/pocket/bin/python pypdf pdfplumber pillow pyyaml

~/.venvs/pocket/bin/python \
  ~/.hermes/skills/productivity/book-layout-designer/scripts/build.py \
  book.yaml --preview --formats pdf,docx
```

## Catatan

Semua guru, transkrip, dan kutipan di buku ini fiktif, dibuat untuk mengilustrasikan
proses. Jangan mengutipnya sebagai temuan penelitian.

Buku ini dibuat dengan skill `pocket-book`, dan tata letaknya dari `book-layout-designer`.
