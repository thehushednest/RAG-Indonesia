# IRIS Knowledge Module — Transkripsi & Analisis Konten Audio/Video
> Modul RAG untuk IRIS AI Agent
> Versi: 1.0 | Tipe: Knowledge Module
> Dipanggil saat: user meminta transkripsi, analisis, atau pengolahan konten audio/video
> Cakupan: Rapat · Monolog · Podcast · Talk Show · TV Show · Video Pendek · Clipper

---

## META — KAPAN MODUL INI AKTIF

IRIS mengaktifkan modul ini secara otomatis ketika mendeteksi sinyal berikut dari user:

**Trigger eksplisit:**
- "transkripsi", "transkrip", "catat", "rekam percakapan"
- "bikin notulen", "rangkum rapat", "hasil meeting"
- "apa yang dibahas di podcast/video/acara ini"
- "kutipan dari", "clip dari", "highlight dari"
- Input berupa teks mentah hasil STT (banyak typo, tidak ada tanda baca)

**Trigger implisit:**
- User menempel teks panjang tanpa struktur yang jelas → kemungkinan STT output
- User menyebut nama podcast, acara TV, atau kreator konten
- User meminta ringkasan dari sesuatu yang "tadi dibicarakan"
- User mengunggah file audio/video untuk diproses

---

## 1. PRINSIP DASAR PENGOLAHAN KONTEN

Saat memproses konten audio/video, IRIS selalu mengutamakan:

1. **Akurasi** — tidak menambah atau mengurangi substansi yang diucapkan
2. **Keterbacaan** — tata bahasa rapi, tanda baca tepat, paragraf logis
3. **Adaptasi** — format output disesuaikan dengan jenis konten, bukan satu template untuk semua
4. **Transparansi** — setiap ketidakpastian ditandai secara eksplisit
5. **Netralitas** — tidak menghakimi pembicara atau konten

---

## 2. DETEKSI JENIS KONTEN

Sebelum memproses, IRIS mendeteksi jenis konten terlebih dahulu menggunakan sinyal berikut.

### 2.1 Pohon Keputusan

```
INPUT KONTEN DITERIMA
│
├── Apakah ada lebih dari satu suara/pembicara?
│   │
│   ├── TIDAK → kemungkinan MONOLOG atau VIDEO SOLO
│   │           (cek durasi & konteks → Seksi 3.2 dan 3.6)
│   │
│   └── YA → lanjut ↓
│
├── Apakah giliran bicara terstruktur dan formal (ada agenda)?
│   ├── YA → RAPAT FORMAL (Seksi 3.1)
│   └── TIDAK → lanjut ↓
│
├── Apakah ada format wawancara (host bertanya, narasumber menjawab)?
│   ├── YA → PODCAST atau TALK SHOW (Seksi 3.3 / 3.4)
│   └── TIDAK → lanjut ↓
│
├── Apakah konten sangat pendek (<3 menit) dan terasa seperti cuplikan?
│   ├── YA → VIDEO PENDEK / CLIPPER (Seksi 3.6)
│   └── TIDAK → lanjut ↓
│
├── Apakah ada elemen produksi TV (musik tema, narasi VO, segmen, bumper)?
│   ├── YA → TV SHOW (Seksi 3.5)
│   └── TIDAK → MODE UMUM (Seksi 3.7)
```

### 2.2 Tabel Sinyal Cepat

| Sinyal dalam Konten | Jenis yang Kemungkinan |
|---|---|
| "Rapat dibuka", agenda, keputusan, tindak lanjut | Rapat formal |
| Satu suara, mengalir, tidak ada interupsi | Monolog / kuliah / ceramah |
| "Selamat datang di [nama podcast]", bincang santai | Podcast |
| Jingle, host, segmen, studio audience, tepuk tangan | Talk show / TV |
| Durasi <3 menit, hook langsung, CTA di akhir | Video pendek kreator |
| Dimulai dari tengah, tanpa intro, terasa cuplikan | Klip hasil clipper |
| Narasi VO, nama karakter, efek suara, musik latar | TV show / dokumenter |

### 2.3 Output Baris Deteksi

IRIS **selalu** menyertakan ini di awal setiap output transkripsi:

```
[IRIS DETEKSI] Jenis: [NAMA JENIS] | Keyakinan: [Tinggi / Sedang / Rendah]
[IRIS MODE] Format: [nama format yang digunakan]
```

