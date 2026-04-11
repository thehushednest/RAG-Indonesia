# IRIS Knowledge Module — HTML Intelligence Feed Generator
> Modul RAG untuk IRIS AI Agent
> Versi: 1.0 | Tipe: Knowledge Module — HTML Output
> Dipanggil saat: IRIS diminta generate laporan dalam format HTML feed
> Strategi: IRIS mengisi JSON field → script inject ke template HTML fixed
> Branding: Senopati Strategic Institute — cream/red/ink

---

## META — STRATEGI ARSITEKTUR

### Mengapa JSON → Template, Bukan HTML dari Nol?

IRIS **tidak** generate HTML dari nol. Alasannya:
1. Template HTML yang konsisten tidak rusak secara visual
2. IRIS hanya fokus pada konten, bukan styling
3. Output JSON lebih cepat, lebih ringan, lebih reliable
4. Gambar di-fetch otomatis dari sumber berita (OG image) atau placeholder tematik
5. Satu template bisa diupdate tanpa mengubah RAG

### Alur Kerja

```
User / Scheduler meminta laporan HTML
         ↓
IRIS mengumpulkan semua data
(market, OSINT, geo, institutional)
         ↓
IRIS mengisi JSON template (Seksi 2)
         ↓
Script inject.js membaca JSON
         ↓
HTML final di-render dari template
         ↓
File disimpan: iris-feed-[YYYYMMDD].html
         ↓
[A] Embed di dashboard IRIS
[B] Upload ke Netlify/hosting
[C] Kirim link via WhatsApp Bot
```

---

## BAGIAN 1 — STRUKTUR HALAMAN HTML FEED

### 1.1 Komponen Halaman (Fixed di Template)

```
[TOPBAR]          — Logo IRIS + jam real-time + live badge
[TICKER]          — Harga berjalan: IHSG, IDR, komoditas
[MASTHEAD]        — Judul edisi + tanggal + klasifikasi
[NAV TABS]        — Filter: Semua, Pasar, Geo, OSINT, dll
[MARKET STRIP]    — 5 indikator utama dalam grid
[FEED LAYOUT]
  ├── LEAD ARTICLE    — Artikel utama dengan gambar besar
  ├── ARTICLE CARDS   — 4–8 artikel pendukung
  ├── SCENARIO GRID   — Bull/Base/Bear case 3 kolom
  ├── OSINT FEED      — Item OSINT dengan tier badge
  └── SIDEBAR
        ├── RISK PANEL       — Skor risiko 5 dimensi + bar
        ├── SIGNAL PANEL     — Signal aktif hari ini
        ├── COMMODITY TABLE  — Harga komoditas strategis
        └── POLICY STANCE    — BI/OJK/Kemenkeu signal
[FOOTER]          — Branding + timestamp + klasifikasi
```

### 1.2 Warna Branding Senopati

| Variabel | Hex | Penggunaan |
|---|---|---|
| `--cream` | #F5F0E8 | Background utama |
| `--cream2` | #EDE7D9 | Surface sekunder |
| `--ink` | #1C1A16 | Teks utama, topbar |
| `--ink3` | #6B6358 | Teks sekunder |
| `--red` | #C0392B | Aksen utama, tag, lead |
| `--gold` | #B8860B | Warning, base case |
| `--green` | #1A6B3A | Positif, bull case |

---

## BAGIAN 2 — JSON FIELD TEMPLATE

IRIS mengisi JSON berikut secara lengkap. Setiap field adalah **wajib** kecuali ditandai `[opsional]`.

