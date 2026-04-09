# RAG KNOWLEDGE BASE — PANDUAN PEMBUATAN DOKUMEN DOCX BERKUALITAS
# Institusi: Cakrawala Sasmita
# Modul: Standar Produksi Dokumen Analitik
# Cakupan: Konten analitik, desain DOCX, struktur laporan, common errors
# Versi: 1.0 | April 2026

---

## METADATA

```json
{
  "modul": "panduan_docx_analitik",
  "institusi": "Cakrawala Sasmita",
  "versi": "1.0",
  "use_when": [
    "user meminta membuat laporan analitik",
    "user meminta dokumen DOCX",
    "user meminta briefing, policy brief, atau laporan situasional",
    "perlu membangun dokumen bermerek Cakrawala Sasmita",
    "user meminta laporan geopolitik, ekonomi, atau kamtibmas",
    "perlu menghasilkan output dokumen yang terstruktur dan visual"
  ]
}
```

---

# BAGIAN 1 — PRINSIP DASAR DOKUMEN ANALITIK BERKUALITAS

```json
{
  "chunk_id": "CS-DOC-001",
  "topic": "prinsip dasar kualitas dokumen analitik",
  "tags": ["prinsip", "kualitas", "analitik", "standar", "dokumen"]
}
```

## Tiga Standar Kualitas yang Tidak Boleh Dilanggar

Setiap dokumen analitik Cakrawala Sasmita harus memenuhi tiga standar ini sekaligus. Gagal di satu standar berarti dokumen tidak layak dikirim ke klien.

### STANDAR 1 — AKURASI DATA

**Aturan mutlak:**
- Semua tanggal harus konsisten dan akurat. Jika laporan dibuat April 2026, tidak boleh ada tanggal 2023 atau 2024 dalam tubuh laporan kecuali sebagai referensi historis yang eksplisit.
- Semua angka harus spesifik dan terverifikasi. "Harga minyak naik signifikan" tidak acceptable — "Brent naik 16,5% dari USD 109 ke USD 127/barel dalam tujuh hari" adalah standar yang benar.
- Nama tokoh, jabatan, dan institusi harus akurat per tanggal laporan.
- Jika data tidak tersedia, nyatakan secara eksplisit: "Data per tanggal laporan tidak tersedia — estimasi berdasarkan..."

**Kesalahan yang paling sering terjadi (wajib dihindari):**
- Tanggal tahun yang salah — selalu cross-check tanggal di semua bagian dokumen
- Angka yang tidak bersumber — harus ada konteks atau sumber implisit
- Jabatan yang sudah berubah — Indonesia sering rotasi pejabat, selalu pakai versi terkini
- Nama operasi/kebijakan yang salah ejaan atau salah nama

### STANDAR 2 — KEDALAMAN ANALISIS

Laporan analitik Cakrawala Sasmita bukan ringkasan berita. Setiap laporan harus menjawab:

**WHAT** — Apa yang terjadi? (data dan fakta)
**WHY** — Mengapa terjadi? (analisis kausal dan kontekstual)
**SO WHAT** — Apa artinya bagi pembaca/klien? (implikasi dan relevance)
**WHAT NEXT** — Ke mana ini akan berkembang? (proyeksi dan skenario)

Laporan yang hanya menjawab WHAT adalah kliping berita, bukan analisis. Laporan yang baik menghabiskan 40% kontennya untuk SO WHAT dan WHAT NEXT.

**Ciri khas analisis yang dangkal (hindari):**
- Rekomendasi seperti "pemerintah perlu meningkatkan kewaspadaan" — tidak konkret, tidak berguna
- Skenario tanpa probabilitas — "mungkin akan terjadi X" tidak informatif
- Implikasi tanpa mekanisme — "akan berdampak pada ekonomi" tanpa menjelaskan rantai transmisinya
- Proyeksi tanpa kondisi — "jika X terjadi..." selalu harus ada kondisinya

**Ciri khas analisis yang dalam:**
- Data konkret dengan konteks perbandingan: "Kenaikan 16,5% dalam 7 hari — ini laju kenaikan tercepat sejak Maret 2022"
- Proyeksi dengan probabilitas eksplisit: "Skenario A (35%), Skenario B (48%), Skenario C (22%)"
- Implikasi dengan rantai transmisi: "Kenaikan USD 20/barel → tambahan beban subsidi Rp 15-18 triliun/bulan → defisit APBN melebar 0,5% PDB"
- Rekomendasi dengan pelaksana spesifik: "Bank Indonesia, bukan 'pemerintah'"

### STANDAR 3 — STRUKTUR DAN NAVIGABILITAS

Pembaca laporan analitik adalah pengambil keputusan yang sibuk. Dokumen harus memungkinkan pembaca:
- Mendapat gambaran utuh hanya dari membaca cover dan ringkasan eksekutif (2-3 menit)
- Menemukan bagian yang relevan tanpa membaca seluruh dokumen
- Memahami hierarki informasi dari yang paling penting ke paling detail

**Struktur standar laporan analitik Cakrawala Sasmita:**
1. Cover (judul, tanggal, klasifikasi, poin kunci)
2. Ringkasan Eksekutif (situasi + implikasi utama + tingkat risiko)
3. Konteks dan Kronologi (latar belakang + timeline)
4. Temuan Utama (fakta dan data per dimensi analisis)
5. Analisis dan Implikasi (untuk klien/Indonesia)
6. Proyeksi Skenario (3 skenario dengan probabilitas)
7. Matriks Risiko (tabel terstruktur)
8. Rekomendasi Berjenjang (Segera / Jangka Pendek / Jangka Menengah)

