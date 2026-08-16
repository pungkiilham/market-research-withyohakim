# Chatbot Demo Script — 15 Menit untuk Dishub (Pengujian Kendaraan Bermotor / Uji Kir)

> **Purpose:** Skenario demo live untuk meyakinkan Dinas Perhubungan agar memakai Conversa sebagai customer service AI untuk layanan Pengujian Kendaraan Bermotor (Uji Kir). Kepala Dishub/UPUBKB yang mengetik sendiri pertanyaan-pertanyaan masyarakat; bot menjawab dari knowledge base yang sudah dilatih dengan aturan dan data PKB.
> **Filosofi demo:** "Ini dilatih dari aturan dan SOP uji kir. Coba tanyakan apa saja yang sering ditanyakan masyarakat." Biarkan bot yang berbicara — Conversa adalah buktinya. Anda yang memandu dan menutup.

---

## Persiapan (Sebelum Panggilan)

- [ ] Widget terpasang di halaman demo bermerek Dishub/PKB (atau Playground konsol).
- [ ] Persona: "Petugas Informasi PKB — Dinas Perhubungan" (lihat `pkb-master-knowledge-base.md` Bagian 0).
- [ ] Knowledge sources terunggah: `pkb-master-knowledge-base.md` + `pkb-faq-masyarakat.md`.
- [ ] Handoff ke manusia dikonfigurasi (inbox agen terbuka di sisi Anda) untuk demo eskalasi.
- [ ] Layar siap: widget di satu tab browser, konsol/analitik di tab lain.

---

## Babak 1 — Perkenalan Produk & What Is Uji Kir (0:00–2:30)

**Anda katakan:** *"Ini Conversa, dilatih penuh dengan aturan dan SOP uji kir dari Kementerian Perhubungan. Silakan tanya apa saja yang biasa ditanyakan masyarakat soal uji kir."*

**Contoh prompt untuk Kepala Dishub:**
1. **"Apa itu uji kir?"**
   → Jawaban yang diharapkan: pengujian kendaraan bermotor berkala untuk memastikan kendaraan laik jalan (keselamatan teknis + lingkungan), dilaksanakan Dinas Perhubungan/UPUBKB.
2. **"Kendaraan apa saja yang wajib uji kir?"**
   → Jawaban yang diharapkan: mobil penumpang umum, bus, mobil barang, kereta gandengan & tempelan; pribadi plat hitam tidak, kecuali dipakai komersial.

**Sorotan:** Jawaban bersumber dari dokumen resmi — bukan skrip. Tunjukkan **sitation/sumber** yang ditampilkan bot (merujuk ke dokumen KB).

---

## Babak 2 — Prosedur & Syarat (2:30–6:00)

**Anda katakan:** *"Sekarang mari lihat pertanyaan-pertanyaan masyarakat yang paling sering masuk ke loket."*

**Contoh prompt:**
1. **"Syarat perpanjangan uji kir apa saja?"**
   → Jawaban yang diharapkan: bawa kendaraan, fotokopi KTP + STNK + aslinya, bukti lulus uji sebelumnya, SRUT jika ada perubahan bentuk, kartu pengawasan untuk angkutan umum, surat kuasa jika diwakilkan.
2. **"Berapa biaya uji kir?"**
   → Jawaban yang diharapkan: retribusi sudah dihapus (UU 1/2022), di banyak daerah gratis; untuk kepastian cek UPUBKB setempat.
3. **"Berapa lama masa berlaku uji kir?"**
   → Jawaban yang diharapkan: uji pendaftaran 1 tahun, lalu 6 bulan; jadi 2× setahun setelah tahun pertama.

**Sorotan:** Bot paham **logika alur** (syarat → uji → BLUe → perpanjangan), bukan sekadar kata kunci. Coba ingatan lintas sesi: buka sesi baru lalu tanya *"kalau saya punya angkot, kapan harus uji lagi?"* — bot tetap menjawab konsisten.

---

## Babak 3 — Kepatuhan & Sanksi (6:00–9:00)

**Anda katakan:** *"Ini bagian yang sering bikin masyarakat telat — soal konsekuensi."*

**Contoh prompt:**
1. **"Kalau telat uji kir, dendanya berapa?"**
   → Jawaban yang diharapkan: sanksi administrasi/denda sesuai kebijakan daerah; kendaraan dianggap tidak laik dan berisiko kena tilang.
2. **"Kalau tidak uji kir selama 2 kali, apa yang terjadi?"**
   → Jawaban yang diharapkan: dihapus dari daftar kendaraan wajib uji (setelah peringatan tertulis), harus didaftarkan ulang seperti kendaraan baru dengan SRUT.
3. **"Bagaimana kalau tidak lulus uji?"**
   → Jawaban yang diharapkan: dapat Berita Acara, perbaiki, uji ulang tanpa biaya selama masa perbaikan masih berlaku.