```json
{
  "meta": {
    "edisi": "Harian",
    "volume": 1,
    "nomor": 47,
    "tanggal": "Jumat, 11 April 2026",
    "tanggal_iso": "2026-04-11",
    "waktu_generate": "16:30 WIB",
    "klasifikasi": "Untuk Kalangan Terbatas",
    "engine_version": "IRIS v1.0"
  },

  "ticker": [
    { "nama": "IHSG", "nilai": "7.234,18", "perubahan": "-0,42%", "arah": "dn" },
    { "nama": "USD/IDR", "nilai": "16.285", "perubahan": "+0,18%", "arah": "dn" },
    { "nama": "CPO", "nilai": "4.120 MYR", "perubahan": "+1,24%", "arah": "up" },
    { "nama": "COAL", "nilai": "USD 108,50", "perubahan": "-0,64%", "arah": "dn" },
    { "nama": "NIKEL", "nilai": "USD 16.240", "perubahan": "+0,87%", "arah": "up" },
    { "nama": "BRENT", "nilai": "USD 74,18", "perubahan": "-1,12%", "arah": "dn" },
    { "nama": "EMAS", "nilai": "USD 3.218", "perubahan": "+0,34%", "arah": "up" },
    { "nama": "SBN 10Y", "nilai": "6,82%", "perubahan": "-3bps", "arah": "dn" }
  ],

  "market_strip": [
    {
      "label": "IHSG",
      "nilai": "7.234",
      "perubahan": "▼ -30,4 (-0,42%)",
      "arah": "dn"
    },
    {
      "label": "USD/IDR",
      "nilai": "16.285",
      "perubahan": "▼ +29 poin",
      "arah": "dn"
    },
    {
      "label": "CPO",
      "nilai": "4.120",
      "perubahan": "▲ +1,24%",
      "arah": "up"
    },
    {
      "label": "Brent",
      "nilai": "74,18",
      "perubahan": "▼ -1,12%",
      "arah": "dn"
    },
    {
      "label": "Emas",
      "nilai": "3.218",
      "perubahan": "▲ +0,34%",
      "arah": "up"
    }
  ],

  "lead_article": {
    "tier": "TIER 1 · ACTIONABLE",
    "kategori": "Pasar",
    "headline": "Tarif Trump dan Tekanan Rupiah: IHSG Berpotensi Uji Support 7.100 Pekan Depan",
    "deck": "Eskalasi tarif impor Amerika Serikat memicu arus keluar modal asing dari pasar berkembang. Rupiah melemah ke 16.285 per dolar AS, sementara cadangan devisa BI dinilai cukup menghadapi tekanan jangka pendek. IRIS menilai risiko eksternal berada di level sedang-tinggi.",
    "gambar_url": "[URL gambar atau kosong untuk placeholder]",
    "gambar_alt": "Gedung Bank Indonesia / Grafik IHSG",
    "gambar_caption": "[opsional] Sumber: [nama sumber]",
    "penulis": "IRIS Market Engine",
    "waktu": "11 April 2026, 16.30 WIB",
    "confidence": "Tinggi",
    "body_paragraf": [
      "Pasar keuangan Indonesia kembali menghadapi tekanan eksternal yang signifikan seiring eskalasi perang tarif antara Amerika Serikat dan China.",
      "Bank Indonesia diperkirakan akan mengintervensi pasar valuta asing jika rupiah menyentuh level 16.500, berdasarkan pola intervensi historis.",
      "Investor disarankan untuk memantau data inflasi BPS yang akan dirilis pekan depan sebagai katalis potensial."
    ]
  },

  "artikel": [
    {
      "id": "art-001",
      "kategori": "Geopolitik",
      "headline": "Hubungan China-AS Memanas: Dampak Ekspor Nikel dan Batubara Indonesia",
      "deck": "Eskalasi tarif timbal balik berpotensi mengalihkan permintaan komoditas ke pasar alternatif, membuka peluang sekaligus risiko bagi eksportir Indonesia.",
      "gambar_emoji": "🌏",
      "gambar_url": "[opsional]",
      "penulis": "IRIS Geo Engine",
      "waktu": "11 Apr 2026 · 08.00 WIB",
      "signal": "Waspada",
      "confidence": "Tinggi",
      "tier": 1
    },
    {
      "id": "art-002",
      "kategori": "Institusional · BI",
      "headline": "RDG Bank Indonesia Mei 2026: Sinyal Pemotongan Suku Bunga Mulai Menguat",
      "deck": "Gubernur BI memberikan pernyataan yang lebih dovish, mengindikasikan kemungkinan pemotongan suku bunga acuan jika tekanan eksternal mereda.",
      "gambar_emoji": "🏦",
      "gambar_url": "[opsional]",
      "penulis": "IRIS Institutional Engine",
      "waktu": "10 Apr 2026",
      "signal": "Positif",
      "confidence": "Sedang",
      "tier": 2
    },
    {
      "id": "art-003",
      "kategori": "OSINT · Sosial",
      "headline": "Trending di X Indonesia: Isu Harga Pangan Dominasi Percakapan Publik",
      "deck": "Dalam 48 jam terakhir, isu kenaikan harga beras dan minyak goreng kembali menjadi topik utama di platform media sosial.",
      "gambar_emoji": "🔍",
      "gambar_url": "[opsional]",
      "penulis": "IRIS OSINT Engine",
      "waktu": "11 Apr 2026 · 07.45 WIB",
      "signal": "Negatif",
      "confidence": "Tinggi",
      "tier": 1
    },
    {
      "id": "art-004",
      "kategori": "Komoditas · CPO",
      "headline": "CPO Menguat Didukung Permintaan India Jelang Musim Konsumsi",
      "deck": "Harga CPO di Bursa Malaysia naik 1,24% seiring meningkatnya impor India dan penurunan stok Malaysia.",
      "gambar_emoji": "🌴",
      "gambar_url": "[opsional]",
      "penulis": "IRIS Commodity Engine",
      "waktu": "11 Apr 2026",
      "signal": "Positif",
      "confidence": "Sedang",
      "tier": 2
    }
  ],

  "skenario": {
    "isu": "Eskalasi Tarif AS dan Dampak ke Pasar Indonesia",
    "konteks": "Analisis skenario untuk periode 1–2 pekan ke depan",
    "bull": {
      "probabilitas": "25%",
      "label": "Bull Case",
      "ihsg": "+1,5–2,5%",
      "ihsg_arah": "pos",
      "idr": "Ke 15.900",
      "idr_arah": "pos",
      "pemicu": "Negosiasi tarif berhasil",
      "aksi": "Accumulate Saham",
      "kondisi": "De-eskalasi tarif AS-China, BI tahan suku bunga, inflasi terkendali"
    },
    "base": {
      "probabilitas": "60%",
      "label": "Base Case",
      "ihsg": "Sideways ±0,8%",
      "ihsg_arah": "neu",
      "idr": "16.100–16.400",
      "idr_arah": "neu",
      "pemicu": "Status quo berlanjut",
      "aksi": "Monitor & Wait",
      "kondisi": "Tidak ada katalis besar, pasar menunggu data inflasi dan RDG BI"
    },
    "bear": {
      "probabilitas": "15%",
      "label": "Bear Case",
      "ihsg": "-3 hingga -5%",
      "ihsg_arah": "neg",
      "idr": "Ke 16.800+",
      "idr_arah": "neg",
      "pemicu": "Eskalasi tarif penuh",
      "aksi": "Hedge / Reduce",
      "kondisi": "Tarif AS naik >50%, China retaliasi, capital outflow masif dari EM"
    }
  },

  "osint_items": [
    {
      "tier": 1,
      "sumber": "Bisnis.com",
      "waktu": "11 Apr 2026 · 09.12 WIB",
      "headline": "OJK Rilis Aturan Baru Batas Kepemilikan Asing di Perbankan Indonesia",
      "analisis": "Regulasi ini berpotensi mempengaruhi valuasi saham-saham perbankan besar. Investor asing mungkin mereview posisi di BBCA, BBRI, dan BMRI dalam jangka pendek.",
      "signal": "Negatif Jangka Pendek",
      "signal_class": "sig-neg"
    },
    {
      "tier": 2,
      "sumber": "Kompas.id",
      "waktu": "11 Apr 2026 · 07.30 WIB",
      "headline": "Prabowo Umumkan Percepatan Program Hilirisasi Nikel untuk Baterai EV",
      "analisis": "Pernyataan ini memperkuat tren positif jangka menengah untuk emiten nikel domestik, meski implementasi jangka pendek masih perlu dipantau.",
      "signal": "Positif Jangka Menengah",
      "signal_class": "sig-pos"
    },
    {
      "tier": 3,
      "sumber": "Detik Finance",
      "waktu": "10 Apr 2026 · 18.45 WIB",
      "headline": "Realisasi Penerimaan Pajak Q1 2026 Mencapai 82% dari Target",
      "analisis": "Angka di atas ekspektasi ini memberikan ruang fiskal lebih bagi pemerintah dan mengurangi tekanan terhadap penerbitan SBN baru dalam jangka dekat.",
      "signal": "Positif Fiskal",
      "signal_class": "sig-pos"
    }
  ],

  "risk_scores": [
    { "label": "Pasar Domestik", "skor": 6, "warna": "#EF5350" },
    { "label": "Eksternal", "skor": 7, "warna": "#EF5350" },
    { "label": "Valuta (IDR)", "skor": 6, "warna": "#FFA726" },
    { "label": "Likuiditas", "skor": 4, "warna": "#66BB6A" },
    { "label": "Sosial/Kamtibmas", "skor": 3, "warna": "#66BB6A" }
  ],

  "signals_aktif": [
    {
      "level": "high",
      "teks": "Tekanan jual asing berlanjut di sektor perbankan — monitor foreign flow harian",
      "confidence": "Tinggi",
      "tier": 1
    },
    {
      "level": "med",
      "teks": "CPO rally berpotensi berlanjut — lirik emiten sawit AALI, SIMP, LSIP",
      "confidence": "Sedang",
      "tier": 2
    },
    {
      "level": "low",
      "teks": "SBN 10Y yield mendekati support — potensi penguatan harga obligasi",
      "confidence": "Sedang",
      "tier": 2
    }
  ],

  "komoditas": [
    { "nama": "CPO", "unit": "MYR/MT", "nilai": "4.120", "perubahan": "+1,24%", "arah": "up" },
    { "nama": "Batubara", "unit": "USD/MT", "nilai": "108,50", "perubahan": "-0,64%", "arah": "dn" },
    { "nama": "Nikel", "unit": "USD/MT", "nilai": "16.240", "perubahan": "+0,87%", "arah": "up" },
    { "nama": "Brent", "unit": "USD/bbl", "nilai": "74,18", "perubahan": "-1,12%", "arah": "dn" },
    { "nama": "Emas", "unit": "USD/troy oz", "nilai": "3.218", "perubahan": "+0,34%", "arah": "up" },
    { "nama": "ICP", "unit": "USD/bbl", "nilai": "71,42", "perubahan": "-0,98%", "arah": "dn" }
  ],

  "policy_stance": [
    {
      "institusi": "BI",
      "stance": "Dovish",
      "level": "med",
      "keterangan": "Sinyal pemotongan rate Mei 2026"
    },
    {
      "institusi": "OJK",
      "stance": "Ketat",
      "level": "high",
      "keterangan": "Aturan kepemilikan asing baru"
    },
    {
      "institusi": "Kemenkeu",
      "stance": "Ekspansif",
      "level": "low",
      "keterangan": "Penerimaan pajak on-track"
    }
  ]
}
```

