# IRIS Knowledge Module — Sistem Menu, Konfigurasi User & Standar Konten Feed HTML
> Modul RAG untuk IRIS AI Agent
> Versi: 1.0 | Tipe: Knowledge Module
> Dipanggil saat: IRIS generate konten HTML feed, menerima permintaan kustomisasi menu, atau mengisi field JSON per kategori
> Melengkapi: iris_knowledge_html_feed.md
> Template referensi: iris_feed_v6.html

---

## META — KAPAN MODUL INI AKTIF

IRIS mengaktifkan modul ini ketika:
- User meminta generate HTML feed
- User meminta tambah, hapus, atau ubah menu
- IRIS perlu tahu konten apa yang harus diisi untuk kategori tertentu
- User menyebut salah satu dari 7 nama menu

---

## BAGIAN 1 — ARSITEKTUR SATU TEMPLATE

### 1.1 Prinsip Dasar

IRIS **tidak pernah** membuat template HTML baru untuk setiap kombinasi menu.
Satu template (`iris_feed_v6.html`) yang fixed + satu `config.json` per user + satu `data.json` yang diisi IRIS.

```
iris_feed_v6.html       ← TIDAK PERNAH DIUBAH oleh IRIS
      +
config.json             ← Preferensi user (menu aktif, nama, frekuensi)
      +
data-[YYYYMMDD].json    ← Konten yang diisi IRIS setiap edisi
      ↓
inject.js               ← Script render otomatis
      ↓
iris-feed-[YYYYMMDD].html ← Output akhir siap publish
```

### 1.2 Mengapa Ini Cukup

Setiap kombinasi menu yang mungkin dilayani cukup dengan mengisi atau mengosongkan field di `data.json`. Template secara otomatis menyembunyikan seksi yang datanya kosong. Tidak ada probabilitas kombinasi yang mengharuskan template baru.

---

## BAGIAN 2 — CONFIG.JSON — KONFIGURASI PER USER

### 2.1 Struktur Lengkap

```json
{
  "config_version": "1.0",
  "user_id": "user-001",
  "nama_feed": "IRIS Intelligence Feed",
  "klasifikasi": "Untuk Kalangan Terbatas",
  "frekuensi": "harian",
  "waktu_publish": {
    "pagi": "07:00",
    "siang": "12:00",
    "sore": "16:30"
  },
  "menu_aktif": [
    "overview",
    "geopolitik",
    "nasional",
    "politik",
    "ekonomi",
    "hukum",
    "polri"
  ],
  "menu_urutan": [
    "overview",
    "geopolitik",
    "nasional",
    "politik",
    "ekonomi",
    "hukum",
    "polri"
  ],
  "kedalaman_analisis": "mendalam",
  "bahasa": "id",
  "distribusi": {
    "embed_dashboard": true,
    "whatsapp_bot": true,
    "wa_notif_format": "ringkas"
  },
  "lead_article_kategori": "auto",
  "max_artikel_per_menu": 5,
  "tampilkan_skor_risiko": true,
  "tampilkan_skenario": true,
  "tampilkan_rekomendasi": true
}
```

### 2.2 Field Kunci

| Field | Nilai Valid | Keterangan |
|---|---|---|
| `menu_aktif` | Array dari 7 ID menu | Hanya menu ini yang diisi IRIS |
| `frekuensi` | `harian`, `mingguan`, `insidentil` | Menentukan kedalaman dan panjang |
| `kedalaman_analisis` | `ringkas`, `menengah`, `mendalam` | Berlaku untuk semua menu |
| `lead_article_kategori` | `auto` atau ID menu | `auto` = IRIS pilih yang paling penting |
| `distribusi.wa_notif_format` | `ringkas`, `penuh` | Format notifikasi WA Bot |

### 2.3 Perintah Kustomisasi User

Ketika user mengetik perintah berikut, IRIS update `config.json` lalu regenerate feed:

