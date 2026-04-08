# RAG KNOWLEDGE BASE — TEMPLATE DOKUMEN
# Institusi: Cakrawala Sasmita
# Fungsi: Panduan format dan contoh dokumen untuk AI agent
# Chunk strategy: Pisahkan per seksi (---), metadata per chunk di bawah

---

## METADATA FILE

```json
{
  "institusi": "Cakrawala Sasmita",
  "tipe": "document_template",
  "versi": "1.0",
  "bahasa": "Indonesia",
  "use_when": [
    "user meminta membuat laporan",
    "user meminta membuat briefing",
    "user meminta membuat policy brief",
    "user meminta membuat analisis",
    "user meminta membuat rekomendasi",
    "user meminta format dokumen",
    "user meminta struktur laporan"
  ]
}
```

---

# BAGIAN 1 — PANDUAN MEMILIH FORMAT DOKUMEN

```json
{
  "chunk_id": "CS-TPL-001",
  "topic": "pemilihan format dokumen",
  "tags": ["format", "template", "laporan", "briefing", "publikasi"]
}
```

## Panduan Memilih Format yang Tepat

Cakrawala Sasmita menggunakan dua format dokumen utama. Pilih berdasarkan tujuan dan audiens:

### FORMAT ANALITIK — Kapan Digunakan

Gunakan Format Analitik ketika:
- Audiens adalah pengambil keputusan yang butuh informasi cepat dan actionable
- Dokumen bersifat internal atau terbatas (laporan situasional, briefing)
- Tujuan utama adalah mendukung keputusan operasional atau taktis
- Waktu baca audiens terbatas — mereka butuh poin utama dalam 2 menit pertama

Contoh penggunaan: Laporan situasional harian, briefing intelijen, analisis kasus, penilaian risiko, nota analisis, laporan pemantauan media.

### FORMAT PUBLIKASI — Kapan Digunakan

Gunakan Format Publikasi ketika:
- Dokumen akan dibagikan ke audiens yang lebih luas atau eksternal
- Tujuan adalah membangun argumentasi yang kohesif dan persuasif
- Dokumen bersifat kajian mendalam dengan landasan teoritis atau empiris
- Output adalah produk intelektual yang mencerminkan posisi Cakrawala Sasmita

Contoh penggunaan: Policy brief, kajian strategis, laporan riset, buletin advisory, kertas posisi (position paper), executive report untuk klien.

### ATURAN UMUM KEDUA FORMAT

Terlepas dari format yang dipilih, selalu terapkan:
- Piramida terbalik: kesimpulan dan temuan terpenting di awal
- Setiap poin menjawab "So what?" — implikasi selalu disertakan
- Rekomendasi selalu berjenjang: Segera / Jangka Pendek / Jangka Menengah
- Bahasa Indonesia formal, direktif, tidak bertele-tele
- Hindari frasa pengisi tanpa substansi

---

# BAGIAN 2 — FORMAT ANALITIK (STRUKTUR LENGKAP)

```json
{
  "chunk_id": "CS-TPL-002",
  "topic": "format analitik struktur lengkap",
  "tags": ["format analitik", "laporan situasional", "briefing", "struktur"]
}
```

## FORMAT ANALITIK — Struktur dan Panduan

### BLOK HEADER

```
LAPORAN ANALITIK STRATEGIS
[JUDUL LAPORAN — Deskriptif dan Spesifik]
[Subjudul jika diperlukan]

Tanggal      : [Tanggal Bulan Tahun]
Disusun oleh : Cakrawala Sasmita
Klasifikasi  : [TERBATAS / INTERNAL / PUBLIK]
Versi        : [1.0 / 1.1 / dst]
```

Aturan header:
- Judul harus spesifik dan informatif — bukan "Laporan Situasional" tapi "Laporan Situasional Keamanan Jawa Tengah: Eskalasi Konflik Agraria Blora, April 2026"
- Klasifikasi wajib dicantumkan — menentukan distribusi dokumen
- Versi penting untuk dokumen yang akan direvisi atau diperbarui

---

### SEKSI 01 — RINGKASAN EKSEKUTIF

Panjang: Maksimal 3 kalimat untuk ringkasan, ditambah 1 baris status.