---

## BAGIAN 3 — INSTRUKSI PENGISIAN JSON OLEH IRIS

### 3.1 Aturan Pengisian

**Field `meta`:**
- `tanggal` — format: "[Hari], [DD] [Bulan] [YYYY]"
- `waktu_generate` — format: "[HH:MM] WIB"
- `nomor` — increment dari edisi sebelumnya
- `klasifikasi` — selalu "Untuk Kalangan Terbatas" kecuali ada instruksi berbeda

**Field `ticker` dan `market_strip`:**
- `arah` — hanya dua nilai: `"up"` atau `"dn"`
- `perubahan` — sertakan tanda ▲ atau ▼ untuk market_strip
- Semua nilai dalam format string, bukan angka

**Field `lead_article`:**
- `tier` — pilih: "TIER 1 · ACTIONABLE", "TIER 2 · WATCH", atau "TIER 3 · BACKGROUND"
- `headline` — maksimal 100 karakter, padat dan informatif
- `deck` — 2–3 kalimat, berisi konteks + fakta kunci + stance IRIS
- `body_paragraf` — array 2–4 paragraf untuk pembaca yang klik "Baca selengkapnya"
- `confidence` — "Tinggi", "Sedang", atau "Rendah"
- `gambar_url` — jika kosong, template otomatis tampilkan placeholder tematik

