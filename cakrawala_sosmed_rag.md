# RAG KNOWLEDGE BASE — ANALISIS SOSIAL MEDIA
# Institusi: Cakrawala Sasmita
# Modul: Intelijen Digital & Analisis Percakapan Publik
# Versi: 1.0 | April 2026

---

## METADATA

```json
{
  "modul": "analisis_sosial_media",
  "institusi": "Cakrawala Sasmita",
  "versi": "1.0",
  "use_when": [
    "user memberikan data social media listening",
    "user meminta analisis sentimen",
    "user meminta analisis percakapan publik",
    "user meminta analisis tren sosial media",
    "user meminta pemetaan narasi",
    "user meminta analisis influencer",
    "user meminta analisis berita online",
    "data dari Apify masuk untuk dianalisis",
    "user menyebut Twitter, TikTok, Instagram, Facebook, YouTube",
    "user meminta intelijen digital",
    "user meminta pemantauan isu"
  ]
}
```

---

# BAGIAN 1 — KERANGKA ANALISIS BERLAPIS

```json
{
  "chunk_id": "CS-SMA-001",
  "topic": "kerangka analisis sosial media berlapis",
  "tags": ["kerangka", "metodologi", "analisis", "sosial media"]
}
```

## Kerangka Analisis Sosial Media Cakrawala Sasmita

Analisis sosial media yang baik beroperasi di tiga lapisan secara bersamaan. Analis yang hanya melihat satu lapisan akan menghasilkan analisis yang dangkal dan menyesatkan.

### Lapisan 1 — WHAT (Apa yang terjadi)
Permukaan data yang terukur: volume, sentimen kasar, platform, engagement. Ini adalah lapisan yang bisa dibaca mesin. Analis pemula berhenti di sini.

### Lapisan 2 — WHY (Mengapa terjadi)
Motivasi, emosi, dan konteks di balik angka. Mengapa orang berbicara demikian? Apa yang mendorong sentimen ini? Apa konteks sosial-politik yang melatarbelakangi percakapan? Ini membutuhkan pemahaman konteks Indonesia yang mendalam.

### Lapisan 3 — SO WHAT (Apa implikasinya)
Proyeksi, risiko, dan peluang strategis. Ke mana ini akan berkembang? Apa yang perlu dilakukan? Ini adalah nilai tambah sesungguhnya dari analis senior.

**Aturan emas:** Output analisis Cakrawala Sasmita harus selalu menjangkau lapisan ketiga. Klien membayar untuk lapisan ketiga — lapisan pertama bisa mereka baca sendiri dari dashboard.

---

# BAGIAN 2 — TAKSONOMI SENTIMEN BERLAPIS

```json
{
  "chunk_id": "CS-SMA-002",
  "topic": "taksonomi sentimen berlapis Indonesia",
  "tags": ["sentimen", "emosi", "taksonomi", "analisis sentimen"]
}
```

## Taksonomi Sentimen untuk Konteks Indonesia

### Dimensi Pertama: Label Dasar
Positif / Negatif / Netral — hanya titik awal, bukan tujuan.

### Dimensi Kedua: Emosi Primer

**Klaster Negatif:**
| Emosi | Ciri Khas di Sosmed Indonesia | Intensitas |
|---|---|---|
| Marah (Outrage) | Capslock, tanda seru, kata-kata keras, tag langsung ke akun target | Sangat Tinggi |
| Kecewa (Disappointment) | Nada lelah, "sudah tidak kaget lagi", "memang begitu adanya" | Sedang-Tinggi |
| Takut (Fear) | Berbagi informasi peringatan, meminta konfirmasi, "benarkah ini?" | Tinggi |
| Sinis (Cynicism) | Sarkasme halus, meme, ironi — sering dilabeli "netral" tapi sebenarnya negatif dalam | Sedang |
| Apatis (Apathy) | Volume komentar rendah meski reach tinggi — sinyal bahaya yang sering terlewat | Rendah-Sedang |
| Jijik (Disgust) | Frasa "memalukan", "tidak pantas", "malu-maluin", "ampun dah" | Tinggi |

**Klaster Positif:**
| Emosi | Ciri Khas di Sosmed Indonesia | Intensitas |
|---|---|---|
| Bangga (Pride) | Share dengan caption positif, tag teman, "ini Indonesia kita" | Tinggi |
| Harapan (Hope) | "Semoga", "mudah-mudahan", tanda doa 🤲 | Sedang |
| Simpati (Sympathy) | Ekspresi bela rasa, dukungan moral, tanda hati ❤️ | Sedang |
| Antusias (Enthusiasm) | Banyak tanda seru, emoji semangat, share masif | Tinggi |