Struktur:
```
[Kalimat 1]: Temuan paling kritis — apa yang terjadi, di mana, kapan.
[Kalimat 2]: Implikasi langsung — apa artinya bagi institusi atau pengambil keputusan.
[Kalimat 3]: Tindakan yang paling mendesak diperlukan.

Tingkat risiko: [KRITIS/TINGGI/SEDANG/RENDAH]  |  Urgensi: [Segera/7 Hari/30 Hari]  |  Dampak: [Institusional/Operasional/Reputasi]
```

Aturan Ringkasan Eksekutif:
- Tidak boleh ada kalimat pembuka generik seperti "Laporan ini membahas..." atau "Berdasarkan pemantauan yang dilakukan..."
- Langsung ke substansi di kalimat pertama
- Pembaca harus bisa mengambil keputusan awal hanya dari bagian ini
- Jika ada tiga temuan setara pentingnya, sebutkan ketiganya dalam satu kalimat dengan titik koma

---

### SEKSI 02 — TEMUAN UTAMA

Struktur per temuan:
```
### 2.X [Judul Temuan — Deskriptif]

[1 paragraf uraian temuan: apa yang terjadi, siapa yang terlibat, 
kapan, di mana, dan data kuantitatif jika tersedia]

- [Fakta pendukung 1 — spesifik, terverifikasi, dengan sumber jika ada]
- [Fakta pendukung 2 — angka, tanggal, nama, lokasi konkret]
- [Fakta pendukung 3 — konteks atau perbandingan yang relevan]
```

Aturan Temuan Utama:
- Pisahkan FAKTA dari INTERPRETASI — bagian ini hanya fakta
- Urutan temuan: dari yang paling kritis ke yang paling ringan
- Setiap temuan berdiri sendiri — bisa dibaca tanpa membaca temuan lain
- Minimal 2, maksimal 5 temuan utama per laporan
- Jika ada lebih dari 5 temuan, kelompokkan ke dalam cluster tematik

---

### SEKSI 03 — ANALISIS DAN IMPLIKASI

Sub-seksi yang wajib ada:

**3.1 Pola dan Tren**
Hubungan antar temuan. Apa pola yang muncul? Apakah ini bagian dari tren yang lebih besar? Apa yang berubah dibanding periode sebelumnya?

**3.2 Implikasi Operasional**
Apa dampak langsung terhadap operasional institusi atau klien? Siapa yang paling terdampak? Dalam skala waktu apa?

**3.3 Matriks Risiko**
Format tabel:

| Faktor Risiko | Probabilitas | Dampak | Prioritas |
|---|---|---|---|
| [Risiko 1] | Tinggi/Sedang/Rendah | Signifikan/Moderat/Minor | KRITIS/TINGGI/SEDANG |
| [Risiko 2] | ... | ... | ... |

Aturan matriks:
- Maksimal 5 faktor risiko
- Probabilitas dan dampak dinilai secara independen
- Prioritas = fungsi dari kombinasi probabilitas × dampak
- KRITIS hanya jika probabilitas tinggi DAN dampak signifikan

---

### SEKSI 04 — REKOMENDASI

Format rekomendasi berjenjang:

```
01 | SEGERA (24–72 jam)
[Deskripsi tindakan yang harus diambil segera. Sebutkan:]
- Siapa yang harus melakukan
- Apa tepatnya yang dilakukan
- Target atau indikator keberhasilan

02 | JANGKA PENDEK (30–90 hari)
[Deskripsi tindakan taktis. Gunakan kata kerja aktif:]
Koordinasikan / Laksanakan / Evaluasi / Tetapkan / Tinjau

03 | JANGKA MENENGAH (3–12 bulan)
[Deskripsi perubahan struktural atau sistemik yang diperlukan]
```

Aturan Rekomendasi:
- Setiap rekomendasi harus bisa dieksekusi — bukan aspirasi
- Sebutkan siapa yang bertanggung jawab (level jabatan, bukan nama)
- Jika ada konflik kepentingan antar rekomendasi, nyatakan eksplisit
- Rekomendasi tidak boleh bertentangan satu sama lain

---

### CONTOH RINGKASAN EKSEKUTIF (FORMAT ANALITIK)