| Perintah User | Aksi IRIS |
|---|---|
| `iris: tambah menu [nama]` | Tambahkan ID menu ke `menu_aktif` |
| `iris: hapus menu [nama]` | Hapus ID menu dari `menu_aktif` |
| `iris: urutan menu [a,b,c]` | Update `menu_urutan` |
| `iris: analisis [ringkas/menengah/mendalam]` | Update `kedalaman_analisis` |
| `iris: lead dari [nama menu]` | Update `lead_article_kategori` |
| `iris: max artikel [n]` | Update `max_artikel_per_menu` |
| `iris: config lihat` | Tampilkan config aktif |
| `iris: config reset` | Reset ke default semua menu aktif |

---

## BAGIAN 3 — 7 MENU UTAMA — DEFINISI & STANDAR KONTEN

### ID Referensi Menu

| ID | Label Tampil | Emoji | Prioritas Default |
|---|---|---|---|
| `overview` | Overview | 📋 | 1 — selalu pertama |
| `geopolitik` | Geopolitik | 🌏 | 2 |
| `nasional` | Berita Nasional | 🇮🇩 | 3 |
| `politik` | Politik Dalam Negeri | 🏛 | 4 |
| `ekonomi` | Ekonomi & Bisnis | 📊 | 5 |
| `hukum` | Hukum & HAM | ⚖ | 6 |
| `polri` | Polri | 🚔 | 7 |

---

### 3.1 MENU: OVERVIEW

**Fungsi:** Ringkasan eksekutif seluruh feed — selalu menjadi halaman pertama yang dilihat user. Berisi snapshot situasi terkini lintas semua kategori aktif.

**Kapan diisi:** Selalu — bahkan jika hanya satu menu lain yang aktif.

**Komponen wajib:**

```
A. Executive Summary (3–5 kalimat)
   → Kondisi umum hari ini / pekan ini
   → Isu paling kritis yang perlu perhatian
   → Tone keseluruhan: kondusif / waspada / kritis

B. Skor Risiko Keseluruhan
   → Skala 1–10 per dimensi yang relevan
   → Warna: hijau (<4), kuning (4–6), merah (>6)

C. Highlight per Menu Aktif
   → Satu bullet per menu: isu terpenting hari ini
   → Maksimal 10 kata per bullet

D. Signal Penting Hari Ini
   → 2–3 signal actionable dengan confidence level
   → Tier 1/2/3

E. Kalender / Agenda Penting
   → Event terjadwal yang relevan (sidang, rapat, rilis data)
```

**Sumber data yang diprioritaskan:**
- Agregasi dari semua menu aktif
- Pernyataan pejabat tinggi (Presiden, Menko, Kapolri)
- Data resmi BPS, BI, Kemenkeu yang dirilis hari ini

**Field JSON:**

```json
"overview": {
  "executive_summary": "Narasi 3–5 kalimat kondisi umum...",
  "tone_keseluruhan": "kondusif",
  "skor_risiko": [
    { "label": "Politik", "skor": 4, "warna": "#FFA726" },
    { "label": "Keamanan", "skor": 3, "warna": "#66BB6A" },
    { "label": "Ekonomi", "skor": 6, "warna": "#EF5350" },
    { "label": "Sosial", "skor": 3, "warna": "#66BB6A" },
    { "label": "Hukum", "skor": 4, "warna": "#FFA726" }
  ],
  "highlight_per_menu": [
    { "menu": "geopolitik", "teks": "Ketegangan Indo-Pasifik meningkat pasca pernyataan Trump" },
    { "menu": "ekonomi", "teks": "Rupiah tembus 16.300, BI siapkan intervensi" },
    { "menu": "polri", "teks": "Kasus viral dugaan pelanggaran etik anggota Polda Metro" }
  ],
  "signals": [
    {
      "tier": 1,
      "teks": "Rupiah di level kritis — monitor kebijakan BI",
      "confidence": "Tinggi"
    }
  ],
  "agenda": [
    { "waktu": "10.00 WIB", "event": "Sidang Paripurna DPR — agenda RUU Kepolisian" },
    { "waktu": "14.00 WIB", "event": "Konferensi pers Menkeu soal APBN" }
  ]
}
```

---

### 3.2 MENU: GEOPOLITIK

**Fungsi:** Analisis dinamika internasional dengan fokus pada dampak langsung ke Indonesia — bukan sekadar rangkuman berita luar negeri.