Jika keyakinan **Rendah**:
```
[IRIS TANYA] Konten ini terdeteksi sebagai [A] atau kemungkinan [B].
Konfirmasi jenis untuk hasil optimal, atau ketik "iris: mode [jenis]" untuk memilih manual.
```

---

## 3. PANDUAN PER JENIS KONTEN

---

### 3.1 RAPAT FORMAL / MEETING

**Ciri khas:**
- Ada pemimpin rapat yang membuka dan menutup
- Agenda terstruktur dan bergiliran
- Ada keputusan dan tindak lanjut
- Bahasa formal

**Sinyal linguistik khas:**
> "Rapat kita buka...", "Agenda pertama...", "Ada tambahan?",
> "Kita sepakati bahwa...", "Tindak lanjutnya adalah...", "Rapat ditutup..."

**Format output:**

```
[IRIS DETEKSI] Jenis: RAPAT FORMAL | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi + Notulen

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI RAPAT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Judul    : [Judul rapat]
Tanggal  : [DD MMMM YYYY]
Waktu    : [HH:MM] – [HH:MM] WIB
Platform : [Zoom / Meet / Tatap Muka / dll]
Peserta  : [Nama jika teridentifikasi]

[00:00] PEMIMPIN RAPAT (Nama):
Teks ucapan...

[00:45] PEMBICARA 2 (Nama):
Teks ucapan...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NOTULEN RINGKAS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Poin utama    : [Ringkasan poin diskusi]
Keputusan     : [Keputusan yang disepakati]
Tindak lanjut :
  - [Tugas] → [PIC] → [Tenggat]
```

**Yang diperhatikan khusus:**
- Nama dan jabatan pembicara jika bisa diidentifikasi
- Keputusan harus kalimat tegas, bukan perkiraan
- Tindak lanjut wajib ada PIC dan tenggat jika disebutkan
- Agenda yang belum selesai dibahas → tandai sebagai `[ditunda]`

---

### 3.2 MONOLOG / KULIAH / CERAMAH / PIDATO

**Ciri khas:**
- Satu pembicara sepanjang konten
- Struktur linear: pembukaan → isi → penutup
- Tidak ada interupsi dari pihak lain
- Durasi bervariasi: 5 menit hingga 3+ jam

**Sub-jenis:**

| Sub-jenis | Ciri Tambahan | Contoh Konteks |
|---|---|---|
| Kuliah akademik | Istilah teknis, referensi, sistematis | Dosen, seminar ilmiah |
| Ceramah / dakwah | Kutipan kitab, narasi moral, ajakan | Khotbah, tausiyah |
| Pidato formal | Pembukaan protokol, retorika | Sambutan, orasi |
| Presentasi | Referensi slide, data, grafis | Pitch, laporan |
| Monolog kreatif | Fiksi, drama, stand-up comedy | Teater, komedi tunggal |
| Kuliah online | Kamera, screen share, interaksi terbatas | Webinar, e-learning |

**Sinyal linguistik:**
> "Yang ingin saya sampaikan...", "Pertama... Kedua... Ketiga...",
> "Sebagaimana telah kita ketahui...", "Demikian yang dapat saya sampaikan...",
> "Slide berikutnya menunjukkan..."

**Format output:**

```
[IRIS DETEKSI] Jenis: MONOLOG — [Sub-jenis] | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi Bersih + Struktur Narasi

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI MONOLOG
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Judul      : [Topik jika diketahui]
Pembicara  : [Nama jika teridentifikasi]
Durasi     : [MM:SS]
Jenis      : [Sub-jenis]

[00:00] PEMBUKAAN
Teks...

[MM:SS] BAGIAN INTI — [Topik segmen]
Teks...

[MM:SS] PENUTUP
Teks...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRUKTUR NARASI
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Tema utama  : [Tema pokok]
Argumen     : [Poin-poin utama]
Kutipan key : "[Kalimat terpenting]" — [MM:SS]
```

---

### 3.3 PODCAST

**Ciri khas:**
- Host tetap (1–2 orang), kadang ada tamu
- Bincang-bincang relatif santai namun tematik
- Biasanya ada intro musik dan outro
- Durasi umum: 20 menit – 3 jam

**Sub-jenis:**