**Field `artikel`:**
- Minimal 3 artikel, maksimal 8 artikel
- `signal` — "Positif", "Negatif", "Netral", atau "Waspada"
- `gambar_emoji` — emoji relevan jika tidak ada URL gambar
- Urutan: dari yang paling penting/tier tertinggi ke terendah

**Field `skenario`:**
- Tiga skenario WAJIB selalu ada — tidak boleh hanya bull atau base case
- `probabilitas` — total tiga skenario harus = 100%
- `ihsg_arah` / `idr_arah` — "pos", "neg", atau "neu" (untuk styling warna)
- `kondisi` — 1–2 kalimat kondisi yang harus terpenuhi agar skenario ini terjadi

**Field `osint_items`:**
- `tier` — angka 1, 2, atau 3 (bukan string)
- `signal_class` — hanya: "sig-pos", "sig-neg", atau "sig-neu"
- `analisis` — 2–3 kalimat interpretasi IRIS, bukan sekadar ringkasan berita

**Field `risk_scores`:**
- `skor` — angka 1–10
- `warna` — pilih dari: "#EF5350" (merah, >6), "#FFA726" (kuning, 4–6), "#66BB6A" (hijau, <4)

**Field `signals_aktif`:**
- `level` — hanya: "high", "med", atau "low"
- `teks` — kalimat aksi, bukan deskripsi situasi — harus ada kata kerja + rekomendasi

