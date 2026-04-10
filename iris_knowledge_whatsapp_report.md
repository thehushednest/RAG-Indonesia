# IRIS Knowledge Module — Penyusunan Laporan WhatsApp Polri
> Modul RAG untuk IRIS AI Agent
> Versi: 2.0 | Tipe: Knowledge Module
> Dipanggil saat: user meminta penyusunan, konversi, atau pemformatan laporan untuk dikirim via WhatsApp
> Cakupan: 5 format laporan Polri + aturan formatting WhatsApp + highlighting otomatis

---

## META — KAPAN MODUL INI AKTIF

IRIS mengaktifkan modul ini secara otomatis ketika mendeteksi sinyal berikut:

**Trigger eksplisit:**
- "buatkan laporan WA", "format WhatsApp", "laporan siap kirim"
- "susun laporan dari dokumen ini", "ubah ke format WA"
- "bikin laporan untuk Irwasum / Kapolri / atasan"
- "draft laporan", "tulis laporan situasi", "laporkan hasil kunjungan"
- "buatkan rengiat", "susun rencana kegiatan pimpinan", "jadwal kegiatan hari ini"
- "rengiat harian", "agenda pimpinan", "jadwal irwasum"

**Trigger implisit:**
- User menempel dokumen laporan dan meminta "rapikan" atau "format ulang"
- User menempel notulen rapat dan meminta dijadikan laporan
- User menyebut konteks Polri, BPK, kunjungan pengadaan, atau insiden keamanan
- Input berupa teks laporan yang belum terformat

**Yang SELALU dilakukan sebelum menulis laporan:**
IRIS wajib menanyakan kepada user:
1. **Kepada** — siapa penerima laporan? (nama + jabatan)
2. **Dari** — siapa pengirim laporan? (nama + jabatan)
3. **Tembusan** — apakah ada tembusan? (jika Format 1)

Jika user tidak memberikan informasi ini, IRIS menggunakan placeholder:
`[NAMA PENERIMA / JABATAN]` dan `[NAMA PENGIRIM / JABATAN]`

---

## 1. SINTAKS FORMATTING WHATSAPP

IRIS wajib menguasai dan menerapkan sintaks berikut pada setiap laporan:

### 1.1 Tabel Sintaks Dasar

| Efek | Sintaks | Contoh Input | Hasil |
|---|---|---|---|
| **Tebal / Bold** | `*teks*` | `*Irwasum Polri*` | **Irwasum Polri** |
| _Miring / Italic_ | `_teks_` | `_factory inspection_` | _factory inspection_ |
| ~~Coret~~ | `~teks~` | `~dibatalkan~` | ~~dibatalkan~~ |
| `Monospace` | ` ```teks``` ` | Kode/nomor teknis | `teks` |
| Bullet | `- teks` atau `• teks` | Item daftar | • teks |
| Angka | `1. teks` | Item bernomor | 1. teks |
| Kutipan | `> teks` | Informasi tambahan | > teks |
| Baris kosong | baris kosong | Pemisah antar bagian | spasi |

### 1.2 Aturan Penggunaan

**Bold (`*teks*`) digunakan untuk:**
- Nama jabatan dan institusi: `*Irwasum Polri*`, `*BPK RI*`
- Nama orang dengan pangkat: `*Komjen. Pol. Wahyu Widada*`
- Judul bab/seksi: `*A. PELAKSANAAN KEGIATAN*`
- Angka dan nilai penting: `*USD 19.990.775,-*`
- Kata kunci kritis dalam kalimat: `*tidak ditemukan indikasi penyimpangan*`
- Keputusan dan kesimpulan: `*memenuhi standar teknologi tinggi*`
- Status dan kondisi: `*kondusif*`, `*legitimate*`, `*justified*`
- Tenggat, tanggal penting, dan lokasi kunci

**Italic (`_teks_`) digunakan untuk:**
- Semua kata/frasa bahasa Inggris: `_factory inspection_`, `_remote collaboration_`
- Nama produk/merek asing: `_VisionX_`, `_AW139_`
- Nama perusahaan asing: `_Projectina AG_`, `_Leonardo S.p.A._`
- Istilah teknis berbahasa asing: `_apochromatic optics_`, `_auto-focus_`
- Singkatan asing yang belum dibakukan: `_lender_`, `_maintenance_`

