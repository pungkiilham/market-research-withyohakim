# Master Knowledge Base — Pengujian Kendaraan Bermotor (Uji Kir) Dishub

> **Audience:** Masyarakat umum (pemilik kendaraan wajib uji, sopir, pengusaha angkutan) + chatbot training.
> **Purpose:** Dokumen tunggal yang berisi seluruh pengetahuan yang harus dikuasai chatbot CS Dishub tentang Pengujian Kendaraan Bermotor (PKB) / Uji Kir. Format siap-unggah ke platform Conversa.
> **Bahasa jawaban bot:** Bahasa Indonesia.
> **Ruang lingkup:** Standar nasional (peraturan pusat). Rincian operasional (jam buka, tarif, portal online) **bervariasi per daerah** — bot wajib mengarahkan warga untuk cek Unit Pelaksana Uji Berkala Kendaraan Bermotor (UPUBKB) setempat.

---

## BAGIAN 0 — Persona & Strategi CS Chatbot

### 0.1 Identitas Bot

- **Nama:** Petugas Informasi Pengujian Kendaraan Bermotor (PKB) — Dinas Perhubungan.
- **Peran:** Customer service informasi layanan Uji Kir kepada masyarakat: syarat, berkas, biaya, alur, masa berlaku, sanksi, dan layanan lainnya.
- **Nada bicara:** Ramah, sopan, sabar, bahasa Indonesia formal sehari-hari yang mudah dipahami masyarakat awam. Tidak kaku (tidak "kayak dokumen hukum"), tidak terlalu santai. Menggunakan sapaan "Bapak/Ibu/Saudara/Saudari".

### 0.2 Tujuan Utama Bot

1. Menjawab pertanyaan masyarakat tentang Uji Kir / PKB secara akurat dan lengkap.
2. Mengedukasi pemilik kendaraan wajib uji tentang kewajiban, masa berlaku, dan konsekuensi telat uji.
3. Mengurangi beban kerja petugas loket dengan menangani pertanyaan berulang yang bersifat informatif.
4. Mengarahkan masyarakat yang butuh bantuan spesifik/urgent ke petugas manusia (handoff).

### 0.3 Pedoman Perilaku Inti

- **Grounded pada regulasi:** Jawaban mengacu pada UU No. 22 Tahun 2009, PP No. 55 Tahun 2012, Permenhub PM 19 Tahun 2021, dan KP-DRJD 5201 Tahun 2025 (BLUe Full Cycle). Jangan mengarang aturan baru.
- **Jujur bila tidak tahu:** Jika pertanyaan bersifat spesifik-per-daerah (jam buka, tarif, status kendaraan), bot menjawab dengan aturan umum lalu mengarahkan ke UPUBKB/Dishub setempat.
- **Tidak menanyakan data sensitif:** Bot tidak meminta NIK, nomor STNK, atau data pribadi berlebihan. Tidak pernah meminta biaya transfer/pembayaran.
- **Keselamatan dulu:** Ingatkan bahwa Uji Kir adalah untuk keselamatan jalan dan kelestarian lingkungan, bukan sekadar kewajiban administrasi.
- **Handoff:** Jika warga melaporkan kendala, keberatan hasil uji, atau meminta manusia — segera arahkan ke petugas (handoff).

### 0.4 Istilah yang Harus Dipahami Bot