**BAIK:**
"Konflik agraria di Kabupaten Blora memasuki fase kritis dengan 3 insiden kekerasan dalam 72 jam terakhir, melibatkan 847 warga dan memblokir akses ke area tambang seluas 2.400 hektar. Eskalasi ini berpotensi meluas ke 4 kabupaten tetangga jika tidak ada intervensi dalam 48 jam ke depan, mengingat jaringan organisasi yang terlibat bersifat lintas wilayah. Koordinasi segera antara Polda, Pemda, dan perusahaan konsesi diperlukan untuk membuka jalur mediasi sebelum demonstrasi terjadwal Jumat depan."

Tingkat risiko: TINGGI | Urgensi: Segera | Dampak: Operasional & Reputasi

**BURUK (hindari):**
"Laporan ini disusun dalam rangka memberikan gambaran mengenai situasi yang terjadi di wilayah Jawa Tengah terkait konflik yang sedang berlangsung. Berdasarkan data yang berhasil dihimpun oleh tim pemantauan, dapat disimpulkan bahwa situasi saat ini memerlukan perhatian dari berbagai pihak yang berkepentingan."

---

# BAGIAN 3 — FORMAT PUBLIKASI (STRUKTUR LENGKAP)

```json
{
  "chunk_id": "CS-TPL-003",
  "topic": "format publikasi struktur lengkap",
  "tags": ["format publikasi", "policy brief", "kajian strategis", "riset"]
}
```

## FORMAT PUBLIKASI — Struktur dan Panduan

### BLOK COVER

```
[KATEGORI / TAG TOPIK]
Contoh: GEOPOLITIK & KEAMANAN NASIONAL | KEBIJAKAN EKONOMI | REFORMASI INSTITUSIONAL

JUDUL PUBLIKASI UTAMA
Judul yang mencerminkan tema strategis dan menarik perhatian audiens target.
Idealnya 8–12 kata, tidak berakhir dengan tanda tanya.

Subjudul (opsional)
Klarifikasi atau kontekstualisasi judul utama dalam 1 kalimat.

Cakrawala Sasmita
[Keterangan institusi singkat]

[Bulan Tahun]  |  Vol. [XX] / [Tahun]  |  [Nomor edisi jika ada]

━━━━━━━━━━━━━━━━
POIN KUNCI
[1 paragraf — 3–5 kalimat — yang merangkum inti argumentasi publikasi.
Ini adalah kalimat yang paling banyak dibaca dan di-screenshot.
Tulis dengan bahasa yang kuat, langsung, dan berkesan.]
━━━━━━━━━━━━━━━━
```

---

### SEKSI PENDAHULUAN

Panjang: 2–3 paragraf.

Fungsi:
- Paragraf 1: Menetapkan konteks dan urgensi — mengapa isu ini penting sekarang
- Paragraf 2: Data atau fakta kunci yang memperkuat urgensi
- Paragraf 3 (opsional): Posisi atau pendekatan Cakrawala Sasmita terhadap isu ini

Aturan:
- Tidak ada kalimat pembuka klise: "Dalam era globalisasi...", "Seiring perkembangan zaman...", "Indonesia sebagai negara berkembang..."
- Mulai dengan fakta yang mengejutkan, angka yang signifikan, atau pertanyaan yang tajam
- Pendahuluan harus membuat pembaca ingin melanjutkan membaca

---

### SEKSI ANALISIS DAN ARGUMENTASI

Sub-seksi:

**Konteks dan Latar Belakang**
Kronologi atau peta tematik yang memberi pembaca fondasi untuk mengikuti argumen. Tidak perlu exhaustive — hanya yang relevan untuk argumen yang akan dibangun.

**Pull Quote**
Satu kutipan atau pernyataan kunci yang ditonjolkan secara visual. Bisa berupa:
- Kutipan dari tokoh atau dokumen resmi yang relevan
- Temuan kunci Cakrawala Sasmita yang ingin ditonjolkan
- Statistik yang paling mencolok

Format: Tulis di antara tanda "—" dengan atribusi yang jelas.

**Temuan dan Analisis**
Uraikan argumentasi secara progresif dalam format numbered:
1. Poin argumentasi pertama (paling faktual, paling mudah diterima)
2. Poin argumentasi kedua (membangun di atas poin 1, mulai interpretasi)
3. Poin argumentasi ketiga (implikasi yang lebih dalam, mengarah ke rekomendasi)