**Kombinasi Bold+Italic (`*_teks_*`) digunakan untuk:**
- Nama produk asing yang sekaligus kritis: `*_VisionX_*`
- Pernyataan kunci dalam bahasa Inggris: `*_Scientific Crime Investigation_*`
- Istilah teknis yang menjadi poin utama laporan

**Kutipan (`> teks`) digunakan untuk:**
- Rincian teknis yang merupakan sub-poin
- Detail spesifikasi atau temuan yang panjang
- Informasi pendukung yang bukan poin utama

**DILARANG:**
- Menggunakan bold untuk seluruh kalimat panjang (lebih dari 8 kata)
- Menggunakan italic untuk kata Indonesia biasa
- Bold berlebihan yang menghilangkan efek penekanan
- Menggunakan simbol formatting di tengah kata tanpa alasan

---

## 2. ATURAN HIGHLIGHTING KATA KUNCI

IRIS menerapkan highlighting **pada semua kata kunci penting** dengan prinsip berikut:

### 2.1 Kategori Kata Kunci yang Wajib Di-bold

| Kategori | Contoh | Perlakuan |
|---|---|---|
| Nama jabatan | Irwasum Polri, Kapolri, Karorenmin | `*Irwasum Polri*` |
| Nama orang + pangkat | Komjen. Pol. Wahyu Widada | `*Komjen. Pol. Wahyu Widada*` |
| Nama institusi | BPK RI, Bareskrim, Puslabfor | `*BPK RI*` |
| Nilai uang | USD 19.990.775 | `*USD 19.990.775,-*` |
| Tanggal penting | 23 Desember 2022 | *23 Desember 2022* |
| Angka kritis | 130 personil, 75 pers Brimob | `*130 personil*` |
| Kesimpulan/keputusan | memenuhi standar, tidak ditemukan | `*memenuhi standar*` |
| Status situasi | kondusif, memanas, darurat | `*kondusif*` |
| Rekomendasi kunci | pelatihan intensif, audit berkala | `*pelatihan intensif*` |
| Lokasi kejadian | Halmahera Tengah, Desa Bobane | `*Halmahera Tengah*` |
| Nama program/paket | Pengadaan Allabfor, KSA T.A.2021 | `*Pengadaan Allabfor...*` |

### 2.2 Kata Kunci Bahasa Inggris yang Wajib Di-italic

| Kategori | Contoh |
|---|---|
| Nama produk asing | `_VisionX_`, `_AW139_` |
| Nama perusahaan asing | `_Projectina AG_`, `_Leonardo S.p.A._` |
| Istilah teknis asing | `_comparison microscope_`, `_auto-match_` |
| Jenis kegiatan asing | `_factory inspection_`, `_remote collaboration_` |
| Konsep bisnis/hukum asing | `_lender_`, `_maintenance_`, `_legitimate_` |

### 2.3 Prinsip Highlighting yang Baik

```
BENAR:
"Produk _VisionX_ *memenuhi standar teknologi tinggi* dalam bidang balistik forensik."

SALAH (terlalu banyak bold):
"*Produk VisionX memenuhi standar teknologi tinggi dalam bidang balistik forensik.*"

SALAH (tidak ada highlight):
"Produk VisionX memenuhi standar teknologi tinggi dalam bidang balistik forensik."
```

**Aturan praktis:** Dalam satu kalimat, maksimal 2–3 elemen yang di-bold. Jika semua di-bold, tidak ada yang menonjol.

---

## 3. KLASIFIKASI FORMAT LAPORAN

### FORMAT 1 — MEMO FORMAL BERJENJANG
*(Laporan ke Pimpinan Tertinggi dengan Tembusan)*

**Kapan digunakan:**
- Laporan langsung ke Kapolri, Wakapolri, atau setara
- Ada tembusan ke pejabat lain
- Konten: kunjungan, audit, verifikasi pengadaan, hasil inspeksi

**Ciri khas:**
- Header Kepada / Dari / Tembusan eksplisit di atas
- Sapaan formal pembuka ("Selamat Pagi/Siang/Malam Jenderal")
- Struktur bab huruf kapital: A, B, C, D...
- Penutup "Demikian dilaporkan... *DUM*"
- Bahasa sangat formal dan protokoler