**Klaster Ambigu (paling sering salah dianalisis):**
| Emosi | Mengapa Ambigu | Cara Membedakan |
|---|---|---|
| Humor/Meme | Sering positif di permukaan tapi negatif substansinya | Baca konteks dan objek yang dimeme-kan |
| Nostalgia | Bisa positif (kenangan indah) atau negatif (kritik perbandingan) | Lihat apa yang dibandingkan |
| Shock/Disbelief | "Kok bisa?" bisa dari kagum atau dari kengerian | Lihat konteks berita atau kejadian |

### Dimensi Ketiga: Orientasi Sentimen

**Sentimen kepada SIAPA atau APA:**
- Sentimen terhadap institusi vs individu (berbeda signifikan)
- Sentimen terhadap kebijakan vs pelaksana kebijakan
- Sentimen terhadap korban vs pelaku dalam satu kasus
- Sentimen terhadap isu itu sendiri vs cara penanganannya

Contoh: Dalam isu bencana, publik bisa sekaligus:
- Bersimpati (positif) kepada korban
- Marah (negatif) kepada pemerintah yang lambat
- Bangga (positif) kepada relawan
- Sinis (negatif) kepada liputan media yang sensasional

Keempat sentimen ini hidup bersamaan. Analisis yang meratanya menjadi "60% negatif" kehilangan semua nuansa ini.

---

# BAGIAN 3 — FRAMEWORK ANALISIS NARASI

```json
{
  "chunk_id": "CS-SMA-003",
  "topic": "framework analisis narasi sosial media",
  "tags": ["narasi", "framing", "analisis narasi", "storytelling publik"]
}
```

## Framework Analisis Narasi Percakapan Publik

### Komponen Narasi yang Harus Diidentifikasi

**1. PLOT** — Alur cerita yang dipercayai publik
- Siapa protagonis (pihak yang benar/baik)?
- Siapa antagonis (pihak yang salah/jahat)?
- Apa konfliknya?
- Bagaimana "seharusnya" cerita ini berakhir menurut publik?

**2. FRAME** — Cara isu dikonstruksi
Setiap isu bisa diframe berbeda. Contoh untuk isu yang sama:

| Frame | Fokus | Implikasi Berbeda |
|---|---|---|
| Frame Keselamatan | Risiko dan perlindungan | Mendorong respons darurat |
| Frame Akuntabilitas | Siapa yang salah | Mendorong tuntutan pertanggungjawaban |
| Frame Ekonomi | Dampak finansial | Mendorong kalkulasi untung-rugi |
| Frame HAM | Hak yang dilanggar | Mendorong advokasi dan litigasi |
| Frame Konspirasi | Ada pihak yang sengaja | Mendorong ketidakpercayaan institusional |

Identifikasi frame mana yang dominan dan siapa yang mendorongnya.

**3. VILLAIN NARRATIVE** — Narasi musuh
Apakah ada pihak yang secara konsisten dijadikan "kambing hitam"? 
Narasi villain lebih mudah viral karena manusia secara kognitif 
lebih mudah memproses ancaman daripada kompleksitas.

**4. VICTIM NARRATIVE** — Narasi korban
Siapa yang diposisikan sebagai korban? Seberapa kuat empati publik 
terhadap "korban" ini? Narasi korban yang kuat adalah bahan bakar 
mobilisasi.

**5. HERO NARRATIVE** — Narasi pahlawan
Apakah ada tokoh atau kelompok yang diposisikan sebagai penyelamat?
Narasi hero positif bisa menjadi penyeimbang atau penangkal narasi negatif.

### Peta Persaingan Narasi

```
NARASI DOMINAN
(terbanyak volume, terbesar reach)
        |
        v
NARASI CHALLENGER
(sedang tumbuh, momentum naik)
        |
        v
NARASI ALTERNATIF
(minoritas tapi intensitas tinggi,
 potensial menjadi challenger)
        |
        v
NARASI TERSEMBUNYI
(beredar di grup tertutup, WhatsApp,
 belum masuk public discourse)
```

Analis harus memetakan SEMUA lapisan, bukan hanya yang terlihat.

### Red Flags Narasi yang Perlu Diwaspadai

