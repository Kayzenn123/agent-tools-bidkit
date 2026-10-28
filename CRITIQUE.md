# CRITIQUE — bidkit — 2026-10-28

## Slop test (v3) + 3 hal paling template + yang dirombak
- slop test: logo ditutup pun tetap ketahuan — kata raksasa tulisan tangan + semua teks huruf kecil + garis putus-putus + stempel "sah" berputar. bukan web ai generik.
- 3 hal paling template: (1) tabel contoh kisaran harga — mirip tabel biasa; dirombak: label "estimasi" eksplisit + kolom sumber per baris. (2) faq details standar; dirombak: jawaban pakai suara makelar + sumber resmi per jawaban. (3) tombol cta "buka kiosnya" — generik; dipertahankan karena fungsional, tapi didahului kata raksasa sebagai pembeda.
- keputusan berani & signature moment kelihatan dalam 5 detik: kata "bidkit" 28vw + "nego dulu, jangan asal bid" + tombol kios — terverifikasi di screenshot mobile-390.

## Gerbang gerak (v4)
- lapisan gerak: 5 kategori — A terbang scroll (zoom 1,6× + rotate + pan), B 3 marquee band + skew velocity, C flip huruf + kata jatuh-menumpuk, D hover kartu ubah tema halaman, E clip-path lingkaran reveal + draw-on. F tidak dipakai (sengaja).
- zoom: ya (1→1,6×). pan horizontal: tidak ada pan pinned — diganti pan translateX 30px saat zoom (alasan: konten kios vertikal, pan pinned akan mengunci scroll). marquee: 3 band, arah berlawanan, kecepatan beda. FPS 4x: 59,8 (chromium throttle).
- font/palet/gaya ikon beda dari 7 build terakhir: allura/catamaran/playwrite-au-vic baru; light/tetradic baru; garis putus-putus — dipakai warteg 2026-10-19 (dashed 2px lucide) — mirip tapi bukan sama: di sini dashed jadi sistem (border, marquee, stempel, ikon custom), bukan aksen. dicatat sebagai risiko kemiripan parsial.
- kontras AA: teks #241a33 di #f6f1fb ±13:1; muted #6b5a80 ±5,4:1; tombol oranye + teks putih ±4,6:1. lolos AA.
- body terbaca di 390px: ya (screenshot dicek).
- reduced-motion dites: 0 animasi berjalan. mode ringan: aktif otomatis di vm (hardware ≤4 core) — tombol "gerak: mati" tampil benar.

## Gerbang v5
- tes bandingkan: vs loakan (papan stiker), dompetkita (papan loket), timlomba (terminal) — bidkit beda: poster tipografi raksasa + semua huruf kecil + script font.
- tes blur: komposisi masih punya identitas — satu kata raksasa + 3 band garis.
- tes 3 detik: orang asing paham ini tentang bid freelance (subline + kata "kios" + cta).
- keyboard-only: tab kategori pakai arrow keys, kartu pakai enter/spasi, skip link ada, focus ring jelas. lulus (diuji manual via playwright untuk tab + kartu).
- reduced-motion: lulus (0 animasi).
- mode ringan: lulus — marquee statis, zoom mati, layout tetap rapi.
- budget: js total (inline script ~9kb) + astro runtime kecil; css ≤60kb; font 3 family self-hosted; gambar di atas fold: 0 raster (semua svg/css). lcp/cls/inp: belum terukur di vm (lihat bawah).
- keamanan: tidak ada innerhtml untuk data user (textcontent/pre), url params divalidasi tipe & panjang (number, url https), localstorage try/catch + cek skema, tidak ada api key, tidak ada tracker.
- lisensi: font ofl, ikon tabler mit, semua gambar buatan sendiri (svg/css). lolos.
- dipangkas: lapisan F (shader/fisika) — tidak butuh; halaman demo template (homes/landing/pricing/services/about/contact/blog) dihapus dari build; gsap/lenis tidak dipakai — vanilla js cukup & lebih ringan.

## Budget performa + Lighthouse
- qa.js: exit 0 (chromium + webkit tidak dites webkit — lihat bawah). fps4x 59,8.
- lighthouse: BELUM TERUKUR — chrome headless tidak bisa launch di vm (plafon yang sama seperti build 2026-10-22/23/25). dicoba lagi di url live; kalau gagal, catat sebagai belum terverifikasi, bukan dikarang.
- js/css/font: js inline ~9kb, css tailwind terkompresi, font 7 file self-hosted.

## Skor 1-10
- karakter: 9 — persona makelar + huruf kecil total + stempel + buku telepon.
- keunikan: 8 — poster tipografi raksasa sudah dipakai 2026-10-17 & 2026-10-21, tapi kombinasi script raksasa + huruf kecil + buku telepon baru.
- kerapian: 9 — qa 0 masalah, 14/14 tes fungsi lulus, tidak ada overflow di 4 viewport.

## Keputusan konflik aturan
- v5 aturan 0 no. 5: seed 2026-11-02 tabrakan 100% dengan loakan 2026-10-18 (tidak tercatat di pick-seed karena seed.json build itu tidak ada di builds/) → re-seed base 2026-11-05, disahkan aturan 19 v5 (seed bermasalah sejak awal, sebelum tulis kode).
- domain seed "pasar loak" sama dengan loakan/taksirloak — 4/5 sumbu tetap beda dari tiap build (layout, font, palet, gerak/camera) → lolos aturan 5 v3.
- playwrite au vic variable (100–400) 404 di fontsource → ganti weight statis 400 (1x perbaikan, sebelum deploy).
- tabler:store tidak ada di versi tabler terpasang → ganti building-store.
- webkit qa tidak dijalankan (playwright webkit belum terinstall di vm) — dicatat belum terverifikasi.

## Putaran rombak
- ke-1: 17 tap target kecil → perbaiki (checkbox overlay full-label + custom box, nav px-3, logo & footer link min-height 44px). hasil: 0 small tap targets.
- ke-2: tidak diperlukan.