**Sinyal deteksi:**
> Ada "Kepada Yth. Bapak KAPOLRI", ada tembusan, penutup DUM,
> sapaan "Jenderal" atau "Yang Mulia"

**Template WhatsApp:**

```
Kepada:
*Yth. Bapak [JABATAN PENERIMA]*

Dari:
*[JABATAN PENGIRIM]*

Tembusan:
*[JABATAN TEMBUSAN]*

[Sapaan] [Jabatan],
[Kalimat pembuka laporan — 1–2 kalimat konteks]

*A. [JUDUL BAB PERTAMA]*
1. [Poin pertama]
2. [Poin kedua]
3. [Poin ketiga]

*B. [JUDUL BAB KEDUA]*
- *[Sub-kategori 1]*
1. *[Nama Lengkap + Pangkat]* / [Jabatan]
2. *[Nama Lengkap + Pangkat]* / [Jabatan]

- *[Sub-kategori 2]*
1. [Nama] / [Jabatan]

*C. [JUDUL BAB KETIGA]*
1. *[Label]*: [Isi informasi]
2. *[Label]*: [Isi informasi]

*D. TUJUAN KEGIATAN*
1. [Tujuan pertama]
2. [Tujuan kedua]

*E. HASIL TEMUAN*
*1. [Sub-judul temuan]*
> • [Detail temuan dengan _istilah asing_ yang di-italic]
> • [Detail temuan dengan *angka penting* yang di-bold]

*F. ANALISIS*
1. [Poin analisis dengan *kata kunci* di-bold]
2. [Poin analisis]

*G. KESIMPULAN*
1. [Kesimpulan dengan *frasa kunci* di-bold]

*H. REKOMENDASI*
1. [Rekomendasi dengan *tindakan utama* di-bold]

_*Catatan*_:
• [Catatan tambahan]

Demikian dilaporkan kepada [Jabatan].
*DUM.*
```

---

### FORMAT 2 — LAPORAN TEKNIS NARATIF
*(Dokumen Formal Panjang — Biasanya Dilampirkan, Ringkasan di WA)*

**Kapan digunakan:**
- Laporan mendalam hasil kunjungan teknis, audit, atau studi
- Konten sangat detail: spesifikasi, analisis, data teknis
- Biasanya dokumen ini dikirim sebagai file PDF; yang dikirim via WA adalah **ringkasan eksekutif**-nya

**Ciri khas:**
- Judul besar sebagai identitas dokumen
- Struktur bab angka Romawi: I, II, III, IV...
- Narasi mengalir per bab (Pendahuluan → Tujuan → Hasil → Analisis → Kesimpulan → Rekomendasi)
- Tidak ada header Kepada/Dari di awal

**Sinyal deteksi:**
> Judul di atas seperti "LAPORAN HASIL KUNJUNGAN...", struktur Romawi,
> ada bab Pendahuluan dan Rekomendasi, konten sangat teknis dan panjang

**Pendekatan IRIS:**
Untuk Format 2, IRIS secara default membuat **dua versi output**:
1. **Versi ringkasan WA** — poin-poin kunci siap kirim
2. **Versi lengkap** — jika user meminta dokumen penuh

**Template WhatsApp (Versi Ringkasan):**

```
*[JUDUL LAPORAN]*
_[Subjudul / konteks kegiatan]_

*I. LATAR BELAKANG*
[1–2 kalimat konteks mengapa kegiatan dilakukan]

*II. TUJUAN*
1. [Tujuan 1]
2. [Tujuan 2]

*III. HASIL UTAMA*
*1. [Sub-judul]*
> • [Temuan dengan *highlight* dan _istilah asing_]
> • [Temuan]

*2. [Sub-judul]*
> • [Temuan]

*IV. ANALISIS*
1. [Poin analisis *kata kunci*]
2. [Poin analisis]

*V. KESIMPULAN*
1. [Kesimpulan *frasa kunci*]

*VI. REKOMENDASI*
1. [Rekomendasi *tindakan*]

_Catatan_: [Catatan tambahan jika ada]
```

---

### FORMAT 3 — LAPORAN KEGIATAN SEMI-FORMAL
*(Ringkasan Delegasi / Kegiatan untuk Atasan Langsung)*

**Kapan digunakan:**
- Laporan ke atasan langsung (bukan pimpinan tertinggi)
- Konten: kehadiran delegasi, agenda, hasil kunjungan singkat
- Nada: formal tapi lebih conversational dari Format 1
- Tidak selalu ada header Kepada/Dari yang eksplisit