| Istilah | Arti |
|---|---|
| **Uji Kir / Uji Berkala** | Pengujian kendaraan bermotor secara berkala untuk memastikan kelaikan jalan. Nama resmi: **Pengujian Kendaraan Bermotor (PKB)**. "Kir" dari bahasa Belanda *keur* (uji). |
| **KBWU** | Kendaraan Bermotor Wajib Uji — kendaraan yang wajib melakukan uji berkala. |
| **UPUBKB** | Unit Pelaksana Uji Berkala Kendaraan Bermotor — unit teknis di bawah Dinas Perhubungan yang melaksanakan uji. (Dulu disebut UPTD PKB.) |
| **SRUT** | Sertifikat Registrasi Uji Tipe — dokumen pengesahan tipe kendaraan (asli/e-SRUT). |
| **BLUe** | Bukti Lulus Uji Elektronik — bukti digital lulus uji (kartu uji smartcard + stiker RFID). |
| **SIM PKB / SIM BLUe** | Sistem Informasi Manajemen Pengujian Kendaraan Bermotor — aplikasi pendataan dan penerbitan BLUe, terintegrasi ke pusat data Kemenhub. |
| **BLUe Full Cycle** | Sistem terpadu nasional pengujian berkala (berlaku sejak 2 Januari 2026) dengan SOP seragam nasional. |
| **ODOL** | Over Dimension Over Load — kendaraan kelebihan dimensi/muatan; target pemberantasan nasional. |

---

## BAGIAN 1 — Pengertian & Dasar Hukum

### 1.1 Apa Itu Uji Kir / PKB?

- **Uji Kir** adalah rangkaian pemeriksaan dan pengujian komponen serta bagian kendaraan bermotor untuk memastikan kendaraan **laik jalan** dan memenuhi **persyaratan teknis** serta **kelestarian lingkungan**.
- Nama resmi layanan: **Pengujian Kendaraan Bermotor (PKB)**, dilaksanakan oleh **Dinas Perhubungan** melalui **UPUBKB**.
- Uji dilakukan oleh **penguji** yang memenuhi persyaratan pemerintah.
- Kendaraan yang lulus uji mendapat **Bukti Lulus Uji Elektronik (BLUe)**.

### 1.2 Tujuan Uji Kir (Pasal 2 ayat 2 Permenhub PM 19/2021)

1. Memberikan **jaminan keselamatan secara teknis** terhadap penggunaan kendaraan bermotor wajib uji di jalan.
2. Mendukung **kelestarian lingkungan** dari kemungkinan pencemaran akibat penggunaan kendaraan.
3. Memberikan **pelayanan umum** kepada masyarakat.

### 1.3 Dasar Hukum

| Regulasi | Isi |
|---|---|
| **UU No. 22 Tahun 2009** (Lalu Lintas dan Angkutan Jalan), Pasal 49 & 53 | Kewajiban uji berkala kendaraan bermotor dan kelaikan jalan. |
| **PP No. 55 Tahun 2012** (Kendaraan) | Pengaturan teknis kendaraan dan uji berkala. |
| **Permenhub PM No. 19 Tahun 2021** (Pengujian Berkala Kendaraan Bermotor) | Aturan utama uji berkala; menggantikan Permenhub PM 133/2015. |
| **KP-DRJD No. 5201 Tahun 2025** (Prosedur & Tata Cara Pelaksanaan Pengujian Berkala) | SOP seragam nasional + aplikasi **BLUe Full Cycle**; berlaku **2 Januari 2026**. |
| **UU No. 1 Tahun 2022** (Hubungan Keuangan Pusat dan Daerah) | **Menghapus retribusi** uji berkala — di banyak daerah uji kir menjadi gratis. |
| **UU No. 22 Tahun 2009 + PP No. 55/2012** | Dasar bukti lulus uji berupa Kartu Uji (smartcard) dan Tanda Uji (stiker RFID). |

---

## BAGIAN 2 — Kendaraan Wajib Uji (KBWU)

### 2.1 Kendaraan yang Wajib Uji Berkala (Pasal 3 Permenhub PM 19/2021)

| Jenis | Contoh |
|---|---|
| **Mobil Penumpang Umum** | Angkutan kota (angkot), taksi, mobil travel, angkutan sewa/rental, mobil penumpang ojek online |
| **Mobil Bus** | Bus kecil, bus sedang, bus besar (AKAP/AKDP/pariwisata) |
| **Mobil Barang** | Truk, pick-up pengangkut barang, truk tangki, truk derek, armada logistik |
| **Kereta Gandengan** | Trailer / kontainer |
| **Kereta Tempelan** | Kereta tempel yang ditarik kendaraan |

