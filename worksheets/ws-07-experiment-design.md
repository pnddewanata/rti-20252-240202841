
# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : ____________________
Hypothesis        : ____________________
Tipe Eksperimen   : [ ] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control |           |          |             |
| Treatment |         |          |             |

Fairness Checklist:
  [ ] Dataset identik untuk semua kondisi
  [ ] Preprocessing setara
  [ ] Tuning effort setara
  [ ] Environment identik
  [ ] Metrik evaluasi sama

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    |                 |          |
| External    |                 |          |
| Construct   |                 |          |
| Conclusion  |                 |          |

Statistical Plan:
  Uji statistik   : ____________________
  Justifikasi      : ____________________
  Alpha            : ____________________
  Effect size min  : ____________________
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Bagaimana hubungan korelasi antara intensitas penggunaan TikTok berdasarkan data Log Screen Time terhadap tingkat fokus belajar koding mahasiswa Informatika UPB menggunakan metode analisis korelasi bivariat guna menyempurnakan kelemahan data subjektif pada riset Azizah & Anshori 2025?
**Tipe eksperimen:** [✔] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Mereplikasi model riset terdahulu (baseline dari literatur) yang mengandalkan ingatan untuk menangkap intensitas durasi. | Durasi subjektif (perkiraan menit dari kuesioner responden). | Mahasiswa Informatika UPB, kuesioner fokus berskala Likert 1-10, batas waktu pelaporan yang sama. |
| Treatment | Menerapkan model pengukuran baru yang diusulkan dalam penelitian ini untuk mendapatkan validitas data yang presisi. | Durasi objektif (angka menit riil dari Log Screen Time). | Mahasiswa Informatika UPB, kuesioner fokus berskala Likert 1-10, batas waktu pelaporan yang sama. |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✅ | Subjek penelitian tidak diubah; kelompok mahasiswa Informatika UPB yang sama digunakan untuk mengisi kedua jenis parameter durasi tersebut. |
| Preprocessing setara | ✅ | Aturan penyaringan data aneh (outlier) diberlakukan sama rata, seperti mengeliminasi data jika ada responden yang mengisi skor fokus namun durasi lognya kosong |
| Tuning effort setara | ✅ | Kedua kondisi data diuji menggunakan perangkat lunak analisis statistik yang sama dan diuji pada tingkat kepercayaan (alpha) 0,05 yang identik. |
| Environment identik | ✅ | Proses pengambilan data dilakukan pada rentang minggu kuliah yang sama agar beban tugas praktikum mahasiswa tidak berubah di tengah jalan. |
| Metrik evaluasi sama | ✅ | Instrumen pengukur variabel dependen (DV) pada kedua kondisi tetap mengacu pada instrumen pengukuran ketahanan atensi (Deep Work) yang sama. |

**Ada yang tidak fair?** [ ] Ya / [✔] Tidak
> Jika ya, bagaimana cara memperbaikinya? ________________

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Confounding variables: Mahasiswa merasa hilang fokus bukan karena TikTok, tetapi karena kurang tidur atau kopi yang dikonsumsi sebelum koding. | Menambahkan pertanyaan penapis (screening question) mengenai durasi tidur malam sebelum sesi belajar koding dimulai untuk menyaring data bias. |
| External | Hasil korelasi hanya mencerminkan ekosistem belajar mahasiswa di internal kampus UPB kelas 4IKRA dan tidak mewakili kampus lain. | Mengumpulkan sampel dari beberapa kelas paralel di program studi Informatika UPB agar variasi data dan karakteristik responden lebih luas. |
| Construct | Responden salah memahami definisi "fokus belajar koding", sehingga pengisian skala Likert menjadi asal-asalan. | Menyediakan glosarium singkat dan contoh konkret dari setiap angka skala Likert (1-10) di bagian atas kuesioner sebelum responden mengisi. |
| Conclusion | Data durasi log sistem tidak terdistribusi secara normal, sehingga pemaksaan uji statistik linier bisa menghasilkan kesimpulan keliru. | Melakukan uji normalitas (seperti Shapiro-Wilk) terlebih dahulu. Jika data tidak normal, analisis langsung dialihkan ke uji korelasi non-parametrik Spearman Rank. |

**Ancaman mana yang paling sulit dimitigasi?**Internal Validity (Faktor Pengganggu/Confounding Variables).
**Mengapa?**
> Karena fokus atau konsentrasi manusia bersifat sangat dinamis dan dipengaruhi oleh banyak faktor eksternal psikologis maupun fisik dalam satu waktu (seperti tingkat stres, masalah pribadi, gangguan lingkungan sekitar, hingga kondisi kesehatan fisik). Sangat sulit untuk mengisolasi 100% bahwa penurunan fokus belajar koding murni hanya disebabkan oleh distraksi TikTok tanpa adanya campur tangan dari faktor-faktor tak terduga tersebut.
---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah perbandingan yang dilakukan sudah adil (fair comparison)? (Apakah metode baru tersebut diuji pada dataset yang sama, lingkungan perangkat keras yang setara, dan dengan tingkat optimasi parameter yang adil terhadap metode baseline?)
2. Metrik apa yang digunakan untuk menyatakan bahwa metode tersebut "menang"? (Apakah peningkatan performa tersebut dinilai dari metrik yang relevan dengan masalah nyata, atau jangan-jangan metriknya sengaja dipilih yang hanya menguntungkan metode mereka saja?)
3. Apakah perbedaan hasil performa tersebut signifikan secara statistik? (Apakah klaim keunggulan itu sudah dibuktikan lewat uji signifikansi statistik seperti t-test atau p-value, atau sebenarnya perbedaannya sangat tipis dan masuk dalam kategori margin error kebetulan?)