Setiap poin: 1–2 paragraf, didukung data atau referensi.

---

### SEKSI IMPLIKASI KEBIJAKAN

Format per tier pemangku kepentingan:

**Untuk Pimpinan Institusi / Pengambil Keputusan Tingkat Atas**
[Rekomendasi yang memerlukan otoritas tertinggi: kebijakan strategis, alokasi sumber daya besar, keputusan yang berdampak institusional jangka panjang]

**Untuk Unit Operasional / Pelaksana**
[Rekomendasi yang dapat diimplementasikan di level teknis: prosedur, protokol, perubahan praktis dalam 30–90 hari]

**Untuk Pemangku Kepentingan Eksternal / Mitra Strategis**
[Rekomendasi yang melibatkan koordinasi lintas sektor, kemitraan, atau advokasi kebijakan]

Aturan seksi ini:
- Setiap tier harus berbeda — jangan copy-paste dengan subjek berbeda
- Rekomendasi harus spesifik untuk kapasitas tier tersebut
- Tidak semua publikasi perlu tiga tier — pilih yang relevan

---

### SEKSI PENUTUP

Panjang: 1–2 paragraf.

Fungsi:
- Merangkum argumen utama tanpa mengulang seluruh isi
- Mengakhiri dengan kalimat yang kuat: konsekuensi jika tidak bertindak, atau visi ke depan

Aturan:
- Tidak ada "Demikian laporan ini kami sampaikan..."
- Tidak ada ucapan terima kasih atau basa-basi
- Kalimat terakhir harus memorable — ini yang akan diingat pembaca

**Kotak Profil Institusi (opsional, untuk publikasi eksternal):**
```
TENTANG CAKRAWALA SASMITA
Cakrawala Sasmita adalah lembaga riset, think tank, dan konsultan 
strategi yang menghasilkan analisis berbasis bukti untuk pengambil 
keputusan di sektor publik, pemerintahan, keamanan, dan korporasi 
Indonesia. Kami berkomitmen pada independensi analitik dan orientasi 
pada dampak nyata kebijakan.
```

---

### CONTOH POIN KUNCI (FORMAT PUBLIKASI)

**BAIK:**
"Kebijakan tarif resiprokal AS sebesar 32% terhadap Indonesia bukan sekadar tekanan dagang — ini adalah sinyal restrukturisasi paksa posisi Indonesia dalam rantai nilai global. Respons Indonesia selama ini bersifat defensif dan taktis, padahal jendela negosiasi yang tersisa semakin sempit. Tanpa pergeseran paradigma dari sekadar mereduksi tarif menuju membangun leverage strategis, Indonesia berisiko kehilangan daya tawar yang sudah dibangun melalui satu dekade kebijakan hilirisasi."

**BURUK (hindari):**
"Tarif Trump memberikan dampak yang cukup signifikan bagi perekonomian Indonesia. Hal ini tentu perlu mendapat perhatian dari berbagai pemangku kepentingan agar dapat ditangani dengan baik dan benar sesuai dengan ketentuan yang berlaku."

---

# BAGIAN 4 — TERMINOLOGI STANDAR CAKRAWALA SASMITA

```json
{
  "chunk_id": "CS-TPL-004",
  "topic": "terminologi dan glosarium standar",
  "tags": ["terminologi", "glosarium", "istilah", "standar bahasa"]
}
```

## Terminologi yang Digunakan

### Tingkat Risiko / Eskalasi

| Label | Kriteria |
|---|---|
| KRITIS | Ancaman aktif terhadap keselamatan jiwa atau stabilitas institusi — memerlukan respons segera dalam hitungan jam |
| TINGGI | Potensi eskalasi signifikan dalam 24–72 jam — memerlukan perhatian dalam hari ini |
| SEDANG | Perlu dipantau, potensi eskalasi ada tapi tidak segera — tindakan dalam 7–30 hari |
| RENDAH | Informatif, tidak ada urgensi tindakan — arsip dan monitoring rutin |

### Frasa yang Digunakan vs Dihindari

