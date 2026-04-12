# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Muhammad Pandu Dewanata Yaseh Hidayat
Tanggal          : 31 Maret 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: "Angka 95% itu didapatkan dari kondisi yang bagaimana? Apakah diukur saat kondisi ideal atau saat banyak gangguan?"
   - Data yang dibutuhkan untuk verifikasi:Data mentah pengerjaan, jumlah responden (N), dan bagaimana cara peneliti menentukan standar 'akurat' tersebut.

2. Posisi paradigma:
   - Pendekatan: [✔] Positivis  [ ] Interpretivis  [✔] Design Science  [ ] Mixed
   - Alasan: Saya ingin membuktikan hubungan antara durasi TikTok (angka objektif) dengan skor fokus mahasiswa secara statistik. Saya juga menggunakan Design Science karena kuesioner dan cara pengambilan data yang saya rancang adalah instrumen untuk menguji hipotesis saya.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Menganggap semua penggunaan TikTok adalah distraksi, padahal mungkin ada mahasiswa yang menjadikannya selingan agar tidak stres.
   - Sumber bias potensial: Mahasiswa mungkin malu mengakui durasi asli mereka bermain TikTok (Social Desirability Bias).
   - Langkah mitigasi: Meminta bukti screenshot "Screen Time" asli dari smartphone responden, jadi datanya tidak hanya berdasarkan perkiraan atau ingatan.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Screenshot durasi layar dan waktu asli pengerjaan tugas Workshop. Saya tidak akan mengubah data agar hasilnya terlihat signifikan.
   - Batasan yang diakui sejak awal: Riset ini hanya dilakukan pada mahasiswa Ilmu Komputer di Universitas Putra Bangsa (UPB), sehingga hasilnya belum tentu sama untuk mahasiswa jurusan lain.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: Pengaruh Media Sosial terhadap Prestasi Akademik Gen Z
> Penulis (Tahun): Donita Winda Sihite (2025)

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Peneliti menggunakan metode kualitatif dengan pendekatan etnografi untuk menggali pengalaman digital siswa secara mendalam. | Subjectivity Bias: Karena peneliti terlibat langsung sebagai partisipan aktif, ada risiko interpretasi data menjadi terlalu subjektif berdasarkan sudut pandang peneliti saja. |
| Data → Processing | Data yang diperoleh mencakup makna, nilai, dan persepsi yang hidup dalam kelompok yang diteliti | Information Overload: Data kualitatif yang sangat luas dan mendalam  bisa membuat proses penyaringan informasi menjadi sulit, sehingga ada risiko hanya data yang mendukung argumen peneliti yang diproses. |
| Processing → Analysis | Menganalisis tingkat penggunaan (3-6 jam per hari) dan dampaknya terhadap motivasi serta perilaku belajar | Confirmation Bias: Peneliti mungkin cenderung mencari bukti dampak negatif (seperti distraksi) karena intensitas penggunaan yang tinggi. |
| Analysis → Inference |Menyimpulkan bahwa penggunaan berlebihan menimbulkan distraksi dan menurunkan prestasi akademik. | Causal Oversimplification: Penurunan prestasi akademik mungkin dipengaruhi faktor lain di luar media sosial, namun dalam analisis ini fokus utama hanya pada pola penggunaan platform digital. |
| Inference → Knowledge | 
Klaim bahwa pengaruh media sosial sangat bergantung pada pola penggunaan: produktif jika diarahkan, merugikan jika tanpa kontrol. | Idealized Knowledge: Kesimpulan ini bersifat normatif/teoretis ; kenyataannya, kontrol diri Gen Z terhadap notifikasi dan algoritma TikTok/Instagram sangat sulit dilakukan secara konsisten. |

**Distorsi paling besar di tahap:** Reality → Data
**Dua distorsi spesifik yang teridentifikasi:**
1. Sampling Bias (External Validity): Karena menggunakan pendekatan etnografi pada komunitas tertentu, hasil penelitian ini mungkin sangat akurat untuk kelompok tersebut tapi sulit diterapkan secara umum untuk seluruh Gen Z dengan latar belakang budaya atau fasilitas internet yang berbeda.
2. Construct Validity (Measurement): Prestasi akademik diukur melalui nilai angka atau simbol dari guru , namun riset ini tidak membedakan secara spesifik apakah penurunan nilai tersebut murni karena distraksi media sosial atau karena metode pengajaran di kelas yang memang kurang menarik bagi Gen Z yang terbiasa dengan multimedia.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Saya tidak boleh menghapus data cuma karena hasilnya nggak sesuai keinginan. Kalau data itu dihapus tanpa alasan teknis yang jelas, itu namanya memanipulasi hasil riset. |
| Transparansi | Saya harus terbuka menceritakan semua data yang didapat, termasuk data yang aneh tadi. Semua proses dari awal sampai akhir nggak boleh ada yang disembunyiin. |
| Peer review | Dosen atau penguji pasti bakal curiga kalau data saya terlalu "sempurna". Mereka butuh tahu fakta yang sebenarnya biar riset ini bener-bener bisa dipercaya. |

**Keputusan akhir dan justifikasi:**
> Saya akan tetap melaporkan hasil riset dengan menyertakan semua data yang masuk. Jika memang ada data yang sangat aneh (outlier), saya akan tetap menampilkannya tapi memberikan catatan tambahan (penjelasan) di laporan. Alasannya, dalam riset Teknologi Informasi, kejujuran data jauh lebih penting daripada hasil yang terlihat bagus tapi hasil manipulasi.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Dampak Durasi Penggunaan TikTok terhadap Fokus Belajar Mahasiswa Ilmu Komputer Universitas Putra Bangsa (UPB).

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 | 2 | 4 |
| Jenis data yang dikumpulkan | Angka durasi (menit/jam) dan skor skala fokus 1-10. | Cerita atau curhatan mahasiswa soal kenapa mereka suka scrolling TikTok. | Rancangan kuesioner atau sistem pengumpulan data yang valid. |
| Limitasi paradigma | Kurang bisa menjelaskan alasan emosional kenapa mahasiswa kecanduan. | Hasilnya subjektif dan susah dibuktikan pakai statistik. | Terlalu fokus bikin alatnya saja, bukan fenomena sosialnya. |

**Paradigma yang dipilih:** Positivis
**Alasan:** Karena saya ingin membuktikan secara objektif dan terukur apakah benar ada hubungan (korelasi) antara lamanya waktu bermain TikTok dengan menurunnya daya konsentrasi mahasiswa saat mengerjakan tugas. Sesuai dengan pendekatan ini, fenomena TI harus bisa diukur secara nyata melalui data.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sejujurnya, dulu kalau ada angka persen-persenan saya langsung percaya saja. Tapi setelah tahu soal "Research Trust Model", sekarang saya bakal lebih kritis. Pertanyaan saya sekarang adalah: "Gimana cara mereka dapet datanya? Jangan-jangan cuma nanya seingatnya saja (bias) dan bukan data asli dari sistem?" Saya jadi paham kalau data itu bisa menipu kalau proses transformasinya dari kenyataan ke pengetahuan tidak dijaga etikanya.
