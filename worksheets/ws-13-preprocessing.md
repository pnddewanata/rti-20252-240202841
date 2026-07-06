# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

## Ringkasan Materi

### Data Refinement Pipeline

```
Raw Data → Cleaning → Transformation → Normalization → Processed Data → Analysis Ready
```

Setiap tahap memiliki tujuan berbeda. **Preprocessing bukan langkah teknis biasa** — setiap keputusan preprocessing adalah keputusan riset yang bisa mengubah kesimpulan.

### Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|----------|
| **Consistency** | Metode sama untuk data yang sama |
| **Transparency** | Setiap langkah terdokumentasi |
| **Reproducibility** | Orang lain bisa mengulang dengan hasil sama |
| **Minimal Distortion** | Ubah sesedikit mungkin; jika normalisasi tidak perlu, jangan lakukan |

### Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|---------|--------|
| **Missing values** | | |
| — Listwise deletion | Missing < 5%, random | Data loss |
| — Mean/median imputation | Sedikit missing, dist. normal | Mengurangi variabilitas |
| — Model-based imputation | Banyak missing, pola sistematis | Introduces dependency |
| — Flag & separate | Missing karena alasan substantif | Kompleksitas analisis |
| **Duplikat** | Identifikasi → verifikasi → hapus | False positive (data mirip ≠ duplikat) |
| **Error format** | Standardisasi tipe, encoding | Kehilangan informasi saat konversi |

### Normalisasi — Kapan & Metode Mana

| Metode | Formula | Output | Sensitif Outlier? |
|--------|---------|--------|-------------------|
| Min-max | (x-min)/(max-min) | [0, 1] | Ya |
| Z-score | (x-mean)/std | Unbounded | Lebih robust |
| Robust scaling | (x-median)/IQR | Unbounded | Paling robust |

**Kunci:** Parameter normalisasi harus dihitung dari **training set saja** — bukan seluruh data. Pelanggaran = **data leakage**.

### Data Leakage Prevention

Data leakage terjadi ketika informasi dari test set "bocor" ke preprocessing:
- Normalisasi parameter dari seluruh dataset ← **SALAH**
- Cross-validation dilakukan sebelum split ← **SALAH**
- Feature selection menggunakan label test set ← **SALAH**

### Jebakan Kognitif

1. "Preprocessing cuma teknis — tidak perlu detail" → bisa ubah kesimpulan
2. "Lebih banyak preprocessing = lebih bersih = lebih baik" → over-processing distorsi data
3. "Normalisasi selalu diperlukan" → belum tentu, tergantung metode analisis
4. "Imputation sama untuk semua situasi" → strategi harus sesuai konteks

---

## Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : ____________________
Jumlah data awal  : ____________________

Cleaning:
| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing |             |            |             |
| Duplikat|             |            |             |
| Error   |             |            |             |

Transformation:
| Transformasi | Variabel | Detail | Alasan |
|-------------|----------|--------|--------|
|             |          |        |        |

Normalization:
  Metode    : ____________________
  Alasan    : ____________________
  Parameter : (dihitung dari: training set / seluruh data)

Leakage Check:
  [ ] Parameter normalisasi dari training set saja
  [ ] Tidak ada informasi test set dalam preprocessing
  [ ] Cross-validation dilakukan setelah split