---

# BAGIAN 2 — PANDUAN KONTEN PER SEKSI

```json
{
  "chunk_id": "CS-DOC-002",
  "topic": "panduan konten per seksi laporan analitik",
  "tags": ["konten", "seksi", "ringkasan eksekutif", "skenario", "rekomendasi"]
}
```

## Panduan Menulis Setiap Seksi

### COVER — Poin Kunci

Poin Kunci di cover bukan abstrak akademis. Ini adalah "hook" yang membuat pembaca ingin membaca lebih lanjut. Harus menjawab dalam 3-4 kalimat:
- Apa yang sedang terjadi (1 kalimat, spesifik)
- Mengapa ini penting untuk pembaca/Indonesia (1 kalimat)
- Apa yang paling perlu diantisipasi (1-2 kalimat)

**Contoh BAD (terlalu abstrak):**
"Konflik AS-Iran terus berkembang dan berpotensi berdampak pada perekonomian global dan Indonesia."

**Contoh GOOD (spesifik dan actionable):**
"Penutupan Selat Hormuz per 2 April 2026 telah mendorong Brent ke USD 127/barel (+16,5% dalam 7 hari), menekan rupiah ke Rp 16.800/USD, dan menaikkan biaya logistik impor 12%. Tanpa paket respons dalam 30 hari, ruang fiskal APBN 2026 bisa menyempit hingga hanya 0,3% PDB."

### RINGKASAN EKSEKUTIF

Panjang: 3-4 paragraf, total tidak lebih dari 300 kata.

Paragraf 1: Situasi saat ini dalam 1-2 kalimat yang paling penting.
Paragraf 2: Implikasi langsung untuk Indonesia/klien.
Paragraf 3: Yang paling perlu diantisipasi (skenario terburuk yang realistis).
Baris terakhir: Label risiko formal — "Tingkat Risiko: [RENDAH/SEDANG/TINGGI/SANGAT TINGGI] | Urgensi: [Segera/Tidak Mendesak]"

### KRONOLOGI

Format terbaik: tabel dua kolom (Tanggal | Peristiwa).

Standar penulisan kronologi:
- Tanggal spesifik, bukan "awal April" atau "beberapa hari lalu"
- Setiap entri maksimal 2-3 kalimat
- Entri harus mengandung data atau tindakan konkret, bukan interpretasi
- Interpretasi masuk ke seksi Analisis, bukan Kronologi
- Urutan kronologis, bukan urutan kepentingan

### SKENARIO

Setiap skenario harus memiliki:
- Label jelas (A/B/C atau nama deskriptif)
- Probabilitas eksplisit dalam persen (harus total 100%)
- Horizon waktu spesifik (bukan "jangka pendek")
- Deskripsi kondisi yang harus terpenuhi agar skenario ini terjadi
- Proyeksi dampak konkret (harga, kurs, indikator spesifik)
- Implikasi khusus untuk Indonesia/klien

**Template skenario:**
```
Skenario [label] — Probabilitas [X%] — Horizon [waktu]
Kondisi: [apa yang harus terjadi]
Proyeksi: [dampak konkret dengan angka]
Implikasi Indonesia: [apa artinya bagi pembaca]
```

Jumlah skenario: selalu 3 (optimis, tengah, pesimis). Skenario tengah biasanya memiliki probabilitas tertinggi (40-50%).

### MATRIKS RISIKO

Kolom yang harus ada: Faktor Risiko | Probabilitas | Dampak | Horizon Waktu | Prioritas

Skala probabilitas: Sangat Rendah / Rendah / Sedang / Tinggi / Sangat Tinggi
Skala dampak: Rendah / Sedang / Tinggi / Sangat Tinggi
Prioritas: KRITIS / TINGGI / SEDANG / RENDAH

Aturan prioritas:
- KRITIS: Probabilitas Tinggi/Sangat Tinggi + Dampak Tinggi/Sangat Tinggi
- TINGGI: Probabilitas Sedang + Dampak Tinggi, atau Probabilitas Tinggi + Dampak Sedang
- SEDANG: Probabilitas Rendah + Dampak Tinggi, atau Probabilitas Sedang + Dampak Sedang
- RENDAH: Probabilitas Rendah + Dampak Rendah/Sedang

Minimum 5 faktor risiko, maksimal 10. Urutkan dari KRITIS ke RENDAH.

### REKOMENDASI

Struktur berjenjang wajib:

**SEGERA (24-72 jam):**
- Tindakan yang harus dimulai dalam 3 hari
- Spesifik: siapa melakukan apa
- Maksimal 3 poin

**JANGKA PENDEK (7-30 hari):**
- Kebijakan dan tindakan yang butuh persiapan
- Spesifik: kementerian/lembaga pelaksana
- Maksimal 5 poin

**JANGKA MENENGAH (30-90 hari atau lebih):**
- Kebijakan struktural yang perlu diinisiasi sekarang
- Spesifik: target yang bisa diukur
- Maksimal 4 poin

**Standar rekomendasi yang BAIK:**
- Ada subjek yang jelas: "Bank Indonesia" bukan "pemerintah"
- Ada tindakan konkret: "mempersiapkan intervensi NDF tambahan" bukan "menjaga stabilitas rupiah"
- Ada target atau kondisi keberhasilan: "menjaga rupiah tidak menembus Rp 17.000/USD"

