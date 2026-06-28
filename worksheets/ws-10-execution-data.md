# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1     |          |      |           |        |       |             |
| 2     |          |      |           |        |       |             |
| 3     |          |      |           |        |       |             |
| ...   |          |      |           |        |       |             |

Jumlah runs per skenario : ____
Total runs               : ____

DATA LOG (per run):
  Run ID    : ____________________
  Timestamp : ____________________
  Skenario  : ____________________
  Input     : ____________________
  Output    : ____________________
  Anomali   : ____________________
  Catatan   : ____________________
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 | Uji Korelasi Kelompok Android | Android OS (Digital Wellbeing) | $N \ge 20$, Retrospektif 30 Hari, $\alpha=0,05$ | Planned |
| 2 | Uji Korelasi Kelompok iOS | iOS (Screen Time) | $N \ge 15$, Retrospektif 30 Hari, $\alpha=0,05$ | Planned |
| 3 | Uji Korelasi Gabungan Total  | All OS (Android + iOS) | $N = 40$, Retrospektif 30 Hari, $\alpha=0,05$ | Planned |


**Total skenario:**3 Skenario Analisis
**Run per skenario:**1 Kali Running Formula Statistik
**Total run keseluruhan:** 3 Kali Run Uji Korelasi

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Responden ID | RESP-IK-001 sampai RESP-IK-040 |
| Timestamp | 2026-06-29 11:24:05 |
| Sistem Operasi | Android / iOS |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Target Parameter | Rata-rata Menit Harian (30 Hari Terakhir) |
| Alat Ukur Fokus | Kuesioner Skala Likert 1-10 (Deep Work) |
| Status Validasi | VALID / ANOMALI |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Skor_Fokus_Belajar (DV)| Integer | 1 – 10 |
| Estimasi_Menit_TikTok (IV - Kondisi A) | Integer | 0 – 1440 Menit |
| Log_Riil_Menit_TikTok (IV - Kondisi B) | Integer | 0 – 1440 Menit |

**Format output:** [X] CSV / [X] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Berkas Rusak / Salah Upload | Responden mengunggah foto blur, screenshot galeri foto, atau salah menu log (bukan rata-rata 30 hari). |Dokumentasikan ID Responden, hubungi via WhatsApp untuk meminta screenshot ulang. Jika tidak merespons dalam 1x24 jam, status diubah menjadi DNF (Data Not Found) dan dianulir dari matriks hitung. |
| Underestimate Bias Ekstrem | Responden menebak durasi TikTok hanya 10 menit (Kondisi A), tetapi di log sistem aslinya tercatat 180 menit (Kondisi B). | Jangan Dihapus. Ini bukan bug, melainkan bukti nyata terjadinya dopamin recall bias. Data ini wajib dipertahankan dan dicatat sebagai temuan utama di Bab 3. |
| Format Input Tidak Sesuai | Responden mengetik teks manual seperti "2 jam" di kolom menit kuesioner. | Lakukan perbaikan manual (data cleaning) di Excel dengan mengonversinya langsung menjadi angka menit murni ("120") berdasarkan validasi gambar bukti fisik. |


**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Ya, pada tugas-tugas kuliah praktikum sebelumnya saya sering menggunakan data sekali ambil (single run) tanpa adanya proses validasi bukti fisik atau pengujian komparatif. Risikonya adalah terjadinya bias data yang sangat tinggi, data rentan rekayasa, dan kesimpulan statistik yang diambil bisa meleset jauh dari realitas objektif di lapangan (falsifikasi tidak disengaja).
**Yang akan dilakukan berbeda:**
> Pada riset ini, saya menerapkan metode pengumpulan paralel (Kondisi A vs Kondisi B) dengan sistem Upload Lock sebagai bentuk pembuktian berlapis (multiple verification). Dengan membandingkan tebakan ingatan langsung dengan data sistem operasi pada 40 responden, tingkat kepercayaan dosen penguji terhadap keaslian dataset saya akan meningkat drastis karena data terbukti bersih, memiliki bukti fisik digital, dan lolos uji anomali secara transparan.