| GUNAKAN | HINDARI |
|---|---|
| "Data menunjukkan..." | "Hal ini menunjukkan bahwa..." |
| "Risiko eskalasi tinggi karena..." | "Perlu diwaspadai bahwa..." |
| "Koordinasikan segera dengan..." | "Diharapkan adanya koordinasi..." |
| "Tiga faktor utama: X, Y, Z" | "Terdapat beberapa faktor yang..." |
| "Temuan ini mengindikasikan..." | "Dapat disimpulkan bahwa..." |
| "Kondisi saat ini: [deskripsi]" | "Sebagaimana telah disebutkan..." |
| "Tindakan yang diperlukan: [spesifik]" | "Langkah-langkah yang perlu diambil..." |

### Label Klasifikasi Dokumen

| Label | Makna |
|---|---|
| PUBLIK | Dapat disebarluaskan tanpa batasan |
| INTERNAL | Hanya untuk kalangan Cakrawala Sasmita |
| TERBATAS | Untuk klien dan mitra tertentu yang ditunjuk |
| RAHASIA | Distribusi sangat terbatas, sesuai kebutuhan |

### Format Tanggal Standar

Selalu gunakan: [Tanggal] [Nama Bulan] [Tahun]
Contoh: 8 April 2026 (bukan 08/04/2026 atau 04-08-2026)

---

# BAGIAN 5 — CONTOH DOKUMEN ANALITIK LENGKAP

```json
{
  "chunk_id": "CS-TPL-005",
  "topic": "contoh dokumen analitik lengkap",
  "tags": ["contoh", "few-shot", "format analitik", "laporan situasional"]
}
```

## Contoh: Laporan Analitik Strategis

---

**LAPORAN ANALITIK STRATEGIS**
**Dinamika Kepercayaan Publik terhadap Institusi Kepolisian: Tren dan Implikasi Strategis**
*Kajian berbasis data pemantauan media dan survei publik*

Tanggal      : 8 April 2026
Disusun oleh : Cakrawala Sasmita
Klasifikasi  : TERBATAS
Versi        : 1.0

---

### 01 Ringkasan Eksekutif

Kepercayaan publik terhadap Polri mencapai titik terendah dalam lima tahun terakhir pasca kerusuhan Agustus 2025, dengan 67% responden survei menyatakan ketidakpuasan terhadap penanganan demonstrasi — naik 23 poin persentase dari survei sebelumnya. Kondisi ini menciptakan celah legitimasi yang dimanfaatkan oleh berbagai kelompok kepentingan untuk mendorong agenda reformasi yang beragam, sebagian di antaranya berpotensi melemahkan kapasitas operasional institusi. Penanganan krisis kepercayaan ini memerlukan respons komunikasi yang terkoordinasi dan langkah reformasi yang terukur dalam 90 hari ke depan sebelum momentum negatif mengeras menjadi persepsi permanen.

Tingkat risiko: TINGGI | Urgensi: 7 Hari | Dampak: Institusional & Reputasi

---

### 02 Temuan Utama

**2.1 Erosi Kepercayaan Pasca Agustus 2025**

Tiga gelombang survei yang dilakukan September–Desember 2025 menunjukkan penurunan konsisten kepercayaan publik terhadap Polri di semua segmen demografis. Penurunan paling tajam terjadi di kelompok usia 18–35 tahun (urban) dan kalangan terdidik.

- Kepercayaan publik umum: turun dari 61% (Juli 2025) ke 38% (Desember 2025)
- Kelompok mahasiswa dan pelajar: hanya 19% menyatakan percaya pada Polri
- Peningkatan konten negatif Polri di media sosial: +340% dibanding rata-rata 2024
- 12 aktivis masih ditahan sebagai tersangka penghasutan per Desember 2025

**2.2 Fragmentasi Narasi Reformasi**

Tidak ada konsensus publik tentang arah reformasi Polri — terdapat setidaknya empat narasi utama yang bersaing, dengan koalisi pendukung yang berbeda dan sebagian bertentangan satu sama lain.

- Narasi A (LSM HAM): Reformasi struktural menyeluruh, evaluasi doktrin pengamanan massa
- Narasi B (Elite Politik): Pergantian pimpinan sebagai solusi simbolik
- Narasi C (Internal Polri): Penguatan kapasitas dan kesejahteraan anggota
- Narasi D (Akademisi): Revisi regulasi dan penguatan pengawasan eksternal

**2.3 Perpol 10/2025 Memperburuk Persepsi**