- **Narasi dehumanisasi:** Menyebut kelompok tertentu dengan istilah yang merendahkan — potensi eskalasi konflik
- **Narasi konspirasi:** "Mereka sengaja", "ada yang mengatur" — sulit dipatahkan, cenderung abadi
- **Narasi whataboutism:** "Tapi yang itu bagaimana?" — defleksi yang efektif memecah fokus publik
- **Narasi fatalism:** "Sudah begini adanya", "tidak akan berubah" — sinyal erosi kepercayaan yang dalam
- **Narasi martyrdom:** Mengangkat individu sebagai simbol pengorbanan — potensial menjadi trigger mobilisasi

---

# BAGIAN 4 — ANALISIS AKTOR DAN JARINGAN

```json
{
  "chunk_id": "CS-SMA-004",
  "topic": "analisis aktor jaringan influencer sosial media",
  "tags": ["aktor", "influencer", "jaringan", "koordinasi", "amplifikasi"]
}
```

## Tipologi Aktor di Ekosistem Sosial Media Indonesia

### Kategori Aktor

**TIER 1 — AGENDA SETTER**
Aktor yang memulai atau mendefinisikan isu. Konten mereka yang pertama kali beredar dan membentuk framing awal.
- Media mainstream besar (Kompas, Tempo, CNN Indonesia, dll)
- Pejabat publik dengan akun resmi
- Tokoh publik dengan follower masif dan kredibilitas tinggi
- Analis/akademisi yang dikutip media

**TIER 2 — AMPLIFIER**
Aktor yang memperkuat dan menyebarkan konten dari Tier 1. Tidak menciptakan narasi baru tapi menentukan seberapa jauh narasi menjangkau.
- Influencer mid-tier (100K-1M follower)
- Akun komunitas dan organisasi
- Akun media lokal/regional
- Jurnalis individual yang aktif di sosmed

**TIER 3 — ECHO CHAMBER**
Pengguna biasa yang menshare dalam jaringan mereka sendiri. Menentukan kedalaman penetrasi ke berbagai segmen.
- Netizen umum dengan jaringan personal
- Anggota komunitas online spesifik

**TIER 4 — DARK AMPLIFIER**
Aktor yang sulit diidentifikasi tapi memiliki dampak signifikan.
- Akun anonim dengan engagement tinggi
- Jaringan akun yang terkoordinasi (bot atau manusia)
- Grup WhatsApp yang menyebarkan konten ke offline

### Indikator Amplifikasi Tidak Organik

Tandai sebagai TERINDIKASI KOORDINASI jika ditemukan 2+ dari berikut:

```
□ Lonjakan posting dalam rentang waktu sangat pendek 
  (puluhan/ratusan posting dalam <30 menit)

□ Kesamaan framing yang terlalu persis (bukan parafrase, 
  tapi copy-paste atau variasi minimal)

□ Akun baru atau akun dengan riwayat posting jarang 
  tiba-tiba sangat aktif di isu ini

□ Hashtag yang sama muncul di akun-akun yang tidak 
  memiliki koneksi organik satu sama lain

□ Pola posting di luar jam aktif normal (misalnya 
  ratusan posting antara pukul 02.00-04.00 WIB)

□ Engagement ratio yang tidak wajar (ribuan share 
  tapi komentar hampir nol, atau sebaliknya)

□ Akun-akun yang saling follow dan saling engage 
  hanya di isu ini, tidak di konten lain
```

Tingkat kepastian:
- 2-3 indikator: TERINDIKASI
- 4-5 indikator: KEMUNGKINAN BESAR TERKOORDINASI
- 6-7 indikator: SANGAT KUAT INDIKASI KOORDINASI

### Metrik Pengaruh yang Benar

Jangan hanya pakai follower count. Gunakan kombinasi:

| Metrik | Mengukur Apa | Keterbatasan |
|---|---|---|
| Follower Count | Potensi reach | Bisa dibeli, tidak mencerminkan engagement nyata |
| Engagement Rate | Interaksi per follower | Bisa dimanipulasi dengan engagement pod |
| Amplification Rate | Seberapa banyak konten di-share | Lebih sulit dimanipulasi |
| Comment Quality | Kedalaman diskusi yang dipicu | Butuh analisis kualitatif |
| Citation Rate | Seberapa sering dikutip media lain | Indikator kuat kredibilitas |
| Cross-Platform Presence | Ada di mana saja | Indikator organicness |

---

# BAGIAN 5 — ANALISIS PER PLATFORM

```json
{
  "chunk_id": "CS-SMA-005",
  "topic": "karakteristik analisis per platform sosial media",
  "tags": ["platform", "Twitter", "TikTok", "Instagram", "Facebook", "YouTube", "karakteristik"]
}
```

