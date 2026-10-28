# BRIEF — bidkit — 2026-10-28

## Masalah/usecase (1 kalimat + siapa yang kena)
Freelancer Indonesia yang bid di projects.co.id/sribu buang waktu nulis proposal dari nol tiap kali, salah patok harga, dan portofolio berantakan — bidkit kasih template siap kirim + kalkulator harga bersih + checklist portofolio dalam satu kios.

## Konsep visual (1 kalimat)
Satu kios pasar loak berbentuk buku telepon: kata raksasa "bidkit" tulisan tangan jadi pintu, isinya daftar template kayak entri buku telepon, semua teks huruf kecil.

## Hasil seed (2026-11-09, base 2026-11-05 — re-seed sah ATURAN 19 v5 karena seed 2026-11-02 tabrakan 100% dengan build 2026-10-18 Loakan yang tidak tercatat di pick-seed)
- domain: pasar loak · layout: poster tipografi raksasa · referensi: buku telepon
- constraint: semua teks huruf kecil
- gerak: kamera terbang scroll (scale+translate+rotate) · marquee 3 band beda kecepatan · kata jatuh menumpuk + split huruf flip 3D · hover ubah tema halaman · clip-path lingkaran
- ikon: garis putus-putus, Phosphor (diwujudkan: tabler + divider dashed + 3 SVG custom dashed)
- font: Allura (display) / Catamaran (body) / Playwrite AU VIC (aksen)
- palet: light/tetradic hue 278 — kertas ungu muda + tinta plum + oranye bata + lime (dirapikan ke AA, lihat bawah)

## 3 arah desain (2 kalimat masing-masing) + arah terpilih
1. koran kuning multi-kolom: bidkit kayak koran lowongan — kolom rapat, headline tebal, stempel merah. aman, tapi sudah dipakai warteg 2026-10-19.
2. kios pasar / buku telepon (TERPILIH): pengunjung langsung di depan kios, template = entri buku telepon bernomor, kata "bidkit" raksasa tulisan tangan. paling jauh dari default + nyambung sama ide "pasar penawaran".
3. terminal loket CRT: bidkit = loket, proposal diketik kayak perintah. sudah dipakai timlomba 2026-10-23.
Alasan pilih 2: metafora pasar = tempat orang nawar-menawar, persis perilaku bid; buku telepon = direktori, persis fungsi template.

## Keputusan berani
Tanpa navbar, tanpa hero marketing — pengunjung langsung di depan kios dalam 5 detik pertama; seluruh situs huruf kecil (termasuk judul dan tombol); kata "bidkit" 28vw jadi pintu zoom-through.

## Persona/suara
"bang loak", makelar pasar yang lugas dan lowercase: "nego dulu, jangan asal bid." semua copy — judul, tombol, pesan error, empty state, footer — pakai suara ini.

## Palet (harmoni, kenapa, psikologi warna, token final, kontras AA)
Harmoni tetradic hue 278 (ungu kertas + oranye bata + lime). psikologi: kertas ungu muda = tenang kayak buku catatan lama; oranye bata = tinta stempel pasar, tegas dan hangat; lime = "lolos/oke". proporsi 60-30-10.
- --bg: #f6f1fb (oklch .96 .037 278) · --surface: #fffdf9 · --text: #241a33 (oklch .20 .05 278, kontras vs bg ±13:1) · --muted: #6b5a80 (kontras ±5,4:1) · --accent: #c2410c oranye bata (teks putih di atasnya ±4,6:1, AA) · --accent-2: #4d7c0f lime gelap (teks/ikon ok) · --pop: #f5c518 kuning stempel (<5% area).
- gradient ungu-biru dilarang; tidak ada shadow lembut seragam; border = garis putus-putus 2px.