**Standar rekomendasi yang BURUK (hindari):**
- "Pemerintah perlu meningkatkan kewaspadaan"
- "Indonesia harus memperkuat diplomasi"
- "Perlu kajian lebih lanjut mengenai..."
- "Diharapkan semua pihak..."

---

# BAGIAN 3 — STANDAR TEKNIS DOCX

```json
{
  "chunk_id": "CS-DOC-003",
  "topic": "standar teknis pembuatan file DOCX dengan docx-js",
  "tags": ["DOCX", "teknis", "docx-js", "JavaScript", "kode", "template"]
}
```

## Standar Teknis Pembuatan File DOCX

### Stack dan Setup

Library: `docx` (npm) — selalu gunakan versi terbaru yang terinstal
Runtime: Node.js
Validasi: `python3 /mnt/skills/public/docx/scripts/office/validate.py [file.docx]`

Import wajib minimal:
```javascript
const {
  Document, Packer, Paragraph, TextRun, Table, TableRow, TableCell,
  Header, Footer, AlignmentType, HeadingLevel, BorderStyle, WidthType,
  ShadingType, VerticalAlign, PageBreak, TabStopType, TabStopPosition,
  LevelFormat, PageNumber,
} = require('docx');
```

### Ukuran Halaman

Selalu gunakan A4 (default Indonesia):
```javascript
page: {
  size: { width: 11906, height: 16838 },  // A4 dalam DXA
  margin: { top: 1000, right: 1200, bottom: 1200, left: 1200 }
}
// Content width = 11906 - 1200 - 1200 = 9506 DXA
// Pakai 9026 untuk sedikit padding (rekomendasi)
```

### Palette Warna Cakrawala Sasmita

Selalu gunakan palette ini — jangan gunakan warna lain kecuali diminta:
```javascript
const C = {
  navy:       "1E2A3A",   // Heading utama, judul, teks penting
  teal:       "2AB07C",   // Aksen utama, heading2, callout border
  tealMid:    "C5EBD9",   // Rule line, header/footer border
  tealLight:  "E8F7F1",   // Callout box background (netral/informatif)
  coral:      "F06E6E",   // Warning, kritis, label risiko tinggi
  coralLight: "FEF0F0",   // Background untuk konten kritis
  amber:      "C49A00",   // Peringatan sedang, data ekonomi
  amberLight: "FEF9E7",   // Background untuk konten peringatan
  slate:      "4A5568",   // Teks body default
  gray:       "6B7280",   // Teks sekunder, keterangan
  grayLight:  "F3F4F6",   // Background baris tabel alternatif
  border:     "E2E8F0",   // Border tabel, garis pemisah
  white:      "FFFFFF",   // Background default, teks di atas warna gelap
};
```

### Typography

Font wajib: Arial (universal, aman di semua platform)
Ukuran dalam satuan half-points (DXA). Ukuran 22 = 11pt, 24 = 12pt, 28 = 14pt, 32 = 16pt.

```javascript
// Ukuran standar:
// Body text: 21 (10.5pt)
// Caption/small: 19 (9.5pt)
// Header/label: 17-19 (8.5-9.5pt)
// Heading 3: 21 bold
// Heading 2: 23 bold (teal)
// Heading 1: 28 bold (navy)
// Cover subtitle: 22-24
// Cover title: 32-52 bold (navy)
```

### Struktur Styles

```javascript
const styles = {
  default: { document: { run: { font: "Arial", size: 21, color: "4A5568" } } },
  paragraphStyles: [
    {
      id: "Heading1", name: "Heading 1", basedOn: "Normal", next: "Normal",
      quickFormat: true,
      run: { size: 28, bold: true, font: "Arial", color: "1E2A3A" },
      paragraph: { spacing: { before: 320, after: 100 }, outlineLevel: 0 },
    },
    {
      id: "Heading2", name: "Heading 2", basedOn: "Normal", next: "Normal",
      quickFormat: true,
      run: { size: 23, bold: true, font: "Arial", color: "2AB07C" },
      paragraph: { spacing: { before: 220, after: 60 }, outlineLevel: 1 },
    },
    {
      id: "Heading3", name: "Heading 3", basedOn: "Normal", next: "Normal",
      quickFormat: true,
      run: { size: 21, bold: true, font: "Arial", color: "1E2A3A" },
      paragraph: { spacing: { before: 160, after: 40 }, outlineLevel: 2 },
    },
  ],
};
```

### Numbering (Bullet dan Nomor)

WAJIB menggunakan numbering config — JANGAN gunakan karakter bullet manual:
```javascript
const numbering = {
  config: [
    {
      reference: "bullets",
      levels: [{
        level: 0, format: LevelFormat.BULLET, text: "•",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 640, hanging: 320 } } },
      }],
    },
    {
      reference: "nums",
      levels: [{
        level: 0, format: LevelFormat.DECIMAL, text: "%1.",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 640, hanging: 320 } } },
      }],
    },
  ],
};

// Penggunaan:
new Paragraph({
  numbering: { reference: "bullets", level: 0 },
  children: [new TextRun("Isi bullet")],
})
```

### Header dan Footer Standar

