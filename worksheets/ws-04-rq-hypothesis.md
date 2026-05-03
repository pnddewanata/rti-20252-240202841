# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Riset-riset sebelumnya (seperti Azizah, 2025) hanya menggunakan tebakan responden soal berapa lama mereka main TikTok, padahal ingatan orang sering nggak akurat (recall bias). Selain itu, belum ada penelitian yang fokus ke mahasiswa Ilmu Komputer yang butuh konsentrasi tinggi buat koding.

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [✔] Exploratory
  Formulasi    : Seberapa besar pengaruh durasi main TikTok yang tercatat di HP (Screen Time) terhadap tingkat fokus belajar koding pada mahasiswa Ilmu Komputer UPB?
  Variabel IV  : Durasi penggunaan TikTok (Menit per hari).
  Variabel DV  : Skor fokus belajar mandiri (Skala 1-10).
  Metrik       : Angka korelasi (untuk melihat seberapa kuat hubungannya).
  Dataset      : Data primer dari mahasiswa aktif Ilmu Komputer UPB.
  Baseline     : Hasil riset Azizah & Anshori (2025) yang masih pakai kuesioner ingatan responden.

Quality Check RQ:
  [✔] Variabel spesifik
  [✔] Metrik jelas
  [✔] Baseline ada
  [✔] Konteks disebutkan
  [✔] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui :Hubungan nyata (berdasarkan data asli dari sistem HP) antara main TikTok dan kemampuan fokus mahasiswa IT.
  Jenis kontribusi        : [ ] Improvement  [✔] Comparison  [ ] Novel approach
  Gap yang diisi          : Menutup Data Gap dengan menggunakan data durasi yang lebih objektif/asli.
  
Hypothesis Pair:
  H₀ : Bermain/Scroll TikTok tidak ada hubungannya sama tingkat fokus belajar mahasiswa.
  H₁ : Semakin lama main/scroll TikTok, tingkat fokus belajar mahasiswa bakal semakin turun.
  Threshold              :$p < 0.05$.
  Justifikasi threshold  : Standar umum biar hasil risetnya dianggap sah dan bukan kebetulan saja.

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:**Riset lama hanya bertanya "kira-kira main/scroll TikTok berapa lama?", dan belum meneliti mahasiswa koding yang butuh fokus tinggi. umum, belum menyentuh mahasiswa IT yang butuh fokus tinggi untuk debugging.
**RQ versi pertama (tulis bebas):**
> Apakah waktu yang dihabiskan mahasiswa IT di TikTok mempengaruhi kemampuan mereka untuk fokus saat belajar koding?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya | Analisis korelasi data sistem vs skor fokus. |
| Metrik terukur | Ya | Menit durasi (Screen Time) dan skor skala fokus. |
| Baseline | Ya | Riset Azizah dkk (2025). |
| Dataset/konteks | Ya | Mahasiswa Informatika Universitas Putra Bangsa. |

**Tipe RQ:** [ ] Comparison / [ ] Improvement / [✔] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Bagaimana hubungan antara durasi penggunaan TikTok (berdasarkan data sistem) terhadap tingkat konsentrasi belajar mahasiswa Ilmu Komputer di Universitas Putra Bangsa?
---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Bermain/Scroll TikTok tidak ada hubungannya sama tingkat fokus belajar mahasiswa. |
| H₁ | Semakin lama main/scroll TikTok, tingkat fokus belajar mahasiswa bakal semakin turun. |
| Metrik | Koefisien korelasi ($r$). |
| Threshold | Sig. < 0.05. |
| Justifikasi threshold | Batas aman biar hasil penelitian dianggap akurat secara statistik.. |

**Apakah hipotesis ini falsifiable?** [✔] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Pada saat dihitung menggunakan statistik ternyata nilainya di atas 0.05, berarti dugaan kita (H₁) salah dan kita harus terima H₀.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Seberapa besar pengaruh durasi TikTok ke fokus belajar mahasiswa IT? |
| Variable (IV) | Waktu harian main TikTok (Data sistem). |
| Variable (DV) | Tingkat konsentrasi/fokus belajar. |
| Metric | Menit (untuk durasi) dan Skala 1-10 (untuk fokus). |
| Data source | Bukti Screen Time dan Kuesioner. |
| Analysis method | Uji Korelasi Bivariat. |

**Apakah rantai lengkap?** [✔] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? -

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Analisis Pengaruh Penggunaan Media Sosial TikTok Terhadap Konsentrasi Belajar Mahasiswa (Azizah & Anshori, 2025).
**RQ yang diekstrak:** Apakah main TikTok berpengaruh ke konsentrasi belajar mahasiswa?
**Komponen yang hilang:**Belum menyebutkan metrik yang jelas, nggak ada baseline pembanding, dan nggak nyebutin konteks belajar yang spesifik (misal: koding).