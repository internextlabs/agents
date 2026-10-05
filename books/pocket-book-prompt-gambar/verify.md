# Catatan Verifikasi

Buku ini untuk belajar pribadi. Verifikasi di sini kecil saja: hanya klaim yang kalau
salah akan membuat pembaca menyimpulkan sesuatu yang keliru.

Tujuh sumber, semua dicek ulang.

## Klaim yang diverifikasi

**1. Urutan kata memengaruhi berat interpretasi model, dan frame sebaiknya di depan.**
Praktik ini konsisten di panduan praktis maupun di kerangka terstruktur. Sumber: [2], [3].

**2. Prompt yang bekerja bukan prompt panjang, tapi prompt yang mengurangi ruang tebakan.**
Ini konsisten di seluruh sumber: [2], [3], [5].

**3. Kerangka SCHEMA memakai tujuh label inti.**
Subject, style, lighting, background, composition, mandatory, prohibitions. Dari 850
prediksi API terverifikasi. Sumber: [1].

**4. Memberi setiap gambar referensi satu peran tertentu.**
Ketiga sumber menyebut ini eksplisit. Model tidak menebak mana yang untuk apa.
Sumber: [1], [2], [3].

**5. Mengubah satu variabel besar per putaran.**
Aturan ini muncul konsisten, dan SCHEMA mencatatnya sebagai penyebab utama
iterative drift yang destruktif. Sumber: [1], [2].

**6. Negasi sering berbalik menghasilkan hal yang dilarang.**
Model lebih andal untuk melakukan daripada tidak melakukan. Sumber: [2], [3].

**7. Watermark SynthID dan metadata C2PA tetap tertanam meski watermark tampilan
dimatikan.**
Dikonfirmasi terbuka oleh Josh Woodward, VP Google Labs, dan dalam dokumentasi Google.
Sumber: [5], [6], [7].

**8. Watermark tampilan Gemini menjadi opsional sejak 14 Agustus 2026.**
Sebelum tanggal itu,oggle tidak tersedia. Sumber: [5], [6], [7].

**9. SynthID tahan terhadap crop, resize, filter, dan kompresi lossy.**
Berkas yang di-crop menghilangkan watermark pojok, tapi bukan pola SynthID. Sumber: [7].

**10. Kewajiban pengungkapan AI Act Pasal 50 ada di pihak deployer, bukan provider.**
Dan kewajiban itu tidak discharged oleh badge. Sumber: [5], [6].

**11. Larangan Google adalah soal menyesatkan asal-usul, bukan soal menghapus badge.**
Google juga menyatakan tidak mengklaim kepemilikan atas konten yang dihasilkan.
Sumber: [5], [7].

## Yang sengaja tidak diklaim

- Tidak ada angka empiris tentang seberapa sering model complies dengan setiap
  label. Angka yang beredar berasal dari self-report praktisi, bukan pengukuran
  independen, dan saya tidak meneruskannya sebagai fakta.
- Tidak ada klaim tentang model selain yang disebut. Model lain mungkin tidak bisa
  membaca teks di dalam gambar seperti yang disebut di sini, atau sebaliknya lebih
  ketat. Periksa dulu sebelum Anda percaya.
- Tidak ada tafsir hukum di luar yang tertulis di atas. Shipping di yurisdiksi Anda
  sendiri adalah urusan lawyer, bukan buku saku.

## Daftar Sumber

[1] SCHEMA: A Structured Methodology for Controlled AI Image Generation on Google's
Native Multimodal Model.
https://arxiv.org/pdf/2602.18903

[2] How to Prompt Nano Banana 2 and Nano Banana Pro.
https://hubstudio.ai/resources/how-to/nano-banana-prompting-guide

[3] The Nano Banana Pro prompting guide.
https://sceneos.io/kb/nano-banana-pro-prompting-guide

[4] The Nano Banana Pro guide: spesifikasi, aspect ratio, resolusi.
https://sceneos.io/kb/nano-banana-pro

[5] Google's Gemini Watermark Toggle Doesn't Touch Your Article 50 Duty.
https://softxone.com/google-gemini-watermark-toggle-ai-act

[6] Visible AI watermarks in 2026: what Google's toggle changed, why invisible SynthID
stays, and how creators disclose now.
https://kompozy.io/guides/visible-ai-watermarks

[7] Does a watermark remover remove SynthID too?
https://atlascloud.ai/blog/tips/does-a-gemini-watermark-remover-remove-synthid