### 2.2 Kendaraan yang Umumnya TIDAK Wajib

- **Kendaraan pribadi plat hitam** (mobil penumpang pribadi, sepeda motor) **tidak wajib** uji kir — **kecuali** kendaraan tersebut **digunakan untuk kegiatan komersial/angkutan**.
- Kendaraan plat merah (dinas) yang semula bukan wajib uji, wajib uji jika digunakan untuk mengangkut barang.

### 2.3 Prinsip Kewajiban

- Kendaraan wajib uji **wajib diuji sebelum dioperasikan di jalan**.
- Kewajiban melekat pada **pemilik kendaraan**.
- Mengoperasikan kendaraan wajib uji **tanpa uji berkala yang masih berlaku = pelanggaran** (bisa kena tilang / sanksi).

---

## BAGIAN 3 — Jenis Uji & Masa Berlaku

### 3.1 Tiga Jenis Uji Berkala

| Jenis Uji | Kapan | Masa Berlaku |
|---|---|---|
| **Uji Berkala Pendaftaran** | Paling lama **13 hari kerja sejak STNK pertama kali diterbitkan** | **1 tahun** sejak tanggal STNK |
| **Uji Berkala Pertama** | Setelah masa berlaku uji pendaftaran habis (± 1 tahun sejak STNK pertama) | **6 bulan** |
| **Uji Berkala Perpanjangan Masa Berlaku** | Setiap kali masa berlaku habis; dapat didaftarkan **paling cepat 1 bulan sebelum berakhir** | **6 bulan** per kali |

### 3.2 Pola Masa Berlaku (untuk edukasi warga)

- STNK pertama → uji **pendaftaran** (berlaku 1 tahun) → uji **pertama** (berlaku 6 bulan) → uji **perpanjangan** setiap 6 bulan.
- **Ringkasnya:** setelah tahun pertama, kendaraan wajib uji kir **2 kali setahun** (setiap 6 bulan).

### 3.3 Penting: Kendaraan yang Dihapus dari Daftar

- Kendaraan wajib uji yang **tidak melakukan uji berkala selama 2 (dua) kali masa berlaku** akan **dihapus dari daftar KBWU** (Pasal 32 Permenhub PM 19/2021).
- Sebelum dihapus, pemilik mendapat **peringatan tertulis bertahap** (3 tahap, interval ± 30 hari kalender).
- Kendaraan yang sudah dihapus **harus didaftarkan ulang** seperti uji berkala pertama, dengan menunjukkan **SRUT** (Pasal 34).

---

## BAGIAN 4 — Persyaratan & Berkas

> **Catatan:** persyaratan dapat sedikit berbeda antar daerah; berikut adalah standar nasional.

### 4.1 Uji Berkala Pendaftaran (kendaraan baru)

1. Kendaraan dibawa ke tempat uji dalam kondisi siap uji.
2. Fotokopi **KTP** (tunjukkan aslinya).
3. Fotokopi **STNK** (tunjukkan aslinya).
4. **SRUT** asli atau e-SRUT.
5. Fotokopi pengesahan rancang bangun kendaraan bermotor (bila ada).
6. Surat kuasa (jika diwakilkan pihak lain).

### 4.2 Uji Berkala Perpanjangan (paling umum)

1. Kendaraan dibawa ke tempat uji.
2. Fotokopi **KTP** (tunjukkan aslinya).
3. Fotokopi **STNK** (tunjukkan aslinya).
4. **Bukti lulus uji** sebelumnya (BLUe / kartu uji).
5. **SRUT** asli (hanya jika ada perubahan bentuk).
6. **Kartu pengawasan** (khusus angkutan umum).
7. Surat kuasa (jika diwakilkan).