```javascript
// Header: nama institusi kiri | judul laporan + tanggal kanan
// Dipisahkan oleh border bawah tipis teal
const makeHeader = (judulPendek, tanggal) =>
  new Header({
    children: [
      new Paragraph({
        children: [
          new TextRun({ text: "CAKRAWALA SASMITA", font: "Arial", size: 17, bold: true, color: "2AB07C", characterSpacing: 50 }),
          new TextRun({ text: `\t${judulPendek}  •  ${tanggal}`, font: "Arial", size: 16, color: "6B7280" }),
        ],
        tabStops: [{ type: TabStopType.RIGHT, position: TabStopPosition.MAX }],
        border: { bottom: { style: BorderStyle.SINGLE, size: 4, color: "C5EBD9", space: 1 } },
        spacing: { before: 0, after: 60 },
      }),
    ],
  });

// Footer: keterangan kiri | nomor halaman kanan
const makeFooter = (keterangan) =>
  new Footer({
    children: [
      new Paragraph({
        children: [
          new TextRun({ text: `© 2026 Cakrawala Sasmita  •  ${keterangan}`, font: "Arial", size: 16, color: "6B7280" }),
          new TextRun({ text: "\tHal. ", font: "Arial", size: 16, color: "6B7280" }),
          new TextRun({ children: [PageNumber.CURRENT], font: "Arial", size: 16, color: "6B7280" }),
        ],
        tabStops: [{ type: TabStopType.RIGHT, position: TabStopPosition.MAX }],
        border: { top: { style: BorderStyle.SINGLE, size: 4, color: "C5EBD9", space: 1 } },
        spacing: { before: 60, after: 0 },
      }),
    ],
  });
```

### Helper Functions Standar

Selalu gunakan helper berikut — jangan inline semua properti:

```javascript
// Spacer paragraph
const sp = (after = 100) =>
  new Paragraph({ children: [], spacing: { before: 0, after } });

// TextRun shorthand
const t = (text, opts = {}) =>
  new TextRun({ text, font: "Arial", size: 21, color: "4A5568", ...opts });

// Rule (garis tipis via paragraph border — BUKAN via tabel)
const rule = (color = "E2E8F0", size = 6) =>
  new Paragraph({
    children: [],
    border: { bottom: { style: BorderStyle.SINGLE, size, color, space: 1 } },
    spacing: { before: 0, after: 80 },
  });

// Accent rule (garis tebal teal — biasanya di cover)
const accentRule = () =>
  new Paragraph({
    children: [],
    border: { bottom: { style: BorderStyle.SINGLE, size: 16, color: "2AB07C", space: 1 } },
    spacing: { before: 0, after: 180 },
  });
```

---

# BAGIAN 4 — PATTERN KOMPONEN VISUAL

```json
{
  "chunk_id": "CS-DOC-004",
  "topic": "pattern komponen visual DOCX callout box tabel dua kolom",
  "tags": ["callout", "box", "tabel", "dua kolom", "visual", "komponen", "pattern"]
}
```

## Pattern Komponen Visual yang Wajib Dikuasai

### 1. CALLOUT BOX (Kotak Highlight)

Digunakan untuk: Poin Kunci, Ringkasan, Data Penting, Warning
Implementasi: Single-cell table dengan shading

```javascript
function callout(children, fill = "E8F7F1", leftColor = null) {
  const nb = { style: BorderStyle.NONE, size: 0, color: "auto" };
  return new Table({
    width: { size: 9026, type: WidthType.DXA },
    columnWidths: [9026],
    borders: { top: nb, bottom: nb, left: nb, right: nb, insideH: nb, insideV: nb },
    rows: [new TableRow({
      children: [new TableCell({
        width: { size: 9026, type: WidthType.DXA },
        shading: { fill, type: ShadingType.CLEAR },
        borders: {
          top: nb, bottom: nb, right: nb,
          left: leftColor
            ? { style: BorderStyle.SINGLE, size: 20, color: leftColor }
            : nb,
        },
        margins: { top: 160, bottom: 160, left: 220, right: 220 },
        children,
      })],
    })],
  });
}

// Penggunaan:
callout([
  new Paragraph({ children: [t("LABEL", { size: 17, bold: true, color: "2AB07C", characterSpacing: 30 })] }),
  sp(60),
  new Paragraph({ children: [t("Isi konten di sini...")] }),
], "E8F7F1", "2AB07C")  // tealLight background, teal left border
```

**Variasi warna callout:**
- Informatif/netral: fill `E8F7F1`, leftColor `2AB07C` (teal)
- Warning/peringatan: fill `FEF9E7`, leftColor `C49A00` (amber)
- Kritis/bahaya: fill `FEF0F0`, leftColor `F06E6E` (coral)
- Netral/abu: fill `F3F4F6`, leftColor `6B7280` (gray)

### 2. DUA KOLOM SIDE-BY-SIDE

Digunakan untuk: metadata cover, label + konten, info berpasangan
Implementasi: Two-cell table tanpa border

```javascript
function twoCol(w1, w2, leftChildren, rightChildren) {
  const nb = { style: BorderStyle.NONE, size: 0, color: "auto" };
  const allNone = { top: nb, bottom: nb, left: nb, right: nb, insideH: nb, insideV: nb };
  return new Table({
    width: { size: 9026, type: WidthType.DXA },
    columnWidths: [w1, w2],
    borders: allNone,
    rows: [new TableRow({
      children: [
        new TableCell({
          width: { size: w1, type: WidthType.DXA }, borders: allNone,
          margins: { top: 0, bottom: 0, left: 0, right: 120 },
          children: leftChildren,
        }),
        new TableCell({
          width: { size: w2, type: WidthType.DXA }, borders: allNone,
          margins: { top: 0, bottom: 0, left: 0, right: 0 },
          children: rightChildren,
        }),
      ],
    })],
  });
}

// Penggunaan untuk cover metadata:
twoCol(5800, 3226,
  [
    new Paragraph({ children: [t("Cakrawala Sasmita", { bold: true, color: "1E2A3A", size: 23 })] }),
    new Paragraph({ children: [t("Lembaga Riset & Think Tank", { color: "6B7280", size: 19 })] }),
  ],
  [
    new Paragraph({ alignment: AlignmentType.RIGHT, children: [t("9 April 2026", { bold: true, color: "1E2A3A", size: 21 })] }),
    new Paragraph({ alignment: AlignmentType.RIGHT, children: [t("INTERNAL", { color: "F06E6E", bold: true, size: 19 })] }),
  ],
)
```