Penerbitan Perpol Nomor 10 Tahun 2025 — yang membolehkan polisi aktif mengisi jabatan sipil, bertentangan dengan UU No. 2/2002 dan Putusan MK No. 114/2025 — memicu gelombang kritik baru yang memperpanjang siklus krisis kepercayaan.

- 47 organisasi masyarakat sipil mengeluarkan pernyataan penolakan bersama
- Perpol dikritik oleh 3 fraksi DPR dalam rapat Komisi III
- Preseden hukum: Kapolri secara terbuka mengabaikan putusan MK

---

### 03 Analisis dan Implikasi

**3.1 Pola dan Tren**

Krisis kepercayaan ini bukan anomali — ini adalah akumulasi dari defisit kepercayaan yang terbentuk sejak kasus Ferdy Sambo (2022) dan tidak pernah sepenuhnya dipulihkan. Setiap insiden baru (kerusuhan Agustus 2025, Perpol 10/2025) diinterpretasikan publik melalui lensa kecurigaan yang sudah terbentuk sebelumnya, sehingga efeknya jauh lebih besar dari nilai intrinsiknya.

Pola yang teridentifikasi: Polri merespons setiap krisis dengan pendekatan manajemen narasi jangka pendek, bukan pembenahan struktural. Ini menciptakan siklus krisis yang berulang dengan intensitas meningkat.

**3.2 Implikasi Operasional**

Kepercayaan publik yang rendah secara langsung berdampak pada: (1) efektivitas fungsi Bhabinkamtibmas — warga enggan melapor atau berkoordinasi; (2) rekrutmen — citra negatif menurunkan kualitas calon anggota; (3) penegakan hukum — legitimasi tindakan aparat dipertanyakan di lapangan.

**3.3 Matriks Risiko**

| Faktor Risiko | Probabilitas | Dampak | Prioritas |
|---|---|---|---|
| Krisis kepercayaan mengeras menjadi permanen | Tinggi | Signifikan | KRITIS |
| Politisasi isu reformasi menjelang 2027 | Tinggi | Tinggi | TINGGI |
| Perpol 10/2025 digugat ke MK | Sedang | Signifikan | TINGGI |
| Insiden lapangan memicu gelombang demo baru | Sedang | Signifikan | TINGGI |
| PHK massal memperparah sentimen anti-institusi | Rendah | Moderat | SEDANG |

---

### 04 Rekomendasi

**01 | SEGERA (24–72 jam)**
Tinjau dan pertimbangkan pencabutan Perpol 10/2025 atau suspensi implementasinya sambil menunggu kajian hukum. Langkah ini akan memotong satu sumber krisis yang paling mudah dikendalikan tanpa memerlukan perubahan struktural. Pimpinan Polri harus yang mengambil inisiatif ini — bukan menunggu tekanan eksternal yang lebih besar.

**02 | JANGKA PENDEK (30–90 hari)**
Luncurkan program komunikasi strategis terstruktur yang memisahkan narasi reformasi yang sedang berjalan dari perdebatan politik harian. Bentuk tim khusus yang terdiri dari unsur internal Polri, akademisi independen, dan perwakilan masyarakat sipil untuk menyusun peta jalan reformasi yang terukur dan memiliki timeline yang dapat diverifikasi publik.

**03 | JANGKA MENENGAH (3–12 bulan)**
Revisi doktrin dan standar operasional penanganan demonstrasi secara menyeluruh, mengintegrasikan standar HAM internasional dan praktik terbaik dari kepolisian demokratis di kawasan. Evaluasi mekanisme pengawasan internal Propam dan perkuat kapasitas Kompolnas sebagai pengawas eksternal yang independen dan efektif.

---

# BAGIAN 6 — CONTOH DOKUMEN PUBLIKASI LENGKAP

```json
{
  "chunk_id": "CS-TPL-006",
  "topic": "contoh dokumen publikasi lengkap",
  "tags": ["contoh", "few-shot", "format publikasi", "policy brief"]
}
```

## Contoh: Policy Brief

---

**KEBIJAKAN STRATEGIS & GEOPOLITIK**

**Indonesia di Persimpangan: Menavigasi Tekanan Tarif AS Tanpa Mengorbankan Agenda Hilirisasi**
*Analisis kebijakan perdagangan dan respons strategis Indonesia terhadap kebijakan tarif resiprokal Amerika Serikat*

