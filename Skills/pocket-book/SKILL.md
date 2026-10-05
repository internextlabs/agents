---
name: pocket-book
description: Use for pocket books on a topic. 3 gated phases.
version: 1.0.0
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

Buku saku untuk belajar pribadi. Pengguna memberi satu topik; skill ini memastikannya menjadi
buku pendek yang benar-benar membantu memahami, bukan ringkasan bertele-tele.

Tiga aturan yang tidak bisa ditawar:

1. **Tiga gerbang, berurutan.** Pemetaan tujuan → outline → tulis. Tidak ada penulisan sebelum
   outline disetujui pengguna.
2. **Komprehensif, bukan ringkas.** Penjelasan harus membuat pembaca bisa menerapkan,
   bukan cuma mengenali.
3. **Callout minimal.** Dinding prosa adalah bentuk defaultnya. Kotak warna adalah pengecualian.

Skill ini mengatur **isi**. Skill `book-layout-designer` mengatur **tata letak** — jangan
tulis HTML/CSS sendiri, jangan bikin dokumen manual, teruskan naskahnya ke `build.py`.

## When to Use

Pakai skill ini saat pengguna memberi satu topik dan ingin memahaminya lewat buku
pribadi yang pendek:

- "buatkan buku saku soal X", "ebook pribadi untuk belajar X", "buku pengantar X dari nol"
- Topik masih berupa ide besar ("mau paham soal X") dan perlu dipersempit lebih dulu
- Pengguna sedang dalam tahap belajar dan mau paham, bukan pembaca yang butuh materi siap pakai

Jangan pakai untuk:

- Buku anak → butuh brief dan rentang usia tersendiri; `book-layout-designer` langsung
- Modul pelatihan / LKPD → `book-layout-designer` langsung, tanpa gerbang
- Konversi naskah yang sudah ada → itu pekerjaan `book-layout-designer` (lihat bagian
  "Sumber masukan yang sudah ada" di SKILL.md itu), bukan penulisan baru
- Ebook akademik untuk publikasi → brief-nya berbeda total: perlu rujukan ilmiah,
  format sitasi, dan peer review; bukan target 5-12 sumber

Tanda jelas skill ini yang tepat: pengguna meminta sesuatu yang **membuat dia sendiri paham**,
dan belum jelas aplikasi output-nya.

---

## Step 0 — Periksa prasyarat lebih dulu

`book-layout-designer` butuh build yang sehat. Jalankan sekali:

```bash
python ~/.hermes/skills/productivity/book-layout-designer/scripts/check_env.py
```

Kalau ada `MISS` untuk `pypdf` / `pdfplumber` / `PIL` / `yaml`, install ke venv lokal
(container ini uid 10000, tanpa sudo — jangan coba `apt-get`):

```bash
uv venv ~/.venvs/pocket && source ~/.venvs/pocket/activate
uv pip install pypdf pdfplumber pillow pyyaml
```

`pdftoppm` dan LibreOffice itu OPSIONAL. Tanpa mereka preview visual tidak bisa dirender dan
nomor halaman DOCX tidak ter-cache — PDF tetap jalan. Katakan ke pengguna, jangan diamkan.

---

## Gerbang 1 — Memetakan tujuan belajar

Pengguna memberi topik. **Jangan tulis apa pun.**

Turunkan topik itu menjadi 3-5 pertanyaan yang paling menarik dan berguna *khusus untuk orang
ini*. Terlalu luas = buku dangkal, terlalu sempit = buku catatan.

**Tanya 2-4 pertanyaan.** Pilih yang benar-benar mengubah isi, bukan yang bisa diasumsikan:

- Sudut pandang — ingin paham mekanismenya, atau cari jawaban masalah spesifik?
- Level — sudah tahu dasar atau benar-benar nol?
- Kegunaan — mau dipakai dalam pekerjaan, atau rasa ingin tahu pribadi?
- Batas — berapa yang reader tidak mau sentuh?

Kalau pengguna sudah menjawab sebagian besar, jangan tanya yang sudah terjawab. Tanya sisanya
atau langsung ke Gerbang 2.

Format: tabel 5 kolom — `#` | pertanyaan | mengapa penting | jawaban yang cukup | status.
Status `✓` kalau terjawab, `?` kalau belum, `—` kalau sengaja diabaikan.

Tutup gerbang dengan pertanyaan produk akhir yang realistis: "Setelah baca ini, Anda akan
bisa <x> dan bisa menjawab <y>."