**Prinsip analisis:**
- Setiap isu internasional HARUS dikaitkan dampaknya ke Indonesia
- Fokus pada: Indo-Pasifik, ASEAN, hubungan bilateral strategis (China, AS, Australia, India), konflik regional
- Analisis selalu menyertakan implikasi ke keamanan, ekonomi, dan diplomasi RI

**Kedalaman per level:**

| Level | Isi |
|---|---|
| Ringkas | Fakta + dampak ke RI dalam 2 kalimat |
| Menengah | Fakta + konteks + dampak ke RI + 1 skenario |
| Mendalam | Fakta + konteks + analisis struktural + 3 skenario + rekomendasi |

**Komponen artikel Geopolitik:**

```
- Judul: Isu + dampak spesifik ke Indonesia
- Deck: 2–3 kalimat konteks + stance IRIS
- Fakta kunci: 4 data terverifikasi
- Analisis: Pembacaan struktural IRIS (bukan ringkasan berita)
- Skenario: Bull/Base/Bear jika isu material
- Rekomendasi: Aksi spesifik (diplomatik, ekonomi, keamanan)
- Confidence: Tinggi/Sedang/Rendah
- Tier: 1/2/3
```

**Sumber yang diprioritaskan:**
- Reuters, AP, AFP (berita primer)
- CSIS, IISS, Lowy Institute (analisis)
- Kemenlu RI, Kemhan RI (respons resmi)
- Pernyataan Presiden/Wapres soal isu luar negeri

**Field JSON:**

```json
"geopolitik": {
  "artikel": [
    {
      "id": "geo-001",
      "tier": 1,
      "confidence": "Tinggi",
      "headline": "...",
      "deck": "...",
      "emoji": "🌏",
      "gambar_url": "",
      "penulis": "IRIS Geo Engine",
      "waktu": "11 Apr 2026 · 08.00 WIB",
      "card": {
        "kategori": "Geopolitik",
        "signal": "Waspada"
      },
      "detail": {
        "body": ["paragraf 1", "paragraf 2", "paragraf 3"],
        "fakta": [
          { "label": "Label", "nilai": "Nilai" }
        ],
        "analisis": ["analisis 1", "analisis 2"],
        "rekomendasi": ["rekomendasi 1", "rekomendasi 2"],
        "skenario": {
          "aktif": true,
          "isu": "Nama isu",
          "bull": { "prob": "20%", "ihsg": "+1%", "pemicu": "...", "aksi": "..." },
          "base": { "prob": "65%", "ihsg": "Flat", "pemicu": "...", "aksi": "..." },
          "bear": { "prob": "15%", "ihsg": "-3%", "pemicu": "...", "aksi": "..." }
        }
      }
    }
  ]
}
```

---

### 3.3 MENU: BERITA NASIONAL

**Fungsi:** Isu dan peristiwa penting di dalam negeri yang berdampak luas — bukan berita lokal biasa. Fokus pada isu yang memiliki signifikansi nasional.

**Prinsip seleksi berita:**
- Dampak ke lebih dari satu provinsi atau lebih dari satu sektor
- Melibatkan tokoh nasional atau kebijakan nasional
- Berpotensi mempengaruhi opini publik secara luas
- Bukan berita kriminal biasa — kecuali berdampak sistemik

**Kategori yang masuk Berita Nasional:**
- Bencana alam skala nasional
- Kebijakan pemerintah pusat yang berdampak langsung ke masyarakat
- Isu sosial yang viral dan memiliki dampak kebijakan
- Demonstrasi atau gerakan sosial berskala nasional
- Pemilu, pilkada, atau proses demokrasi penting
- Isu kesehatan publik (wabah, kebijakan BPJS, dll)
- Infrastruktur dan pembangunan strategis

**Yang TIDAK masuk Berita Nasional:**
- Kriminal lokal tanpa dampak nasional → masuk Hukum & HAM jika relevan
- Isu ekonomi murni → masuk Ekonomi & Bisnis
- Isu Polri → masuk menu Polri
- Isu politik partai → masuk Politik Dalam Negeri

**Field JSON:**

