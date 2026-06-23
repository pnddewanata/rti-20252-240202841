# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment)
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [ ] Problem → Gap: masalah terdokumentasi di literatur
  [ ] Gap → RQ: pertanyaan menjawab gap spesifik
  [ ] RQ → Hypothesis: hipotesis memprediksi jawaban
  [ ] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [ ] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [ ] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [ ] Istilah sama di semua bagian
  [ ] Variabel di RQ = variabel di hipotesis = metrik di desain
  [ ] Scope tidak berubah dari masalah ke eksperimen

Rubrik Self-Assessment:
| Kriteria | 1 (Lemah) | 2 (Cukup) | 3 (Baik) | Skor |
|----------|-----------|-----------|----------|------|
| Koherensi |          |           |          |      |
| Specificity |        |           |          |      |
| Feasibility |        |           |          |      |
| Rigor     |          |           |          |      |
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Aktivitas belajar koding mahasiswa S1 Ilmu Komputer UPB mengalami penurunan kualitas fokus akibat distraksi video pendek TikTok sehingga proses penyelesaian tugas pemrograman menjadi lebih lambat. Riset terdahulu masih bertumpu pada kuesioner subjektif yang rentan terhadap bias ingatan (recall bias). |
| Gap | WS-03 | Belum adanya pengujian komparatif yang mengevaluasi selisih akurasi statistik antara model estimasi ingatan manusia (subjektif) berbanding data riwayat digital sistem perangkat (objektif) dalam memetakan distraksi aplikasi. |
| RQ | WS-04 | Apakah hubungan antara durasi penggunaan TikTok dan tingkat fokus belajar koding mahasiswa S1 Ilmu Komputer UPB menghasilkan nilai korelasi yang berbeda jika durasi penggunaan diukur menggunakan data estimasi kuesioner dibandingkan dengan data objektif dari Log Screen Time dalam periode 30 hari terakhir? |
| Hipotesis | WS-04 | H1: Analisis korelasi data Log Screen Time (Kondisi B) menghasilkan koefisien korelasi negatif yang lebih kuat (r mendekati-1) dan signifikansi lebih valid (p-value < 0,05$) dibanding data estimasi kuesioner (Kondisi A) akibat eliminasi recall bias. |
| Variabel & Metrik | WS-05 | Penelitian ini menggunakan tingkat akurasi durasi penggunaan TikTok sebagai variabel independen (IV), yang dibandingkan antara data estimasi berdasarkan kuesioner dan data aktual yang diperoleh dari fitur Log Screen Time. Sementara itu, variabel dependen (DV) yang dianalisis adalah tingkat fokus belajar koding, yang diukur menggunakan skala Likert 1–10 berdasarkan konsep Deep Work. Analisis dilakukan dengan menggunakan nilai koefisien korelasi (r) untuk mengukur kekuatan hubungan antarvariabel, p-value dengan tingkat signifikansi α = 0,05 untuk menguji signifikansi statistik, serta rata-rata durasi penggunaan TikTok harian selama 30 hari terakhir sebagai data pendukung dalam pengukuran. |
| Sistem | WS-06 | Instrumen penelitian menggunakan Google Form terintegrasi yang dirancang dalam dua komponen utama. Komponen pertama berupa kuesioner digital untuk mengukur tingkat fokus belajar responden berdasarkan skor atensi yang telah ditetapkan. Komponen kedua berupa fitur unggah bukti yang dilengkapi mekanisme pemetaan visual (visual mapping interface) guna memvalidasi data objektif melalui tangkapan layar fitur Digital Wellbeing atau Screen Time. Integrasi kedua komponen tersebut memungkinkan proses verifikasi antara data yang dilaporkan responden dan data aktual penggunaan aplikasi pada perangkat mereka. |
| Desain Eksperimen | WS-07 | Penelitian ini menerapkan desain studi perbandingan paralel yang dilakukan secara kronologis pada kelompok subjek yang sama, yaitu sebanyak 40 responden. Proses pengumpulan data dilakukan melalui dua kondisi pengujian yang dipisahkan secara berurutan. Pada Kondisi A, responden diminta memperkirakan durasi penggunaan TikTok berdasarkan ingatan mereka tanpa melihat atau membuka ponsel. Selanjutnya, pada Kondisi B, responden diminta mengakses data aktual penggunaan aplikasi yang tercatat pada fitur log perangkat dan mengunggah bukti berupa tangkapan layar sebagai bentuk verifikasi. Data yang diperoleh dari kedua kondisi tersebut kemudian dianalisis untuk mengetahui perbedaan dan hubungan antarvariabel melalui uji normalitas Shapiro-Wilk serta analisis korelasi bivariat. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ | Gap muncul langsung dari kritik terhadap metode riset terdahulu (Azizah & Anshori, 2025) yang masih mengandalkan data kuesioner durasi subjektif yang rentan recall bias. |
| Gap → RQ | ✅ | RQ secara eksplisit menanyakan perbedaan nilai korelasi ketika sumber data durasi diubah dari estimasi subjektif ke data objektif Log Screen Time. |
| RQ → Hypothesis |  ✅  | Hipotesis secara presisi memprediksi arah pergeseran parameter statistik (r negatif lebih kuat mendekati -1 dan p < 0,05) pada pembandingan 30 hari terakhir. |
| Hypothesis → Metric | ✅ | Variabel yang digunakan dalam hipotesis penelitian diukur secara langsung melalui sejumlah indikator kuantitatif yang telah ditetapkan. Pengukuran tersebut meliputi nilai koefisien korelasi (r) untuk menunjukkan kekuatan hubungan antarvariabel, p-value untuk menentukan tingkat signifikansi statistik, skor fokus belajar pada skala 1–10 sebagai representasi tingkat konsentrasi responden, serta rata-rata durasi penggunaan TikTok harian dalam satuan menit berdasarkan data 30 hari terakhir.|
| Metric → System | ✅ | Sistem pengumpulan data terdiri atas dua komponen yang saling terintegrasi. Komponen pertama berupa kuesioner digital yang digunakan untuk mengukur tingkat fokus belajar responden melalui skor atensi yang telah ditetapkan. Komponen kedua berupa fitur Upload Lock yang berfungsi mengumpulkan data durasi penggunaan TikTok secara objektif melalui unggahan tangkapan layar log penggunaan perangkat pada fitur Digital Wellbeing atau Screen Time. Pembagian fungsi tersebut memungkinkan pengukuran masing-masing variabel dilakukan secara terpisah namun tetap dalam satu alur pengumpulan data yang terintegrasi. |
| System → Experiment | ✅ | Pelaksanaan eksperimen dilakukan melalui alur pengisian Google Form yang disusun secara kronologis, yaitu Kondisi A diikuti oleh Kondisi B. Urutan tersebut dirancang sebagai instrumen uji paralel untuk menghasilkan paired dataset pada setiap responden. Melalui desain ini, data estimasi durasi penggunaan yang diperoleh pada tahap pertama dapat dipasangkan dan dibandingkan secara langsung dengan data durasi aktual yang diperoleh dari log perangkat pada tahap kedua, sehingga memungkinkan analisis perbedaan dan hubungan antarvariabel dilakukan secara lebih akurat. |