**JANGAN** lanjut menulis. Minta persetujuan eksplisit: *"Cukup? Lanjut outline?"*

## Gerbang 2 — Merancang outline

6-8 bab. Fokus, bukan komprehensif. Setiap bab punya SATU pekerjaan dalam progresi belajar.

Format tiap baris:

```
Bab 3 · Memahami mekanisme inti
   Job    : menjelaskan kenapa <x> terjadi seperti itu
   Muat   : 2-3 konsep kunci
   Contoh : satu analogi konkret dari kehidupan sehari-hari
   Ketiklan: Bab 2 (menyiapkan istilah)
   Output : pembaca bisa menjelaskan sendiri ke orang lain
```

Tunjukkan. Minta persetujuan per bab: mana yang terlalu dalam, mana yang kurang, ada yang
tidak perlu. Setelah disetujui, **kunci urutannya** — jangan ubah struktur di tengah penulisan
tanpa menjelaskan.

Tetapkan juga:
- **Judul + subjudul** yang jujur (bukan hiperbolis; ini buku pribadi)
- **Tema** dari `book-layout-designer` — pilih yang cocok isi dan sebutkan dalam satu kalimat.
  Default: `edukasi` (teal/amber, Poppins/Lora).
- **Ukuran**: A5.

## Gerbang 3 — Verifikasi klaim mayor, lalu tulis

### 3a. Verifikasi (WAJIB, dan kecil)

Tulis dulu naskah di kepala: klaim faktual atau psikologis apa yang kalau salah akan membuat
buku ini menyesatkan? Daftar hanya yang **load-bearing** — biasanya 3-7.

Untuk tiap klaim itu, cari 1-2 sumber kredibel. Gunakan `web_search` lalu `web_extract`, dan
catat URL-nya di ledger `grounded-citations`:

```bash
S=~/.hermes/skills/research/grounded-citations/scripts/sources.py
python "$S" reset
python "$S" add https://... --title "..."
python "$S" list
```

**Ini bukan proyek riset.** Target 5-12 sumber untuk seluruh buku. Kalau sudah 20 sumber dan
masih menggali, berhenti — Anda menulis skripsi, bukan buku saku. Yang diverifikasi cuma klaim
mayor; detail umum cukup dari pengetahuan model, tandai `[unverified]` kalau memang tidak bisa
di-sumberkan.

Simpan hasilnya sebagai `verify.md` — catatan singkat per klaim, sumber, status. Jejak yang
berguna untuk pembaca skeptis dan untuk revisi.

### 3b. Menulis bab per bab

Tulis satu bab, baru lanjut. Menulis semuanya sekaligus adalah cara tercepat untuk
menghasilkan tiga bab repetitif dan satu bab bagus di akhir.

Aturan isi:

- **Prosa atau blok.** Tujuh baris tanpa jeda = dinding. Pecah, atau ubah jadi daftar/tabel.
- **Bahasa percakapan.** Mulai dengan "Bayangkan..." bukan "Kita akan membahas...". Jelaskan
  tiap istilah baru di tempat pertama muncul.
- **Contoh konkret.** Setiap konsep abstrak butuh contoh. Kalau tidak ada, tulis analoginya.
- **Jelaskan, jangan listingkan.** Tiap konsep kunci: apa itu → kenapa penting → bagaimana
  bekerja → contoh → kapan berlaku/tidak.
- **Sesuaikan level.** Kalau pembaca belum tahu prasyaratnya, masukkan di bab awal atau di
  kotak definisi, jangan diasumsikan.
- **Tutup tiap bab dengan satu kalimat kunci**, bukan kotak summary berwarna.

### 3c. Pass humanizer WAJIB

Sebelum build, jalankan setiap bab terhadap skill `humanizer` (26 pola). Wajib — tanda AI
sangat mudah bocor di prosa panjang.

Yang paling sering bocor di prosa buku: §1 kontras "bukan X tapi Y", §2 penutup satu kalimat,
§6 triad paksa, §8 dash untuk semua, §19 **tebal** sebagai hiasan, §22 sisa gaya chatbot
("Berikut ringkasannya", "Semoga bermanfaat"), §23 penyebutan batas pengetahuan.

Aturan §8 berlaku keras di sini: panduan buku secara teknis juga memakai em-dash, jadi abaikan
tanda itu hanya di prosa. Code, command, dan nama file dikecualikan seperti biasa.