```json
"nasional": {
  "artikel": [
    {
      "id": "nas-001",
      "tier": 2,
      "confidence": "Tinggi",
      "headline": "...",
      "deck": "...",
      "emoji": "🇮🇩",
      "gambar_url": "",
      "penulis": "IRIS National Engine",
      "waktu": "...",
      "card": {
        "kategori": "Berita Nasional",
        "signal": "Netral"
      },
      "detail": {
        "body": ["paragraf 1", "paragraf 2"],
        "fakta": [{ "label": "...", "nilai": "..." }],
        "analisis": ["analisis dampak nasional"],
        "rekomendasi": ["tindak lanjut yang perlu dipantau"]
      }
    }
  ]
}
```

---

### 3.4 MENU: POLITIK DALAM NEGERI

**Fungsi:** Dinamika politik Indonesia — partai, koalisi, kabinet, DPR, pilkada, dan manuver aktor politik.

**Prinsip analisis:**
- Tidak berpihak pada partai atau figur politik manapun
- Fokus pada implikasi kebijakan, bukan drama politik
- Analisis kekuatan dan kelemahan posisi aktor secara objektif
- Selalu sertakan implikasi ke stabilitas dan tata kelola

**Kategori yang masuk Politik Dalam Negeri:**
- Manuver koalisi dan oposisi
- Pernyataan dan kebijakan partai politik
- Dinamika kabinet (reshuffle, konflik antar menteri)
- Proses legislasi di DPR (RUU strategis)
- Pilkada dan kontestasi elektoral
- Hubungan eksekutif-legislatif-yudikatif
- Isu kepemimpinan dan regenerasi politik

**Standar netralitas IRIS:**
- Tidak menggunakan kata "mengkritik" tapi "menyampaikan pandangan berbeda"
- Tidak menyebut partai/figur sebagai "baik" atau "buruk"
- Selalu tampilkan perspektif minimal dua pihak
- Gunakan framing: "pihak A berpendapat... sementara pihak B menyatakan..."

**Field JSON:**

```json
"politik": {
  "artikel": [
    {
      "id": "pol-001",
      "tier": 2,
      "confidence": "Sedang",
      "headline": "...",
      "deck": "...",
      "emoji": "🏛",
      "gambar_url": "",
      "penulis": "IRIS Political Engine",
      "waktu": "...",
      "card": {
        "kategori": "Politik Dalam Negeri",
        "signal": "Waspada"
      },
      "detail": {
        "body": ["paragraf 1", "paragraf 2", "paragraf 3"],
        "fakta": [{ "label": "...", "nilai": "..." }],
        "analisis": [
          "Analisis kekuatan posisi aktor...",
          "Implikasi ke stabilitas pemerintahan...",
          "Risiko dan peluang jangka menengah..."
        ],
        "rekomendasi": [
          "Monitor: perkembangan yang perlu dipantau",
          "Watch: aktor atau event kunci minggu depan"
        ]
      }
    }
  ]
}
```

---

### 3.5 MENU: EKONOMI & BISNIS

**Fungsi:** Kondisi ekonomi makro Indonesia, kebijakan fiskal/moneter, korporasi, dan pasar keuangan — dengan analisis dampak ke masyarakat dan investor.

**Sub-kategori dalam Ekonomi & Bisnis:**

| Sub | Fokus |
|---|---|
| Makro | PDB, inflasi, current account, cadangan devisa |
| Fiskal | APBN, pajak, utang negara, belanja pemerintah |
| Moneter | Suku bunga BI, kurs, likuiditas |
| Pasar Modal | IHSG, saham, obligasi, reksadana |
| Komoditas | CPO, batubara, nikel, minyak bumi |
| Korporasi | Kinerja BUMN, merger akuisisi, IPO strategis |
| Perdagangan | Ekspor-impor, neraca dagang, tarif |
| Ketenagakerjaan | PHK, upah, pengangguran |

**Standar data:**
- Semua angka harus disebutkan sumbernya (BPS, BI, OJK, Kemenkeu, Bloomberg)
- Perbandingan selalu Year-on-Year (YoY) dan Month-on-Month (MoM)
- Ekspektasi konsensus harus disertakan jika data dirilis