Jumlah data akhir : ____________________
Script tersedia   : [ ] Ya → path: ____ | [ ] Belum
```

---

## Latihan 1 — Cleaning Plan

Periksa dataset Anda (atau dataset contoh) dan dokumentasikan masalah yang ditemukan.

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Format input tidak seragam (ditulis manual) | 3 dari 40 data (7,5%) | Penyuntingan data secara manual (data editing) | Data yang ditulis dalam bentuk teks, seperti "1,5 jam", dikonversi menjadi satuan menit (90 menit) berdasarkan bukti tangkapan layar log penggunaan perangkat sehingga seluruh data memiliki format yang sama. |


**Jumlah data sebelum cleaning:** 40 Data
**Jumlah data setelah cleaning:** 40 Data
**Persentase data yang hilang/berubah:** Sebanyak 7,5% data mengalami penyesuaian format, sedangkan tidak ada data yang dihapus selama proses pembersihan.

---

## Latihan 2 — Normalisasi Decision

Tentukan apakah data Anda perlu normalisasi, dan jika ya, metode apa yang tepat.

| Variabel | Range Asli | Distribusi | Outlier? | Metode Normalisasi | Alasan |
|----------|-----------|-----------|----------|-------------------|--------|
| Durasi penggunaan TikTok | 0–360 menit | Tidak normal (right-skewed) | Ada | Tidak dilakukan | Data sudah menggunakan satuan menit yang seragam. Analisis yang digunakan adalah korelasi Spearman, sehingga tetap dapat mengolah data yang tidak berdistribusi normal tanpa perlu mengubah skala nilainya. | 
| Skor fokus belajar | 1–10 | Normal | Tidak ada | Tidak dilakukan |Nilai sudah berada pada rentang skala yang baku sehingga tidak memerlukan penyesuaian tambahan. |


**Apakah normalisasi diperlukan?** [ ] Ya / [ ] Tidak
**Justifikasi:**
> Normalisasi tidak dilakukan karena penelitian ini menggunakan analisis korelasi untuk melihat hubungan antara durasi penggunaan TikTok dan tingkat fokus belajar. Kedua variabel telah berbentuk data numerik dengan satuan yang jelas sehingga dapat langsung dianalisis. Berbeda dengan algoritma machine learning yang berbasis perhitungan jarak (distance-based algorithm), analisis korelasi tidak mensyaratkan normalisasi. Apabila data tetap dinormalisasi, terdapat kemungkinan nilai asli hasil pengamatan berubah sehingga karakteristik data asli lapangan akan terdistorsi dan kehilangan variabilitas alaminya.

**Leakage check:**
- [X] Tidak relevan karena penelitian ini tidak menggunakan model prediksi maupun pembagian data latih dan data uji.
- [X] Seluruh proses prapengolahan dilakukan pada keseluruhan data karena analisis yang digunakan bersifat statistik konvensional.

---

## Latihan 3 — Preprocessing Report

Buat ringkasan preprocessing lengkap — dokumentasi yang cukup bagi orang lain untuk mereplikasi.

```
PREPROCESSING SUMMARY

1. Dataset: yang digunakan adalah dataset survei komparatif mengenai durasi penggunaan TikTok dan tingkat fokus belajar mahasiswa Universitas Putra Bangsa.
2. Data awal: Terdiri dari 40 responden dengan tiga variabel utama, yaitu skor fokus belajar, estimasi durasi penggunaan TikTok berdasarkan ingatan responden, dan durasi penggunaan berdasarkan log aktivitas perangkat.
3. Cleaning:
   - Missing values:Tidak ditemukan missing value karena seluruh pertanyaan pada Google Form bersifat wajib diisi.
   - Duplikat: Tidak ditemukan data duplikat karena setiap respon dibatasi menggunakan satu akun Google.Ditemukan tiga data dengan format penulisan yang tidak seragam, kemudian disesuaikan menjadi angka dalam satuan menit agar konsisten dengan data lainnya
4. Transformation: dilakukan dengan mengubah data yang semula berbentuk teks menjadi nilai numerik (integer) agar siap dianalisis.
5. Normalisasi: tidak dilakukan karena data sudah sesuai dengan kebutuhan analisis statistik yang digunakan dan tetap dipertahankan dalam bentuk nilai aslinya (raw data).
6. Data akhir:tetap berjumlah 40 responden dengan tiga variabel utama yang siap digunakan pada tahap analisis.
7. Leakage check: dinyatakan lolos karena penelitian ini menggunakan pendekatan statistik konvensional dan tidak melibatkan proses pelatihan model maupun pembagian dataset.
```

---

## Refleksi

> Apakah Anda pernah melakukan normalisasi "karena biasa dilakukan" tanpa mempertimbangkan apakah benar-benar diperlukan? Apa risiko over-preprocessing?

> Ya, saya pernah mengalaminya ketika mengerjakan praktikum pada mata kuliah dasar. Saat itu saya terbiasa melakukan normalisasi hanya karena mengikuti contoh dari berbagai tutorial, tanpa mempertimbangkan apakah langkah tersebut memang diperlukan untuk jenis analisis yang digunakan. Setelah mempelajari lebih lanjut, saya menyadari bahwa setiap metode analisis memiliki kebutuhan yang berbeda.

> Melakukan over-preprocessing dapat menimbulkan beberapa dampak negatif. Data asli yang diperoleh dari lapangan bisa kehilangan karakteristik alaminya, penyebaran data menjadi berubah, dan variasi yang sebenarnya penting justru berkurang. Akibatnya, hasil analisis statistik berpotensi kurang akurat dan tidak lagi mencerminkan kondisi nyata yang dialami oleh responden. Oleh karena itu, setiap tahapan prapengolahan data sebaiknya dilakukan berdasarkan kebutuhan penelitian, bukan sekadar mengikuti kebiasaan atau contoh yang ada.