### 3. TABEL DATA STANDAR (Kronologi, Matriks Risiko, dll)

```javascript
// Pola tabel dengan header navy dan baris bergantian putih/grayLight
function dataTable(columnWidths, headers, rows) {
  const nb = { style: BorderStyle.NONE, size: 0, color: "auto" };
  const totalW = columnWidths.reduce((a, b) => a + b, 0);

  return new Table({
    width: { size: totalW, type: WidthType.DXA },
    columnWidths,
    rows: [
      // Header row
      new TableRow({
        tableHeader: true,
        children: headers.map((h, i) =>
          new TableCell({
            width: { size: columnWidths[i], type: WidthType.DXA },
            shading: { fill: "1E2A3A", type: ShadingType.CLEAR },
            borders: { top: nb, bottom: nb, left: nb, right: nb },
            margins: { top: 100, bottom: 100, left: 140, right: 140 },
            children: [new Paragraph({ children: [t(h, { size: 19, bold: true, color: "FFFFFF" })] })],
          })
        ),
      }),
      // Data rows
      ...rows.map((row, ri) =>
        new TableRow({
          children: row.map((cell, ci) =>
            new TableCell({
              width: { size: columnWidths[ci], type: WidthType.DXA },
              shading: { fill: ri % 2 === 0 ? "FFFFFF" : "F3F4F6", type: ShadingType.CLEAR },
              borders: {
                top: { style: BorderStyle.SINGLE, size: 1, color: "E2E8F0" },
                bottom: { style: BorderStyle.SINGLE, size: 1, color: "E2E8F0" },
                left: nb, right: nb,
              },
              margins: { top: 100, bottom: 100, left: 140, right: 140 },
              children: [new Paragraph({ children: [t(cell.text || cell, { size: 19, ...(cell.opts || {}) })] })],
            })
          ),
        })
      ),
    ],
  });
}
```

### 4. KARTU SKENARIO (Numbered Card)

Digunakan untuk: Skenario A/B/C, Rekomendasi berjenjang
Implementasi: Two-cell table — sel kiri warna solid (nomor), sel kanan callout

```javascript
function scenarioCard(num, label, prob, horizon, fill, accent, bodyChildren) {
  const nb = { style: BorderStyle.NONE, size: 0, color: "auto" };
  return new Table({
    width: { size: 9026, type: WidthType.DXA },
    columnWidths: [380, 8646],
    borders: { top: nb, bottom: nb, left: nb, right: nb, insideH: nb, insideV: nb },
    rows: [new TableRow({
      children: [
        // Nomor — solid color
        new TableCell({
          width: { size: 380, type: WidthType.DXA },
          shading: { fill: accent, type: ShadingType.CLEAR },
          borders: { top: nb, bottom: nb, left: nb, right: nb },
          verticalAlign: VerticalAlign.CENTER,
          margins: { top: 0, bottom: 0, left: 0, right: 0 },
          children: [new Paragraph({
            alignment: AlignmentType.CENTER,
            children: [t(num, { size: 24, bold: true, color: "FFFFFF" })],
          })],
        }),
        // Konten — light fill
        new TableCell({
          width: { size: 8646, type: WidthType.DXA },
          shading: { fill, type: ShadingType.CLEAR },
          borders: { top: nb, bottom: nb, right: nb, left: nb },
          margins: { top: 160, bottom: 160, left: 200, right: 200 },
          children: [
            twoCol(5800, 2846,
              [new Paragraph({ children: [t(`${label}`, { bold: true, color: accent, size: 21 })] })],
              [
                new Paragraph({ alignment: AlignmentType.RIGHT, children: [t(`Probabilitas: ${prob}`, { bold: true, color: accent, size: 19 })] }),
                new Paragraph({ alignment: AlignmentType.RIGHT, children: [t(`Horizon: ${horizon}`, { color: "6B7280", size: 18 })] }),
              ],
            ),
            sp(80),
            ...bodyChildren,
          ],
        }),
      ],
    })],
  });
}
```

---

# BAGIAN 5 — RULES KRITIS YANG TIDAK BOLEH DILANGGAR

```json
{
  "chunk_id": "CS-DOC-005",
  "topic": "rules kritis DOCX yang sering menyebabkan error atau tampilan buruk",
  "tags": ["rules", "error", "common mistakes", "pitfalls", "DOCX", "validasi"]
}
```

## Rules Kritis — Wajib Diikuti

### ATURAN 1: Jangan gunakan tabel sebagai divider/garis

SALAH — tabel kosong sebagai garis:
```javascript
// ❌ JANGAN LAKUKAN INI
new Table({ rows: [new TableRow({ children: [new TableCell({ children: [] })] })] })
```

BENAR — gunakan border paragraph:
```javascript
// ✅ BENAR
new Paragraph({
  children: [],
  border: { bottom: { style: BorderStyle.SINGLE, size: 6, color: "E2E8F0", space: 1 } },
  spacing: { before: 0, after: 80 },
})
```