## Font (display/body/aksen, alasan, id Fontsource, variable atau bukan)
- display Allura (fontsource id `allura`, 400, script) — tulisan tangan tanda kios, ekstrem dan beda dari 30 build terakhir.
- body Catamaran (id `catamaran`, 400–800) — humanis, x-height lega, terbaca di 390px.
- aksen Playwrite AU VIC (id `playwrite-au-vic`, variable 100–400) — catatan tangan pinggir buku telepon.

## Ikon (gaya, sumber, daftar 12+, 3+ custom)
Gaya garis putus-putus (dashed 2px), sumber Tabler via astro-icon + SVG custom. daftar: koin, karcis, stempel, amplop, salin, unduh, tautan, kalkulator, centang, jam, dompet, telepon, panah, gerak, cari. custom SVG dashed: (1) karcis bidkit bernomor, (2) koin rp, (3) stempel "sah" berputar.

## Gerak (kategori A-F, narasi, MODE RINGAN)
Narasi: scroll = jalan masuk ke dalam kios pasar. A: kata "bidkit" zoom 1→1,6× + rotate -2° + pan saat scroll (pintu). B: 3 marquee band beda kecepatan + skew ikut kecepatan scroll + tombol jeda. C: kata jatuh-menumpuk di subjudul + split huruf flip 3D di kata raksasa. D: hover kartu template ubah tema aksen seluruh halaman (data-theme di html). E: clip-path lingkaran reveal tiap section + draw-on garis dashed. F: tidak dipakai. MODE RINGAN (hardware ≤4 core / save-data / fps <40): matikan A dan D, marquee jadi statis.

## Storyboard hero moment
| Scroll | Yang terlihat | Kamera | Marquee | Teks | Interaksi |
|---|---|---|---|---|---|
| 0% | kata "bidkit" 28vw + subline + 3 band marquee | diam, kata utuh | 3 band jalan | kata flip-in per huruf | klik kata 5× = easter egg |
| 25% | kata membesar, kios mulai kelihatan | zoom 1,3× rotate -1° | skew naik | subline jatuh-menumpuk | — |
| 50% | kata jadi pintu, kartu template masuk | zoom 1,6× + pan kanan | band 1 jeda | judul section reveal lingkaran | tab kategori |
| 75% | kalkulator + checklist | keluar lagi, skala normal | 2 band jalan | angka odometer | isi harga |
| 100% | faq + footer sumber | statis | statis | — | salin proposal |

Pertunjukan utama: kata "bidkit" membesar jadi pintu saat scroll — pengunjung "masuk kios". 5 detik pertama: kata raksasa + "nego dulu, jangan asal bid" + tombol "buka kiosnya".

## Konten (15+ item nyata, easter egg)
- 9 template (3 kategori × 3 gaya: sopan / to-the-point / portofolio-dulu) — struktur ikut contoh RFP nyata projects.co.id: pemahaman + solusi + lingkup + estimasi waktu + pengalaman + biaya + tahapan bayar.
- 12 checklist portofolio. 5 faq (fee 12% projects.co.id, bid gratis & tertutup, escrow, kontes sribu 7 hari, penarikan gratis bca/bni/mandiri).
- fakta terverifikasi + sumber: https://projects.co.id/public/pages/faq_umum, https://projects.co.id/public/pages/syarat_layanan, https://go.sribu.com/id/syarat-ketentuan/.
- fee sribu TIDAK dipublikasi resmi → di tool jadi input "[isi manual]", bukan angka.
- kisaran harga contoh = estimasi blog, dilabeli "estimasi, bukan harga pasar".
- easter egg: klik kata "bidkit" 5× → toast "makelarnya lagi ngopi, bentar ya."

## Teknik visual orisinal (2+)
1. pola garis putus-putus + noise feTurbulence (kertas fotokopi buku telepon).
2. stempel "sah" SVG berputar + sobekan karcis (clip-path gerigi).
3. tipografi raksasa sebagai pintu zoom-through.

## Suara
Tidak ada audio (bonus dilewati, fokus fungsi).