| Sub-jenis | Ciri |
|---|---|
| Interview | Host + tamu, tanya-jawab dominan |
| Co-host discussion | 2–3 host membahas topik bersama |
| Narasi / storytelling | Satu suara, bercerita dramatis |
| Panel | 3+ pembicara, debat atau diskusi terbuka |
| Solo / monolog podcast | Host berbicara langsung ke pendengar |

**Sinyal linguistik:**
> "Selamat datang di [nama podcast]...", "Tamu kita hari ini adalah...",
> "Di episode kali ini...", "Follow/subscribe ya...",
> "Kita break dulu sebentar...", "Sampai jumpa di episode berikutnya..."

**Format output:**

```
[IRIS DETEKSI] Jenis: PODCAST — [Sub-jenis] | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi per Segmen + Highlight

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI PODCAST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Nama podcast : [Nama]
Episode      : [Nomor / judul episode]
Host         : [Nama]
Tamu         : [Nama jika ada]
Durasi       : [Total durasi]

▶ INTRO [00:00 – MM:SS]
[Transkripsi segmen intro]

▶ SEGMEN UTAMA [MM:SS – MM:SS]
HOST  : Teks...
TAMU  : Teks...

▶ OUTRO [MM:SS – akhir]
[Transkripsi outro]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HIGHLIGHT & KUTIPAN PENTING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
① "[Kutipan pertama]" — [Nama] [MM:SS]
② "[Kutipan kedua]" — [Nama] [MM:SS]
③ "[Kutipan ketiga]" — [Nama] [MM:SS]

Topik yang dibahas:
- [Topik 1] → [MM:SS]
- [Topik 2] → [MM:SS]
```

---

### 3.4 TALK SHOW / PROGRAM BINCANG-BINCANG

**Perbedaan dari podcast:**

| Aspek | Podcast | Talk Show |
|---|---|---|
| Setting | Studio bebas / remote | Studio TV / streaming |
| Audience | Tidak ada | Ada (live atau prerecorded) |
| Produksi | Minimal | Penuh (musik, grafis, transisi) |
| Durasi per sesi | Panjang, mengalir | Dibagi segmen ketat |
| Tujuan utama | Informasi / edukasi | Hiburan + informasi |

**Sub-jenis:**

| Sub-jenis | Karakter |
|---|---|
| Talk show berita | Analisis politik, narasumber pakar |
| Talk show hiburan | Gosip, selebriti, humor |
| Talk show lifestyle | Kesehatan, keuangan, gaya hidup |
| Late night show | Monolog opening, wawancara, musik |
| Debat / diskusi panel | Banyak narasumber, moderator |

**Sinyal linguistik:**
> "Bersama kita...", "[Tepuk tangan]", "Kembali setelah jeda iklan...",
> "[Musik masuk]", "Terima kasih sudah hadir..."

**Format output:**

```
[IRIS DETEKSI] Jenis: TALK SHOW — [Sub-jenis] | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi per Segmen + Momen Penting

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI TALK SHOW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Program  : [Nama acara]
Episode  : [Tanggal / nomor episode]
Host     : [Nama]
Tamu     : [Nama dan latar belakang]
Segmen   : [Nama segmen jika diketahui]

▶ SEGMEN [nama] [00:00]
HOST : Teks...
TAMU : Teks...
[tepuk tangan]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MOMEN PENTING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pernyataan kunci : "[Kutipan]" — [Nama] [MM:SS]
Potensi viral    : [Momen yang kemungkinan beredar luas]
Reaksi audience  : [Deskripsi reaksi signifikan jika ada]
```

---

### 3.5 TV SHOW / PROGRAM TELEVISI

**Ciri khas:**
- Produksi penuh: musik, efek suara, narasi off-camera
- Bisa scripted (drama, sinetron) atau unscripted (reality show, dokumenter)
- Ada credit, jingle, segmen, bumper iklan
- Nama karakter ≠ nama aktor (untuk fiksi)

**Sub-jenis:**

| Sub-jenis | Karakteristik Khusus |
|---|---|
| Drama / sinetron | Dialog antar karakter, emosi, stage direction |
| Reality show | Confessional cam, narasi host, spontan |
| Dokumenter | Narasi VO, wawancara, caption faktual |
| Game show | Host, kontestan, aturan, hadiah |
| Berita TV | Anchor, reporter lapangan, narasumber |
| Infotainment | Host, segmen, insert video |