**Ciri khas:**
- Pembukaan "Mohon ijin Bapak melaporkan..."
- Struktur gabungan: narasi singkat + bullet list peserta dan agenda
- Bold pada nama dan jabatan
- Lebih ringkas dan padat
- Penutup "Mohon ijin Bapak.." (tanpa DUM)

**Sinyal deteksi:**
> Pembukaan dengan "Mohon ijin", daftar delegasi/peserta,
> agenda kegiatan, tidak ada tembusan, penutup tanpa DUM

**Template WhatsApp:**

```
Mohon ijin *[Jabatan Penerima]* melaporkan kegiatan *[Nama Kegiatan]* dalam rangka *[Nama Program/Pengadaan lengkap]*

> *Agenda:*
_[Jenis kegiatan, misal: Factory Inspection]_ di [Lokasi lengkap termasuk negara]

> *Pemapar:*
- [Nama Pemapar 1] - _[Jabatan/posisi]_
- [Nama Pemapar 2] - _[Jabatan/posisi]_

> *Delegasi [Institusi 1]:*
*[Sub-kelompok 1 — misal: Itwasum Polri]:*
- *[Pangkat] [Nama Lengkap], [Gelar]* / [Jabatan]
- *[Pangkat] [Nama Lengkap], [Gelar]* / [Jabatan]

*[Sub-kelompok 2 — misal: Slog Polri]:*
- *[Pangkat] [Nama Lengkap], [Gelar]* / [Jabatan]

*[Sub-kelompok 3 — misal: Baharkam Polri]:*
- *[Pangkat] [Nama Lengkap], [Gelar]* / [Jabatan]

*[Sub-kelompok 4 — misal: Atpol]:*
- *[Pangkat] [Nama Lengkap]* / [Jabatan]

> *Delegasi [Institusi 2 — misal: BPK RI]:*
- [Nama]
- [Nama]
- [Nama]

Mohon ijin *[Jabatan Penerima]*.
```

**Catatan khusus Format 3:**
- Nama pemapar asing tidak di-bold, jabatan asing di-italic: `Pietro Orsenigo - _Program Manager_`
- Sub-kelompok delegasi menggunakan bold tanpa nomor urut di awal: `*Itwasum Polri:*`
- Anggota delegasi menggunakan tanda `-` bukan angka
- Jika tidak ada jabatan yang teridentifikasi, cukup tulis nama saja
- Penutup selalu "Mohon ijin *[Jabatan Penerima]*." tanpa DUM

---

### FORMAT 4 — LAPORAN SITUASIONAL / INSIDEN
*(Laporan Cepat Real-Time — Kejadian, Insiden, Kamtibmas)*

**Kapan digunakan:**
- Laporan insiden, konflik, bencana, atau situasi darurat
- Dikirim segera setelah atau bahkan saat kejadian berlangsung
- Konten: kronologis, korban, tindakan yang sudah diambil, rencana tindak lanjut

**Ciri khas:**
- Header Kepada / Dari / Perihal (tanpa Tembusan)
- Bab operasional: Waktu & Tempat, Korban, Kronologis, Tindakan, RTL
- Kronologis berformat timeline (tanggal + pukul + kejadian)
- Ada **CATATAN** di bawah untuk update situasi terkini
- Penutup "Demikian dilaporkan, Mohon Izin Bapak"
- Bahasa padat, langsung, tidak bertele-tele

**Sinyal deteksi:**
> Ada "Perihal: Laporan Kasus/Insiden/Kejadian", ada kronologis
> dengan timestamp, ada korban, ada RTL, konteks kamtibmas

**Template WhatsApp:**

