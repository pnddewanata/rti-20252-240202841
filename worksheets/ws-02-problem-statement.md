# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Human-Computer Interaction (HCI) & Educational Technology
  Konteks  : Proses belajar mandiri mahasiswa Ilmu Komputer UPB di era distraksi digital.

System Context
  Input       : Waktu luang mahasiswa, konten video pendek TikTok, tugas pemrograman (Workshop).
  Process     : Konsumsi konten (scrolling), perpindahan fokus (context switching), pengerjaan tugas.
  Output      : Durasi penggunaan aplikasi (menit), waktu penyelesaian tugas, skor fokus.
  Outcome     :Kualitas pemahaman materi koding dan performa akademik.
  Constraints : Algoritma TikTok yang adiktif, keterbatasan waktu dalam satu hari, deadline tugas.
  Stakeholders: Mahasiswa Ilmu Komputer, Dosen Pengampu, Universitas Putra Bangsa.

Fenomena → Problem
  Fenomena yang diamati             : Mahasiswa sering membuka TikTok saat sela-sela koding/belajar.
  Gejala (symptom) yang terukur     : Tugas Workshop selesai lebih lama dari estimasi; sering terjadi "blank" saat koding.
  Masalah yang didiagnosis          : Penurunan daya fokus (deep work) akibat stimulasi dopamin instan secara terus-menerus.
  Masalah riset (researchable)      :Korelasi antara intensitas penggunaan TikTok (menit/hari) terhadap skor konsentrasi mahasiswa IT saat sesi belajar mandiri.
  Variabel yang terukur             : Durasi Screen Time (menit), Skor Fokus (skala 1-10), jumlah interupsi per sesi.

Problem Quality Check
  [✔] Clarity — Jelas, fokus pada satu aplikasi (TikTok) dan satu kelompok (Mahasiswa Ilmu Komputer Universitas Putra Bangsa).
  [✔] Measurability — Bisa diukur dengan data Screen Time asli.
  [✔] Relevance — Sangat penting karena menyangkut produktivitas mahasiswa IT.
  [✔] Testability — Bisa gagal jika ternyata TikTok tidak berpengaruh (falsifiable).
  [✔] Impact — Memberikan solusi manajemen waktu bagi mahasiswa.

Problem Statement (1 paragraf):
  Penggunaan media sosial TikTok yang masif di kalangan mahasiswa Informatika Universitas Putra 
  Bangsa (UPB) diduga menciptakan pola distraksi digital yang menghambat kemampuan fokus 
  mendalam (deep work). Meskipun memberikan hiburan, stimulasi konten pendek yang terus-menerus 
  berpotensi menurunkan daya konsentrasi saat pengerjaan tugas logika pemrograman yang kompleks. 
  Riset ini bertujuan untuk membuktikan secara kuantitatif apakah durasi penggunaan TikTok yang 
  terekam pada log Screen Time memiliki korelasi negatif terhadap skor fokus belajar mandiri, 
  sebagai dasar untuk merumuskan strategi literasi digital yang lebih efektif bagi mahasiswa.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** ________________________________________

| Tahap | Hasil |
|-------|-------|
| Reality | Mahasiswa sering terdistraksi smartphone saat sedang belajar mandiri. |
| Observed Issue (Symptom) | Waktu pengerjaan tugas Workshop molor dan mahasiswa merasa cepat lelah secara mental. |
| Diagnosed Problem (Root Cause) | Context switching yang terlalu sering antara konten hiburan TikTok dan logika koding. |
| Researchable Problem |Pengaruh durasi harian TikTok terhadap tingkat atensi mahasiswa Informatika UPB. |
| Measurable Variable | Durasi harian (menit), Skor Atensi (skala), dan Frekuensi buka aplikasi.|

**Apakah terjebak solution-first thinking?** [ ] Ya / [✔] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Notifikasi TikTok, durasi waktu luang, tugas pemrograman dari dosen. |
| Process | Aktivitas scrolling video (konsumsi konten) vs Aktivitas berpikir logis (koding). |
| Output | Data statistik waktu layar (Screen Time) dan hasil penilaian tugas (kuantitas). |
| Outcome | Tingkat penguasaan kompetensi Informatika dan indeks fokus mahasiswa. |
| Constraints | Algoritma For You Page (FYP) yang memicu adiksi, batas kuota internet, durasi tidur. |
| Stakeholders | Mahasiswa (objek), Dosen (evaluator), dan Kampus UPB (penjamin mutu). |

**Komponen mana yang paling relevan dengan masalah riset?** Process (Perpindahan atensi dari hiburan ke koding).

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Sangat spesifik menyebut subjek (Mhs IT) dan objek (TikTok). |
| Measurability | 5 | Menggunakan data objektif dari log sistem (Screen Time). |
| Relevance | 5 | Distraksi digital adalah hambatan utama belajar di bidang IT saat ini. |
| Testability | 4 | Bisa diuji dengan analisis korelasi, namun butuh kejujuran responden. |
| Impact | 4 | Bermanfaat untuk memperbaiki pola belajar mahasiswa angkatan 24. |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
> Riset ini mengkaji fenomena penurunan fokus belajar pada mahasiswa Ilmu Komputer Universitas Putra Bangsa (UPB) yang diakibatkan oleh penggunaan aplikasi TikTok secara intensif. Dengan memanfaatkan data log Screen Time dan penilaian mandiri terhadap tingkat konsentrasi, penelitian ini bertujuan untuk mengukur hubungan kausal antara durasi paparan konten video pendek dengan hambatan dalam melakukan deep work saat pengerjaan tugas pemrograman. Hasil riset ini diharapkan dapat menjadi rujukan ilmiah dalam pembentukan kebijakan literasi digital dan manajemen waktu bagi mahasiswa di lingkungan UPB.


---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Perbedaan fundamentalnya terletak pada tujuan akhir. Saat coding, masalah (bug/error) didefinisikan sebagai "sesuatu yang rusak dan harus diperbaiki" agar sistem jalan (solve). Pendekatannya teknis dan solutif. Sedangkan dalam riset, masalah didefinisikan sebagai "celah pengetahuan" (gap) yang harus dipahami dan dibuktikan kebenarannya melalui bukti ilmiah (understand & prove). Jika bug harus dihilangkan, kegagalan dalam hipotesis riset (hasil negatif) tetap dianggap sebagai kontribusi pengetahuan yang valid asalkan prosesnya sistematis.