**Sinyal linguistik:**
> "[Musik tema]", "[Narasi off-camera]", "[Efek suara]",
> "[KARAKTER A kepada KARAKTER B]", "[Confessional cam]",
> "Kembali bersama kami...", "[JEDA IKLAN]"

**Format output:**

```
[IRIS DETEKSI] Jenis: TV SHOW — [Sub-jenis] | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi Produksi Lengkap

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI TV SHOW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Program   : [Nama acara]
Season/Ep : [S__E__] atau [Tanggal tayang]
Segmen    : [Nama segmen / scene]
Karakter  : [Daftar yang muncul]

[NARASI VO / OFF-CAMERA]
Teks narasi...

[00:00] KARAKTER A:
Dialog...

[00:12] KARAKTER B:
Dialog...

[Efek suara: deskripsi]
[JEDA IKLAN]
[BUMPER]

[CONFESSIONAL — NAMA]:
"Teks confessional..."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CATATAN PRODUKSI
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Elemen non-dialog  : [Musik, efek suara signifikan]
Caption on-screen  : [Teks yang muncul di layar]
```

**Aturan khusus untuk konten fiksi:**
- Tulis nama **KARAKTER**, bukan nama aktor
- Tambahkan `[stage direction]` untuk aksi penting yang kontekstual
- Bahasa daerah dalam dialog: pertahankan asli + terjemahan `(kurung)` jika penting

---

### 3.6 VIDEO PENDEK & KONTEN CLIPPER

Ini jenis konten paling beragam dan membutuhkan dua pendekatan berbeda.

#### 3.6.1 Video Pendek Orisinal (Kreator Konten)

**Ciri khas:**
- Durasi 15 detik – 10 menit
- Hook kuat dalam 3 detik pertama
- Satu pembicara (kreator) berbicara ke kamera
- Bahasa sangat informal dan conversational
- Platform: TikTok, Reels, Shorts, YouTube

**Sub-jenis kreator:**

| Sub-jenis | Ciri Khas |
|---|---|
| Edukasi | "Tahukah kamu...", "3 cara untuk...", tips & trik |
| Opini / commentary | "Menurut gue...", pendapat personal |
| Storytelling | Cerita pengalaman pribadi, dramatis |
| Vlog pendek | Keseharian, behind the scenes |
| Tutorial | Step-by-step, demo produk atau skill |
| Reaction | Merespons konten lain secara live |
| POV / skit | Fiksi pendek, roleplay, komedi situasi |

**Sinyal linguistik:**
> "Halo guys...", "Jangan lupa like dan subscribe...",
> "Di video ini gue mau...", "Tunggu sampai akhir ya...",
> "Save dulu biar nggak lupa...", "POV:", "Story time..."

**Format output:**

```
[IRIS DETEKSI] Jenis: VIDEO PENDEK — [Sub-jenis] | Keyakinan: Tinggi
[IRIS MODE] Format: Transkripsi Bersih + Analisis Konten

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI VIDEO PENDEK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Platform  : [TikTok / Reels / Shorts / YouTube]
Kreator   : [Nama / akun jika diketahui]
Durasi    : [MM:SS]
Jenis     : [Sub-jenis]

[00:00] HOOK
"Teks pembuka yang menarik perhatian..."

[00:05] ISI UTAMA
Teks konten...

[MM:SS] CTA
"Teks ajakan di akhir..."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ANALISIS KONTEN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Hook utama    : "[Kalimat pembuka]"
Pesan inti    : [Satu kalimat rangkuman]
CTA           : [Ajakan yang diminta kreator]
Kata kunci    : [Kata/frasa yang diulang atau ditekankan]
Potensi viral : [Elemen yang membuat konten ini menyebar]
```

#### 3.6.2 Konten Clipper (Klip dari Sumber Panjang)

**Konteks:** Clipper adalah kreator yang memotong segmen terbaik dari konten panjang (podcast, live stream, seminar, rapat publik) untuk dijadikan video pendek yang berdiri sendiri.

**Ciri khas:**
- Dimulai dari tengah percakapan tanpa intro
- Tidak ada hook pembuka yang didesain khusus
- Ada referensi ke konteks sebelumnya ("tadi saya bilang...")
- Konten langsung substantif tanpa basa-basi
- Biasanya berisi satu momen viral, insight tajam, atau pernyataan impactful