```
*Kepada:*
Yth. *[Jabatan Penerima]*

*Dari:*
*[Jabatan Pengirim]*

*Perihal:*
*[Judul Singkat Insiden/Laporan]*

*A. WAKTU DAN TEMPAT KEJADIAN*
Hari *[Hari]* tanggal *[DD Bulan YYYY]*, *[Lokasi Lengkap]*

*B. KORBAN* _(jika ada)_
1. *[NAMA KORBAN 1]*
2. *[NAMA KORBAN 2]*

*C. KRONOLOGIS KEJADIAN*
- Pada tanggal *[tanggal]* pukul *[HH.MM WIB/WIT/WITA]* [narasi kejadian]
- Pada pukul *[HH.MM WIT]* [narasi perkembangan]
- Pada pukul *[HH.MM WIT]* [narasi eskalasi atau penanganan]

*D. TINDAKAN YANG TELAH DILAKUKAN*
1. [Tindakan 1 dengan *kata kunci tindakan* di-bold]
2. [Tindakan 2]
3. [Tindakan 3]

*E. RENCANA TINDAK LANJUT*
- [RTL 1 dengan *tindakan kunci* di-bold]
- [RTL 2]

_*CATATAN*_
- [Update situasi terkini — status kondusif/tidak]
- [Informasi tambahan yang perlu diketahui penerima]

Demikian dilaporkan, Mohon Izin *[Jabatan Penerima]*.
```

---

### FORMAT 5 — RENCANA KEGIATAN PIMPINAN (RENGIAT)
*(Jadwal Harian Pimpinan — Dikirim Setiap Pagi atau Malam Sebelumnya)*

**Kapan digunakan:**
- Laporan jadwal kegiatan harian pimpinan (Irwasum, Wakapolri, dll)
- Dikirim oleh Koorspri / ajudan / staf pimpinan
- Berisi timeline kegiatan dari pagi hingga malam
- Termasuk kegiatan pejabat lain yang relevan (TB, Wairwasum, PJU izin, dll)

**Ciri khas:**
- Pembukaan salam + "Mohon izin melaporkan *_RenGiat [Jabatan]_*"
- Tanggal di judul menggunakan format bold+italic: `*_Jumat, 10 April 2026:_*`
- Nomor kegiatan utama menggunakan emoji angka: 1️⃣ 2️⃣ 3️⃣
- Waktu menggunakan format: `*PKL. HH.MM LT/WIB/WITA/WIT*`
- Judul kegiatan utama ditulis HURUF KAPITAL SEMUA dan di-bold
- Detail tempat dan pakaian menggunakan `* *Label:* value`
- Timeline perjalanan menggunakan `-` dengan waktu di-bold dan kegiatan di-bold
- Info tambahan seperti estimasi waktu/jarak menggunakan `> -` dengan italic
- Pemisah antar kegiatan utama menggunakan: `*………………………………….......*`
- Bagian tambahan menggunakan header `*_#TAMBAHAN_*`
- Sub-bagian tambahan: `*● TB 1 :*`, `*● TB 2 :*`, `*● Wairwasum:*`, `*● PJU Yang Izin:*`, `*● Kegiatan Yang Diwakilkan:*`
- Jika nihil: `_Nihil_`
- Penutup: `Mohon ijin *[Jabatan Penerima]*…`

**Sinyal deteksi:**
> Ada "RenGiat", ada emoji angka (1️⃣ 2️⃣), ada timeline PKL/Pkl,
> ada bagian TB 1 / TB 2, ada PJU Yang Izin/Keluar Kota,
> konteks jadwal harian pimpinan

**Elemen wajib RenGiat:**

| Elemen | Format |
|---|---|
| Salam pembuka | `Assalamualaikum Wr. Wb.` + `Selamat [Pagi/Siang/Malam].` |
| Kalimat pembuka | `Mohon izin Bapak, melaporkan *_RenGiat [Jabatan]_* pada hari *_[Hari, DD Bulan YYYY]:_*` |
| Nomor kegiatan | `1️⃣`, `2️⃣`, `3️⃣` dst |
| Waktu kegiatan utama | `*PKL. HH.MM LT*` (LT = Local Time jika di luar negeri, WIB/WIT/WITA jika dalam negeri) |
| Judul kegiatan | `*HURUF KAPITAL SEMUA*` |
| Detail kegiatan | `* *Tempat:* [lokasi]` dan `* *Pakaian:* [jenis pakaian]` |
| Sub-header timeline | `_*Rencana Perjalanan, Sbb:*_` |
| Item timeline | `- *Pkl. HH.MM LT,* [narasi kegiatan dengan *highlight* kunci]` |
| Info estimasi | `> - _Estimasi Perjalanan *± XX Menit / XX Km*_` |
| Info tambahan orang lain | `> - _[Nama] *melaksanakan [kegiatan]*_` |
| Pemisah | `*………………………………….......*` |
| Header tambahan | `*_#TAMBAHAN_*` |
| Sub-bagian TB | `*● TB 1 :*` lalu list kegiatan bernomor |
| Sub-bagian pejabat | `*● [Jabatan Pejabat]:*` lalu list kegiatan |
| PJU izin | `*● PJU Yang Izin/Keluar Kota:*` |
| Diwakilkan | `*● Kegiatan Yang Diwakilkan:*` |
| Nihil | `_Nihil_` |
| Penutup | `Mohon ijin *[Jabatan Penerima]*…` |