**Koneksi mana yang paling lemah?** Koneksi Metric → System (khususnya pada potensi terjadinya background idle bias).
**Bagaimana cara memperkuatnya?**
> Untuk meningkatkan kualitas data penelitian, diperlukan standardisasi yang lebih ketat terhadap instruksi operasional yang ditampilkan dalam panduan visual antarmuka (interface mapping) pada Google Form. Standardisasi tersebut bertujuan memastikan responden benar-benar mengambil data durasi penggunaan dari log aktivitas perangkat yang sesuai dengan kriteria penelitian. Selain itu, penelitian ini merekomendasikan penyusunan peta jalan pengembangan tahap ketiga yang diarahkan pada pengembangan sistem pengukuran yang lebih terotomatisasi, peningkatan proses validasi data, serta integrasi mekanisme verifikasi yang mampu mengurangi ketergantungan pada pelaporan mandiri (self-report) responden.

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [X] Ya / [ ] Tidak
> Jika tidak, di bagian mana terjadi inkonsistensi? _________

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Seluruh alur riset mengalir tanpa putus dari rumusan masalah distraksi TikTok hingga rancangan uji statistik komparatif. |
| Specificity | 3 | Seluruh variabel, metrik kuantitatif (r, p-value, α = 0,05), target sampel (N=40), dan nama program studi sudah terdefinisi secara definitif. |
| Feasibility | 3 | Penelitian ini dirancang menggunakan metode pengambilan data retrospektif melalui log penggunaan perangkat yang secara otomatis merekam aktivitas pengguna selama 30 hari terakhir. Pemanfaatan data historis tersebut mengurangi kebutuhan observasi longitudinal yang memakan waktu, sehingga proses pengumpulan data dapat dilakukan dalam waktu relatif singkat. Oleh karena itu, penelitian dinilai memiliki tingkat kelayakan yang tinggi untuk diselesaikan dalam timeline delapan minggu dengan risiko kendala waktu yang minimal. |
| Rigor | 2 | Pengujian statistik sudah ketat menggunakan Shapiro-Wilk dan rencana mitigasi ke Spearman Rank, namun nilai kontrol ruang fisik responden belum bisa diintervensi penuh (background idle bias). |

**Skor total:** 11 / 12

**Apakah proposal siap untuk fase eksekusi?** [X] Ya / [ ] Belum
> Jika belum, apa yang perlu diperbaiki? Proposal sudah siap sepenuhnya karena instrumen pengumpul data (Google Form terintegrasi) dan draf metodologi komparatif telah tervalidasi serta dikunci secara sinkron.__________________

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** Rumusan masalah dan hipotesis penelitian (WS-04) disusun berdasarkan fenomena yang berkembang di kalangan mahasiswa, khususnya terkait menurunnya fokus dalam aktivitas belajar koding yang diduga dipengaruhi oleh paparan konten TikTok melalui algoritma For You Page (FYP). Fenomena tersebut dipandang relevan karena merupakan bagian dari realitas yang sering ditemui dalam kehidupan akademik sehari-hari. Kedekatan antara permasalahan penelitian dan kondisi aktual di lapangan menjadikan topik ini layak untuk dikaji lebih lanjut guna memperoleh pemahaman yang lebih mendalam mengenai hubungan antara intensitas penggunaan TikTok dan tingkat fokus belajar mahasiswa.

**Bagian tersulit:** Mengunci metodologi dan variabel kontrol (WS-05 & WS-07) untuk memastikan aspek fairness. Menghilangkan bias ingatan responden tanpa melanggar batasan waktu riset 8 minggu menuntut pemikiran kritis untuk mengalihkan desain dari observasi langsung (prospective) ke penarikan data riwayat log (retrospective 30 hari terakhir).

**Yang akan dilakukan berbeda:**
> Jika mengulang dari awal, saya akan mendokumentasikan panduan visual interface mapping untuk sistem operasi iOS dan Android secara lebih awal sejak tahap tinjauan pustaka. Langkah ini penting agar struktur fitur upload lock pada instrumen pengumpulan data bisa langsung diuji coba dalam skala kecil (pilot testing) sebelum proposal diajukan ke dosen pengampu.
> _________________________________________________