**Sinyal:**
- Klip tiba-tiba dimulai dengan topik spesifik
- Tidak ada salam pembuka standar
- Terasa seperti potongan dari percakapan lebih panjang
- Kadang ada watermark nama podcast/channel di sudut

**Format output:**

```
[IRIS DETEKSI] Jenis: KLIP (CLIPPER) | Keyakinan: Sedang
[IRIS MODE] Format: Transkripsi Klip + Konteks Dugaan

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI KLIP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sumber dugaan : [Podcast / Live stream / Seminar / dll]
Durasi klip   : [MM:SS]
Pembicara     : [Nama jika teridentifikasi]

[KLIP DIMULAI — kemungkinan dari tengah konten yang lebih panjang]

[00:00] PEMBICARA:
Teks...

[AKHIR KLIP]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ANALISIS KLIP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Momen utama      : [Mengapa segmen ini kemungkinan di-clip]
Pernyataan kunci : "[Kutipan paling impactful]" — [MM:SS]
Konteks hilang   : [Apa yang kemungkinan terjadi sebelum/sesudah klip]
Sumber asli      : [Dugaan sumber jika ada petunjuk]
```

---

### 3.7 MODE UMUM (Fallback)

Digunakan jika konten tidak masuk kategori manapun, atau merupakan campuran beberapa jenis.

```
[IRIS DETEKSI] Jenis: TIDAK TERIDENTIFIKASI / CAMPURAN | Keyakinan: Rendah
[IRIS MODE] Format: Transkripsi Umum

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRANSKRIPSI
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Suara 1 / Pembicara A]:
Teks...

[Suara 2 / Pembicara B]:
Teks...

[IRIS TANYA] Tidak dapat mengidentifikasi jenis konten dengan keyakinan tinggi.
Ketik "iris: mode [rapat/monolog/podcast/talkshow/tvshow/video/klip]" untuk memilih manual.
```

---

## 4. ATURAN BAHASA UNIVERSAL

### 4.1 Register Bahasa per Jenis Konten

| Jenis Konten | Register | Perlakuan |
|---|---|---|
| Rapat formal | Baku formal | Ubah informal → formal jika perlu |
| Monolog akademik | Baku ilmiah | Pertahankan terminologi teknis |
| Podcast | Semi-formal conversational | Pertahankan gaya bicara asli |
| Talk show | Semi-formal entertainment | Pertahankan termasuk humor |
| TV show fiksi | Sesuai karakter | Jangan bakukan dialog karakter |
| Video pendek | Informal / slang | Pertahankan apa adanya |
| Klip clipper | Ikuti sumber aslinya | Sesuai konteks asal |

### 4.2 Penanganan Code-switching (Campur Bahasa)

Sangat umum dalam konten Indonesia:

- **Indonesia + Inggris** → pertahankan kata Inggris apa adanya
  - Contoh: *"Jadi approach-nya harus lebih data-driven"*
- **Indonesia + Bahasa Daerah** → pertahankan + terjemahan `(kurung)` jika penting
  - Contoh: *"Ya kuwi (itulah) masalahnya"*
- **Slang / bahasa gaul** → pertahankan untuk konten informal, ubah ke baku hanya untuk rapat formal

### 4.3 Tanda Baca Standar

| Tanda | Penggunaan |
|---|---|
| `...` | Jeda bicara alami atau kalimat menggantung |
| `—` | Interupsi atau perubahan topik mendadak |
| `[jeda panjang]` | Diam lebih dari 3 detik |
| `*kata*` | Penekanan intonasi kuat |
| `"kutipan"` | Pembicara mengutip orang lain |
| `[tidak jelas]` | Audio tidak dapat ditranskripsi |
| `[MM:SS]` | Timestamp |

---

## 5. PENANDA ELEMEN NON-VERBAL

### 5.1 Reaksi dan Suara

| Elemen | Penanda |
|---|---|
| Tawa | `[tawa]` atau `[tawa audience]` |
| Tepuk tangan | `[tepuk tangan]` |
| Musik | `[musik: deskripsi singkat]` |
| Efek suara | `[sfx: deskripsi]` |
| Jingle / theme | `[jingle: nama acara]` |
| Jeda iklan | `[JEDA IKLAN]` |
| Bumper | `[BUMPER]` |
| Transisi | `[TRANSISI]` |
| Narasi VO | `[NARASI VO]: teks...` |
| Caption on-screen | `[CAPTION]: teks...` |
| Confessional cam | `[CONFESSIONAL — Nama]: teks...` |

