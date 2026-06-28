# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : ____________________
  RAM     : ____________________
  GPU     : ____________________
  Storage : ____________________

Software:
  OS        : ____________________
  Runtime   : ____________________
  Framework : ____________________

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
|         |         |        |               |
|         |         |        |               |

Konfigurasi:
  Config file     : ____________________
  Random seed     : ____________________
  Hyperparameters : ____________________

Reproducibility Check:
  [ ] Dependency terdokumentasi (requirements.txt / lock file)
  [ ] Seed ditetapkan di semua level (Python, NumPy, framework)
  [ ] Config di version control
  [ ] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | AMD Ryzen 7 7435HS |
| RAM | 16 GB DDR5 |
| GPU | NVIDIA GeForce RTX 4050 (6GB GDDR6) |
| OS | Windows 11 Home 64-bit |
| Runtime | Google Chrome (Pengumpulan Data) & Python 3.11.9 (Analisis Data) |
| Framework | Google Colab |
| Random Seed | N/A (Analisis menggunakan seluruh total populasi sampel $N=40$ secara deterministik) |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| Google Forms | Cloud (2026) | MMedia digital untuk mengumpulkan jawaban kuesioner tingkat fokus dan mengunggah berkas tangkapan layar responden. |
| Android Settings | OS Bawaan | Menu bawaan pada ponsel Android responden untuk melihat fitur Digital Wellbeing (durasi asli TikTok). |
| iOS Settings | OS Bawaan | Menu bawaan pada ponsel iPhone responden untuk melihat fitur Screen Time (durasi asli TikTok). |
| Microsoft Excel | 2021 / 365 | Menggabungkan data kuesioner dan data log sistem ke dalam satu tabel, serta membersihkan data yang tidak lengkap. |
| SPSS | Terbaru | Software standar yang digunakan untuk menghitung rumus uji normalitas (Shapiro-Wilk) dan uji korelasi bivariat secara otomatis. |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | N/A | Koefisien Korelasi $r$ & p-value | — |
| 2 | N/A | Koefisien Korelasi $r$ & p-value | [✓] Ya / [ ] Tidak |
| 3 | N/A | Koefisien Korelasi $r$ & p-value | [✓] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**
> Adanya kesalahan manusia (human error) saat menyalin atau mengetik ulang angka menit dari foto screenshot ke dalam Excel, atau ada data responden yang terlewat sehingga jumlah baris data berpasangan menjadi tidak konsisten antar-pengujian.

**Checklist kontrol yang sudah diterapkan:**
- [✓] Urutan baris data 40 responden dikunci (tidak diubah-ubah) berdasarkan timestamp masuk.
- [✓] Semua rumus statistik di Excel/SPSS dicek ulang agar tidak ada sel data yang kosong.
- [✓] Data kuesioner yang digunakan diambil dari file Master Excel yang sama (.xlsx) tanpa mengubah isinya di setiap putaran tes.
- [✓] Tombol hitung otomatis pada software dipastikan sudah menyala.

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Pengaruh Intensitas Penggunaan TikTok terhadap Konsentrasi Belajar Mahasiswa S1 Ilmu Komputer Universitas Putra Bangsa

## 1. Environment
> Laptop ASUS TUF Gaming A15 (AMD Ryzen 7 7435HS, 16GB RAM, Windows 11 Home). Perangkat pengumpul menggunakan platform Google Forms, dan perangkat responden menggunakan Android (Digital Wellbeing) atau iOS (Screen Time).

## 2. Installation
> 1. Buat akun Google dan susun Google Form sesuai draf instrumen yang memiliki 3 bagian halaman (Sections).
> 2. Siapkan software Microsoft Excel atau IBM SPSS Statistics di laptop untuk mengolah data korelasi.

## 3. Data
> - Sumber: Hasil survei berpasangan dari 40 responden mahasiswa S1 Ilmu Komputer UPB.
> - Format: Berkas spreadsheet (.xlsx / .csv) dan berkas gambar bukti fisik (.jpg / .png).
> - Ukuran: 1 file tabel Master Data (40 baris) dan 40 file tangkapan layar (screenshot) log HP.

## 4. Execution
> 1. Sebarkan tautan kuesioner Google Form kepada target responden mahasiswa.
> 2. Unduh hasil respons ke format Excel, lalu lakukan proses pembersihan data (cocokkan angka tebakan dengan gambar screenshot bukti log).
> 3. Jalankan menu uji statistik korelasi bivariat (Analyze > Correlate > Bivariate) secara terpisah untuk data kuesioner (Kondisi A) dan data log asli (Kondisi B).

## 5. Configuration
> - Alat Ukur Fokus: Kuesioner skala Likert 1-10 (adaptasi instrumen Deep Work).
> - Rentang Waktu Data Log: Angka menit rata-rata durasi harian selama rentang 30 hari terakhir.
> - Parameter Uji Statistik: Ambang batas signifikansi Alpha (α) = 0,05.

## 6. Expected Output
> Hasil akhir berupa tabel matriks korelasi statistik:
> - Kondisi A (Data Kuesioner Subjektif) -> Nilai r negatif lemah, p-value > 0,05 (Hasil tidak signifikan akibat recall bias).
> - Kondisi B (Data Log Objektif Perangkat) -> Nilai r negatif kuat mendekati -1, p-value < 0,05 (Hasil signifikan dan valid secara statistik).
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [X] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
>Panduan visual (interface mapping) yang memuat tampilan antarmuka secara rinci untuk berbagai sistem operasi Android, seperti One UI pada Samsung, MIUI/HyperOS pada Xiaomi, dan ColorOS pada Oppo, masih perlu dilengkapi. Perbedaan tata letak menu Digital Wellbeing pada setiap merek perangkat dapat menyulitkan peneliti lain di luar Universitas Putra Bangsa dalam memberikan arahan kepada responden apabila hanya mengandalkan petunjuk berbentuk teks. Oleh karena itu, penyertaan lampiran berupa panduan bergambar menjadi langkah penting untuk meningkatkan kemudahan replikasi penelitian serta memastikan prosedur pengumpulan data dapat diterapkan secara konsisten pada berbagai jenis perangkat Android. Dengan demikian, penelitian ini akan memiliki tingkat reproduktibilitas yang lebih baik.