**Field JSON:**

```json
"ekonomi": {
  "data_utama": [
    { "label": "IHSG", "nilai": "7.234", "perubahan": "-0,42%", "arah": "dn" },
    { "label": "USD/IDR", "nilai": "16.285", "perubahan": "+0,18%", "arah": "dn" },
    { "label": "Inflasi", "nilai": "2,1% YoY", "perubahan": "-0,2%", "arah": "up" }
  ],
  "artikel": [
    {
      "id": "eko-001",
      "sub_kategori": "Moneter",
      "tier": 1,
      "confidence": "Tinggi",
      "headline": "...",
      "deck": "...",
      "emoji": "📊",
      "gambar_url": "",
      "penulis": "IRIS Economic Engine",
      "waktu": "...",
      "card": {
        "kategori": "Ekonomi & Bisnis",
        "signal": "Waspada"
      },
      "detail": {
        "body": ["paragraf 1", "paragraf 2"],
        "fakta": [
          { "label": "Data kunci", "nilai": "Angka + sumber" }
        ],
        "analisis": ["analisis mendalam dengan konteks historis"],
        "rekomendasi": ["aksi atau monitor spesifik"],
        "skenario": {
          "aktif": false
        }
      }
    }
  ]
}
```

---

### 3.6 MENU: HUKUM & HAM

**Fungsi:** Perkembangan hukum, peradilan, dan isu hak asasi manusia di Indonesia — dengan fokus pada implikasi sistemik dan rule of law.

**Prinsip analisis:**
- Fokus pada implikasi sistemik, bukan drama persidangan
- Analisis preseden hukum yang dapat mempengaruhi kebijakan
- HAM: berbasis standar internasional yang diratifikasi Indonesia
- Tidak menyatakan tersangka/terdakwa bersalah sebelum putusan inkrah
- Gunakan "diduga", "menurut dakwaan", "jaksa menyatakan"

**Kategori yang masuk Hukum & HAM:**
- Putusan MK, MA, dan Pengadilan Tipikor yang berdampak luas
- Kasus korupsi pejabat publik dan BUMN
- RUU dan kebijakan hukum baru
- Isu kebebasan pers dan kebebasan sipil
- Kasus pelanggaran HAM — kekerasan aparat, kasus adat, dll
- Penegakan hukum lingkungan
- Kasus hukum korporasi besar

**Yang TIDAK masuk Hukum & HAM:**
- Kasus kriminal biasa tanpa dampak sistemik
- Isu Polri → masuk menu Polri
- Isu korupsi yang melibatkan Polri → bisa masuk keduanya

**Field JSON:**

```json
"hukum": {
  "artikel": [
    {
      "id": "hkm-001",
      "sub_kategori": "Korupsi",
      "tier": 2,
      "confidence": "Tinggi",
      "headline": "...",
      "deck": "...",
      "emoji": "⚖",
      "gambar_url": "",
      "penulis": "IRIS Legal Engine",
      "waktu": "...",
      "card": {
        "kategori": "Hukum & HAM",
        "signal": "Negatif"
      },
      "detail": {
        "body": ["paragraf faktual dengan framing hukum yang benar"],
        "fakta": [{ "label": "Pasal", "nilai": "Pasal 2 ayat 1 UU Tipikor" }],
        "analisis": [
          "Implikasi preseden hukum...",
          "Dampak ke tata kelola dan rule of law..."
        ],
        "rekomendasi": [
          "Monitor: jadwal sidang berikutnya",
          "Watch: respons institusi terkait"
        ]
      }
    }
  ]
}
```

---

### 3.7 MENU: POLRI

**Fungsi:** Perkembangan institusional Polri — kinerja, reformasi, kasus viral, kebijakan internal, dan isu kamtibmas strategis.

**Ini menu paling spesifik** — membutuhkan pemahaman mendalam tentang struktur dan dinamika internal Polri.

**Sub-kategori dalam Polri:**

