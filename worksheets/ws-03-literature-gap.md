# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Dampak Durasi TikTok terhadap Fokus Belajar Mahasiswa.
Database   : Google Scholar, Jurnal Terakreditasi (Jasima, Risoma, Jupendir).
Query      : "TikTok" AND "fokus belajar" AND "mahasiswa"
Tahun      : 2025
Hasil awal : 7 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Azizah & Anshori | 2025 | Survei & Wawancara |  Mhs Sosiologi UINSA |  Ada pengaruh signifikan terhadap fokus dan produktivitas. |  Fokus pada rumpun sosial; data durasi bersifat kualitatif. |
| Helen Aubryla | 2025 | Kuantitatif (Korelasi) | Siswa MTs Zainul Hasan |    Penggunaan TikTok berpengaruh pada konsentrasi belajar.| Subjek adalah siswa sekolah menengah, bukan mahasiswa IT. |
| Anggi Mailinda | 2025 | Kuantitatif | Siswa SDN 007 Teratak | Tidak ada pengaruh signifikan terhadap hasil belajar. | Konteks pendidikan dasar; instrumen tidak mengukur durasi aktif. |
| Romansyah, dkk. | 2025 | Kuantitatif (SEM) | Mahasiswa UNM | Intensitas TikTok berpengaruh pada produktivitas via motivasi. | Fokus pada manajemen dan ekonomi; data durasi berbasis persepsi. |
| Lestari & Setiawan | 2025 | Eksperimen  Siswa MAN Kota Blitar | TikTok mempengaruhi motivasi belajar secara signifikan, | Metode eksperimen pada subjek remaja sekolah. |

Pola yang ditemukan:
  Metode dominan     : Mayoritas menggunakan pendekatan kuantitatif dengan teknik pengumpulan data kuesioner.
  Dataset umum       : Penelitian banyak dilakukan pada siswa sekolah (SD/MTs/MAN) atau mahasiswa rumpun Ilmu Sosial.
  Limitasi berulang  : Semua riset masih mengandalkan jawaban responden (self-report) untuk menentukan intensitas, bukan data log sistem.

GAP IDENTIFICATION

Gap 1: [Jenis: performance / method / data / context]
  Deskripsi    : Kebanyakan studi yang sudah ada masih memakai kuesioner ingatan responden untuk menghitung durasi main TikTok. Cara ini rawan kena recall bias atau ketidakakuratan data karena responden cuma mengira-ngira.
  Bukti        : Paper Azizah & Anshori (2025) dan Romansyah dkk. (2025) hanya menggunakan survei/kuesioner mandiri tanpa validasi data sistem.
  Signifikansi : Riset ini menggunakan data Log Screen Time asli dari perangkat responden, sehingga hubungan antara durasi penggunaan aplikasi dan tingkat fokus dapat diukur dengan jauh lebih presisi secara kuantitatif.

Gap 2: [Jenis: Context Gap]
  Deskripsi    : Kurangnya studi literatur yang menguji dampak distraksi TikTok secara spesifik pada aktivitas belajar teknis yang membutuhkan konsentrasi mendalam (Deep Work), seperti pemrograman.
  Bukti        : Paper Helen Aubryla (2025) dan Lestari & Setiawan (2025) berfokus pada siswa sekolah menengah (MTs/MAN), sedangkan Anggi Mailinda (2025) pada pendidikan dasar. Belum ada yang menyasar mahasiswa Ilmu Komputer.
  Signifikansi : Mahasiswa Ilmu Komputer memiliki beban kognitif yang berbeda (logika koding). Menemukan dampak distraksi pada konteks ini penting untuk membantu mahasiswa IT membangun pola kerja digital yang lebih produktif.

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
| Riset Azizah & Anshori (2025) | Meneliti dampak TikTok terhadap fokus belajar mahasiswa. | Mewakili tren riset terbaru (2025) di tingkat universitas. | Jurnal Jasima (2025) |
| Riset Romansyah, dkk. (2025) | Mengukur produktivitas mahasiswa yang dipengaruhi intensitas TikTok. | Mewakili metode kuantitatif yang mengaitkan intensitas aplikasi dengan kinerja. | Jurnal Rumpun Manajemen & Ekonomi (2025) |
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Dampak Durasi Penggunaan TikTok terhadap Fokus Belajar Mahasiswa Ilmu Komputer Universitas Putra Bangsa (UPB).
**Query pencarian:** TikTok" AND "fokus belajar" AND "mahasiswa" AND "intensitas"
**Database:** Google Scholar, Jurnal Jasima, Jupendir, JRME, dan Risoma.

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Azizah & Anshori | 2025 | Survei & Wawancara | Mahasiswa Sosiologi UINSA | *AAda pengaruh penggunaan TikTok terhadap penurunan fokus belajar. | Data durasi bersifat subjektif (persepsi) dan subjek bukan anak IT. |
| 2 | Helen Aubryla | 2025 | Kuantitatif Korelasional | Siswa MTs Zainul Hasan | Intensitas TikTok berpengaruh pada konsentrasi belajar siswa. |Subjek penelitian adalah siswa sekolah menengah, bukan mahasiswa. |
| 3 | Anggi Mailinda | 2025 | Kuantitatif | Siswa SDN 007 Teratak | Tidak ditemukan pengaruh signifikan terhadap hasil belajar. | Hanya mengukur nilai akhir (hasil), bukan proses atensi saat belajar. |
| 4 | Romansyah, dkk. | 2025 | Kuantitatif (SEM) | Mahasiswa UNM | Intensitas TikTok memengaruhi produktivitas melalui motivasi. | Fokus pada sisi manajemen dan hanya menggunakan kuesioner ingatan. |
| 5 | Lestari & Setiawan | 2025 | Eksperimen Kuantitatif | Siswa Kelas X MAN Kota Blitar | TikTok memiliki pengaruh signifikan terhadap motivasi belajar. | Belum menguji dampak pada aktivitas teknis seperti pemrograman. |