## Panduan Analisis Spesifik Per Platform

### TWITTER / X

**Karakteristik Unik:**
- Percakapan publik paling transparan dan paling mudah dianalisis
- Trending topic = barometer isu nasional (tapi bisa dimanipulasi)
- Echo chamber sangat kuat — kubu kiri dan kanan hampir tidak berinteraksi
- Durasi relevansi isu pendek: rata-rata 24-48 jam sebelum digantikan isu baru

**Yang Harus Dicek:**
- Trending organik vs trending yang didorong: lihat apakah trending muncul bersamaan dengan lonjakan posting terkoordinasi
- Ratio (reply lebih banyak dari like/RT): sinyal konten kontroversial atau tidak disetujui mayoritas
- Kutipan tweet (Quote Tweet) dengan komentar: lebih bermakna dari RT biasa karena menambahkan pendapat
- Thread panjang dari akun berpengaruh: sering menjadi referensi narasi yang disebarkan

**Metrik Kritis:**
- Impression : Engagement ratio (idealnya engagement 1-3% dari impression)
- RT : Reply ratio (RT >> Reply = amplifikasi pasif; Reply >> RT = konten kontroversial)
- Like : Reply ratio (Like >> Reply = approval; Reply >> Like = perdebatan)

### TIKTOK

**Karakteristik Unik:**
- Algoritma For You Page (FYP) sangat powerful — konten bisa viral tanpa follower besar
- Emosi lebih intens karena format video + audio
- Demografi lebih muda (16-30 tahun) dan lebih urban
- Komentar sering menjadi "konten dalam konten" — diskusi di komentar bisa sama viralnya dengan video

**Yang Harus Dicek:**
- Video vs komentar: sentiment video sering berbeda dengan sentiment komentar
- Duet dan stitch: lihat bagaimana konten asli "direspons" secara kreatif
- Suara/audio yang digunakan: audio yang sama dipakai di banyak video = sinyal tren atau meme
- View : Like ratio: video dengan view tinggi tapi like rendah = konten yang ditonton tapi tidak disetujui

**Metrik Kritis:**
- View Count vs Like-to-View Ratio (1-3% untuk konten organik biasa)
- Comment Sentiment (sering berlawanan dengan like)
- Share Count (paling sulit dimanipulasi di TikTok)

### INSTAGRAM

**Karakteristik Unik:**
- Visual-first: gambar dan caption memiliki bobot berbeda
- Stories bersifat ephemeral tapi sering lebih jujur dari Feed
- Komentar di Instagram lebih terfilter — negatif sering dihapus oleh pemilik akun
- Hashtag masih relevan sebagai discovery tool

**Yang Harus Dicek:**
- Caption vs komentar: diskrepansi besar = konten yang controversial
- Saved posts: konten yang banyak disimpan = konten yang dianggap penting/bernilai
- Reels vs static post: Reels mendapat lebih banyak reach tapi engagement berbeda
- Direct messages tidak terbaca — analisis terbatas pada konten publik

**Metrik Kritis:**
- Saves : Likes ratio (saves tinggi = konten yang dipercaya penting)
- Comment to Like ratio (1:10 normal; comment lebih tinggi = konten yang memancing diskusi)

### FACEBOOK

**Karakteristik Unik:**
- Demografi lebih tua (30-55 tahun) — representasi segmen yang sering diabaikan analisis
- Share dengan komentar = endorsement personal yang sangat kuat
- Grup tertutup adalah "ruang gelap" analisis — tidak terjangkau tapi sangat berpengaruh
- Berita palsu paling masif beredar di sini

**Yang Harus Dicek:**
- Angry reaction vs Like: perbandingan ini lebih informatif dari engagement total
- Share dengan komentar vs share tanpa komentar: share tanpa komentar mungkin impulsif
- Konten dari grup publik: indikator apa yang sedang hangat di komunitas organik
- Kecepatan share: konten yang share-nya cepat di awal biasanya menyebar lebih jauh

**Metrik Kritis:**
- Angry : Like reaction ratio (>20% Angry = konten yang memicu kemarahan signifikan)
- Comment : Share ratio (comment >> share = opini kuat; share >> comment = penyebaran informasi)

### YOUTUBE

**Karakteristik Unik:**
- Konten long-form: penonton yang engage biasanya lebih terdidik dan informed
- Komentar YouTube sering sangat panjang dan substantif — goldmine untuk analisis narasi
- Watch time lebih penting dari view count untuk mengukur engagement nyata
- Subscribe rate setelah menonton = indikator konten yang mengubah sikap