| Sub | Fokus |
|---|---|
| Institusional | Kebijakan Kapolri, reformasi, reorganisasi |
| Etik & Disiplin | Pelanggaran etik, sidang KKEP, pemecatan |
| Kamtibmas | Situasi keamanan nasional, operasi besar |
| Penyidikan | Kasus besar yang ditangani Bareskrim/Polda |
| Pengawasan | Temuan Itwasum, BPK, Kompolnas |
| Sumber Daya | Anggaran, pengadaan, penerimaan anggota |
| Viral & Publik | Kasus yang viral di media sosial |

**Standar penulisan Polri:**
- Pangkat ditulis lengkap sesuai hierarki: Komjen. Pol., Irjen. Pol., Brigjen. Pol., dll
- Nama satuan ditulis benar: Bareskrim Polri (bukan Bareskim), Divpropam (bukan Propam saja)
- Kasus etik: gunakan "dugaan pelanggaran" sebelum ada putusan KKEP
- Selalu sertakan konteks institusional — bukan sekadar berita personal anggota

**Kosakata institusional Polri yang wajib dikenal IRIS:**

```
Struktur:
Mabes Polri, Polda (34 wilayah), Polres, Polsek
Bareskrim, Brimob, Baharkam, Slog, Lemdiklat
Itwasum (pengawasan utama), Divpropam (profesi & pengamanan)
Kompolnas (pengawas eksternal), Ombudsman

Proses:
KKEP = Komisi Kode Etik Polri (sidang etik)
PTDH = Pemberhentian Tidak Dengan Hormat (pemecatan)
SP3 = Surat Perintah Penghentian Penyidikan
P21 = berkas perkara dinyatakan lengkap

Jabatan penting:
Kapolri, Wakapolri, Irwasum, Kadiv Propam
Kabareskrim, Kabaharkam, Kaslog
```

**Field JSON:**

```json
"polri": {
  "situasi_kamtibmas": "kondusif",
  "skor_institusional": 6,
  "artikel": [
    {
      "id": "plr-001",
      "sub_kategori": "Etik & Disiplin",
      "tier": 1,
      "confidence": "Tinggi",
      "headline": "...",
      "deck": "...",
      "emoji": "🚔",
      "gambar_url": "",
      "penulis": "IRIS Polri Engine",
      "waktu": "...",
      "card": {
        "kategori": "Polri",
        "signal": "Negatif"
      },
      "detail": {
        "body": [
          "Paragraf dengan framing institusional yang tepat...",
          "Konteks proses hukum/etik yang sedang berjalan...",
          "Dampak ke citra dan kepercayaan publik terhadap Polri..."
        ],
        "fakta": [
          { "label": "Satuan", "nilai": "Polda [nama]" },
          { "label": "Proses", "nilai": "Sidang KKEP" },
          { "label": "Status", "nilai": "Dugaan pelanggaran kode etik" }
        ],
        "analisis": [
          "Analisis implikasi institusional...",
          "Pola yang terdeteksi dibanding kasus serupa...",
          "Efektivitas mekanisme pengawasan internal..."
        ],
        "rekomendasi": [
          "Monitor: jadwal sidang KKEP",
          "Watch: respons Divpropam dan Itwasum",
          "Perhatikan: tren kepercayaan publik pasca kasus ini"
        ]
      }
    }
  ]
}
```

---

## BAGIAN 4 — STRUKTUR DATA.JSON LENGKAP

Ini adalah template lengkap `data.json` yang diisi IRIS setiap edisi. Field yang menunya tidak aktif diisi dengan array kosong `[]` atau string kosong `""`.

```json
{
  "meta": {
    "edisi": "Harian",
    "volume": 1,
    "nomor": 48,
    "tanggal": "Sabtu, 12 April 2026",
    "tanggal_iso": "2026-04-12",
    "waktu_generate": "07:00 WIB",
    "klasifikasi": "Untuk Kalangan Terbatas",
    "menu_aktif": ["overview","geopolitik","nasional","politik","ekonomi","hukum","polri"]
  },

  "ticker": [],

  "market_strip": [],

  "overview": {
    "executive_summary": "",
    "tone_keseluruhan": "kondusif",
    "skor_risiko": [],
    "highlight_per_menu": [],
    "signals": [],
    "agenda": []
  },

  "lead_article": {},

  "geopolitik": { "artikel": [] },
  "nasional":   { "artikel": [] },
  "politik":    { "artikel": [] },

  "ekonomi": {
    "data_utama": [],
    "artikel": []
  },

  "hukum":  { "artikel": [] },

  "polri": {
    "situasi_kamtibmas": "kondusif",
    "skor_institusional": 5,
    "artikel": []
  }
}
```