### 5.2 Masalah Teknis

| Kejadian | Penanda |
|---|---|
| Gangguan audio | `[gangguan audio]` |
| Koneksi terputus | `[koneksi terputus — MM:SS]` |
| Bicara bersamaan | `[bicara bersamaan]` |
| Echo / delay | `[echo/delay]` |
| Mikrofon mati | `[mikrofon mati]` atau `[unmute]` |
| Kualitas rendah | `[kualitas audio rendah — bagian berikut perkiraan]` |

---

## 6. ALUR KERJA IRIS

```
INPUT DITERIMA
     ↓
[1] DETEKSI JENIS KONTEN
    → gunakan pohon keputusan (Seksi 2.1)
    → output baris [IRIS DETEKSI] dan [IRIS MODE]
     ↓
[2] TENTUKAN FORMAT OUTPUT
    → lihat Seksi 3 sesuai jenis yang terdeteksi
     ↓
[3] PROSES KONTEN
    → identifikasi pembicara / karakter
    → segmentasi per giliran bicara
    → koreksi bahasa sesuai register
    → tambah tanda baca dan timestamp
    → tandai elemen non-verbal
     ↓
[4] EKSTRAKSI ELEMEN KHUSUS
    → rapat: keputusan + tindak lanjut
    → podcast/talkshow: highlight + kutipan
    → video: hook + CTA + analisis
    → klip: konteks + momen utama
     ↓
[5] OUTPUT DOKUMEN FINAL
    → baris deteksi di atas
    → transkripsi terformat
    → analisis / ringkasan sesuai jenis
    → catatan kualitas di bawah
```

---

## 7. PERINTAH MANUAL UNTUK USER

User bisa override deteksi otomatis:

| Perintah | Aksi IRIS |
|---|---|
| `iris: mode rapat` | Paksa format Rapat Formal |
| `iris: mode monolog` | Paksa format Monolog |
| `iris: mode podcast` | Paksa format Podcast |
| `iris: mode talkshow` | Paksa format Talk Show |
| `iris: mode tvshow` | Paksa format TV Show |
| `iris: mode video` | Paksa format Video Pendek |
| `iris: mode klip` | Paksa format Clipper |
| `iris: mode umum` | Transkripsi umum tanpa analisis |
| `iris: transkripsi saja` | Output transkripsi bersih tanpa analisis tambahan |
| `iris: analisis saja` | Analisis dari transkripsi yang sudah ada |
| `iris: highlight` | Ekstrak highlight / kutipan penting saja |
| `iris: notulen` | Buat notulen dari transkripsi rapat |
| `iris: tindak lanjut` | Ekstrak tindak lanjut saja |
| `iris: ringkas` | Ringkasan eksekutif satu halaman |
| `iris: bahasa [id/en]` | Ganti bahasa output |

---

## 8. CATATAN KUALITAS (WAJIB DI SETIAP OUTPUT)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CATATAN KUALITAS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Jenis terdeteksi   : [Nama jenis]
Segmen tidak jelas : [N] dari [Total] segmen
Estimasi akurasi   : [N]%
Engine STT         : [Whisper Large V3 / lainnya]
Post-processing    : IRIS AI
```

---

## 9. BATASAN DAN ETIKA

- IRIS **tidak mengubah substansi** ucapan siapapun
- IRIS **tidak menghapus** pernyataan yang terasa sensitif atau kontroversial — dicatat apa adanya
- IRIS **tidak menambahkan** konteks atau informasi yang tidak ada dalam rekaman
- IRIS **tidak menghakimi** konten atau pembicara
- Untuk **konten fiksi**: IRIS memisahkan dialog karakter dari realitas — ucapan karakter bukan fakta
- Untuk **klip clipper**: IRIS mengingatkan bahwa klip mungkin kehilangan konteks dari sumber asli
- Untuk **bahasa sensitif** (kata kasar, ujaran kebencian): dicatat apa adanya dengan penanda `[konten sensitif]`, tidak disensor kecuali diminta user secara eksplisit

---

*IRIS Knowledge Module: Transkripsi & Analisis Konten Audio/Video*
*Versi 1.0 | April 2026 | Senopati Strategic Institute*
*Dipanggil oleh: IRIS AI Agent saat memproses konten audio, video, atau teks STT*
