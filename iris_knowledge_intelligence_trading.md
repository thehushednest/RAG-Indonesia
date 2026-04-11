# IRIS Knowledge Module — Intelligence Trading & Strategic Market Analysis
> Modul RAG untuk IRIS AI Agent
> Versi: 1.0 | Tipe: Knowledge Module — KOMPLEKS
> Dipanggil saat: IRIS menjalankan analisis pasar, geopolitik, institusional, dan OSINT
> Target: Tim Internal Senopati Strategic Institute
> Output: Laporan WhatsApp harian & mingguan via WhatsApp Bot
> Cakupan: Pasar Indonesia · Geopolitik · Institusional · OSINT · Sentimen Media

---

## META — ARSITEKTUR SISTEM

```
IRIS Intelligence Trading Engine
│
├── DATA LAYER (Input)
│   ├── Market Feed    — IHSG, IDR, komoditas, crypto
│   ├── News Scraper   — Kompas, Tempo, Detik, CNBC ID, Bisnis
│   ├── Gov Scanner    — BI, OJK, Kemenkeu, ESDM, Bappenas
│   ├── OSINT Layer    — Twitter ID, TikTok, Telegram publik
│   └── Geo Signal     — Indo-Pasifik, ASEAN, tarif global
│
├── ANALYSIS ENGINE (Proses)
│   ├── Market Analysis     — teknikal + fundamental lokal
│   ├── Sentiment Engine    — NLP Bahasa Indonesia
│   ├── Risk Scoring        — 1–10 per sektor/aset
│   ├── Scenario Builder    — 3 skenario per isu
│   └── Signal Classifier   — noise vs actionable signal
│
├── REPORT ENGINE (Output)
│   ├── Laporan Harian Pasar         — setiap hari kerja 07.00 WIB
│   ├── Laporan Harian OSINT         — setiap hari 08.00 WIB
│   ├── Laporan Mingguan Geopolitik  — setiap Senin 06.00 WIB
│   ├── Laporan Mingguan Institusional — setiap Jumat 17.00 WIB
│   └── Laporan Insidentil           — triggered by event
│
└── DELIVERY (Distribusi)
    └── WhatsApp Bot → Grup Tim Internal Senopati
```

---

## BAGIAN 1 — LAPORAN HARIAN PASAR

### 1.1 Jadwal & Trigger

| Laporan | Waktu Kirim | Trigger |
|---|---|---|
| Pre-market briefing | 07.00 WIB | Scheduled harian |
| Closing summary | 16.30 WIB | Setelah bursa tutup |
| Alert insidentil | Real-time | Pergerakan >2% dalam 1 jam |

### 1.2 Komponen Wajib Laporan Harian Pasar

**A. IHSG & Indeks Sektoral**
- Level IHSG saat ini vs hari sebelumnya (poin + persentase)
- Volume transaksi vs rata-rata 20 hari
- Sektor terkuat dan terlemah hari ini
- Foreign flow: net buy/sell asing
- Saham top gainer dan top loser (masing-masing 3)

**B. Nilai Tukar**
- USD/IDR: level, perubahan harian, posisi vs JISDOR
- Perbandingan dengan mata uang regional (MYR, SGD, THB, PHP)
- Intervensi BI jika terdeteksi

**C. Komoditas Strategis Indonesia**
- Crude Palm Oil (CPO): harga spot + perubahan
- Batubara (Newcastle): harga spot + perubahan
- Nikel LME: harga spot + perubahan
- Minyak Bumi (Brent + WTI): dampak ke BBM subsidi
- Emas: harga domestik vs internasional

**D. Signal Hari Ini**
- 1–3 signal actionable dengan confidence level
- Sektor yang perlu diperhatikan
- Event ekonomi terjadwal hari ini (rilis data, rapat BI, dll)

**E. Skor Risiko Harian**
Skala 1–10 per dimensi:
- Risiko pasar domestik
- Risiko eksternal/global
- Risiko valuta
- Risiko likuiditas

### 1.3 Format WhatsApp — Pre-Market Briefing