**Yang Harus Dicek:**
- Like : Dislike ratio: YouTube menyembunyikan dislike count tapi third-party tools bisa mengestimasi
- Top komentar: komentar yang di-like paling banyak = opini yang paling disetujui komunitas
- Komentar yang dipinned oleh kreator: biasanya mewakili posisi resmi kreator
- Video respons dari channel lain: indikator tingkat kontroversi

**Metrik Kritis:**
- Comment Density (komentar per 1000 view): >1 = konten yang memancing diskusi kuat
- Like Rate (like per 1000 view): <10 untuk konten kontroversial, >50 untuk konten yang sangat disetujui

### BERITA ONLINE DAN WEB

**Karakteristik Unik:**
- Headline menentukan 80% persepsi publik — banyak yang tidak membaca isi artikel
- SEO optimization kadang mendistorsi framing untuk mengejar traffic
- Berita dari media kredibel dipakai sebagai "sumber" yang mensahkan narasi di sosmed
- Kecepatan publikasi vs akurasi: media yang lebih cepat sering di-share lebih banyak meski kurang akurat

**Yang Harus Dicek:**
- Perbedaan headline vs isi artikel: diskrepansi besar = media yang sensasionalis atau clickbait
- Update dan koreksi: media yang sering mengupdate atau mengeluarkan koreksi vs yang tidak
- Sumber yang dikutip: apakah ada narasumber yang sama muncul di banyak media (sinyal framing terpusat)?
- Waktu publikasi: berita yang dirilis malam hari atau akhir pekan sering berusaha menghindari perhatian

**Metrik Kritis:**
- Share dari artikel di sosmed vs traffic langsung: artikel yang share-nya tinggi = konten yang memicu reaksi emosional
- Jumlah media yang pick up: berita yang diliput banyak media = memiliki news value tinggi atau ada dorongan tertentu

---

# BAGIAN 6 — POLA VIRAL DAN ESKALASI DI INDONESIA

```json
{
  "chunk_id": "CS-SMA-006",
  "topic": "pola viral eskalasi isu Indonesia sosial media",
  "tags": ["viral", "eskalasi", "pola", "Indonesia", "tren"]
}
```

## Pola Eskalasi Isu di Sosial Media Indonesia

### Kurva Eskalasi Standar

```
FASE 1 — IGNITION (0-6 jam)
Konten pertama muncul, biasanya dari satu sumber.
Volume rendah, share masih terbatas.
KRITIS: Framing awal di fase ini menentukan segalanya.

FASE 2 — SPREADING (6-24 jam)
Media mainstream mulai mengangkat.
Influencer mulai ikut bicara.
Volume naik eksponensial.
KRITIS: Apakah ada counter-narrative yang muncul?

FASE 3 — PEAK (24-72 jam)
Volume maksimal. Semua platform membahas.
Trending di Twitter. Muncul di berita nasional.
KRITIS: Apakah ada eskalasi offline (demo, pernyataan resmi)?

FASE 4 — DECLINE (3-7 hari)
Volume mulai turun kecuali ada trigger baru.
Isu mulai digantikan oleh isu lain.
KRITIS: Apakah ada "isu baru" yang muncul sebagai defleksi?

FASE 5 — RESIDUAL (7-30 hari)
Hanya tersisa di akun-akun yang passionate atau dalam pencarian.
Bisa diaktifkan kembali oleh trigger baru.
KRITIS: Monitor apakah ada upaya menghidupkan kembali.
```

### Faktor Akselerasi Viral di Indonesia

**Faktor yang MEMPERCEPAT viral:**
- Konten visual (video > foto > teks)
- Ada figur publik yang terlibat (pejabat, selebriti, tokoh agama)
- Menyentuh identitas: agama, etnis, nasionalisme
- Ada elemen emosi ekstrem: outrage, humor, horror, inspirasi
- Mudah dikonsumsi dalam <30 detik (terutama TikTok)
- Ada "underdog" yang melawan "kekuatan besar"
- Beredar di WhatsApp (off-platform amplification)

**Faktor yang MEMPERLAMBAT viral:**
- Konten teknis atau panjang
- Tidak ada visual
- Isu yang sudah pernah viral sebelumnya (fatigue)
- Counter-narrative kuat yang muncul cepat
- Platform membatasi distribusi (shadow ban)
- Tidak ada "wajah" atau karakter yang bisa diidentifikasi

### Trigger Reaktivasi Isu