---

## BAGIAN 5 — ATURAN LEAD ARTICLE

Lead article adalah artikel utama yang tampil paling atas dengan gambar besar. IRIS menentukan lead article berdasarkan aturan berikut:

### 5.1 Jika `lead_article_kategori = "auto"`

IRIS memilih lead dari menu aktif berdasarkan hierarki prioritas:

```
PRIORITAS 1: Tier 1 + Confidence Tinggi dari menu manapun
PRIORITAS 2: Tier 1 + Confidence Sedang
PRIORITAS 3: Artikel pertama dari menu dengan urutan tertinggi
```

Jika ada dua atau lebih Tier 1 + Confidence Tinggi, IRIS memilih yang:
- Paling berdampak ke keamanan nasional → pilih Polri atau Geopolitik
- Paling berdampak ke ekonomi → pilih Ekonomi
- Paling relevan dengan tanggal/momentum → judgment IRIS

### 5.2 Jika `lead_article_kategori = "[id menu]"`

IRIS wajib mengambil artikel pertama dari menu tersebut sebagai lead, apapun tier-nya.

### 5.3 Format Lead Article di JSON

```json
"lead_article": {
  "sumber_menu": "polri",
  "artikel_id": "plr-001",
  "override_headline": "",
  "override_deck": ""
}
```

Jika `override_headline` dan `override_deck` kosong, IRIS menggunakan headline dan deck dari artikel sumber. Jika diisi, IRIS menggunakan override untuk tampilan lead (tapi isi modal tetap dari artikel asli).

---

## BAGIAN 6 — ATURAN KONTEN PER LEVEL KEDALAMAN

### 6.1 Ringkas (`kedalaman_analisis: "ringkas"`)

```
Body     : 1 paragraf (3–4 kalimat)
Fakta    : 2 item
Analisis : 1 paragraf (2–3 kalimat)
Rekomendasi: 1–2 item
Skenario : Tidak ada
```

Cocok untuk: update harian cepat, notifikasi, digest pagi.

### 6.2 Menengah (`kedalaman_analisis: "menengah"`)

```
Body     : 2 paragraf (4–5 kalimat masing-masing)
Fakta    : 3–4 item
Analisis : 2 paragraf
Rekomendasi: 2–3 item
Skenario : Hanya jika isu material (Tier 1)
```

Cocok untuk: laporan harian standar.

### 6.3 Mendalam (`kedalaman_analisis: "mendalam"`)

```
Body     : 3–4 paragraf
Fakta    : 4 item
Analisis : 3 paragraf (konteks + pembacaan struktural + implikasi)
Rekomendasi: 3–4 item spesifik
Skenario : Selalu ada untuk semua artikel Tier 1 dan Tier 2
```

Cocok untuk: laporan mingguan, briefing senior, analisis krisis.

---

## BAGIAN 7 — ALUR KERJA IRIS SAAT GENERATE FEED

```
[1] BACA config.json
    → Tentukan menu yang aktif
    → Tentukan kedalaman analisis
    → Catat waktu dan frekuensi

[2] KUMPULKAN DATA per menu aktif
    → Scan sumber sesuai prioritas tiap menu
    → Klasifikasi Tier 1/2/3
    → Hitung confidence level

[3] ISI data.json
    → Overview terakhir diisi (setelah semua menu terisi)
    → Lead article ditentukan berdasarkan aturan Bagian 5
    → Setiap artikel diisi sesuai level kedalaman (Bagian 6)

[4] VALIDASI data.json
    → Semua field meta terisi
    → Minimal 1 artikel per menu aktif
    → Overview sudah merangkum semua menu aktif
    → Lead article valid dan ada sumber menu-nya

[5] INJECT ke template
    → inject.js membaca data.json
    → Render iris-feed-[YYYYMMDD].html
    → Menu yang tidak aktif otomatis tersembunyi

[6] DISTRIBUSI
    → Upload ke hosting (jika dikonfigurasi)
    → Kirim notifikasi WA Bot
    → Embed di dashboard IRIS
```

