# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : ____________________
Metrik Utama      : ____________________

Tabel Hasil:
| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
|          |                      |                      |   |

Visualisasi yang Direncanakan:
| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
| 1 |             |             |        |
| 2 |             |             |        |

Bias Check:
  [ ] Y-axis mulai dari 0 (atau dijustifikasi)
  [ ] Error bar/CI ditampilkan
  [ ] Semua data disertakan (tidak cherry-picked)
  [ ] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Kondisi B (Log Riil Perangkat) | 168.0 ± 58.4 Menit | 6.2 ± 1.4 | 40 |
| Kondisi A (Estimasi Subjektif) |54.5 ± 25.2 Menit | 6.2 ± 1.4 | 40 |


**Checklist tabel:**
- [X] Self-contained (judul jelas, satuan ada, N tercantum)
- [X] Mean ± std (bukan single number)
- [X] Diurutkan berdasarkan metrik utama
- [X] Format konsisten di semua baris

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Scatter Plot | Memperlihatkan bahwa sebaran titik nilai fokus belajar coding mahasiswa bergerak turun seiring makin besarnya angka menit durasi dari sistem HP. | Sumbu X: Data Angka Asli HP, Sumbu Y: Data Nilai Fokus Belajar |
| 2 | Grouped Bar Chart | Memperlihatkan jurang perbedaan berupa grafik balok tebakan mahasiswa yang jauh lebih pendek dibanding grafik balok angka riil dari sistem HP. | Nilai rata-rata (Mean) serta angka simpangan (Standard Deviasi) dari Kondisi A dan B. |


---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Ya. Karena angka grafik sumbu Y dipotong mulai dari 90%, balok Metode A jadi kelihatan seolah-olah 2 kali lipat lebih tinggi dari Metode B. Padahal selisih aslinya sangat kecil, cuma beda 0.4%. |
| Apakah error bar ditampilkan? | Tidak. Grafik contoh tidak memakai garis batas ketidakpastian (error bar), sehingga menyembunyikan naik-turunnya sebaran variasi data yang asli. |
| Apakah semua kondisi ditampilkan? | Ya. Nama kedua metode tetap ditulis dan ditampilkan, tapi cara membuat skala grafiknya tidak adil dan tidak jujur. |
| Apa solusinya? | Angka sumbu Y grafiknya harus dikembalikan mulai dari angka 0% supaya tinggi baloknya jujur sesuai selisih asli, serta wajib ditambahkan garis error bar di atas baloknya. |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [X] Semua bias check lulus
- [X] Ada yang perlu diperbaiki: Tidak ada. Angka grafik untuk durasi menit dipastikan akan selalu mulai tegak lurus dari angka 0 tanpa dipotong-potong, supaya datanya jujur di mata dosen penguji.

---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Mengapa Keduanya Diperlukan:
Karena keduanya punya fungsi yang saling melengkapi. Tabel sangat bagus untuk menampilkan angka-angka secara tepat, detail, dan teliti yang kita butuhkan untuk membuktikan kebenaran data. Tapi, mata manusia pasti pusing kalau cuma melihat tumpukan angka di tabel. Makanya kita butuh grafik (seperti grafik titik-titik Scatter Plot) untuk mengubah angka rumit tersebut menjadi bentuk gambar, sehingga dosen penguji bisa langsung paham ke mana arah hubungan data kita hanya dalam sekali lihat. 
> Pengalaman Mengenai Grafik Menyesatkan:
Ya, dulu saya pernah tidak sengaja membuat grafik garis yang jarak angka sumbunya diatur otomatis oleh komputer, sehingga garisnya kelihatan menanjak sangat tajam. Hal itu membuat orang salah paham dikira ada lonjakan yang sangat heboh, padahal aslinya perubahannya biasa saja. Sejak saat itu, saya sadar bahwa angka sumbu grafik harus diatur dari nol agar hasilnya jujur dan objektif.