Isu yang sudah turun bisa diaktifkan kembali oleh:
- Perkembangan hukum baru (sidang, putusan, penangkapan)
- Pernyataan terbaru dari pihak yang terlibat
- Anniversary atau momen peringatan
- Isu serupa yang terjadi kembali
- Dokumenter atau konten panjang yang membahasnya kembali
- Tindakan salah satu pihak yang dianggap tidak adil

---

# BAGIAN 7 — ANALISIS RISIKO REPUTASI DAN MISINFORMASI

```json
{
  "chunk_id": "CS-SMA-007",
  "topic": "analisis risiko reputasi misinformasi hoaks sosial media",
  "tags": ["risiko", "reputasi", "misinformasi", "hoaks", "krisis"]
}
```

## Framework Analisis Risiko Reputasi Digital

### Matriks Risiko Konten

| Tipe Konten | Probabilitas Viral | Dampak Reputasi | Prioritas Respons |
|---|---|---|---|
| Video insiden langsung (eyewitness) | Sangat Tinggi | Sangat Tinggi | SEGERA |
| Screenshot percakapan internal | Tinggi | Sangat Tinggi | SEGERA |
| Investigasi media kredibel | Tinggi | Tinggi | 24 Jam |
| Opini influencer besar | Sedang-Tinggi | Sedang | 24-48 Jam |
| Meme dan humor | Sedang | Sedang | 48-72 Jam |
| Artikel media kecil | Rendah | Rendah-Sedang | Monitor |
| Komentar akun anonim | Sangat Rendah | Rendah | Monitor saja |

### Identifikasi Misinformasi dan Hoaks

**Sinyal Konten yang Perlu Diverifikasi:**
- Klaim yang sangat ekstrem atau emosional tanpa sumber jelas
- Foto atau video tanpa konteks, caption yang mencurigakan
- Statistik atau angka tanpa sumber
- Cerita yang "terlalu sempurna" untuk digunakan sebagai propaganda
- Konten yang beredar ulang setelah waktu lama (recirculation)
- Konten yang meminta untuk "segera disebarkan sebelum dihapus"

**Level Verifikasi:**
```
TERVERIFIKASI: Dikonfirmasi sumber primer atau media kredibel
KEMUNGKINAN BENAR: Konsisten dengan fakta yang ada, sumber masuk akal
BELUM TERVERIFIKASI: Belum ada konfirmasi, perlu pengecekan
DIRAGUKAN: Inkonsisten dengan fakta yang ada
HOAKS TERKONFIRMASI: Sudah dibantah sumber primer atau fact-checker
```

**Dampak Berbeda Hoaks vs Fakta Negatif:**
- Hoaks yang terlanjur viral: bahaya meski sudah dibantah, 
  karena koreksi tidak pernah se-viral konten aslinya
- Fakta negatif yang akurat: lebih berbahaya jangka panjang 
  karena tidak bisa dibantah — hanya bisa dikontekstualisasikan
- Setengah fakta (half-truth): paling berbahaya karena tidak 
  bisa sepenuhnya dibantah tapi menyesatkan

---

# BAGIAN 8 — CONTOH ANALISIS LENGKAP

```json
{
  "chunk_id": "CS-SMA-008",
  "topic": "contoh analisis sosial media lengkap few-shot",
  "tags": ["contoh", "few-shot", "analisis lengkap", "referensi"]
}
```

## Contoh: Analisis Percakapan Publik

---

**RINGKASAN INTELIJEN DIGITAL**
**Isu: Viralnya Video Dugaan Brutalitas Aparat dalam Penanganan Demonstrasi**
Platform: Twitter/X, TikTok, YouTube, Facebook, Berita Online
Periode: 28-30 Agustus 2025 | Total konten terhimpun: 2.847 item

---

**SITUASI SEKARANG**

Percakapan publik berada di fase peak dengan kecenderungan belum menurun dalam 12 jam terakhir — sinyal bahwa isu ini memiliki sustaining power yang lebih kuat dari isu viral rata-rata. Volume tertinggi ada di Twitter/X (1.247 tweet) dan TikTok (743 video) dengan engagement gabungan melampaui 8,4 juta interaksi. Yang membedakan isu ini dari kontroversi serupa: percakapan tidak terpusat di satu platform atau satu kubu politik — muncul secara organik dan merata di berbagai segmen demografis.

Titik awal percakapan dapat ditelusuri ke sebuah video 47 detik yang diposting akun @saksi_mata_jkt pukul 14:23 WIB. Dalam enam jam, video tersebut sudah di-retweet 23.000 kali sebelum akun tersebut mengunci profilnya. Pola ini (akun memposting lalu segera membatasi akses) konsisten dengan taktik distribusi konten yang sudah terencana, meski tidak cukup untuk menyimpulkan adanya operasi koordinasi berskala penuh.