**Sorotan:** Bot mengedukasi masyarakat agar patuh, mengurangi pertanyaan berulang di loket, dan membantu menaikkan kepatuhan uji berkala (tingkat kepatuhan nasional masih rendah ~37% di 2024).

---

## Babak 4 — Layanan Khusus & Praktis (9:00–11:00)

**Anda katakan:** *"Layanan uji kir tidak hanya perpanjangan — banyak yang perlu dijelaskan ke masyarakat."*

**Contoh prompt:**
1. **"Kendaraan saya pindah domisili, bagaimana?"**
   → Jawaban yang diharapkan: lakukan mutasi uji masuk di daerah baru.
2. **"BLUe saya hilang, bisa diganti?"**
   → Jawaban yang diharapkan: ada layanan penggantian BLUe hilang/rusak di Dishub setempat.
3. **"Bisa daftar uji kir online?"**
   → Jawaban yang diharapkan: banyak daerah punya pendaftaran online via SIM PKB/portal Dishub; cek portal resmi daerah.

**Sorotan:** Bot menangani berbagai jenis layanan — bukan cuma jawaban tunggal. Ini mengurangi beban petugas loket untuk pertanyaan berulang.

---

## Babak 5 — Human Handoff (11:00–12:00)

**Anda katakan:** *"Dan ketika bot tidak cukup, dia menyerahkan ke petugas manusia — di sini, di inbox saya."*

**Prompt:** **"Saya ingin bicara dengan petugas soal keberatan hasil uji."**

- Bot mengakui dan menyerahkan dengan rapi (bot berhenti bicara).
- Anda tunjukkan **live agent inbox** di layar dan membalas sebagai petugas.

**Sorotan:** State machine penuh — bot → handoff pending → agen aktif. Fitur yang membuat instansi pemerintah nyaman: masyarakat tetap mendapat jawaban manusia bila perlu.

---

## Babak 6 — Penutupan & Deal (12:00–15:00)

**Anda katakan:** *"Ini Conversa, live di layanan uji kir Anda sekarang juga. Berapa beban pertanyaan berulang yang selama ini masuk ke petugas loket dan telepon?"*

**Contoh prompt penutup:**
1. **"Bagaimana bot membantu kepatuhan uji berkala?"**
   → Jawaban yang diharapkan: menjawab 24 jam, mengingatkan kapan perpanjang, mengedukasi konsekuensi — menurunkan hambatan masyarakat untuk uji tepat waktu.

**Penutupan:**
> *"Itu Conversa, sudah berjalan di layanan uji kir Anda dalam demo ini. Saya bisa integrasikan untuk Dishub dalam 1 hari — knowledge base-nya sudah dilatih. Biaya: (sesuaikan penawaran Conversa, mis. Rp…/bulan + ongkos integrasi). Masyarakat dapat jawaban cepat 24 jam, petugas fokus ke kasus yang butuh manusia. Saya tunjukkan hasilnya dalam beberapa minggu — berapa pertanyaan yang terjawab otomatis dan berapa yang turun di loket."*

---

## Baris Kontingensi

| Jika Kepala Dishub berkata… | Anda menjawab… |
|---|---|
| "Apakah ini menggantikan petugas?" | "Bukan — bot menangani pertanyaan berulang, petugas fokus ke pengecekan, keberatan, dan kasus kompleks." |
| "Bagaimana dengan data warga?" | "Bot menjawab dari knowledge base aturan/SOP — tidak menyimpan data pribadi warga, dan privasi dijaga." |
| "Berapa lama integrasinya?" | "Di bawah 1 hari untuk integrasi; knowledge base uji kir sudah dilatih." |
| "Berbeda dari bot FAQ biasa bagaimana?" | "Bot menjawab pertanyaan terbuka dengan bahasa masyarakat, bersumber pada dokumen, dan mengingat warga yang kembali bertanya." |
| "Bagaimana kalau aturannya berubah?" | "Cukup update dokumen KB-nya, bot langsung ikut — misalnya aturan BLUe Full Cycle 2026 sudah masuk." |
| "Apakah bisa di WhatsApp?" | "Otak yang sama berjalan di WhatsApp — itu build berikutnya di roadmap. Knowledge, memory, handoff yang sama." |

---

## Setelah Demo (Langkah Berikutnya)

1. Kirim **recap singkat**: pertanyaan yang diajukan + jawaban bot (bukti grounding).
2. Kirim penawaran integrasi + harga.
3. Jadwalkan kickoff integrasi (upload KB, pasang widget di situs Dishub / WhatsApp).
4. Tentukan daftar pertanyaan yang mau di-handoff ke petugas (handoff rules).
5. Pantau analitik: deflection rate, pertanyaan terbanyak, jam sibuk — bahan laporan manfaat ke Dishub.