### ATURAN 2: Jangan gunakan karakter bullet manual

SALAH:
```javascript
// ❌ JANGAN
new Paragraph({ children: [new TextRun("• Item pertama")] })
new Paragraph({ children: [new TextRun("\u2022 Item pertama")] })
```

BENAR — gunakan numbering config:
```javascript
// ✅ BENAR
new Paragraph({
  numbering: { reference: "bullets", level: 0 },
  children: [new TextRun("Item pertama")],
})
```

### ATURAN 3: PageBreak harus di dalam Paragraph

SALAH:
```javascript
// ❌ JANGAN
new PageBreak()
```

BENAR:
```javascript
// ✅ BENAR
new Paragraph({ children: [new PageBreak()] })
```

### ATURAN 4: ShadingType selalu CLEAR, bukan SOLID

SALAH:
```javascript
// ❌ SOLID menyebabkan background hitam
shading: { fill: "E8F7F1", type: ShadingType.SOLID }
```

BENAR:
```javascript
// ✅ CLEAR adalah yang benar untuk background color
shading: { fill: "E8F7F1", type: ShadingType.CLEAR }
```

### ATURAN 5: Tabel selalu butuh dual width

SALAH — hanya set di table:
```javascript
// ❌ Tidak cukup
new Table({
  width: { size: 9026, type: WidthType.DXA },
  columnWidths: [4513, 4513],
  rows: [new TableRow({
    children: [new TableCell({ children: [] })]  // Tanpa width di cell
  })]
})
```

BENAR — set di table DAN di setiap cell:
```javascript
// ✅ Harus ada di keduanya
new Table({
  width: { size: 9026, type: WidthType.DXA },
  columnWidths: [4513, 4513],
  rows: [new TableRow({
    children: [new TableCell({
      width: { size: 4513, type: WidthType.DXA },  // Wajib di cell juga
      children: []
    })]
  })]
})
```

### ATURAN 6: Jangan gunakan WidthType.PERCENTAGE

```javascript
// ❌ JANGAN — breaks di Google Docs
width: { size: 50, type: WidthType.PERCENTAGE }

// ✅ BENAR — selalu DXA
width: { size: 4513, type: WidthType.DXA }
```

### ATURAN 7: Jangan gunakan "\n" untuk baris baru

```javascript
// ❌ JANGAN
new TextRun("Baris pertama\nBaris kedua")

// ✅ BENAR — gunakan Paragraph terpisah
new Paragraph({ children: [new TextRun("Baris pertama")] }),
new Paragraph({ children: [new TextRun("Baris kedua")] }),
```

### ATURAN 8: Selalu validasi setelah build

```bash
# Wajib dijalankan setelah setiap build
python3 /mnt/skills/public/docx/scripts/office/validate.py [file.docx]

# Output yang benar:
# Paragraphs: 0 → XXX (+XXX)
# All validations PASSED!
```

### ATURAN 9: Multi-section untuk cover berbeda

Jika cover tidak boleh ada header/footer tapi halaman isi harus ada, gunakan dua section:

```javascript
const doc = new Document({
  numbering,
  styles,
  sections: [
    // Section 1: Cover (tanpa header/footer)
    {
      properties: {
        page: { size: { width: 11906, height: 16838 }, margin: { top: 800, right: 1200, bottom: 1200, left: 1200 } }
      },
      children: coverContent,
    },
    // Section 2: Isi (dengan header/footer)
    {
      properties: {
        page: { size: { width: 11906, height: 16838 }, margin: { top: 1000, right: 1200, bottom: 1200, left: 1200 } }
      },
      headers: { default: makeHeader() },
      footers: { default: makeFooter() },
      children: bodyContent,
    },
  ],
});
```

---

# BAGIAN 6 — COVER BLOCK STANDAR

```json
{
  "chunk_id": "CS-DOC-006",
  "topic": "template cover block standar Cakrawala Sasmita",
  "tags": ["cover", "template", "cover block", "judul", "desain"]
}
```

## Template Cover Block Standar

Cover block standar terdiri dari 5 elemen berurutan:

```
[1] Banner strip warna (teal) — kategori laporan
[2] Judul besar (48-52pt, navy, bold)
[3] Subjudul (28-32pt, navy, bold)
[4] Deskriptor (22pt, gray)
[5] Spacer
[6] Accent rule (garis teal tebal)
[7] Metadata row (institusi kiri | tanggal+klasifikasi kanan) via twoCol
[8] Spacer
[9] Callout "POIN KUNCI" (tealLight background, teal border kiri)
[10] PageBreak
```

**Banner strip — implementasi:**
```javascript
new Table({
  width: { size: 9026, type: WidthType.DXA },
  columnWidths: [9026],
  borders: {
    top: { style: BorderStyle.NONE, size: 0, color: "auto" },
    bottom: { style: BorderStyle.NONE, size: 0, color: "auto" },
    left: { style: BorderStyle.NONE, size: 0, color: "auto" },
    right: { style: BorderStyle.NONE, size: 0, color: "auto" },
    insideH: { style: BorderStyle.NONE, size: 0, color: "auto" },
    insideV: { style: BorderStyle.NONE, size: 0, color: "auto" },
  },
  rows: [new TableRow({ children: [new TableCell({
    width: { size: 9026, type: WidthType.DXA },
    shading: { fill: "2AB07C", type: ShadingType.CLEAR },
    borders: {
      top: { style: BorderStyle.NONE, size: 0, color: "auto" },
      bottom: { style: BorderStyle.NONE, size: 0, color: "auto" },
      left: { style: BorderStyle.NONE, size: 0, color: "auto" },
      right: { style: BorderStyle.NONE, size: 0, color: "auto" },
    },
    margins: { top: 140, bottom: 140, left: 220, right: 220 },
    children: [
      new Paragraph({
        children: [new TextRun({
          text: "LAPORAN ANALITIK STRATEGIS  |  [KATEGORI]",
          font: "Arial", size: 17, bold: true, color: "FFFFFF", characterSpacing: 30,
        })],
      }),
    ],
  })]})],
})
```

