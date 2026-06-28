# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [ ] Semua skenario tercakup
  [ ] Jumlah run sesuai rencana
  [ ] Tidak ada file output hilang
  Missing: ____ dari ____ data points

Format Consistency:
  [ ] Semua file format sama (CSV/JSON/...)
  [ ] Header konsisten
  [ ] Tipe data konsisten (numerik tetap numerik)

Range & Logic:
  [ ] Nilai dalam range masuk akal
  [ ] Tidak ada waktu negatif
  [ ] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: ____________________

Cross-Validation:
  [ ] Run identik → hasil mendekati
  [ ] Trend konsisten dengan ekspektasi teori

Keputusan:
  [ ] Data siap analisis
  [ ] Perlu cleaning
  [ ] Perlu re-run (skenario: ____)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| Pengumpulan Data Kelompok Android | 22 |*22 | 0 | Target terpenuhi melalui kuesioner halaman 2. |
| Pengumpulan Data Kelompok iOS | 18 | 18 | 0 | Target terpenuhi melalui kuesioner halaman 3. |
| Pengumpulan Gabungan (Total) | 40 | 40 | 0 | Seluruh responden berhasil divalidasi berkas upload lock-nya. |

**Total expected:** 40 Responden | **Total actual:**40 Responden | **Missing:** 0

**Keputusan untuk data missing:**
> Karena tidak ada data yang missing (seluruh 40 responden mengisi data secara lengkap dan mengunggah berkas bukti log HP dengan benar), dataset master dinyatakan lolos uji kelengkapan (Completeness Check) dan dapat langsung dilanjutkan ke tahap deteksi anomali.
---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset sampel (atau data Anda sendiri):**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | 35.0 |
| 2 | 42.0 |
| 3 | 28.0|
| 4 | 240.0 |
| 5 | 50.0 |

**Deteksi outlier:**
- Q1 =31.5 | Q3 = 95.0 | IQR = 63.5
- Batas bawah (Q1 - 1.5 × IQR) = -63.75
- Batas atas (Q3 + 1.5 × IQR) = 190.25
- Outlier terdeteksi: Run 4 (Nilai 240.0 menit di luar batas atas)

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Run 4 | 240.0 | Responden mengalami Underestimate Bias ekstrem. Di kuesioner ia menebak hanya bermain TikTok selama 30 menit, padahal bukti screenshot log sistem riil mencatat 270 menit harian. | Pertahankan data. Ini bukan eror teknis laptop atau bug Google Form, melainkan bentuk anomali kontekstual yang valid secara ilmiah untuk membuktikan hipotesis adanya bias ingatan manusia (recall bias). |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:**100% data terkumpul (40 dari 40 responden terisi penuh).
**2. Format:** [X] Konsisten / [ ] Ada inkonsistensi: ____
**3. Range check (anomali):**Seluruh data durasi berada pada batas logis harian (0 - 1440 menit) dan data skala fokus berada pada rentang 1 - 10.
**4. Logic check:** [X] Parameter sesuai plan / [ ] Ada ketidaksesuaian: ____

**Kesimpulan:** [X] Data siap analisis / [ ] Perlu tindakan: ____

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Data asli merupakan data yang diisikan langsung oleh responden ke dalam Google Form berdasarkan ingatan atau persepsi pribadi mengenai durasi penggunaan TikTok. Sebagai contoh, seorang responden dapat menuliskan bahwa dirinya hanya menggunakan TikTok selama 15 menit dalam sehari. Data ini menggambarkan persepsi subjektif responden sehingga masih berpotensi dipengaruhi oleh keterbatasan daya ingat maupun bias pelaporan.
>Sebaliknya, data terverifikasi adalah data yang telah melalui proses pembuktian menggunakan bukti digital berupa tangkapan layar (screenshot) riwayat penggunaan aplikasi yang berasal dari fitur bawaan sistem operasi Android maupun iOS. Bukti tersebut dikumpulkan melalui mekanisme Upload Lock, sehingga setiap data yang digunakan dalam penelitian memiliki dasar verifikasi yang jelas. Dengan adanya bukti pendukung tersebut, data terverifikasi memiliki tingkat keandalan, keaslian, dan integritas yang lebih tinggi dibandingkan data yang hanya bersumber dari pengakuan responden.