**SENTIMEN DAN EMOSI PUBLIK**

Data menunjukkan sentimen negatif 71% secara keseluruhan, namun angka ini menyembunyikan lebih banyak dari yang diungkapkan. Analisis lebih dalam mengungkap dua klaster emosi yang sangat berbeda:

Klaster pertama — outrage aktif (sekitar 43% dari total percakapan) — didominasi oleh ekspresi kemarahan langsung yang menyasar institusi kepolisian secara keseluruhan. Penggunaan frasa seperti "negara tiran", "polisi bajingan", dan tagar #ReformasiPolri menandakan sentimen ini melampaui respons terhadap insiden tunggal — ini adalah pelampiasan akumulasi kekecewaan yang sudah lama tersimpan.

Klaster kedua — kesedihan dan bela rasa (sekitar 28%) — terpusat pada figur korban spesifik. Emosi di klaster ini lebih dalam intensitasnya tapi lebih terbatas jangkauannya. Yang menarik, 64% dari klaster ini berasal dari pengguna yang sebelumnya tidak pernah memposting isu terkait kepolisian — mengindikasikan mobilisasi segmen baru yang sebelumnya apatis.

Sentimen "positif" terhadap aparat (sekitar 17%) hampir seluruhnya datang dari akun-akun yang secara historis pro-pemerintah, dengan framing "provokator di balik kerusuhan" — narasi tandingan resmi yang mulai dibangun.

**NARASI YANG BEREDAR**

Empat narasi utama bersaing dalam percakapan ini. Narasi dominan yang menguasai sekitar 60% percakapan memposisikan kejadian sebagai bukti sistemis kegagalan reformasi Polri: "ini bukan oknum, ini sistem." Kekuatan narasi ini ada pada kemampuannya menghubungkan insiden spesifik ke kritik struktural yang lebih luas — membuatnya sangat sulit dipatahkan hanya dengan membela insiden tunggal.

Narasi kedua (sekitar 18%) berfokus pada figur korban sebagai martir — dengan amplifikasi masif dari komunitas yang sebelumnya tidak terlibat. Narasi ini memiliki potensi mobilisasi offline yang signifikan dalam 48-72 jam ke depan.

Narasi tandingan resmi (sekitar 15%) yang menekankan "provokator asing" dan "agenda makar" sejauh ini gagal mendapat traksi organik — engagement-nya rendah dan rasio reply negatif terhadap konten ini sangat tinggi, mengindikasikan penolakan publik yang kuat terhadap framing ini.

Narasi keempat yang perlu diwaspadai (sekitar 7%, tapi momentum naik) mulai mempersoalkan keaslian video dan membangun keraguan epistemis. Meski volume masih kecil, narasi ini berpotensi membesar jika mendapat dukungan dari akun berpengaruh.

**AKTOR DAN DINAMIKA JARINGAN**

Lima media mainstream (Kompas, Tempo, CNN Indonesia, Tirto, Detik) secara kolektif bertanggung jawab atas 34% total reach, namun framing mereka berbeda signifikan: Tempo dan Tirto secara eksplisit menggunakan framing akuntabilitas institusional, sementara Detik dan CNN cenderung ke framing peristiwa-keamanan yang lebih netral.

Di lapisan influencer, akun @hukum_untuk_rakyat (187K follower) dan @jurnalis_lapangan (94K follower) menjadi amplifier terpenting dengan engagement rate 8-12% — jauh di atas rata-rata. Keduanya bukan akun yang biasanya terlibat dalam isu semacam ini, mengindikasikan bahwa insiden ini berhasil menarik audiens baru.

Terdapat dua klaster akun yang patut dicatat: pertama, 23 akun dengan pola posting identik dalam rentang 11 menit menggunakan framing "provokator asing" — terindikasi koordinasi tapi skala kecil. Kedua, 340+ akun yang baru dibuat dalam 48 jam terakhir yang aktif mendorong narasi keempat (keraguan keaslian video) — ini memerlukan pemantauan lebih lanjut.

**MOMENTUM DAN PROYEKSI**

Percakapan belum menunjukkan tanda penurunan yang konsisten — setiap 4-6 jam muncul konten baru yang memperbarui momentum. Tiga trigger yang berpotensi memperpanjang relevansi isu ini: (1) pernyataan resmi dari pimpinan Polri yang dianggap tidak memuaskan, (2) perkembangan kondisi korban yang dilaporkan memburuk, (3) rencana demonstrasi susulan yang diumumkan untuk Jumat depan.

