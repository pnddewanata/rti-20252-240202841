# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Bagaimana hubungan korelasi antara intensitas penggunaan TikTok berdasarkan data Log Screen Time terhadap tingkat fokus belajar koding mahasiswa Informatika UPB menggunakan metode korelasi bivariat guna menyempurnakan kelemahan data subjektif pada riset Azizah & Anshori 2025?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
|     Intensitas TikTok     | IV   |        Modul Ekstraksi Log Sistem         |           Mengambil durasi penggunaan harian secara presisi dalam satuan menit melalui fitur Digital Wellbeing atau Screen Time.                |
|     Fokus Belajar     | DV   |        Instrumen Penilaian Atensi         |            Pengisian kuesioner self-assessment pasca-aktivitas koding untuk mendapatkan skor konsentrasi (skala 1-10).               |
|    Beban Koding      | CV   |       Modul Filter Profil Responden          |             Membatasi dataset hanya pada mahasiswa yang menempuh mata kuliah praktikum/workshop pada semester berjalan.              |

4 Prinsip Desain:
  [x] Traceability — Tiap data (menit log dan skor kuesioner) punya jalur yang jelas menuju variabel penelitian.
  [x] Variable Isolation — Cara pengambilan durasi TikTok (IV) bisa diubah tanpa mengganggu cara pengukuran fokus (DV).
  [x] Measurement Integration — Pengukuran data durasi sudah menyatu dengan sistem ponsel, bukan lagi tebakan manual.
  [x] Reproducibility — Langkah-langkah pengambilan data bisa dilakukan ulang oleh orang lain dengan prosedur yang sama.

Experimental Setup:
  Input data: Data mentah log aplikasi (menit) dan respon kuesioner koding mahasiswa.
  Parameter: Mahasiswa aktif Prodi Informatika yang terlibat dalam tugas praktikum.
  Output format: Tabel data numerik (format .csv atau .xlsx) yang siap diolah secara statistik
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Research Question: Bagaimana hubungan korelasi antara intensitas penggunaan TikTok berdasarkan data Log Screen Time terhadap tingkat fokus belajar koding mahasiswa Informatika UPB menggunakan metode korelasi bivariat guna menyempurnakan kelemahan data subjektif pada riset Azizah & Anshori 2025?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
|     Intensitas TikTok     | IV   |        Modul Ekstraksi Log Sistem         |           Mengambil durasi penggunaan harian secara presisi dalam satuan menit melalui fitur Digital Wellbeing atau Screen Time.   |
|     Fokus Belajar     | DV   |        Instrumen Penilaian Atensi         |            Pengisian kuesioner self-assessment pasca-aktivitas koding untuk mendapatkan skor konsentrasi (skala 1-10).               |
|    Beban Koding      | CV   |       Modul Filter Profil Responden          |             Membatasi dataset hanya pada mahasiswa yang menempuh mata kuliah praktikum/workshop pada semester berjalan.  | 

**Apakah semua variabel bisa di-map?** [✓] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? _________

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | ✅ | Sangat jelas terlihat; angka menit dari log sistem merepresentasikan variabel intensitas secara konkret. |
| Modularity | ✅ | Modul pengambilan data IV dan DV berdiri sendiri, sehingga salah satu bisa diganti tanpa merusak modul lainnya. |
| Controllability | ✅ | Faktor luar diredam dengan mengunci profil responden (CV) melalui kriteria pemilihan subjek di awal. |
| Measurability | ✅ | Sistem menghasilkan data kuantitatif yang pasti, bukan sekadar perkiraan atau kualitatif biasa. |

**Prinsip mana yang paling sulit dipenuhi?** Controllability.
**Strategi untuk mengatasinya:**
> Melakukan verifikasi ketat pada profil responden saat pengumpulan data untuk memastikan beban tugas mereka benar-benar setara.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅ Log Screen Time | ✅ Spesifik Koding | ✅ Korelasi Bivariat | *Hasil riset yang paling valid dan akurat. |
| – A | ❌ (Ganti Survei) | ✅ | ✅ | Hasil akan bias karena data durasi hanya berdasarkan ingatan responden. |
| – B | ✅ | ❌ (Belajar Umum) | ✅ | |
| – C | ✅ | ✅ | ❌ (Deskriptif) | |

**Komponen mana yang diprediksi paling berkontribusi?** Komponen A (Log Screen Time).
**Mengapa?**
> Karena distorsi terbesar pada riset terdahulu terletak pada ketidakakuratan data durasi. Dengan mengganti metode pengambilan data menjadi log sistem, validitas riset ini meningkat drastis.
---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Risiko utama jika sistem riset dibangun seperti produk (monolitik) adalah kita akan kesulitan menentukan penyebab pasti dari hasil yang ditemukan. Jika sistem terlalu menyatu dan memiliki banyak fitur tambahan, akan muncul banyak "noise" atau variabel pengganggu yang mengaburkan hubungan antara IV dan DV.
> Itulah mengapa arsitektur modular sangat krusial dalam riset. Dengan modul-modul yang terpisah, kita bisa melakukan isolasi variabel—menguji satu faktor sambil memastikan faktor lain tetap konstan. Hal ini membuat penelitian menjadi lebih transparan, akurat, dan yang paling penting, hasilnya bisa diuji kembali oleh peneliti lain dengan tingkat kepercayaan yang tinggi.