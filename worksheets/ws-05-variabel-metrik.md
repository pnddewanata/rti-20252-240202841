# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question:Seberapa besar hubungan antara durasi bermain/scroll TikTok (berdasarkan data asli HP) dengan tingkat fokus belajar koding pada mahasiswa Ilmu Komputer UPB?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| Durasi TikTok | IV   | Konsumsi hiburan digital. | Menit penggunaan harian rata-rata. |   Ratio   |   Menit   |  Cek log Screen Time / Digital Wellbeing (7 hari terakhir).  | Pakai data sistem biar hasilnya jujur, nggak cuma tebak-tebakan responden. |
| Fokus Belajar | DV | Kemampuan konsentrasi kognitif. | Skor fokus mandiri. |   Ordinal | Skala (1-10) | Kuesioner self-assessment (Skala Likert). | Paling pas buat menangkap perasaan mahasiswa pas lagi belajar. |
| Beban Koding  | CV | Tekanan tugas teknis. | Jumlah SKS praktikum. | Ratio |  SKS | Pendataan jumlah mata kuliah Workshop semester berjalan. | Biar adil, karena anak yang tugas kodingnya banyak pasti pola fokusnya beda.|

Alignment Check:
  RQ (Korelasi) → Concept (Atensi) → Variable (Fokus) → Metric (Skala 1-10) → Data (Ordinal) → Result (Hasil Korelasi)
  [X] Setiap langkah terdokumentasi
  [X] Tidak ada "lompatan logis"
  [X] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Bagaimana hubungan antara durasi penggunaan TikTok (berdasarkan data sistem) terhadap tingkat konsentrasi belajar mahasiswa Ilmu Komputer di Universitas Putra Bangsa?
| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Fokus Belajar | IV | Konsumsi hiburan digital. | Menit penggunaan harian rata-rata. | Ratio | Menit |
| Fokus Belajar | DV | Kemampuan konsentrasi kognitif. | Skor fokus mandiri. | Ordinal | Skala (1-10) |
| Beban Koding  | CV | Tekanan tugas teknis. | Jumlah SKS praktikum. |  Ratio |  SKS |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [X] Tidak
> Jika ya, di mana? ____________________________________

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | Skala fokus sangat mewakili perasaan mahasiswa apakah mereka merasa terganggu atau tidak saat sedang koding atau belajar mandiri. |
| Sensitive | 4 | Rentang skala 1-10 cukup adil untuk membedakan level konsentrasi setiap orang, daripada hanya pakai pilihan "Ya/Tidak". |
| Feasible | 5 | Sangat mudah untuk dikumpulkan karena responden hanya perlu mengisi kuesioner singkat di Google Form. |

**Apakah perlu secondary metric?** [✔] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Perlu metrik tambahan berupa "Jumlah Interupsi" (berapa kali mengecek HP saat belajar). Hal ini penting untuk memvalidasi apakah skor fokus yang mereka isi di kuesioner sesuai dengan kenyataan di lapangan.

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika pilihan jawaban maksimal di kuesioner hanya "Bisa fokus selama 30 menit", padahal rata-rata mahasiswa IT di UPB sanggup fokus koding hingga 2 jam. Akibatnya, semua data akan menumpuk di angka maksimal (30 menit) dan kita tidak bisa melihat siapa yang sebenarnya punya ketahanan fokus lebih tinggi.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul? | Ada risiko responden lupa melampirkan bukti screenshot penggunaan TikTok. | Mengaktifkan fitur "Wajib Isi" (required) dan fitur unggah file pada Google Form agar responden tidak bisa mengirim data sebelum bukti terlampir. |
| Consistency | Apakah ada kontradiksi internal dalam data? | Mungkin ada responden yang mengaku jarang membuka TikTok, tapi bukti Screen Time-nya menunjukkan durasi sangat tinggi. | Melakukan pembersihan data (data cleaning) secara manual dengan membuang jawaban yang tidak sinkron antara teks kuesioner dan bukti foto. |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Penggunaan log Screen Time dari sistem HP adalah cara paling sah untuk mengukur durasi aplikasi secara nyata. | Menyertakan gambar tutorial singkat di kuesioner tentang cara mengambil screenshot fitur Digital Wellbeing atau Screen Time yang benar. |
| Representativeness | Apakah sampel mewakili populasi target? | Ada kekhawatiran data hanya terkumpul dari satu kelas atau satu angkatan saja (misalnya kelas 4IKRA saja). | Mendistribusikan link kuesioner secara merata melalui ketua tingkat atau grup WhatsApp resmi setiap angkatan (Informatika angkatan 2024 dan 2025) di UPB. |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik hanya setelah kita melihat hasil data dianggap sebagai p-hacking karena tindakan tersebut merupakan bentuk manipulasi ilmiah. Peneliti cenderung hanya mengambil metrik yang memberikan hasil signifikan atau yang mendukung hipotesis awalnya saja, sementara metrik yang hasilnya tidak sesuai disembunyikan atau dibuang. Hal ini jelas merusak integritas dan objektivitas sebuah penelitian karena kesimpulan yang diambil tidak lagi murni dari fakta yang ada.
> Perbedaannya dengan eksplorasi data yang sah terletak pada tujuannya. Eksplorasi data dilakukan untuk mencari wawasan baru, pola yang tidak terduga, atau anomali menarik di luar hipotesis utama. Namun, dalam eksplorasi yang benar, hasil temuan tersebut harus dilaporkan secara transparan sebagai "temuan tambahan" atau saran untuk penelitian masa depan, bukan digunakan sebagai alat untuk memaksakan pembenaran atas hipotesis utama yang sudah ditetapkan sejak awal desain riset.