## Gerbang 4 — Layout dan build

Pass naskah ke `book-layout-designer`. Baca dialek markdown-nya untuk sintaks persis —
file-nya milik skill itu, bukan skill ini:

```
~/.hermes/skills/productivity/book-layout-designer/references/markdown-dialect.md
```

Isinya mencakup seluruh komponen (`#` bab, `@part`, `:::` callout, `{.dodont}` tabel,
`@figure` diagram, ` ```prompt ` template) beserta kerangka bab yang direkomendasikan.

```
<topik-slug>/
├── verify.md
├── book.yaml
└── chapters/
    ├── 00-awal.md
    └── 01-….md
```

`book.yaml`:

```yaml
title: Memahami <Topik>
subtitle: <satu kalimat jujur tentang apa yang pembaca dapat>
lang: id
theme: edukasi
page_size: A5
part_label: Bab
toc_after: Tentang Buku Ini
cover:
  motif: book
  tagline: <hook spesifik, bukan generalisasi>
  title_lines:
    - {text: Memahami, style: small}
    - {text: <TOPIK>}
chapters: [chapters/*.md]
output:
  name: <Topik>-Pocket-Book
  formats: [pdf, docx]
```

Build:

```bash
python ~/.hermes/skills/productivity/book-layout-designer/scripts/build.py \
  <topik-slug>/book.yaml --preview --formats pdf,docx
```

### Aturan callout — BAGAIMAN

`book-layout-designer` merekomendasikan satu jangkar visual per ±1 halaman. **Untuk buku saku
ini, abaikan.** Itu density modul pelatihan, bukan buku baca.

| Komponen | Density |
|---|---|
| `:::note`, `:::tip`, `:::analogy`, `:::example` | **maks 1 per 2-3 halaman** |
| `:::summary` | **1 per buku**, di bab terakhir saja |
| `:::warning` / `:::limits` | Hanya kalau ada risiko nyata salah paham |
| `{.dodont}` / `{.compare}` | Boleh — ini tubuh, bukan hias |
| `@figure` diagram | 1-2 di seluruh buku |
| `{.steps}` | Hanya untuk prosedur yang benar-benar berurutan |
| `{.glossary}` | 1 di lampiran |

Diagnostik: **kalau >15% halaman berisi kotak/tabel/diagram, itu modul pelatihan.** Kurangi dan
tulis prosa lebih banyak.

Yang tetap boleh banyak: paragraf, subjudul, tabel data, daftar.

### Pemeriksaan visual

WAJIB — ini satu-satunya cara Anda tahu hasilnya bagus:

```bash
ls <topik-slug>/out/preview-pdf/
```

Baca `sheet_*.jpg` dengan vision Anda. Cek: sampul (identitas atau generik?), daftar isi
(nomor halaman benar?), tidak ada halaman nyaris kosong, tabel tidak meluap, tidak ada dinding
teks > 7 baris tanpa jeda, callout tidak lebih dari seperempat halaman. Perbaiki, build ulang,
periksa lagi.

## Menyerahkan

Kirim PDF dan DOCX (DOCX kalau user mau mengedit). Sertakan:

- Topik dan sudut yang dipilih
- Halaman, jumlah bab, jumlah sumber terverifikasi
- **Blokir yang belum terverifikasi** — klaim dari pengetahuan model, jujur disclose
- Satu kalimat tentang apa yang TIDAK dibahas (batas buku ini)

---

## Anti-patterns

- Menulis draft lengkap sebelum outline disetujui
- Langsung 8 bab tanpa Gerbang 1
- 40 sumber untuk buku 40 halaman
- Tiap bab punya `:::summary` + `:::tips` + `:::analogy` — jadi modul pelatihan
- Mengganti nama skill pemanggil jadi "ebook" atau "book" — nama pemanggil wajib
- 200 halaman dengan 6 bab
- Checklist review, bukan penjelasan
- Menyebut `humanizer` tapi tidak menjalankan pass-nya

## Contoh kickoff

Pengguna: *"Buku saku soal how to have difficult conversations at work."*

Jawaban yang benar: **dua pertanyaan klarifikasi, lalu lima pertanyaan turunan, belum satu
paragraf pun naskah.** Pertanyaan pertama bukan "sebutkan subtopik" tapi "konflik apa yang paling
sering Anda hadapi" — itu yang menentukan isi bab, bukan daftar topik generik.