Proyeksi 72 jam: isu ini tidak akan turun ke level residual sebelum ada respons resmi yang substantif dari Polri atau sebelum ada isu besar baru yang mengalihkan perhatian. Skenario terburuk yang perlu diantisipasi: jika terjadi insiden serupa sebelum isu ini mereda, percakapan bisa memasuki fase baru dengan intensitas jauh lebih tinggi.

**IMPLIKASI STRATEGIS DAN REKOMENDASI**

Segera (24 jam): Pantau ketat perkembangan kondisi korban dan rencana demonstrasi susulan — keduanya adalah trigger utama eskalasi. Siapkan dua skenario respons komunikasi: satu untuk eskalasi, satu untuk de-eskalasi. Jangan merespons narasi "provokator asing" secara langsung karena justru memperkuat polarisasi.

Jangka Pendek (7-14 hari): Analisis mendalam terhadap 23 akun terkoordinasi dan 340+ akun baru untuk menentukan apakah ini operasi terorganisir atau respons organik yang kebetulan serupa. Hasil analisis ini menentukan apakah ada dimensi operasi informasi yang perlu ditangani secara berbeda.

Jangka Menengah (30-90 hari): Percakapan ini akan menjadi referensi dalam perdebatan reformasi Polri yang lebih panjang. Rekomendasikan pemantauan berkelanjutan terhadap narasi yang muncul di ruang-ruang yang lebih tertutup (grup Facebook, forum online) sebagai indikator awal momentum berikutnya.

---

# BAGIAN 9 — INSTRUKSI TEKNIS UNTUK MODEL

```json
{
  "chunk_id": "CS-SMA-009",
  "topic": "instruksi teknis pengolahan data JSON sosial media",
  "tags": ["instruksi", "teknis", "JSON", "preprocessing", "data"]
}
```

## Instruksi Pengolahan Data dari Apify

### Cara Membaca Data JSON Sosial Media

Ketika menerima data JSON dari Apify atau tool social media listening lain, lakukan langkah berikut sebelum menganalisis:

**STEP 1 — INVENTARISASI DATA**
```
Hitung dan catat:
- Total item/post/artikel
- Distribusi per platform
- Rentang waktu (timestamp tertua hingga terbaru)
- Field yang tersedia (tidak semua scraper menghasilkan field yang sama)
- Data yang hilang atau kosong (null fields)
```

**STEP 2 — NORMALISASI INTERPRETASI**
Field yang berbeda antar platform tapi bermakna sama:
```
Engagement = likes + comments + shares + views (platform-adjusted)
Reach ≈ views/impressions (Twitter: impression; TikTok: views; YouTube: views)
Amplification = shares/retweets/reposts
Author credibility = follower count + verified status + account age
```

**STEP 3 — IDENTIFIKASI DATA YANG TIDAK BISA DIPERCAYA**
Tandai dan kurangi bobot:
```
- Engagement metrics yang tidak wajar (>10% engagement rate untuk akun >100K follower)
- Timestamp yang aneh (posting di masa depan, atau terlalu lama ke belakang)
- Content yang kosong atau hanya berisi URL
- Akun dengan follower 0 tapi engagement tinggi
```

**STEP 4 — BUAT MENTAL MODEL SEBELUM MENULIS**
Sebelum mulai analisis naratif, buat peta internal:
```
Isu utama: [satu kalimat]
Aktor paling berpengaruh: [top 5]
Narasi dominan: [satu frasa]
Sentimen dominan: [label + emosi primer]
Anomali yang perlu dijelaskan: [apa yang tidak biasa]
Proyeksi satu kalimat: [ke mana ini akan berkembang]
```

Baru setelah mental model ini jelas, mulai tulis analisis naratif.

### Pertanyaan Diagnostik Sebelum Menganalisis

Jawab pertanyaan berikut secara internal sebelum menulis:

1. Apakah data yang ada representatif atau ada bias platform?
2. Apakah volume data cukup untuk membuat klaim yang kuat?
3. Apakah ada konteks eksternal (berita, peristiwa offline) yang tidak ada dalam data tapi relevan?
4. Apa yang paling mengejutkan atau tidak terduga dari data ini?
5. Jika harus memilih SATU insight terpenting untuk disampaikan kepada klien, apa itu?

Jawaban pertanyaan kelima harus menjadi paragraf pembuka atau setidaknya bagian paling menonjol dari analisis.
```