---

## BAGIAN 8 — NOTIFIKASI WHATSAPP BOT PER MENU

Saat feed siap, IRIS mengirim WA Bot sesuai format yang dikonfigurasi.

### Format Ringkas

```
📋 *IRIS Intelligence Feed*
*[Hari], [DD MMMM YYYY]*

*Highlights:*
[Emoji menu] [Highlight 1 — maks 10 kata]
[Emoji menu] [Highlight 2 — maks 10 kata]
[Emoji menu] [Highlight 3 — maks 10 kata]

🔗 [Link feed]
_Untuk Kalangan Terbatas · IRIS AI_
```

### Format Penuh

```
📋 *IRIS Intelligence Feed*
*[Hari], [DD MMMM YYYY] — Edisi [Harian/Mingguan]*
_Untuk Kalangan Terbatas_

*Executive Summary:*
[2–3 kalimat dari overview.executive_summary]

*Menu aktif hari ini:*
[Emoji] [Nama menu] — [highlight singkat]
[Emoji] [Nama menu] — [highlight singkat]
...

*Signal Penting:*
① [Signal Tier 1]
② [Signal Tier 2]

*Skor Risiko Keseluruhan:* [X]/10

🔗 *Baca selengkapnya:*
[Link feed]

_Digenerate oleh IRIS AI · [HH:MM] WIB_
```

---

## BAGIAN 9 — PERINTAH MANUAL LENGKAP

| Perintah | Aksi IRIS |
|---|---|
| `iris: generate` | Generate feed dengan config saat ini |
| `iris: generate [tanggal]` | Generate feed untuk tanggal tertentu |
| `iris: tambah menu [nama]` | Aktifkan menu |
| `iris: hapus menu [nama]` | Nonaktifkan menu |
| `iris: urutan [menu1,menu2,...]` | Atur urutan menu |
| `iris: lead dari [menu]` | Paksa lead dari menu tertentu |
| `iris: analisis ringkas` | Set kedalaman ringkas |
| `iris: analisis menengah` | Set kedalaman menengah |
| `iris: analisis mendalam` | Set kedalaman mendalam |
| `iris: config lihat` | Tampilkan config aktif |
| `iris: config reset` | Reset ke semua menu aktif + mendalam |
| `iris: preview [menu]` | Preview konten menu tertentu saja |
| `iris: update [menu] [judul]` | Update satu artikel di menu tertentu |
| `iris: publish` | Upload dan kirim link WA |
| `iris: wa ringkas` | Kirim notifikasi WA format ringkas |
| `iris: wa penuh` | Kirim notifikasi WA format penuh |

---

## BAGIAN 10 — CHECKLIST VALIDASI SEBELUM PUBLISH

- [ ] `config.json` terbaca dengan benar
- [ ] Semua menu aktif memiliki minimal 1 artikel
- [ ] `overview.executive_summary` tidak kosong
- [ ] `overview.highlight_per_menu` berisi entry untuk setiap menu aktif
- [ ] `lead_article` mengarah ke artikel yang valid
- [ ] Semua `confidence` diisi: Tinggi/Sedang/Rendah
- [ ] Semua `tier` diisi: 1, 2, atau 3 (angka, bukan string)
- [ ] Tidak ada field yang berisi teks "[placeholder]"
- [ ] Artikel Polri menggunakan terminologi institusional yang benar
- [ ] Artikel Politik menggunakan framing netral
- [ ] Artikel Hukum menggunakan "dugaan" sebelum putusan inkrah
- [ ] Semua sumber data disebutkan (BPS, BI, dll)
- [ ] `waktu_generate` diisi dengan waktu aktual

---

*IRIS Knowledge Module: Sistem Menu, Konfigurasi User & Standar Konten Feed HTML*
*Versi 1.0 | April 2026*
*Melengkapi: iris_knowledge_html_feed.md*
*Template referensi: iris_feed_v6.html*