### 4.3 Numpang Uji Masuk (uji di luar daerah domisili)

1. Kendaraan dibawa ke tempat uji.
2. Surat keterangan persetujuan numpang uji dari daerah asal.
3. Fotokopi KTP + STNK (tunjukkan aslinya).
4. Bukti lulus uji sebelumnya / RFID.

### 4.4 Mutasi Uji Masuk (pindah domisili antar daerah)

1. Kendaraan dibawa ke tempat uji.
2. Surat keterangan persetujuan mutasi uji.
3. Fotokopi KTP + STNK (tunjukkan aslinya).
4. **Kartu induk uji berkala** dari daerah asal.
5. Bukti lulus uji sebelumnya / RFID.

### 4.5 Aturan Umum Berkas

- Semua fotokopi **disertai aslinya** untuk diverifikasi.
- Jika diwakilkan, lampirkan **surat kuasa**.
- Untuk kendaraan umum: lampirkan izin trayek / izin operasi.
- Bawa **kendaraan itu sendiri** — uji fisik tidak bisa diwakilkan.

### 4.6 Pendaftaran Online

- Sebagian daerah menyediakan **pendaftaran online** melalui aplikasi/portal SIM PKB daerah (mis. SIBANTER, Ngekir Online, portal resmi Dishub).
- Warga dapat mendaftar dari rumah, mendapat **bukti pendaftaran elektronik**, lalu datang ke UPUBKB membawa kendaraan dan berkas.
- **Bot mengarahkan:** cek portal resmi Dishub daerah masing-masing untuk pendaftaran online.

---

## BAGIAN 5 — Alur & Item Pengujian

### 5.1 Alur Umum di UPUBKB

1. **Pendaftaran** (loket atau online) — berkas diperiksa kelengkapannya.
2. **Pembayaran** (bila daerah masih memungut biaya; banyak daerah kini gratis).
3. **Pemeriksaan fisik** — identitas kendaraan dicocokkan dengan dokumen.
4. **Pengujian teknis** di gedung uji menggunakan alat uji terkalibrasi.
5. **Evaluasi hasil** oleh penyelia penguji → menentukan lulus / tidak lulus.
6. **Penerbitan hasil** → BLUe (jika lulus) atau Berita Acara (jika tidak lulus).

### 5.2 Item Pemeriksaan Pengujian

| Kelompok | Yang Diperiksa |
|---|---|
| **Sistem rem** | Rem utama & rem parkir, efisiensi rem (diuji dengan alat/dinamometer) |
| **Lampu** | Lampu utama dekat/jauh, lampu rem, lampu sein, lampu mundur, lampu plat |
| **Emisi gas buang** | Gas buang kendaraan (smoke tester / uji emisi), ambang batas sesuai standar |
| **Sistem kemudi & suspensi** | Kelonggaran kemudi, kondisi suspensi, **side slip** (selip roda) |
| **Ban** | **Kedalaman alur ban** (tread depth), kondisi ban, tekanan |
| **Kebisingan** | Tingkat kebisingan kendaraan |
| **Dimensi** | Ukuran/dimensi kendaraan sesuai ketentuan (anti-ODOL) |
| **Kelengkapan keselamatan** | Kaca, spion, wiper, sabuk keselamatan, klakson, perlengkapan lainnya |

### 5.3 Uji Ulang (Retest)

- Jika **tidak lulus**, pemilik menerima **Berita Acara Hasil Pengujian** + penjelasan komponen yang harus diperbaiki.
- Perbaikan harus selesai dalam **jangka waktu tertentu** yang ditentukan penguji.
- **Selama masa perbaikan masih berlaku**, kendaraan dapat **uji ulang tanpa pendaftaran ulang dan tanpa pembayaran ulang**.
- Jika masa perbaikan habis → **wajib daftar ulang**.

---

## BAGIAN 6 — Hasil Uji & BLUe

### 6.1 Jika Lulus

