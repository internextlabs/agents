# Menolak Irama Silikon

Buku pendek hasil tulis ulang esai **"Menolak Irama Silikon: Membela Lambatnya Pikiran di Tengah
Badai Akselerasi Mesin"** (Simbioma.net, Oktober 2026).

## Hasil

| Berkas | Isi |
|---|---|
| `out/Menolak-Irama-Silikon.pdf` | 18 halaman, B5, tema alam (hijau & pasir) |

Tema `alam` memakai **Work Sans** untuk judul dan **IBM Plex Serif** untuk teks isi.
Sampul memakai motif gelombang.

## Struktur

- **Pengantar** — adegan stasiun, ironi pembebasan yang tidak terjadi, dan peta
  isi.
- **Bab 1 · Genealogi Tirani Detak** — dari jam mekanis di menara biara abad pertengahan (Lewis
  Mumford) hingga dikotomi Chronos–Kairos dan kronopolitik asimetris.
- **Bab 2 · Biologi Ketidaksabaran** — jaringan mode bawaan, amputasi inkubasi mental, masyarakat
  kelelahan menurut Byung-Chul Han.
- **Bab 3 · Suaka Lambat di Ruang Kelas** — sekolah yang meniru rasionalitas pabrik, pedagogi waktu
  lambat, empat langkah praktis, dan batasnya.
- **Penutup · Kemerdekaan Budi** — satu kutipan, satu intisari, glosarium, dan catatan sumber.

## Catatan penyusunan

- Tepat **satu** callout kutipan dan **satu** callout intisari, keduanya di bab penutup.
- Nama tokoh dan rujukan hanya diambil dari artikel asli: Lewis Mumford, Byung-Chul Han, James
  Watt, serta konsep Chronos dan Kairos. Tidak ada klaim faktual baru yang ditambahkan.
- Tabel memakai gaya `matrix`, `dodont`, dan `glossary`.

## Build ulang

```bash
python scripts/build.py book.yaml --formats pdf --out out
```

Sumber artikel mentah tersimpan di `_sumber/artikel.txt`.