**Klasifikasi yang digunakan:**
- `INTERNAL` — hanya untuk internal Cakrawala Sasmita
- `TERBATAS` — untuk klien tertentu
- `PUBLIK` — bisa disebarkan

---

# BAGIAN 7 — CHECKLIST SEBELUM KIRIM

```json
{
  "chunk_id": "CS-DOC-007",
  "topic": "checklist kualitas dokumen sebelum dikirim ke klien",
  "tags": ["checklist", "quality control", "review", "sebelum kirim"]
}
```

## Checklist Wajib Sebelum Output Dokumen

### CHECKLIST KONTEN

```
□ Semua tanggal akurat dan konsisten (tidak ada tahun yang salah)
□ Semua angka spesifik dan ada konteks perbandingan
□ Tidak ada pernyataan tanpa bukti atau sumber implisit
□ Ringkasan Eksekutif sudah menjawab: WHAT, WHY, SO WHAT, WHAT NEXT
□ Ada minimal 3 skenario dengan probabilitas yang total 100%
□ Rekomendasi memiliki subjek yang spesifik (bukan "pemerintah" generik)
□ Rekomendasi berjenjang: Segera / Jangka Pendek / Jangka Menengah
□ Matriks risiko memiliki minimal 5 faktor dengan kode prioritas
□ Poin Kunci di cover sudah spesifik dan berisi angka/data konkret
□ Label Tingkat Risiko ada di Ringkasan Eksekutif
```

### CHECKLIST TEKNIS DOCX

```
□ File berhasil divalidasi: "All validations PASSED!"
□ Header ada di semua halaman isi (bukan cover)
□ Footer ada di semua halaman isi dengan nomor halaman
□ Cover menggunakan palette warna yang benar
□ Tidak ada karakter bullet manual (•) dalam kode
□ Tidak ada "\n" dalam TextRun
□ Semua tabel menggunakan dual width (table + cell)
□ Semua shading menggunakan ShadingType.CLEAR
□ PageBreak berada di dalam Paragraph
□ Garis pemisah menggunakan border Paragraph, bukan tabel kosong
□ File disimpan ke /mnt/user-data/outputs/ sebelum present
```

### CHECKLIST DESAIN

```
□ Menggunakan palette Cakrawala Sasmita (navy, teal, coral, amber)
□ Cover memiliki banner strip, judul besar, accent rule, metadata row, poin kunci
□ Hierarki heading jelas: H1 (navy) → H2 (teal) → H3 (navy)
□ Callout box digunakan untuk informasi penting (minimal 1 per seksi besar)
□ Tabel kronologi menggunakan baris bergantian putih/gray
□ Skenario menggunakan kartu berwarna (teal/amber/coral sesuai optimisme)
□ Matriks risiko menggunakan kode warna (merah=kritis, kuning=tinggi, abu=sedang)
```

---

# BAGIAN 8 — CONTOH SNIPPET LENGKAP SIAP PAKAI

```json
{
  "chunk_id": "CS-DOC-008",
  "topic": "snippet kode siap pakai untuk komponen DOCX yang umum",
  "tags": ["snippet", "kode", "siap pakai", "contoh", "komponen"]
}
```

## Snippet Siap Pakai

### Matriks Risiko Berwarna

```javascript
// Kolom: Faktor Risiko | Probabilitas | Dampak | Horizon | Prioritas
// Lebar kolom menyesuaikan konten
const riskMatrixData = [
  // [faktor, prob, dampak, horizon, prioritas, rowBgColor]
  ["Nama faktor risiko 1", "Sangat Tinggi", "Sangat Tinggi", "Sekarang", "KRITIS", "FEF0F0"],
  ["Nama faktor risiko 2", "Tinggi",        "Tinggi",        "30 hari",  "KRITIS", "FEF0F0"],
  ["Nama faktor risiko 3", "Sedang",        "Tinggi",        "30-60 hari","TINGGI", "FEF9E7"],
  ["Nama faktor risiko 4", "Sedang",        "Sedang",        "60 hari",  "SEDANG", "F3F4F6"],
];

const prioColor = { "KRITIS": "F06E6E", "TINGGI": "C49A00", "SEDANG": "6B7280", "RENDAH": "6B7280" };
const colW = [2920, 1620, 1620, 1420, 1446]; // total = 9026
const nb = { style: BorderStyle.NONE, size: 0, color: "auto" };

new Table({
  width: { size: 9026, type: WidthType.DXA },
  columnWidths: colW,
  rows: [
    new TableRow({
      tableHeader: true,
      children: ["Faktor Risiko","Probabilitas","Dampak","Horizon","Prioritas"].map((h, i) =>
        new TableCell({
          width: { size: colW[i], type: WidthType.DXA },
          shading: { fill: "1E2A3A", type: ShadingType.CLEAR },
          borders: { top: nb, bottom: nb, left: nb, right: nb },
          margins: { top: 100, bottom: 100, left: 140, right: 140 },
          children: [new Paragraph({ children: [t(h, { size: 19, bold: true, color: "FFFFFF" })] })],
        })
      ),
    }),
    ...riskMatrixData.map(([faktor, prob, dampak, horizon, prio, bg]) =>
      new TableRow({
        children: [faktor, prob, dampak, horizon, prio].map((cell, ci) =>
          new TableCell({
            width: { size: colW[ci], type: WidthType.DXA },
            shading: { fill: bg, type: ShadingType.CLEAR },
            borders: {
              top: { style: BorderStyle.SINGLE, size: 1, color: "E2E8F0" },
              bottom: { style: BorderStyle.SINGLE, size: 1, color: "E2E8F0" },
              left: nb, right: nb,
            },
            margins: { top: 100, bottom: 100, left: 140, right: 140 },
            children: [new Paragraph({ children: [
              t(cell, { size: 19, color: ci === 4 ? prioColor[prio] : "4A5568", bold: ci === 4 }),
            ]})],
          })
        ),
      })
    ),
  ],
})
```

