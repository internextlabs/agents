# agents

Kumpulan agent, skrip otomasi, dan buku yang dibuat dengan
[Hermes Agent](https://hermes-agent.nousresearch.com).

## Struktur

```
books/                    ebook dan panduan (PDF/DOCX)
  deep-vs-shallow/         Deep Work vs Shallow Work — B5, tema premium
  deep-vs-shallow-v1/      versi pertama (A4, tema korporat), dipertahankan
  panduan-layout-buku/     Panduan Layout Buku — A4, tema teknologi
```

Setiap buku berisi `book.yaml` (konfigurasi), `chapters/` (naskah markdown),
`figures/` (diagram), dan `out/` (PDF/DOCX hasil build). Detail tiap buku ada di README-nya
sendiri.

## Slides

- `slides/` — Presentasi mobile-first bergaya editorial (HTML)
  - `index.html` — Agen AI vs Chatbot AI (15 slide, portrait, desain majalah premium)
- `profesi/` — Profesi Masa Depan di Era AI (16 slide)
- `etika/` — Etika Teknologi: Filsafat Hingga AI (16 slide)
- `ontologi/` — Ontologi AI: Apa Artinya Sebuah Mesin "Ada"? (16 slide)