**Pola yang terlihat — Metode dominan:** Hampir semua penelitian menggunakan pendekatan Kuantitatif Korelasional dengan teknik pengumpulan data utama berupa kuesioner atau angket yang disebarkan kepada responden.
**Limitasi yang berulang:** Kekurangan yang paling menonjol adalah instrumen pengukur "durasi" atau "intensitas" masih mengandalkan ingatan responden (self-report) yang rawan tidak akurat (recall bias). Selain itu, belum ada riset yang menyasar subjek mahasiswa Ilmu Komputer yang memiliki beban kerja kognitif spesifik seperti koding.

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ ] Ya / [✔] Tidak| *Sejauh ini belum ditemukan penurunan hasil belajar yang drastis secara angka (Anggi Mailinda, 2025), namun penurunan kualitas fokus mulai terdeteksi secara kualitatif. |
| Method Gap | [✔] Ya / [ ] Tidak | Riset yang ada umumnya menggunakan survei atau Structural Equation Modeling (SEM) berbasis persepsi. Belum ada yang menghubungkan data log sistem secara langsung dengan skor konsentrasi. |
| Data Gap | [✔] Ya / [ ] Tidak | Penelitian sebelumnya (Azizah, Romansyah, dkk) mengandalkan ingatan responden (self-report) terkait durasi TikTok, bukan data objektif dari log Screen Time perangkat. |
| Context Gap | [✔] Ya / [ ] Tidak | Studi yang tersedia (Helen, Lestari, Anggi) lebih banyak fokus pada siswa sekolah (SD/MTs/MAN) atau mahasiswa sosial, bukan mahasiswa Ilmu Komputer yang butuh fokus tinggi untuk koding. |

**Gap utama yang dipilih:** Data Gap dan Context Gap.
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Masalah utama dalam riset perilaku digital saat ini adalah akurasi data. Jika durasi penggunaan TikTok hanya diukur berdasarkan perkiraan responden, hasilnya cenderung bias karena orang sering tidak sadar berapa lama mereka telah melakukan scrolling. Selain itu, pengerjaan tugas di bidang Ilmu Komputer membutuhkan fase Deep Work yang sangat sensitif terhadap gangguan. Membuktikan dampak ini dengan data sistem yang nyata pada mahasiswa IT akan memberikan dasar yang jauh lebih kuat untuk menyusun strategi manajemen waktu belajar di lingkungan kampus.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | Riset Azizah & Anshori (2025) | Meneliti variabel yang sama secara spesifik, yaitu dampak TikTok terhadap fokus belajar mahasiswa. | *Mewakili tren riset terbaru (2025) yang dilakukan di tingkat universitas. | Ya, karena terbitan tahun berjalan (2025). | Innabella Q. Azizah (Jurnal Jasima) |
| 2 | Riset Romansyah, dkk. (2025) | Menghubungkan intensitas penggunaan TikTok dengan produktivitas belajar mahasiswa. | Mewakili metode kuantitatif (SEM) yang umum digunakan untuk mengukur kinerja akademik mahasiswa. | Ya, merupakan literatur terbaru tahun 2025. | Romansyah S. (Jurnal JRME) |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [ ] Tidak
> Justifikasi: emilihan kedua baseline ini bukan bertujuan untuk mencari lawan yang lemah. Sebaliknya, kedua riset tersebut adalah penelitian terbaru (State-of-the-Art) tahun 2025 yang memiliki metodologi kuat di bidangnya. Saya menjadikannya pembanding karena riset saya ingin meningkatkan akurasi dari sisi instrumen data (menggunakan log sistem/Screen Time) yang menjadi keterbatasan pada kedua penelitian tersebut.
---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Perbedaan mendasar terletak pada landasan buktinya. Klaim "belum ada yang meneliti" sering kali hanyalah asumsi sepihak karena kita gagal menemukan jurnal yang relevan saat pencarian cepat. Sebaliknya, research gap yang valid adalah pernyataan yang didasarkan pada hasil pemetaan literatur (literature mapping) yang sistematis. Kita tidak mengatakan topik tersebut "kosong", melainkan menunjukkan bahwa riset-riset sebelumnya memiliki batasan (limitation), seperti metode yang kurang akurat, subjek yang tidak spesifik, atau instrumen data yang masih bersifat subjektif.
> Cara membuktikan bahwa sebuah gap benar-benar ada adalah dengan menyusun Matriks Literatur. Di dalam matriks tersebut, kita membedah karya peneliti lain dan menunjukkan secara eksplisit letak "celahnya"—misalnya dengan membandingkan bahwa riset terdahulu hanya menggunakan kuesioner (seperti pada jurnal Azizah atau Romansyah), sementara riset kita masuk ke aspek yang belum tersentuh, yaitu penggunaan data log sistem (Screen Time) pada konteks mahasiswa Ilmu Komputer. Dengan menunjukkan bukti perbandingan tersebut, gap riset kita menjadi sah secara ilmiah dan bukan sekadar klaim kosong.