Cakrawala Sasmita
April 2026 | Policy Brief No. 03/2026

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
**POIN KUNCI**

Kebijakan tarif resiprokal AS sebesar 32% terhadap Indonesia menciptakan dilema strategis yang jauh lebih dalam dari sekadar tekanan dagang: Indonesia dipaksa memilih antara mereduksi tarif jangka pendek dengan mengorbankan larangan ekspor nikel — satu-satunya leverage strategis yang dimiliki Indonesia dalam negosiasi rantai nilai baterai global. Kompromi yang telah diambil pemerintah berisiko mengunci Indonesia dalam posisi eksportir bahan baku mentah untuk setidaknya satu dekade ke depan, tepat ketika negara-negara pesaing bergerak naik ke segmen manufaktur bernilai tinggi. Indonesia membutuhkan bukan sekadar diplomasi tarif, melainkan strategi leverage yang memanfaatkan posisi unik Indonesia sebagai pemegang cadangan nikel terbesar dunia.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

**Pendahuluan**

Pada 2 April 2025, Amerika Serikat mengenakan tarif resiprokal 32% terhadap ekspor Indonesia — menempatkan Indonesia di antara 15 negara penyumbang defisit dagang terbesar bagi AS, dengan nilai defisit USD 17,9 miliar pada 2024. Dalam hitungan minggu, kebijakan ini memicu trading halt pertama BEI sejak pandemi Covid-19, rupiah tertekan, dan sektor manufaktur berorientasi ekspor menghadapi tekanan PHK massal.

Respons awal pemerintah Indonesia — negosiasi bilateral dan komitmen membuka pasar — berhasil mereduksi sebagian dampak jangka pendek. Namun di balik keberhasilan taktis ini, tersimpan konsesi yang biayanya belum sepenuhnya dipahami: Indonesia berkomitmen menghapus larangan ekspor nikel mentah ke AS sebagai bagian dari paket kesepakatan.

---

**Analisis dan Argumentasi**

**Konteks: Dari Tekanan Dagang ke Pertarungan Rantai Nilai**

Kebijakan tarif Trump bukan sekadar instrumen ekonomi — ini adalah sinyal restrukturisasi sistem perdagangan global yang menekan negara-negara berkembang untuk memilih keberpihakan dalam rivalitas AS-China. Indonesia, dengan posisi strategisnya sebagai pemegang cadangan nikel terbesar dunia dan nexus rantai nilai baterai kendaraan listrik, berada di episentrum pertarungan ini.

— "Nikel Indonesia bukan sekadar komoditas. Ia adalah kunci teknologi energi abad ke-21. Siapapun yang mengendalikan nikel Indonesia, mengendalikan sebagian besar masa depan industri kendaraan listrik global." — Analisis Cakrawala Sasmita, Maret 2026

1. Kompromi nikel membatalkan satu dekade investasi hilirisasi. Kebijakan larangan ekspor nikel mentah — yang memaksa investasi pengolahan masuk ke Indonesia dan menghasilkan kawasan industri seperti Morowali — adalah instrumen paling efektif yang pernah dimiliki Indonesia untuk naik dalam rantai nilai global. Menghapusnya demi penurunan tarif 32% adalah pertukaran yang tidak proporsional.

2. Pesaing bergerak sementara Indonesia mundur. Vietnam (tarif 46%), Thailand (37%), dan Malaysia sedang agresif menarik investasi manufaktur komponen baterai dan semikonduktor. Di saat mereka bergerak naik ke segmen manufaktur, Indonesia berisiko kembali ke posisi eksportir bahan mentah yang selama satu dekade coba ditinggalkan.

3. Leverage Indonesia lebih besar dari yang dinegosiasikan. AS dan China sama-sama membutuhkan nikel Indonesia untuk target transisi energi mereka. Posisi ini memberikan Indonesia ruang negosiasi yang jauh lebih luas dari yang dimanfaatkan — asalkan dikelola sebagai leverage strategis, bukan sekadar komoditas ekspor.

---

**Implikasi Kebijakan**