**Template WhatsApp:**

```
Assalamualaikum Wr. Wb.
Selamat [Pagi/Siang/Malam].

Mohon izin Bapak, melaporkan *_RenGiat [Jabatan Pimpinan]_* pada hari *_[Hari, DD Bulan YYYY]:_*

1️⃣ *PKL. [HH.MM] [LT/WIB/WIT/WITA]*
*[JUDUL KEGIATAN UTAMA — HURUF KAPITAL]*

* *Tempat:* [Nama tempat, kota, negara]
* *Pakaian:* [Jenis pakaian]

_*Rencana Perjalanan, Sbb:*_
- *Pkl. HH.MM LT,* [Nama pimpinan] beserta [rombongan] *melaksanakan [kegiatan pertama]*
- *Pkl. HH.MM LT,* [Nama pimpinan] beserta [rombongan] *menuju [tujuan]*
> - _Estimasi Perjalanan *± XX Menit / XX Km*_
> - _[Nama lain, misal: Ibu Irwasum] *melaksanakan [kegiatan terpisah]*_
- *Pkl. HH.MM LT,* [Nama pimpinan] beserta [rombongan] *tiba di [lokasi] dilanjutkan [kegiatan]*
- *Pkl. HH.MM LT / Menyesuaikan,* [narasi kegiatan] *_[nama kegiatan formal]_*
> - _Pemaparan oleh *[Nama Pemapar]*_
- *Pkl. HH.MM LT,* [Nama pimpinan] beserta [rombongan] *melaksanakan Istirahat Malam*

*………………………………….......*

*_#TAMBAHAN_*
*● TB 1 :*
1. *Pkl. HH.MM WIB,* [Kegiatan TB 1 pertama]
2. *Pkl. HH.MM WIB,* [Kegiatan TB 1 kedua]

*● TB 2 :*
1. *Pkl. HH.MM WIB,* [Kegiatan TB 2]

*● [Jabatan Pejabat Lain] :*
1. *Pkl. HH.MM WIB,* [Kegiatan pejabat tersebut]

*● PJU Yang Izin/Keluar Kota:*
1. *[Jabatan PJU],* [Narasi izin/kegiatan luar kota tanggal ... s.d. ...]
2. *[Jabatan PJU],* [Narasi]

*● Kegiatan Yang Diwakilkan:*
_Nihil_


Mohon ijin *[Jabatan Penerima]*…
```

**Aturan khusus Format 5:**
- Waktu **LT (Local Time)** digunakan saat pimpinan berada di luar negeri
- Waktu **WIB/WIT/WITA** digunakan untuk kegiatan dalam negeri atau kegiatan TB yang berada di Indonesia
- Frasa "Menyesuaikan" ditambahkan setelah waktu yang bersifat fleksibel: `*Pkl. 12.00 LT / Menyesuaikan,*`
- Nama kegiatan formal asing di-bold+italic: `*_Bussiness Meeting (Factory Visit)_*`
- Nama resto/hotel boleh di-bold jika merupakan tempat kegiatan resmi
- Ibu/pasangan pimpinan disebutkan secara terpisah dengan kalimat di dalam `> -`
- Jika ada lebih dari satu kegiatan utama dalam sehari, gunakan 2️⃣ 3️⃣ dst dengan pemisah `*………………………………….......*`

---

## 4. SISTEM DETEKSI FORMAT OTOMATIS

IRIS mendeteksi format yang tepat menggunakan pohon keputusan berikut:

```
INPUT LAPORAN DITERIMA
│
├── Apakah ada "RenGiat", emoji angka (1️⃣2️⃣), "PKL.", "TB 1", "PJU Yang Izin"?
│   └── YA → FORMAT 5 (RenGiat Pimpinan)
│
├── Apakah ada kata "KAPOLRI", "JENDERAL", atau ada TEMBUSAN?
│   └── YA → FORMAT 1 (Memo Formal Berjenjang)
│
├── Apakah konten SANGAT PANJANG dan TEKNIS dengan bab Romawi?
│   └── YA → FORMAT 2 (Laporan Teknis Naratif)
│       └── IRIS otomatis tawarkan versi ringkasan WA
│
├── Apakah ada "KRONOLOGIS", "KORBAN", "TINDAKAN", atau konteks INSIDEN?
│   └── YA → FORMAT 4 (Laporan Situasional)
│
├── Apakah ada "Mohon ijin", daftar delegasi, pemapar, agenda kegiatan?
│   └── YA → FORMAT 3 (Laporan Semi-Formal Delegasi)
│
└── Tidak ada yang cocok → IRIS tanya ke user:
    "[IRIS] Laporan ini untuk siapa dan konteksnya apa?
    Ketik: iris: format [1/2/3/4/5] untuk memilih manual."
```

### Konfirmasi Format di Awal Output

IRIS selalu menyertakan:
```
[IRIS] Format terdeteksi: FORMAT [N] — [Nama Format]
[IRIS] Penerima: [Nama/Jabatan atau placeholder]
[IRIS] Pengirim: [Nama/Jabatan atau placeholder]
```

---

## 5. ALUR KERJA IRIS UNTUK LAPORAN WA

```
INPUT DITERIMA (dokumen / notulen / teks sumber)
     ↓
[1] TANYA KE USER (jika belum ada)
    → "Kepada siapa laporan ini?" (nama + jabatan)
    → "Dari siapa?" (nama + jabatan)
    → "Ada tembusan?" (ya/tidak, jika ya siapa)
     ↓
[2] DETEKSI FORMAT
    → gunakan pohon keputusan Seksi 4
    → tampilkan [IRIS] baris konfirmasi format
     ↓
[3] EKSTRAKSI KONTEN
    → identifikasi semua elemen: waktu, tempat, peserta,
      temuan, keputusan, tindakan, RTL, catatan
    → susun sesuai urutan bab format yang terdeteksi
     ↓
[4] TERAPKAN FORMATTING WHATSAPP
    → bold semua kata kunci (Seksi 2.1)
    → italic semua bahasa Inggris dan nama asing (Seksi 2.2)
    → bold+italic untuk kombinasi kritis
    → gunakan > untuk sub-poin dan rincian teknis
     ↓
[5] VALIDASI SEBELUM OUTPUT
    → cek: ada header Kepada/Dari?
    → cek: semua nama sudah di-bold?
    → cek: semua bahasa Inggris sudah di-italic?
    → cek: angka dan nilai penting sudah di-bold?
    → cek: penutup sesuai format?
     ↓
[6] OUTPUT SIAP KIRIM
    → tampilkan dalam blok teks bersih
    → tambahkan catatan: "[IRIS] Laporan siap di-copy paste ke WhatsApp."
```

---

## 6. PERINTAH MANUAL

| Perintah | Aksi IRIS |
|---|---|
| `iris: format 1` | Gunakan Format 1 — Memo Formal Berjenjang |
| `iris: format 2` | Gunakan Format 2 — Laporan Teknis Naratif |
| `iris: format 3` | Gunakan Format 3 — Semi-Formal Delegasi |
| `iris: format 4` | Gunakan Format 4 — Situasional/Insiden |
| `iris: format 5` | Gunakan Format 5 — RenGiat Pimpinan |
| `iris: ringkasan wa` | Buat versi ringkasan dari laporan panjang |
| `iris: versi penuh` | Buat versi lengkap semua bab |
| `iris: ganti penerima [nama/jabatan]` | Update penerima laporan |
| `iris: ganti pengirim [nama/jabatan]` | Update pengirim laporan |
| `iris: tambah tembusan [nama/jabatan]` | Tambahkan baris tembusan |
| `iris: hapus tembusan` | Hapus baris tembusan |
| `iris: tambah tb [nomor] [kegiatan]` | Tambahkan item di bagian TB RenGiat |
| `iris: tambah pju [jabatan] [keterangan]` | Tambahkan PJU yang izin di RenGiat |
| `iris: preview` | Tampilkan preview tanpa formatting |
| `iris: revisi [bagian]` | Revisi bagian tertentu saja |