### Kartu Rekomendasi Berjenjang

```javascript
const rekoData = [
  {
    num: "01", label: "SEGERA  (24–72 Jam)", fill: "FEF0F0", accent: "F06E6E",
    items: ["Rekomendasi konkret 1...", "Rekomendasi konkret 2..."],
  },
  {
    num: "02", label: "JANGKA PENDEK  (7–30 Hari)", fill: "E8F7F1", accent: "2AB07C",
    items: ["Rekomendasi konkret 3...", "Rekomendasi konkret 4..."],
  },
  {
    num: "03", label: "JANGKA MENENGAH  (30–90 Hari)", fill: "F3F4F6", accent: "6B7280",
    items: ["Rekomendasi konkret 5...", "Rekomendasi konkret 6..."],
  },
];

// Hasilkan kartu untuk setiap tingkat:
rekoData.flatMap(({ num, label, fill, accent, items }) => [
  new Table({
    width: { size: 9026, type: WidthType.DXA },
    columnWidths: [380, 8646],
    borders: { top: nb, bottom: nb, left: nb, right: nb, insideH: nb, insideV: nb },
    rows: [new TableRow({
      children: [
        new TableCell({
          width: { size: 380, type: WidthType.DXA },
          shading: { fill: accent, type: ShadingType.CLEAR },
          borders: { top: nb, bottom: nb, left: nb, right: nb },
          verticalAlign: VerticalAlign.CENTER,
          margins: { top: 0, bottom: 0, left: 0, right: 0 },
          children: [new Paragraph({
            alignment: AlignmentType.CENTER,
            children: [t(num, { size: 24, bold: true, color: "FFFFFF" })],
          })],
        }),
        new TableCell({
          width: { size: 8646, type: WidthType.DXA },
          shading: { fill, type: ShadingType.CLEAR },
          borders: { top: nb, bottom: nb, right: nb, left: nb },
          margins: { top: 160, bottom: 160, left: 200, right: 200 },
          children: [
            new Paragraph({ children: [t(label, { bold: true, color: accent, size: 21 })] }),
            sp(60),
            ...items.map(item => new Paragraph({
              numbering: { reference: "bullets", level: 0 },
              children: [t(item, { size: 21, color: "1E2A3A" })],
            })),
          ],
        }),
      ],
    })],
  }),
  sp(110),
])
```

---

# BAGIAN 9 — ALUR KERJA STANDAR

```json
{
  "chunk_id": "CS-DOC-009",
  "topic": "alur kerja standar pembuatan dokumen DOCX dari awal hingga output",
  "tags": ["alur kerja", "workflow", "step by step", "proses", "standar"]
}
```

## Alur Kerja Standar Membuat Dokumen Analitik

```
STEP 1 — SIAPKAN KONTEN
  - Kumpulkan semua fakta, angka, tanggal yang akan digunakan
  - Verifikasi konsistensi tanggal
  - Tentukan 3 skenario dan probabilitasnya (total 100%)
  - Identifikasi pelaksana spesifik untuk setiap rekomendasi

STEP 2 — TULIS SCRIPT NODE.JS
  Struktur file:
  1. Import semua yang dibutuhkan dari 'docx'
  2. Definisikan konstanta: C (palette), numbering, styles
  3. Definisikan helper functions: sp(), t(), rule(), accentRule(), callout(), twoCol()
  4. Definisikan header dan footer
  5. Bangun konten per seksi sebagai array (cover, execSummary, dll)
  6. Build Document dengan sections
  7. Packer.toBuffer → fs.writeFileSync ke /home/claude/[nama].docx

STEP 3 — JALANKAN
  node [script].js

STEP 4 — VALIDASI
  python3 /mnt/skills/public/docx/scripts/office/validate.py [file.docx]
  → Harus: "All validations PASSED!"

STEP 5 — COPY KE OUTPUT
  cp /home/claude/[file].docx /mnt/user-data/outputs/

STEP 6 — PRESENT
  present_files(["/mnt/user-data/outputs/[file].docx"])
```

**Jika validasi gagal:**
1. Baca pesan error dengan teliti
2. Periksa urutan: PageBreak di dalam Paragraph, ShadingType.CLEAR, dual width tabel
3. Perbaiki di script, jalankan ulang, validasi ulang
4. Jangan present file yang tidak lulus validasi
```