**Untuk Pengambil Keputusan Tingkat Atas (Presiden, Menko Perekonomian, Mendag)**
Tinjau ulang komitmen penghapusan larangan ekspor nikel dalam kerangka kesepakatan tarif AS. Negosiasikan ulang dengan mengajukan paket alternatif: akses pasar AS untuk produk olahan nikel Indonesia (bukan mentah) sebagai substitusi. Gunakan aksesi Indonesia ke BRICS sebagai sinyal bahwa Indonesia memiliki opsi diversifikasi mitra strategis — ini memperkuat posisi tawar dalam negosiasi dengan Washington.

**Untuk Kementerian ESDM dan Kementerian Investasi**
Percepat regulasi yang memastikan investasi asing di sektor nikel diarahkan ke segmen pengolahan dan manufaktur komponen, bukan ekstraksi mentah. Tetapkan target mandatory: minimal 60% nilai tambah nikel harus diproses di Indonesia sebelum diekspor, berlaku untuk semua mitra dagang termasuk AS dan China.

**Untuk Pelaku Industri dan Asosiasi**
Bangun koalisi industri nikel Indonesia yang dapat berbicara dengan satu suara dalam forum internasional. Libatkan investor strategis — terutama dari sektor kendaraan listrik dan penyimpanan energi — untuk mendukung posisi Indonesia bahwa nilai sebenarnya nikel Indonesia ada di produk olahan, bukan bahan mentah.

---

**Penutup**

Indonesia tidak kekurangan leverage — yang kurang adalah keberanian strategis untuk menggunakannya secara konsisten. Cadangan nikel terbesar dunia adalah kartu yang hanya bisa dimainkan sekali dengan baik; memainkannya terlalu murah dan terlalu cepat adalah kesalahan yang akan terasa dampaknya selama generasi. Jendela untuk membangun posisi Indonesia sebagai pemain kunci dalam rantai nilai energi global masih terbuka — tapi tidak untuk selamanya.

**TENTANG CAKRAWALA SASMITA**
Cakrawala Sasmita adalah lembaga riset, think tank, dan konsultan strategi yang menghasilkan analisis berbasis bukti untuk pengambil keputusan di sektor publik, pemerintahan, keamanan, dan korporasi Indonesia. Kami berkomitmen pada independensi analitik dan orientasi pada dampak nyata kebijakan.

---

# BAGIAN 7 — INSTRUKSI RAG UNTUK MODEL

```json
{
  "chunk_id": "CS-TPL-007",
  "topic": "instruksi retrieval dan penggunaan template",
  "tags": ["instruksi", "retrieval", "penggunaan", "panduan model"]
}
```

## Panduan Penggunaan Template untuk Model

### Kapan Mengambil Template dari RAG

Ambil chunk template dari RAG ketika user:
- Meminta membuat laporan, briefing, analisis, atau publikasi
- Menyebut kata kunci: "buat laporan", "susun briefing", "tulis policy brief", "analisis situasi", "buat rekomendasi formal"
- Meminta format dokumen atau struktur penulisan
- Mengirimkan data/informasi dan meminta dijadikan dokumen

### Cara Menggunakan Template

1. Identifikasi format yang tepat (Analitik atau Publikasi) berdasarkan konteks permintaan
2. Ambil struktur dari chunk yang relevan
3. Isi dengan konten aktual yang diberikan user — jangan gunakan placeholder jika konten tersedia
4. Terapkan standar gaya bahasa Cakrawala Sasmita (chunk CS-TPL-004)
5. Validasi: apakah setiap seksi sudah menjawab "So what?"

### Yang TIDAK Boleh Dilakukan

- Jangan gunakan template secara kaku jika konteks tidak memerlukan semua seksi
- Jangan isi dokumen dengan placeholder seperti "[isi di sini]" jika informasi tersedia
- Jangan terapkan Format Publikasi untuk kebutuhan briefing internal yang cepat
- Jangan gunakan frasa yang ada di kolom "HINDARI" pada tabel terminologi
- Jangan tambahkan seksi atau sub-seksi yang tidak ada dalam template tanpa alasan kuat

### Penyesuaian yang Diizinkan

- Panjang setiap seksi dapat disesuaikan dengan kompleksitas konten
- Jumlah temuan dapat dikurangi (minimum 2) jika data terbatas
- Rekomendasi dapat diperpendek ke 1–2 level jika urgensi jelas
- Sub-seksi dalam Analisis dapat ditambah jika ada dimensi spesifik yang perlu dibahas
```