- Kendaraan dinyatakan laik jalan → diterbitkan **BLUe (Bukti Lulus Uji Elektronik)**.
- BLUe terdiri dari 2 item:
  1. **Kartu Uji (smartcard)** — dapat dicek dengan NFC, sekaligus alat bukti penindakan.
  2. **Tanda Uji (stiker RFID)** dengan hologram — ditempel di **kaca depan (windshield)** bagian dalam, **tidak bisa dipindahkan** ke kendaraan lain.
- Hasil uji diinput ke **SIM PKB** dan terhubung ke pusat data Kemenhub (BLUe Full Cycle).
- **Kewajiban pemilik:** simpan baik-baik BLUe; bawa kembali saat uji berikutnya (6 bulan kemudian).

### 6.2 Jika Tidak Lulus

- Pemilik mendapat **Berita Acara Hasil Pengujian** (tidak lulus) + daftar perbaikan.
- Lakukan perbaikan, lalu **uji ulang** sesuai masa waktu yang diberikan (lihat §5.3).

### 6.3 BLUe Hilang / Rusak

- Ada layanan **pendaftaran BLUe hilang / rusak** di Dishub setempat.
- Umumnya dilampiri surat kehilangan (untuk hilang) dan dilakukan **tanpa memperpanjang masa berlaku** uji.

### 6.4 BLUe Full Cycle (mulai 2 Januari 2026)

- Standardisasi **SOP seragam nasional** — prosedur uji sama di seluruh Indonesia.
- **Penghapusan PNBP kartu uji smartcard** dan PNBP kalibrasi.
- Integrasi dengan **WIM (Weigh-In-Motion)** dan **ETLE** untuk pemberantasan **ODOL** — kendaraan kelebihan dimensi/muatan terdeteksi otomatis di jalan tol.
- Target nasional: **Indonesia bebas ODOL mulai 1 Januari 2027**.

---

## BAGIAN 7 — Biaya & Pembayaran

### 7.1 Retribusi Dihapus (UU No. 1/2022)

- Berdasarkan **UU No. 1 Tahun 2022** tentang Hubungan Keuangan Pusat dan Daerah, **retribusi uji berkala dihapus**.
- Di banyak daerah (mis. DKI Jakarta, sejumlah kabupaten/kota) **uji kir kini tidak dipungut biaya**.
- **PNBP kartu uji smartcard juga dihapus** dalam penerapan BLUe Full Cycle.

### 7.2 Bervariasi Per Daerah

- Meski retribusi dihapus, **kebijakan pelaksanaan bisa berbeda antar daerah** (beberapa daerah mungkin masih memiliki biaya administrasi/PNBP tertentu).
- **Panduan bot:** "Secara umum uji kir kini gratis sesuai UU 1/2022. Untuk kepastian biaya di daerah Bapak/Ibu, silakan cek UPUBKB / Dinas Perhubungan setempat."
- **Penting:** bot **tidak boleh meminta pembayaran apa pun** dan tidak meminta transfer ke rekening pribadi.

---

## BAGIAN 8 — Layanan Khusus

| Layanan | Penjelasan |
|---|---|
| **Uji berkala pendaftaran** | Uji pertama untuk kendaraan baru (berlaku 1 tahun) |
| **Uji berkala perpanjangan** | Uji rutin tiap 6 bulan |
| **Numpang uji masuk** | Kendaraan berdomisili di luar daerah diuji di daerah lain (atas izin daerah asal) |
| **Numpang uji keluar** | Kendaraan daerah kita diuji di daerah lain |
| **Mutasi uji masuk** | Kendaraan pindah domisili masuk ke daerah kita |
| **Mutasi uji keluar** | Kendaraan pindah domisili keluar dari daerah kita |
| **BLUe rusak / hilang** | Penerbitan ulang BLUe tanpa perpanjang masa berlaku |
| **Pemeriksaan fisik untuk lelang** | Pemeriksaan kendaraan untuk keperluan lelang |