```
🟢 *IRIS MARKET BRIEFING*
*[Hari], [DD MMMM YYYY] | Pre-Market 07.00 WIB*
_Senopati Strategic Institute — Untuk Kalangan Terbatas_

━━━━━━━━━━━━━━━
📊 *IHSG OVERVIEW*
━━━━━━━━━━━━━━━
Penutupan kemarin : *[XXXX.XX]* ([+/-X.XX%])
Ekspektasi hari ini : *[Bullish/Bearish/Sideways]*
Volume kemarin : *[X,XX T]* vs rata-rata *[X,XX T]*
Foreign flow : *[Net Buy/Sell] Rp [X,XX T]*

*Sektor Watch:*
🔴 Terlemah : [Sektor] ([X.XX%])
🟢 Terkuat  : [Sektor] ([X.XX%])

━━━━━━━━━━━━━━━
💱 *NILAI TUKAR*
━━━━━━━━━━━━━━━
USD/IDR : *[XX.XXX]* ([+/-XX] poin)
Posisi  : [Di atas/bawah] JISDOR *[XX.XXX]*
Regional: MYR [X.XX] | SGD [X.XX] | THB [XX.XX]

━━━━━━━━━━━━━━━
🛢 *KOMODITAS*
━━━━━━━━━━━━━━━
CPO     : *USD [XXX]/MT* ([+/-X.X%])
Batubara : *USD [XXX]/MT* ([+/-X.X%])
Nikel   : *USD [X.XXX]/MT* ([+/-X.X%])
Brent   : *USD [XX.XX]/bbl* ([+/-X.X%])
Emas    : *USD [X.XXX]/troy oz* ([+/-X.X%])

━━━━━━━━━━━━━━━
⚡ *SIGNAL HARI INI*
━━━━━━━━━━━━━━━
① *[Signal 1]* — Confidence: *[Tinggi/Sedang/Rendah]*
> _[Penjelasan 1–2 kalimat]_

② *[Signal 2]* — Confidence: *[Tinggi/Sedang/Rendah]*
> _[Penjelasan 1–2 kalimat]_

━━━━━━━━━━━━━━━
🎯 *EVENT TERJADWAL*
━━━━━━━━━━━━━━━
• *[HH:MM WIB]* — [Nama event, misal: Rilis inflasi BPS]
• *[HH:MM WIB]* — [Nama event]

━━━━━━━━━━━━━━━
🔴 *SKOR RISIKO HARI INI*
━━━━━━━━━━━━━━━
Domestik  : [X]/10 [██████░░░░]
Eksternal : [X]/10 [████░░░░░░]
Valuta    : [X]/10 [█████░░░░░]
Likuiditas: [X]/10 [███░░░░░░░]

_Disiapkan oleh IRIS | Senopati Strategic Institute_
_Data: [sumber] | [HH:MM] WIB_
```

### 1.4 Format WhatsApp — Closing Summary

```
📉 *IRIS CLOSING SUMMARY*
*[Hari], [DD MMMM YYYY] | Penutupan Bursa*
_Senopati Strategic Institute — Untuk Kalangan Terbatas_

━━━━━━━━━━━━━━━
📊 *IHSG HARI INI*
━━━━━━━━━━━━━━━
Penutupan : *[XXXX.XX]* ([+/-X.XX%])
Tertinggi : *[XXXX.XX]* | Terendah: *[XXXX.XX]*
Volume    : *[X,XX T]* | Nilai: *Rp [X,XX T]*
Foreign   : *Net [Buy/Sell] Rp [X,XX T]*

*Top Gainer:*
🟢 [Kode] +[X.X%] | [Kode] +[X.X%] | [Kode] +[X.X%]

*Top Loser:*
🔴 [Kode] -[X.X%] | [Kode] -[X.X%] | [Kode] -[X.X%]

*Sektor:*
🟢 [Sektor] +[X.X%]
🔴 [Sektor] -[X.X%]

━━━━━━━━━━━━━━━
📌 *ANALISIS PENUTUPAN*
━━━━━━━━━━━━━━━
[Narasi 3–5 kalimat tentang dinamika hari ini,
faktor penggerak utama, dan implikasi untuk besok]

━━━━━━━━━━━━━━━
🔭 *OUTLOOK BESOK*
━━━━━━━━━━━━━━━
Bias      : *[Bullish/Bearish/Sideways]*
Support   : *[XXXX]* | Resistance: *[XXXX]*
Katalis   : [Event atau data yang akan mempengaruhi]

_Disiapkan oleh IRIS | Senopati Strategic Institute_
```

### 1.5 Format WhatsApp — Alert Insidentil

```
🚨 *IRIS MARKET ALERT*
*[DD/MM/YYYY] | [HH:MM] WIB*

*⚠ [JUDUL ALERT — HURUF KAPITAL]*

*Apa yang terjadi:*
[Narasi singkat 2–3 kalimat — faktual]

*Dampak ke pasar:*
• IHSG: [dampak]
• IDR: [dampak]
• Sektor terdampak: *[nama sektor]*

*Rekomendasi aksi:*
• [Aksi 1]
• [Aksi 2]

*Confidence level: [Tinggi/Sedang/Rendah]*

_IRIS Alert | [HH:MM] WIB_
```

---

## BAGIAN 2 — LAPORAN HARIAN OSINT & SENTIMEN

### 2.1 Jadwal & Trigger

| Laporan | Waktu Kirim | Sumber |
|---|---|---|
| Morning OSINT | 08.00 WIB | Berita 18 jam terakhir |
| Flash OSINT | Real-time | Viral/breaking event |

### 2.2 Sumber Data OSINT

**Media Mainstream:**
- Kompas, Tempo, Detik, CNN Indonesia
- CNBC Indonesia, Bisnis.com, Kontan
- Antara, Republika, Kumparan

**Media Sosial:**
- Twitter/X Indonesia (trending + akun strategis)
- TikTok (konten viral ekonomi/politik)
- Telegram publik (grup ekonomi, saham, kripto Indonesia)
- YouTube (channel berita dan analis)

