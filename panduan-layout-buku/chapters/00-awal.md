# Pengantar

Buku ini adalah dokumentasi dari sebuah sistem tata letak buku. Bukan teori desain, dan bukan
buku tentang menulis — tapi penjelasan teknis tentang komponen apa saja yang tersedia,
kapan dipakai, dan bagaimana mengaturnya.

Kalau kamu sedang membaca ini karena ingin membuat ebook, modul pelatihan, handbook, atau
laporan panjang, maka semua yang kamu butuhkan ada di sini: daftar komponen, sintaksnya,
dan batasannya.

:::note Untuk siapa buku ini
Buku ini cocok dibaca oleh dua jenis pembaca. Orang pertama ingin tahu komponen apa saja yang
bisa dipakai — bagian 1 sampai 3. Orang kedua sedang membangun naskah dan butuh rujukan cepat
— lampiran di bagian akhir.
:::

## 1. Masalah yang Diselesaikan

Menata dokumen panjang secara manual.itu It'll selalu berhenti di jebakan yang sama. Gambar
terbelah di batas halaman. Label callout terpisah dari isinya. Daftar isi tanpa nomor halaman.
Baris terpotong di DOCX karena spasi baris yang salah.

Sistem ini membungkus semuanya dalam satu perintah build, sehingga jebakan itu ditangani
otomatis.

@figure ../figures/alur-kerja.html | Gambar 1.1 Alur kerja dari naskah menjadi buku

Yang tersisa bagi penulis hanya satu pekerjaan: menyusun isi dan struktur yang baik, lalu
memeriksa hasilnya secara visual.

## 2. Prinsip yang Dimegangi

Sebelum masuk ke detail, empat prinsip yang menjelaskan hampir semua keputusan teknis di
dalam sistem ini.

{widths=26,74}
| Prinsip | Artinya |
|---|---|
| Opt-in | Komponen muncul hanya jika ditulis; tidak ada yang dimuat otomatis |
| Anti-terbelah | Diagram, callout, dan baris tabel tidak pernah dipecah halaman |
| Warna bermakna | Setiap warna punya peran, bukan sekadar hiasan |
| nearsamaan | PDF dan DOCX terlihat sama, walau satu untuk baca dan satu untuk sunting |

Prinsip opt-in adalah yang paling liberating: kamu tidak pernah dibayar komponen yang tidak
mau kamu pakai. Prinsip anti-terbelah yang paling besar pengaruhnya ke rasa profesional —
banyak dokumen pelatihan terlihat murahan karena tepat satu hal: gambar terbelah antar halaman.

## 3. Peta Perjalanan

{widths=14,44,42}
| Bagian | Isi | Untuk siapa |
|---|---|---|
| Bagian I | Kerangka halaman, struktur bab, dan penomoran | Semua orang |
| Bagian II | Tipografi, warna, dan sistem desain angka | Yang ingin paham alasan |
| Bagian III | Komponen visual: callout, tabel, template, diagram | Yang sedang menulis naskah |
| Bagian IV | Tema, kontras, dan kendali build | Yang ingin melakukan kostumisasi |

Bagian I dan III adalah yang paling sering dipakai. Bagian II dan IV bersifat referensi.

## 4. Cara Baca

Buku ini bisa dibaca berurutan dalam satu kali, atau dipakai sebagai rujukan saat menulis.
Kalau kamu sedang terburu-buru, baca bagian I bagian 2 dan bagian III bagian 2 — itu jalur
terpendek untuk bisa langsung menulis naskah.

Semua sintaks komponen ditampilkan apa adanya sehingga bisa langsung disalin.

:::summary Pesan yang perlu dibawa pulang
Sistem tata letak yang baik bukan yang paling banyak komponennya, tapi yang paling mudah
dikendalikan: kamu menentukan apa yang muncul, dan sisanya otomatis benar.

Kuasai kerangkanya, lalu pakai komponen seperlunya.
:::