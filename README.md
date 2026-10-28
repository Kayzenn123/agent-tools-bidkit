# bidkit — kios penawaran freelance

> nego dulu, jangan asal bid.

satu kios buat freelancer indonesia yang bid di **projects.co.id** dan **sribu**: 9 template proposal siap kirim, kalkulator harga bersih setelah fee platform, dan checklist portofolio 12 item.

## fitur

- **kios template** — 9 template (ui/ux, web dev, desain grafis × sopan / to-the-point / portofolio-dulu). isi datamu, proposal langsung jadi di karcis, salin atau unduh .txt.
- **kalkulator harga bersih** — fee projects.co.id 12% (fakta resmi), biaya transfer (gratis bca/bni/mandiri, rp7.500 bank lain), bandingkan dengan budget klien min–maks. fee sribu tidak dipublikasi resmi → diisi manual, bukan dikarang.
- **checklist portofolio** — 12 item, progres tersimpan, ekspor json.
- **deep-link** — `?template=web-cepat&nama=rani&harga=1500000` — isian ikut kebawa lewat tautan.
- **penyimpanan lokal** — semua data di localstorage (`bidkit-v1`), tidak dikirim ke server.

## fakta yang dipakai (dicek 28 okt 2026)

| fakta | sumber |
|---|---|
| fee projects.co.id 12% ke worker, bid gratis & tertutup | [syarat layanan projects.co.id](https://projects.co.id/public/pages/syarat_layanan) |
| escrow: owner bayar dulu, worker dibayar setelah selesai | [faq umum projects.co.id](https://projects.co.id/public/pages/faq_umum) |
| penarikan gratis bca/bni/mandiri, rp7.500 bank lain, maks rp100jt | [syarat layanan projects.co.id](https://projects.co.id/public/pages/syarat_layanan) |
| kontes sribu 7 hari, 1 pemenang, refund kalau &lt;15 desain | [syarat & ketentuan sribu](https://go.sribu.com/id/syarat-ketentuan/) |
| fee sribu **tidak dipublikasi** resmi | — (di tool jadi input manual) |

kisaran harga di halaman berlabel **"estimasi"** — dari blog & price list penyedia individual, bukan survei harga pasar.

## tech

- astro v7 + tailwind css v4 (template astrowind)
- font: allura (display), catamaran (body), playwrite au vic (aksen) — via astro fonts api (fontsource, self-hosted)
- ikon: tabler via astro-icon + svg custom garis putus-putus
- tanpa framework js di klien — vanilla js, tanpa tracker

## jalanin lokal

```bash
npm install
npm run dev     # http://localhost:4321
npm run build   # output ke dist/
```

## skor

- lighthouse: (isi setelah ukur di url live)
- qa.js: (isi setelah jalan)

## lisensi

font ofl (allura, catamaran, playwrite au vic). ikon tabler (mit). kode: mit.