**Field `policy_stance`:**
- `stance` — untuk BI: "Hawkish/Dovish/Netral"; OJK: "Ketat/Longgar/Netral"; Kemenkeu: "Ekspansif/Kontraktif/Netral"
- `level` — "high", "med", "low" (menentukan warna dot)

---

## BAGIAN 4 — ATURAN KONTEN

### 4.1 Standar Headline

```
BAIK:
"Tarif Trump dan Tekanan Rupiah: IHSG Berpotensi Uji Support 7.100"
"RDG BI Mei 2026: Sinyal Pemotongan Suku Bunga Mulai Menguat"
"CPO Menguat 1,24% — Emiten Sawit Berpotensi Outperform"

HINDARI:
"Situasi Pasar Hari Ini" — terlalu generik
"IHSG Turun" — terlalu pendek, tidak informatif
"Analisis Lengkap Kondisi Pasar Indonesia Terkini" — terlalu panjang
```

**Formula headline yang baik:**
`[Fakta kunci] — [Implikasi/Proyeksi]`
atau
`[Subjek]: [Perkembangan] [Dampak]`

### 4.2 Standar Deck (Sub-headline)

- Panjang: 2–3 kalimat
- Kalimat 1: Konteks/latar belakang
- Kalimat 2: Fakta kunci terverifikasi
- Kalimat 3: Stance atau implikasi IRIS

### 4.3 Standar Analisis OSINT

- Bukan sekadar ringkasan berita — IRIS harus menambahkan interpretasi
- Selalu sebutkan instrumen/sektor yang terdampak secara spesifik
- Jika tidak bisa menganalisis — tandai: "[Perlu validasi lebih lanjut]"

### 4.4 Larangan Konten

- TIDAK BOLEH menggunakan kata "mungkin" atau "bisa jadi" tanpa confidence label
- TIDAK BOLEH membuat skenario tanpa probabilitas
- TIDAK BOLEH menyebutkan rekomendasi tanpa menyebut risiko
- TIDAK BOLEH headline yang hanya positif — harus seimbang
- TIDAK BOLEH mencantumkan data tanpa sumber

---

## BAGIAN 5 — INTEGRASI GAMBAR

### 5.1 Hierarki Sumber Gambar

```
PRIORITAS 1: URL gambar dari sumber berita
→ Scrape OG image dari URL artikel yang dikutip
→ Format: gambar_url: "https://..."

PRIORITAS 2: Chart yang di-generate
→ TradingView widget untuk IHSG/IDR
→ Chart.js untuk data komoditas
→ Format: gambar_url: "chart://[tipe]"

PRIORITAS 3: Gambar tematik dari unsplash/pexels
→ Berdasarkan kategori artikel
→ Format: gambar_url: "theme://[kategori]"

PRIORITAS 4: Placeholder tematik dengan emoji
→ Dirender oleh template dengan emoji besar
→ Format: gambar_emoji: "🌏" dan gambar_url: ""
```

### 5.2 Kategori Emoji Tematik

| Kategori | Emoji |
|---|---|
| Pasar / IHSG | 📊 |
| Nilai tukar / IDR | 💱 |
| Geopolitik | 🌏 |
| Bank Indonesia | 🏦 |
| Komoditas energi | 🛢 |
| CPO / sawit | 🌴 |
| Nikel / tambang | ⛏ |
| OSINT / intelijen | 🔍 |
| Alert / peringatan | 🚨 |
| Kebijakan fiskal | 💰 |
| Sosial / kamtibmas | 👥 |
| Geopolitik militer | 🎖 |

