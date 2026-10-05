---
name: pocket-book
description: Use for pocket books on a topic. One pass, no gates.
version: 2.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [pocket-book, ebook, belajar, buku, outline, A5, book-layout, humanizer]
    category: productivity
    related_skills: [book-layout-designer, grounded-citations, humanizer, arxiv, pdf]
---

# Pocket Book

Buku saku untuk belajar pribadi dari satu topik. Pengguna memberi topik, Anda kerjakan
sampai PDF dan DOCX jadi, lalu serahkan.

**Kerjakan dalam satu kali jalan. Jangan berhenti untuk minta persetujuan.**

Exception satu-satunya: kalau topik terlalu kabur untuk ditulis dengan masuk akal, tanya
satu hal, lalu jalan. Itu saja.

## When to Use

- "buatkan buku saku soal X", "ebook pribadi untuk belajar X", "buku pengantar X dari nol"
- Topik masih berupa ide besar dan perlu dipersempit
- Pengguna belajar untuk dirinya sendiri, bukan untuk terbit

Jangan pakai untuk: buku anak, modul pelatihan (langsung `book-layout-designer`), konversi
naskah yang sudah ada, ebook akademik untuk publikasi. Brief terakhir butuh rujukan ilmiah,
sitasi, dan peer review.

## Alur Kerja

### 1. Prasyarat

Sekali saja per mesin, bukan tiap buku:

```bash
python ~/.hermes/skills/productivity/book-layout-designer/scripts/check_env.py
```

Kalau `MISS` untuk `pypdf` / `pdfplumber` / `PIL` / `yaml`:

```bash
uv venv ~/.venvs/pocket
uv pip install --python ~/.venvs/pocket/bin/python pypdf pdfplumber pillow pyyaml
```

Venv `~/.venvs/pocket` sudah ada di mesin Tamim, termasuk `pypdfium2` untuk pratinjau.

### 2. Kunci sudutnya, lalu jalan

Pengguna sering memberi topik yang terlalu luas. Pilih sendiri sudut yang paling berguna,
lalu tulis dalam satu kalimat kerangkanya.

Contoh: topik "AI di kelas" di kunci menjadi "guru yang berubah dari melarang ke
memfasilitasi".

Kalau sudut itu tidak mungkin dipilih tanpa menebak besar, tanya satu hal. Kalau bisa
ditebak, jangan tanya.

Buat kerangka di kepala, tidak perlu ditunjukkan. Enam sampai delapan bab, satu pekerjaan
per bab.

### 3. Verifikasi secukupnya

Cari **3 sampai 7** sumber kredibel untuk klaim yang kalau salah akan menyesatkan.
Daftar di ledger:

```bash
S=~/.hermes/skills/research/grounded-citations/scripts/sources.py
python "$S" reset
python "$S" add https://... --title "..."
```

Ini bukan proyek riset. Kalau sudah 15 sumber, berhenti.

Tulis `verify.md`: klaim, sumber, dan daftar klaim yang sengaja dibiarkan tanpa sumber.

### 4. Tulis

Tulis bab per bab, satu bab satu file.

- **Prosa adalah bentuk defaultnya.** Tujuh baris tanpa jeda = dinding. Pecah.
- **Bahasa percakapan.** Mulai dengan "Bayangkan...", bukan "Kita akan membahas...".
  Jelaskan tiap istilah baru di tempat pertama muncul.
- **Contoh konkret.** Setiap konsep abstrak butuh contoh atau analogi.
- **Jelaskan, jangan listingkan.** Tiap konsep kunci: apa itu, kenapa penting, bagaimana
  bekerja, contoh, kapan berlaku atau tidak.
- **Satu kalimat penutup tiap bab.** Bukan kotak summary.

### 5. Pass humanizer

Jalankan setiap bab terhadap skill `humanizer` (26 pola). Wajib.

Yang paling sering bocor di prosa panjang: kontras "bukan X tapi Y", penutup satu kalimat,
triad paksa, dash, **tebal** sebagai hiasan, sisa gaya chatbot ("Berikut ringkasannya",
"Semoga bermanfaat"), penyebutan batas pengetahuan.

Aturan anti-dash berlaku keras di sini: dokumentasi teknis buku memang pakai em-dash,
jadi abaikan tanda itu hanya di prosa. Code dan path dikecualikan.

### 6. Build

```
<topik-slug>/
├── verify.md
├── book.yaml
└── chapters/00-awal.md, 01-....md
```

`book.yaml`:

```yaml
title: <Judul>
subtitle: <satu kalimat jujur>
lang: id
theme: edukasi        # edukasi | korporat | akademik | teknologi | alam | premium
page_size: A5
part_label: Bab
toc_after: Tentang Buku Ini
cover:
  motif: book
  tagline: <hook spesifik>
chapters: [chapters/*.md]
output:
  name: <Nama>-Pocket-Book
  formats: [pdf, docx]
```

```bash
~/.venvs/pocket/bin/python \
  ~/.hermes/skills/productivity/book-layout-designer/scripts/build.py \
  <topik-slug>/book.yaml --preview --formats pdf,docx
```

### 7. Cek visual, lalu serahkan

Buka `out/preview-pdf/sheet_*.jpg` dengan vision. Cek sampul, daftar isi bernomor, tabel
tidak meluap, tidak ada halaman kosong. Perbaiki kalau perlu, build ulang.

Kirim PDF dan DOCX. Sertakan: sudut yang dipilih, jumlah halaman dan bab, jumlah sumber
terverifikasi, klaim yang belum diverifikasi, dan satu kalimat tentang apa yang tidak
dibahas.

---

## Aturan Callout

`book-layout-designer` menyarankan satu jangkar visual per halaman. Untuk buku saku,
abaikan. Itu density modul pelatihan.

- `:::note/tip/analogy/example` - **maks 1 per 2-3 halaman**
- `:::summary` - **1 per buku**, di bab terakhir saja
- `:::warning` / `:::limits` - hanya kalau ada risiko nyata salah paham
- `{.dodont}` / `{.compare}` - boleh, ini tubuh bukan hias
- `@figure` diagram - 1-2 di seluruh buku
- `{.glossary}` - 1 di lampiran

Diagnostik: kalau lebih dari 15% halaman berisi kotak atau tabel, itu modul pelatihan.

Yang boleh banyak: paragraf, subjudul, tabel data, daftar.

## Anti-patterns

- Berhenti di tengah jalan untuk minta persetujuan
- Mengganti nama skill pemanggil jadi "ebook" atau "book"
- Verifikasi 40 sumber untuk buku 40 halaman
- Tiap bab punya `:::summary` plus `:::tips` plus `:::analogy`
- 200 halaman dengan 6 bab
- Checklist review, bukan penjelasan

## Catatan Teknis

- **Tabel markdown punya risiko rusak.** Pakai daftar bila bisa.
- **Naskah panjang**: tulis per bab. Scan tiap bab untuk karakter non-Latin sebelum build,
  karena karakter asing bisa masuk diam-diam ke prosa Bahasa Indonesia.
