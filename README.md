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