---

## BAGIAN 9 — Kepatuhan, Sanksi & Dukungan

### 9.1 Konsekuensi Tidak Uji Berkala

| Pelanggaran | Konsekuensi |
|---|---|
| Mengoperasikan kendaraan wajib uji tanpa uji berkala yang berlaku | Sanksi sesuai ketentuan LLAJ (tilang/pidana ringan) + kendaraan dianggap tidak laik |
| Telat melakukan perpanjangan uji | Denda/administrasi keterlambatan (kebijakan daerah) |
| Tidak uji selama **2× masa berlaku** | **Dihapus dari daftar KBWU** setelah 3 peringatan tertulis; harus daftar ulang seperti uji baru dengan SRUT |
| **ODOL** (kelebihan dimensi/muatan) | Deteksi WIM → penindakan ETLE (tilang elektronik); menuju bebas ODOL 2027 |

### 9.2 Mengapa Uji Kir Penting (edukasi)

- Menjamin keselamatan pengemudi, penumpang, dan pengguna jalan lain.
- Mencegah kecelakaan akibat kendaraan tidak laik jalan (mis. rem blong, ban gundul).
- Mengurangi pencemaran udara melalui uji emisi.
- Menghindari sanksi/tilang di jalan.

### 9.3 Jam Operasional & Kontak

- **Jam operasional bervariasi per daerah.** Contoh umum: Senin–Kamis 07.00–13.00, Jumat 07.00–11.00. **Cek UPUBKB setempat.**
- Kontak: nomor layanan / WhatsApp / portal resmi Dinas Perhubungan masing-masing daerah.
- **Bot mengarahkan** ke kontak resmi daerah — tidak boleh memberi nomor palsu.

### 9.4 Handoff ke Petugas Manusia

Bot harus segera **menghubungkan ke petugas (handoff)** ketika warga:
- Menanyakan **status/data kendaraan** tertentu yang butuh pengecekan sistem.
- **Keberatan hasil uji** / tidak lulus padahal merasa sudah diperbaiki.
- Melaporkan **kendala pendaftaran online**, kesalahan data, atau dugaan **praktik calo**.
- Meminta berbicara dengan **petugas/manusia**.

---

## BAGIAN 10 — FAQ Ringkas (ringkasan untuk bot)

> FAQ lengkap tersedia di file terpisah: `pkb-faq-masyarakat.md`. Bagian ini ringkasan inti.

| Pertanyaan | Jawaban Ringkas |
|---|---|
| Apa itu uji kir? | Pengujian kendaraan bermotor berkala untuk memastikan kendaraan laik jalan (keselamatan teknis + lingkungan). Nama resmi: PKB, dilaksanakan Dinas Perhubungan. |
| Kendaraan apa yang wajib uji kir? | Mobil penumpang umum, bus, mobil barang (truk/pick-up), kereta gandengan & tempelan. Pribadi plat hitam umumnya tidak, kecuali dipakai komersial. |
| Berapa kali uji kir dalam setahun? | Setelah tahun pertama, wajib **2 kali setahun** (tiap 6 bulan). |
| Berapa biaya uji kir? | Retribusi dihapus (UU 1/2022) — di banyak daerah **gratis**. Cek UPUBKB setempat untuk kepastian. |
| Apa saja yang diperiksa? | Rem, lampu, emisi, kemudi & suspensi, alur ban, kebisingan, dimensi, kelengkapan keselamatan. |
| Bagaimana kalau tidak lulus? | Dapat Berita Acara, perbaiki, lalu **uji ulang gratis** selama masa perbaikan masih berlaku. |
| BLUe itu apa? | Bukti Lulus Uji Elektronik — kartu uji smartcard + stiker RFID. |
| Kalau tidak uji kir, apa sanksinya? | Tilang di jalan; jika 2× masa berlaku tidak diuji, kendaraan dihapus dari daftar KBWU. |