**Akun Strategis yang Dipantau:**
- Pejabat BI, OJK, Kemenkeu (pernyataan resmi)
- Menteri ESDM, Menko Perekonomian
- Analis pasar terkemuka Indonesia
- Lembaga rating (Moody's, Fitch, S&P update Indonesia)

### 2.3 Sistem Scoring Sentimen

```
SENTIMEN SCORE — Skala -5 hingga +5

-5 : Sangat Negatif (krisis, kepanikan, skandal besar)
-3 : Negatif (kekhawatiran signifikan, berita buruk)
-1 : Sedikit Negatif (sentimen waspada)
 0 : Netral
+1 : Sedikit Positif (optimisme terbatas)
+3 : Positif (berita baik, kepercayaan meningkat)
+5 : Sangat Positif (euforia, katalis besar)
```

**Dimensi Sentimen yang Diukur:**
- Sentimen pasar saham
- Sentimen rupiah
- Sentimen kebijakan pemerintah
- Sentimen geopolitik
- Sentimen sosial/kamtibmas

### 2.4 Klasifikasi Signal OSINT

```
TIER 1 — ACTIONABLE (langsung kirim alert)
→ Pernyataan kebijakan mendadak dari BI/OJK/Kemenkeu
→ Keputusan Presiden yang berdampak ekonomi
→ Kejadian geopolitik yang mempengaruhi RI
→ Data ekonomi di luar ekspektasi konsensus

TIER 2 — WATCH (masuk laporan harian)
→ Pernyataan pejabat yang mengindikasikan arah kebijakan
→ Tren sentimen sosial yang membangun
→ Isu regulasi yang sedang berkembang
→ Pergerakan korporasi signifikan

TIER 3 — BACKGROUND (masuk laporan mingguan)
→ Opini analis dan riset broker
→ Tren jangka menengah
→ Isu struktural yang berkembang lambat
```

### 2.5 Format WhatsApp — Morning OSINT

```
🔍 *IRIS MORNING OSINT*
*[Hari], [DD MMMM YYYY] | 08.00 WIB*
_Senopati Strategic Institute — Untuk Kalangan Terbatas_

━━━━━━━━━━━━━━━
📰 *HEADLINE STRATEGIS*
━━━━━━━━━━━━━━━
① *[Judul berita/isu 1]* — [Sumber] [HH:MM]
> _[Analisis singkat 2 kalimat — implikasi ke pasar/kebijakan]_
> Signal: *[Positif/Negatif/Netral]* | Tier: *[1/2/3]*

② *[Judul berita/isu 2]* — [Sumber] [HH:MM]
> _[Analisis singkat]_
> Signal: *[Positif/Negatif/Netral]* | Tier: *[1/2/3]*

③ *[Judul berita/isu 3]* — [Sumber] [HH:MM]
> _[Analisis singkat]_
> Signal: *[Positif/Negatif/Netral]* | Tier: *[1/2/3]*

━━━━━━━━━━━━━━━
📊 *SENTIMEN DASHBOARD*
━━━━━━━━━━━━━━━
Saham    : [+/-X] [████░░░░░░] [Positif/Negatif]
Rupiah   : [+/-X] [███░░░░░░░] [Waspada]
Kebijakan: [+/-X] [█████░░░░░] [Netral]
Geopolitik:[+/-X] [██░░░░░░░░] [Negatif]
Sosial   : [+/-X] [████░░░░░░] [Stabil]

━━━━━━━━━━━━━━━
🌐 *ISU YANG BERKEMBANG*
━━━━━━━━━━━━━━━
*[Nama isu]:*
[Narasi perkembangan isu — 3–5 kalimat dengan konteks,
tren, dan implikasi strategis]

━━━━━━━━━━━━━━━
👁 *YANG PERLU DIPERHATIKAN HARI INI*
━━━━━━━━━━━━━━━
• *[Item 1]* — [Alasan]
• *[Item 2]* — [Alasan]
• *[Item 3]* — [Alasan]

_Disiapkan oleh IRIS OSINT Engine_
_Sumber: [daftar sumber] | [HH:MM] WIB_
```

---

## BAGIAN 3 — LAPORAN MINGGUAN GEOPOLITIK & RISIKO

### 3.1 Jadwal

- **Kirim:** Setiap Senin pukul 06.00 WIB
- **Cakupan:** 7 hari ke belakang + outlook 2 minggu ke depan
- **Panjang:** Laporan mendalam, boleh multi-pesan WA

### 3.2 Komponen Wajib

**A. Matriks Risiko Geopolitik**

| Dimensi | Level | Tren | Dampak ke RI |
|---|---|---|---|
| Konflik Indo-Pasifik | Tinggi/Sedang/Rendah | ↑↓→ | [Dampak spesifik] |
| Hubungan China-AS | ... | ... | ... |
| Stabilitas ASEAN | ... | ... | ... |
| Ketegangan Timur Tengah | ... | ... | ... |
| Dinamika Papua/Dalam Negeri | ... | ... | ... |

**B. Analisis Skenario (3 Skenario)**

Untuk setiap isu utama, IRIS wajib menyajikan:
- **Skenario Base Case** (probabilitas terbesar, ~60%)
- **Skenario Bull Case** (kondisi terbaik, ~25%)
- **Skenario Bear Case** (kondisi terburuk, ~15%)

Setiap skenario berisi:
- Kondisi yang harus terpenuhi
- Dampak ke IHSG, IDR, komoditas
- Rekomendasi posisi/aksi

**C. Radar Risiko Indonesia**

Lima dimensi risiko yang diukur mingguan:
1. Risiko politik domestik
2. Risiko fiskal dan utang
3. Risiko eksternal/current account
4. Risiko sosial/kamtibmas
5. Risiko regulasi/kebijakan

**D. Kalender Risiko 2 Minggu**
Event-event yang perlu diwaspadai: rilis data ekonomi, rapat bank sentral, sidang DPR, kunjungan diplomatik, dll.

### 3.3 Format WhatsApp — Laporan Mingguan Geopolitik

```
🌏 *IRIS WEEKLY GEOPOLITICAL BRIEF*
*Pekan [N] | [DD] – [DD MMMM YYYY]*
_Senopati Strategic Institute — Untuk Kalangan Terbatas_
_Klasifikasi: INTERNAL_

━━━━━━━━━━━━━━━
🎯 *EXECUTIVE SUMMARY*
━━━━━━━━━━━━━━━
[Narasi 4–6 kalimat merangkum kondisi geopolitik pekan ini
dan implikasi strategis utama untuk Indonesia]

*Tema dominan pekan ini:*
① *[Tema 1]*
② *[Tema 2]*
③ *[Tema 3]*

━━━━━━━━━━━━━━━
🗺 *MATRIKS RISIKO GEOPOLITIK*
━━━━━━━━━━━━━━━
Indo-Pasifik   : *[TINGGI]* ↑ | Dampak IDR: *Negatif*
China-AS       : *[SEDANG]* → | Dampak Ekspor: *Waspada*
ASEAN          : *[RENDAH]* ↓ | Dampak FDI: *Positif*
Timur Tengah   : *[SEDANG]* ↑ | Dampak Energi: *Negatif*
Domestik RI    : *[RENDAH]* → | Dampak Politik: *Stabil*

━━━━━━━━━━━━━━━
📋 *ISU UTAMA PEKAN INI*
━━━━━━━━━━━━━━━

*🔴 ISU 1: [Judul Isu]*
Latar   : [Konteks 2–3 kalimat]
Fakta   : [Fakta kunci yang terverifikasi]
Dampak  : [Dampak ke Indonesia — spesifik]
Watch   : [Yang perlu dipantau minggu depan]

*🟡 ISU 2: [Judul Isu]*
[Format sama]

*🟢 ISU 3: [Judul Isu]*
[Format sama]

━━━━━━━━━━━━━━━
📊 *ANALISIS SKENARIO — [ISU UTAMA]*
━━━━━━━━━━━━━━━

*🟢 BULL CASE (~25%)*
Kondisi : [Apa yang harus terjadi]
IHSG    : [Dampak — contoh: +1,5–2,5%]
IDR     : [Dampak — contoh: Menguat ke 15.800]
Aksi    : [Rekomendasi posisi]

*⚪ BASE CASE (~60%)*
Kondisi : [Apa yang kemungkinan terjadi]
IHSG    : [Dampak]
IDR     : [Dampak]
Aksi    : [Rekomendasi]

*🔴 BEAR CASE (~15%)*
Kondisi : [Skenario terburuk]
IHSG    : [Dampak — contoh: -3–5%]
IDR     : [Dampak — contoh: Melemah ke 16.500+]
Aksi    : [Hedging yang disarankan]

━━━━━━━━━━━━━━━
🔭 *RADAR RISIKO INDONESIA*
━━━━━━━━━━━━━━━
Politik Domestik : [X]/10 [████████░░] ↑
Fiskal & Utang   : [X]/10 [██████░░░░] →
Eksternal/CA     : [X]/10 [███████░░░] ↑
Sosial/Kamtibmas : [X]/10 [████░░░░░░] →
Regulasi/Kebijakan:[X]/10 [█████░░░░░] ↓

*Perubahan dari pekan lalu:*
↑ Meningkat | → Stabil | ↓ Membaik

━━━━━━━━━━━━━━━
📅 *KALENDER RISIKO 2 MINGGU*
━━━━━━━━━━━━━━━
*Minggu ini:*
• *[Tgl]* — [Event] — Dampak: *[Tinggi/Sedang]*
• *[Tgl]* — [Event] — Dampak: *[Tinggi/Sedang]*

*Minggu depan:*
• *[Tgl]* — [Event] — Dampak: *[Tinggi/Sedang]*
• *[Tgl]* — [Event] — Dampak: *[Tinggi/Sedang]*

━━━━━━━━━━━━━━━
💡 *REKOMENDASI STRATEGIS*
━━━━━━━━━━━━━━━
① *[Rekomendasi 1]* — [Alasan singkat]
② *[Rekomendasi 2]* — [Alasan singkat]
③ *[Rekomendasi 3]* — [Alasan singkat]

_Disiapkan oleh IRIS Geopolitical Engine_
_Senopati Strategic Institute | Pekan [N]/[YYYY]_
```

---

## BAGIAN 4 — LAPORAN MINGGUAN INSTITUSIONAL

### 4.1 Jadwal

- **Kirim:** Setiap Jumat pukul 17.00 WIB
- **Cakupan:** Sinyal dari BI, OJK, Kemenkeu, BPK, ESDM, Bappenas

### 4.2 Sumber Data Institusional

**Bank Indonesia (BI):**
- Rilis RDG (Rapat Dewan Gubernur) dan keputusan suku bunga
- Data inflasi, current account, cadangan devisa
- Statement Gubernur BI — analisis tone (hawkish/dovish/netral)
- Kurs JISDOR harian
- Laporan Kebijakan Moneter

**Otoritas Jasa Keuangan (OJK):**
- Statistik perbankan dan pasar modal
- Regulasi baru dan rancangan aturan
- Data NPL, CAR, LDR perbankan
- Siaran pers dan konferensi

**Kementerian Keuangan:**
- Realisasi APBN (pendapatan, belanja, defisit)
- Lelang SBN dan hasilnya
- Pernyataan Menkeu dan Dirjen Pajak
- Data utang negara

**ESDM & Komoditas:**
- Harga DMO batubara
- Kuota ekspor komoditas
- Kebijakan hilirisasi terbaru
- ICP (Indonesian Crude Price)

**BPS (Badan Pusat Statistik):**
- Inflasi bulanan dan tahunan
- Data PDB
- Neraca perdagangan
- Data ketenagakerjaan

### 4.3 Sistem Klasifikasi Sinyal Institusional

```
POLICY SIGNAL CLASSIFIER

HAWKISH (Kontraktif — cenderung negatif untuk ekuitas):
→ BI naikkan suku bunga
→ OJK perketat regulasi kredit
→ Kemenkeu potong belanja
→ Signal: Waspada untuk saham, positif untuk IDR jangka pendek

DOVISH (Ekspansif — cenderung positif untuk ekuitas):
→ BI turunkan suku bunga atau beri sinyal pemotongan
→ OJK longgarkan aturan
→ Kemenkeu tambah stimulus
→ Signal: Positif untuk saham, negatif untuk IDR

NEUTRAL (Jaga status quo):
→ BI tahan suku bunga dengan language netral
→ Regulasi baru tidak mengubah landscape secara signifikan
→ Signal: Tunggu katalis berikutnya

STRUCTURAL SHIFT (Perubahan paradigma):
→ Kebijakan hilirisasi baru
→ Reformasi pajak besar
→ Perubahan rezim devisa
→ Signal: Analisis mendalam diperlukan — dampak jangka panjang
```

### 4.4 Format WhatsApp — Laporan Mingguan Institusional

```
🏛 *IRIS WEEKLY INSTITUTIONAL BRIEF*
*Pekan [N] | [DD] – [DD MMMM YYYY]*
_Senopati Strategic Institute — Untuk Kalangan Terbatas_

━━━━━━━━━━━━━━━
🏦 *BANK INDONESIA*
━━━━━━━━━━━━━━━
Suku bunga acuan : *[X,XX%]* ([Naik/Turun/Tahan])
Stance kebijakan : *[Hawkish/Dovish/Netral]*
Cadangan devisa  : *USD [XXX,X] miliar*
Inflasi terkini  : *[X,XX%] YoY*

*Analisis BI:*
[Narasi 3–4 kalimat tentang arah kebijakan BI,
tone komunikasi, dan implikasi untuk pasar]

*Signal:* [Positif/Negatif/Netral] untuk [IHSG/IDR]

━━━━━━━━━━━━━━━
📋 *OJK — PASAR KEUANGAN*
━━━━━━━━━━━━━━━
Regulasi baru    : [Ada/Tidak ada] — *[Judul regulasi]*
NPL perbankan    : *[X,XX%]* ([naik/turun] dari [X,XX%])
Arus modal asing : *[Net masuk/keluar] Rp [X,XX T]*
Kapitalisasi pasar: *Rp [X.XXX T]*

*Poin penting:*
[Narasi singkat perkembangan OJK yang relevan]

━━━━━━━━━━━━━━━
💰 *KEMENKEU — FISKAL*
━━━━━━━━━━━━━━━
Realisasi pendapatan : *Rp [X.XXX T]* ([XX%] target)
Realisasi belanja    : *Rp [X.XXX T]* ([XX%] target)
Defisit/Surplus      : *Rp [X.XXX T]* ([X,XX%] PDB)
Lelang SBN terakhir  : *Rp [XXX T]* — [oversubscribed/undersubscribed]
*[X,XX]x*

*Analisis Fiskal:*
[Narasi kondisi fiskal dan implikasi ke pasar obligasi]

━━━━━━━━━━━━━━━
⚡ *ESDM & KOMODITAS STRATEGIS*
━━━━━━━━━━━━━━━
ICP bulan ini    : *USD [XX,XX]/bbl*
DMO batubara     : *USD [XX]/MT*
Kebijakan baru   : [Ada/Tidak] — [Deskripsi singkat]
Hilirisasi update: [Perkembangan terbaru]

━━━━━━━━━━━━━━━
📊 *DATA EKONOMI PEKAN INI*
━━━━━━━━━━━━━━━
[Data] : *[Angka]* vs ekspektasi *[Angka]* — *[Lebih baik/buruk]*
[Data] : *[Angka]* vs bulan lalu *[Angka]* — *[Naik/Turun]*

━━━━━━━━━━━━━━━
🔮 *FORWARD GUIDANCE*
━━━━━━━━━━━━━━━
*Agenda institusional minggu depan:*
• *[Tgl]* — [Institusi]: [Event — misal: RDG BI]
• *[Tgl]* — [Institusi]: [Rilis data]

*Implikasi posisi:*
① [Implikasi 1 dengan *highlight kunci*]
② [Implikasi 2]
③ [Implikasi 3]

━━━━━━━━━━━━━━━
⚖ *POLICY SIGNAL SUMMARY*
━━━━━━━━━━━━━━━
BI       : *[HAWKISH/DOVISH/NETRAL]*
OJK      : *[KETAT/LONGGAR/NETRAL]*
Kemenkeu : *[EKSPANSIF/KONTRAKTIF/NETRAL]*
Overall  : *[KONDUSIF/WASPADA/HATI-HATI]* untuk pasar

_Disiapkan oleh IRIS Institutional Engine_
_Senopati Strategic Institute | Pekan [N]/[YYYY]_
```

---

## BAGIAN 5 — LAPORAN KOMODITAS STRATEGIS INDONESIA

### 5.1 Komoditas yang Dipantau

| Komoditas | Bursa Referensi | Frekuensi | Relevansi |
|---|---|---|---|
| CPO | Bursa Malaysia (BMD) | Harian | Ekspor terbesar RI |
| Batubara | Newcastle, ICE | Harian | Devisa utama |
| Nikel | LME | Harian | Hilirisasi, EV supply |
| Timah | LME | Mingguan | Bangka Belitung |
| Bauksit/Aluminium | LME | Mingguan | Hilirisasi |
| Karet | SICOM Singapore | Mingguan | Sumatera |
| Udang/Perikanan | FAO Index | Bulanan | Ekspor perikanan |
| Minyak Bumi | ICE Brent, NYMEX | Harian | ICP, BBM subsidi |
| Gas LNG | JKM Asia | Mingguan | Ekspor LNG |
| Emas | COMEX, Antam | Harian | Safe haven + domestik |

### 5.2 Indonesia Commodity Risk Matrix

```
FAKTOR RISIKO PER KOMODITAS:

CPO:
- Regulasi biodiesel mandatori
- Cuaca El Niño/La Niña (produksi)
- Tarif impor Uni Eropa (EUDR)
- Kompetisi dengan minyak kedelai

BATUBARA:
- Kebijakan energi terbarukan global
- Permintaan China dan India
- Domestic Market Obligation (DMO)
- Regulasi lingkungan internasional

NIKEL:
- Permintaan baterai EV (Tesla, CATL, dll)
- Kebijakan hilirisasi (larangan ekspor ore)
- Kompetisi Indonesia vs Filipina
- Regulasi lingkungan smelter
```

---

## BAGIAN 6 — LAPORAN KHUSUS: INDONESIA ECONOMIC PULSE

### 6.1 Indikator Unik IRIS untuk Indonesia

**Indikator yang tidak tersedia di terminal Bloomberg biasa:**

**1. Rupiah Stress Index (RSI-IDR)**
Komposit dari:
- Spread bid-ask USD/IDR vs rata-rata 30 hari
- Volume intervensi BI (estimasi dari data JISDOR)
- Posisi NDF (Non-Deliverable Forward) offshore
- Cadangan devisa vs kebutuhan impor
- CDS (Credit Default Swap) Indonesia 5 tahun

**2. Political Risk Premium**
Komposit dari:
- Sentimen media terhadap kebijakan pemerintah
- Stabilitas koalisi DPR
- Approval rating Presiden (jika tersedia survei terbaru)
- Isu hukum yang melibatkan pejabat kunci

**3. Indonesia Commodity Export Tracker**
- Estimasi penerimaan ekspor bulanan
- Tren harga vs volume ekspor
- Dampak ke current account dan cadangan devisa

**4. Social Stability Index**
- Frekuensi demonstrasi dan intensitasnya
- Isu ketenagakerjaan dan PHK massal
- Isu pangan dan inflasi barang pokok
- Trending isu di media sosial yang berpotensi eskalasi

---

## BAGIAN 7 — SISTEM SKENARIO & REKOMENDASI AKSI

### 7.1 Kerangka 3-Skenario IRIS

Untuk setiap isu material, IRIS **wajib** menyajikan tiga skenario:

```
SKENARIO BULL CASE
Probabilitas    : [15–30%]
Kondisi pemicu  : [Kondisi spesifik yang harus terjadi]
Timeline        : [Kapan kemungkinan terjadi]
Dampak IHSG     : [+X% dalam Y hari/minggu]
Dampak IDR      : [Menguat/Melemah ke level X]
Dampak Komoditas: [Naik/Turun X%]
Rekomendasi     : [Sektor/instrumen yang diuntungkan]

SKENARIO BASE CASE
Probabilitas    : [50–65%]
[Format sama]

SKENARIO BEAR CASE
Probabilitas    : [15–25%]
[Format sama]
Hedging         : [Instrumen atau aksi lindung nilai]
```

### 7.2 Confidence Level Framework

```
CONFIDENCE LEVEL IRIS:

TINGGI (>75%)
→ Didukung minimal 3 sumber independen
→ Data kuantitatif tersedia
→ Preseden historis jelas
→ Label: 🟢 CONFIDENCE TINGGI

SEDANG (50–75%)
→ Didukung 2 sumber
→ Data kualitatif lebih dominan
→ Analisis inferensial
→ Label: 🟡 CONFIDENCE SEDANG

RENDAH (<50%)
→ 1 sumber atau sumber tidak terverifikasi
→ Spekulatif atau early signal
→ Perlu validasi lebih lanjut
→ Label: 🔴 CONFIDENCE RENDAH — PERLU VERIFIKASI
```

### 7.3 Rekomendasi Aksi — Taksonomi

```
TIPE REKOMENDASI:

MONITOR   → Pantau tanpa aksi, set alert
RESEARCH  → Lakukan riset lebih dalam sebelum aksi
PREPARE   → Siapkan posisi, tunggu konfirmasi
ACCUMULATE → Mulai bangun posisi secara bertahap
REDUCE    → Kurangi exposure secara bertahap
EXIT      → Keluar dari posisi
HEDGE     → Lindungi posisi yang ada
AVOID     → Jangan masuk ke instrumen/sektor ini
```

---

## BAGIAN 8 — ATURAN FORMATTING WHATSAPP

### 8.1 Hierarki Visual Laporan IRIS

```
LEVEL 1 — Header Utama
*IRIS [NAMA LAPORAN]*
[Tanggal] | [Waktu]
_Senopati Strategic Institute — Untuk Kalangan Terbatas_

LEVEL 2 — Seksi
━━━━━━━━━━━━━━━
[EMOJI] *JUDUL SEKSI*
━━━━━━━━━━━━━━━

LEVEL 3 — Sub-poin
*[Label]:* [Nilai/Narasi]

LEVEL 4 — Detail/Rincian
> _[Teks detail atau analisis]_

LEVEL 5 — Catatan Kaki
_Disiapkan oleh IRIS | [HH:MM] WIB_
```

### 8.2 Emoji Standar IRIS

| Emoji | Konteks |
|---|---|
| 🟢 | Positif, bullish, membaik |
| 🔴 | Negatif, bearish, memburuk |
| 🟡 | Netral, waspada, perlu perhatian |
| ⚪ | Base case, normal |
| 📊 | Data pasar, grafik |
| 💱 | Nilai tukar |
| 🛢 | Komoditas energi |
| 🌏 | Geopolitik, internasional |
| 🏛 | Institusi pemerintah |
| 🔍 | OSINT, intelijen |
| ⚡ | Alert, peringatan cepat |
| 🚨 | Alert kritis, darurat |
| 🎯 | Rekomendasi, target |
| 🔭 | Outlook, proyeksi |
| 📅 | Kalender, jadwal |
| 💡 | Insight, rekomendasi strategis |
| ⚖ | Keseimbangan, kebijakan |
| 👁 | Watch, pantau |

### 8.3 Aturan Bold & Italic dalam Laporan Trading

**Bold (`*teks*`) untuk:**
- Semua angka dan data kuantitatif: `*6,85%*`, `*IHSG 7.234*`
- Level risiko: `*TINGGI*`, `*SEDANG*`, `*RENDAH*`
- Arah: `*Bullish*`, `*Bearish*`, `*Hawkish*`, `*Dovish*`
- Nama instrumen lokal: `*IHSG*`, `*IDR*`, `*SBN*`
- Rekomendasi aksi: `*ACCUMULATE*`, `*REDUCE*`, `*AVOID*`
- Nama institusi Indonesia: `*Bank Indonesia*`, `*OJK*`, `*Kemenkeu*`

**Italic (`_teks_`) untuk:**
- Istilah keuangan asing: `_net buy_`, `_oversubscribed_`, `_hawkish_`
- Nama indeks asing: `_S&P 500_`, `_Dow Jones_`, `_Nikkei_`
- Nama komoditas dengan kode internasional: `_Newcastle Coal_`, `_LME Nickel_`
- Kutipan atau pernyataan langsung pejabat
- Klasifikasi dokumen: `_Untuk Kalangan Terbatas_`

**Bold+Italic (`*_teks_*`) untuk:**
- Nama laporan: `*_RenGiat Irwasum_*`
- Frasa kunci yang sangat kritis: `*_BEAR CASE TERKONFIRMASI_*`
- Nama program strategis asing: `*_Inflation Reduction Act_*`

---

## BAGIAN 9 — ALUR KERJA OTOMASI IRIS

### 9.1 Pipeline Harian

```
05.30 WIB — IRIS Wake Up
→ Ambil data pasar Asia (Nikkei, Hang Seng, KOSPI)
→ Ambil data futures IHSG (jika tersedia)
→ Scan berita overnight (22.00–05.30 WIB)
→ Update sentimen dashboard

06.00 WIB — Data Processing
→ Hitung semua indikator
→ Jalankan sentiment engine
→ Klasifikasi signal (Tier 1/2/3)
→ Generate draft laporan

07.00 WIB — Pre-Market Briefing
→ Finalisasi laporan
→ Kirim via WhatsApp Bot ke grup Senopati

08.00 WIB — Morning OSINT
→ Scan media lokal pagi
→ Identifikasi headline strategis
→ Kirim OSINT report

09.00–15.45 WIB — Market Hours Monitoring
→ Monitor IHSG real-time
→ Pantau IDR setiap 15 menit
→ Scan breaking news
→ Trigger alert jika kondisi terpenuhi

16.30 WIB — Closing Summary
→ Compile data penutupan
→ Analisis dinamika hari
→ Kirim closing report

17.00 WIB — After Hours
→ Scan berita sore
→ Update skenario jika ada perkembangan
→ Persiapkan data untuk besok
```

### 9.2 Pipeline Mingguan

```
SENIN 06.00 WIB
→ Geopolitical Weekly Brief
→ Outlook minggu ini

JUMAT 17.00 WIB
→ Institutional Weekly Brief
→ Review minggu, outlook minggu depan

SETIAP HARI KERJA
→ Pre-market + OSINT + Closing
→ Alert insidentil jika trigger terpenuhi
```

### 9.3 Trigger Alert Otomatis

| Kondisi | Threshold | Aksi IRIS |
|---|---|---|
| IHSG turun tajam | >1,5% dalam 1 jam | Alert segera |
| IDR melemah cepat | >0,5% dalam 1 jam | Alert segera |
| Berita Tier 1 terdeteksi | Confidence >75% | Alert segera |
| Komoditas spike | >3% dalam sehari | Alert segera |
| Statement BI/OJK mendadak | Kapan saja | Alert segera |
| Data ekonomi di luar ekspektasi | >1 std deviation | Alert segera |
| Trending negatif sosmed | Viral dalam 2 jam | Alert Tier 1 |

---

## BAGIAN 10 — PERINTAH MANUAL

| Perintah | Aksi IRIS |
|---|---|
| `iris: market now` | Snapshot pasar saat ini |
| `iris: osint [topik]` | OSINT on-demand topik tertentu |
| `iris: skenario [isu]` | Generate 3 skenario untuk isu |
| `iris: risk score` | Tampilkan skor risiko terkini |
| `iris: komoditas [nama]` | Detail komoditas tertentu |
| `iris: weekly geo` | Kirim geopolitical brief sekarang |
| `iris: weekly inst` | Kirim institutional brief sekarang |
| `iris: alert test` | Test koneksi WhatsApp bot |
| `iris: sentiment [topik]` | Analisis sentimen topik tertentu |
| `iris: flash [isu]` | Laporan cepat 1 pesan untuk isu tertentu |
| `iris: siapa gerak [kode saham]` | Analisis penggerak saham tertentu |
| `iris: monitor [instrumen]` | Tambahkan ke watchlist aktif |
| `iris: outlook [timeframe]` | Proyeksi untuk timeframe tertentu |
| `iris: calendar` | Kalender event ekonomi minggu ini |
| `iris: pause` | Hentikan semua alert sementara |
| `iris: resume` | Aktifkan kembali semua alert |

---

## BAGIAN 11 — DISCLAIMER & ETIKA

- Semua laporan IRIS adalah **analisis informasi**, bukan rekomendasi investasi yang mengikat secara hukum
- IRIS **tidak bertanggung jawab** atas keputusan investasi yang diambil berdasarkan laporan ini
- Setiap laporan harus dicantumkan: `_Senopati Strategic Institute — Untuk Kalangan Terbatas_`
- Data yang digunakan berasal dari sumber publik — bukan informasi _insider_ atau material non-publik
- IRIS **tidak menyimpan** data posisi atau transaksi finansial user
- Confidence level harus **selalu dicantumkan** untuk menghindari over-confidence
- Skenario bear case harus **selalu disertakan** — tidak boleh hanya menyajikan skenario positif
- Untuk isu yang sangat tidak pasti: tambahkan `*⚠ HIGHLY UNCERTAIN — PERLU VALIDASI INDEPENDEN*`

---

*IRIS Knowledge Module: Intelligence Trading & Strategic Market Analysis*
*Versi 1.0 | April 2026 | Senopati Strategic Institute*
*Dipanggil oleh: IRIS AI Agent untuk analisis pasar, geopolitik, institusional, dan OSINT*
*Output delivery: WhatsApp Bot → Grup Internal Senopati*