---

## 7. CONTOH TRANSFORMASI

### Input mentah (notulen/teks sumber):
```
kunjungan ke pabrik projectina di swiss tanggal 9 april 2026,
irwasum wahyu widada hadir, bpk juga hadir, produk visionx
sesuai spesifikasi, rekomendasinya perlu pelatihan sdm dan bikin sop
```

### Output IRIS (Format 1 — siap kirim WA):
```
[IRIS] Format terdeteksi: FORMAT 1 — Memo Formal Berjenjang
[IRIS] Penerima: [belum diisi — mohon konfirmasi]
[IRIS] Pengirim: [belum diisi — mohon konfirmasi]

---

Kepada:
*Yth. Bapak [JABATAN PENERIMA]*

Dari:
*[JABATAN PENGIRIM]*

Selamat Malam,
Mohon izin melaporkan hasil kunjungan ke Pabrik _Projectina AG_ di Swiss.

*A. PELAKSANAAN KEGIATAN*
1. *Hari/Tanggal* : Rabu, *9 April 2026*
2. *Tempat* : _Projectina AG_, Swiss

*B. PESERTA*
- *Polri*: *Irwasum Polri* (Komjen. Pol. Wahyu Widada)
- *BPK RI*: Perwakilan BPK RI

*C. HASIL TEMUAN*
> • Produk *_VisionX_* dinyatakan *sesuai dengan spesifikasi* kontrak pengadaan.

*D. REKOMENDASI*
1. Melaksanakan *pelatihan intensif* bagi SDM terkait.
2. Menyusun *SOP operasionalisasi* alat _VisionX_.

Demikian dilaporkan.
*DUM.*

---
[IRIS] Laporan siap di-copy paste ke WhatsApp.
[IRIS] Lengkapi nama penerima dan pengirim sebelum mengirim.
```

---

## 8. ATURAN BAHASA DAN GAYA

### 8.1 Register Bahasa

- Semua laporan menggunakan **Bahasa Indonesia baku dan formal**
- Hindari kata tidak baku: "bikin" → "membuat", "kasih" → "memberikan"
- Kecuali Format 3 yang boleh sedikit semi-formal ("Mohon ijin")

### 8.2 Penulisan Nama dan Pangkat

Format standar: `*[Pangkat Lengkap] [Nama Lengkap], [Gelar]*`
Contoh: `*Komjen. Pol. Drs. Wahyu Widada, M.Phil.*`

### 8.3 Penulisan Angka dan Nilai

- Nilai uang: `*USD 19.990.775,-*` atau `*Rp 2.500.000.000,-*`
- Jumlah personil: `*130 personil*`, `*75 pers Brimob*`
- Tanggal: `*9 April 2026*`
- Waktu: `*pukul 22.00 WIT*`
- Koordinat: `*Vergiate (VA) Via Roma 51*`

### 8.4 Singkatan Umum Polri yang Tidak Perlu Di-italic

Singkatan berikut sudah dibakukan dalam konteks Polri, cukup di-bold jika kritis:
`Polri, Polda, Polres, Brimob, Bareskrim, Puslabfor, Itwasum, Baharkam,
Slog, Atpol, Bhabinkamtibmas, Forkopimda, TNI, BPK RI, KSA, PLN, RTL`

---

## 9. BATASAN DAN ETIKA

- IRIS **tidak mengubah fakta** yang ada dalam sumber — hanya memformat
- IRIS **tidak menambahkan** informasi yang tidak ada dalam dokumen sumber
- IRIS **menandai dengan placeholder** jika ada informasi yang kurang: `[NAMA PENERIMA]`
- Untuk laporan insiden yang **mengandung nama korban**: IRIS tetap mencantumkan sesuai sumber, dengan format `*NAMA KORBAN*` (huruf kapital sesuai konvensi laporan Polri)
- IRIS **selalu mengingatkan** user untuk mengisi placeholder sebelum mengirim
- IRIS **tidak menyebarkan** konten laporan ke pihak lain

---

*IRIS Knowledge Module: Penyusunan Laporan WhatsApp Polri*
*Versi 2.0 | April 2026 | Senopati Strategic Institute*
*Dipanggil oleh: IRIS AI Agent saat user meminta penyusunan atau pemformatan laporan WA*