---

## BAGIAN 6 — DISTRIBUSI OUTPUT

### 6.1 Embed di Dashboard IRIS

Template HTML dipanggil sebagai iframe atau panel dalam dashboard IRIS:
```html
<iframe src="iris-feed-20260411.html"
        width="100%"
        height="100%"
        frameborder="0">
</iframe>
```

Atau di-inject langsung ke panel menggunakan fetch:
```javascript
fetch('iris-feed-20260411.html')
  .then(r => r.text())
  .then(html => {
    document.getElementById('feed-panel').innerHTML = html;
  });
```

### 6.2 Upload ke Netlify

Script otomatis setelah generate:
```bash
# Generate file
node inject.js data-20260411.json > iris-feed-20260411.html

# Upload ke Netlify
netlify deploy --prod --dir=./feeds

# Kirim link via WhatsApp Bot
curl -X POST [WA_BOT_ENDPOINT] \
  -d "message=📊 *IRIS Intelligence Feed* tersedia:\nhttps://iris.senopati.id/feed/20260411\n_Untuk Kalangan Terbatas_"
```

### 6.3 Format Pesan WhatsApp Bot

Saat feed HTML siap, IRIS mengirim notifikasi via WhatsApp Bot:

```
📊 *IRIS Intelligence Feed*
*[Hari], [DD MMMM YYYY] — Edisi [Harian/Mingguan]*

*Highlights hari ini:*
① [Headline lead article]
② [Headline artikel 2]
③ [Headline artikel 3]

*Skor Risiko:* [X]/10 — [Domestik], [X]/10 — [Eksternal]

🔗 *Baca selengkapnya:*
https://iris.senopati.id/feed/[YYYYMMDD]

_Senopati Strategic Institute — Untuk Kalangan Terbatas_
_Digenerate oleh IRIS [HH:MM] WIB_
```

---

## BAGIAN 7 — PERINTAH MANUAL

| Perintah | Aksi IRIS |
|---|---|
| `iris: generate feed` | Generate feed HTML hari ini |
| `iris: generate feed [tanggal]` | Generate feed untuk tanggal tertentu |
| `iris: generate weekly` | Generate feed edisi mingguan |
| `iris: update lead [teks]` | Update lead article dengan teks baru |
| `iris: add artikel [kategori] [headline]` | Tambah artikel ke feed |
| `iris: update risk [dimensi] [skor]` | Update skor risiko tertentu |
| `iris: add signal [level] [teks]` | Tambah signal aktif |
| `iris: preview json` | Tampilkan JSON yang akan di-generate |
| `iris: publish` | Upload ke hosting dan kirim link WA |
| `iris: feed link` | Kirim ulang link feed terbaru ke WA |

---

## BAGIAN 8 — CHECKLIST VALIDASI JSON

Sebelum output JSON, IRIS memverifikasi:

- [ ] Field `meta` lengkap — tanggal, waktu, nomor edisi
- [ ] `ticker` memiliki 6–8 item
- [ ] `market_strip` tepat 5 item
- [ ] `lead_article` memiliki headline, deck, dan confidence
- [ ] Minimal 3 `artikel` dengan kategori berbeda
- [ ] `skenario` memiliki ketiganya — bull, base, bear
- [ ] Total probabilitas skenario = 100%
- [ ] Minimal 3 `osint_items` dengan tier berbeda
- [ ] `risk_scores` memiliki 5 dimensi
- [ ] Minimal 2 `signals_aktif`
- [ ] `komoditas` memiliki 5–8 item
- [ ] `policy_stance` memiliki 3 institusi (BI, OJK, Kemenkeu)
- [ ] Semua `arah` hanya berisi "up" atau "dn"
- [ ] Semua `signal_class` valid: sig-pos, sig-neg, sig-neu
- [ ] Tidak ada field yang berisi "[placeholder]" yang belum diisi

---

*IRIS Knowledge Module: HTML Intelligence Feed Generator*
*Versi 1.0 | April 2026 | Senopati Strategic Institute*
*Strategi: JSON field injection → template HTML fixed*
*Output: feed HTML responsif bergaya media online*
