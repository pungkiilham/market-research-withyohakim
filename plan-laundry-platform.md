# Product Plan: [Nama Platform] — Laundry Marketplace

**Tim:** 2 Developer (Bootstrapped)
**Tanggal:** Juli 2026
**Status:** Draf awal — needs discussion

---

## 1. Executive Summary

**Concept:** Platform marketplace yang menghubungkan 3 pihak dalam ekosistem laundry:
- **Customer** — orang yang butuh cuci baju
- **Drop Point (DP)** — toko/tempat terdekat yang menerima titipan cucian
- **Machine Owner (MO)** — pemilik mesin cuci (rumahan atau laundry shop) yang mencuci

**Core Rule:** Setiap order WAJIB melalui Drop Point. Tidak ada pickup/delivery langsung ke rumah customer.

**Model:** Marketplace + Rule-setter (lightweight ops) — seperti Gojek. Platform kontrol pricing range & kualitas via rating/complaint, tanpa terlibat operasional langsung.

**Market Potential:** Pasar laundry online Indonesia ~USD 1.1 miliar (Ken Research 2026), tumbuh 12-15%/tahun. Belum ada platform dengan model drop point + machine owner secara terstandarisasi.

**Key Differentiator:** Menciptakan layer baru di value chain laundry — drop point sebagai node terdekat customer, tanpa harus jadi laundry shop penuh.

**Financial Snapshot:** Modal cash minimal (~Rp 5jt sampai revenue positif). Cumulative break-even bulan ke 5-8 tergantung skenario. Bootstrapped-friendly.

---

## 2. Roles & Actors

| Role | Description | Bisa Gabung Lain? |
|------|-------------|-------------------|
| **Customer** | Orang yang drop cucian dan pickup setelah selesai | Hanya customer |
| **Drop Point (DP)** | Tempat titip cucian — terima, timbang, catat, simpan sementara | Bisa juga jadi MO |
| **Machine Owner (MO)** | Pencuci — ambil cucian dari DP, cuci, kering, setrika, kembalikan ke DP | Bisa juga jadi DP |

### Hybrid Role: Machine Owner + Drop Point
Seorang MO bisa mendaftarkan lokasinya sebagai DP juga. Artinya:
- Customer bisa drop langsung ke tempat MO
- MO cuci di tempat sendiri
- Customer pickup dari tempat yang sama

Ini juga mencakup laundry shop existing yang join platform.

---

## 3. Use Cases

### Core Use Cases

**UC-1: Customer Drop ke Drop Point**
1. Customer cari DP terdekat via app
2. Datang ke DP, serahkan cucian
3. DP timbang, catat jenis layanan (cuci kering / cuci setrika / dry clean), input ke app
4. Order terdaftar → status: `MENUNGGU_AMBIL`

**UC-2: MO Ambil Cucian dari DP**
1. MO terima notifikasi order di area-nya
2. Auto-assign atau MO pilih order (hybrid system)
3. MO ambil cucian dari DP, scan/tandai sebagai `DIAMBIL`
4. MO cuci di tempatnya

**UC-3: MO Kembalikan Cucian ke DP**
1. Selesai cuci, MO antar kembali ke DP
2. DP scan/tandai sebagai `SIAP_DIAMBIL`
3. Customer dapat notifikasi

**UC-4: Customer Pickup dari DP**
1. Customer datang ke DP
2. Tunjukkan kode order / scan QR
3. Ambil cucian → status: `SELESAI`

**UC-5: Drop Point Juga Machine Owner**
Customer drop langsung ke tempat MO + DP. Alur sama, tapi DP dan MO adalah entitas yang sama.

### Additional Use Cases

**UC-6: Subscription Cucian (Mingguan/Bulanan)**
- Customer subscribe paket mingguan: Rp X/sack
- Pickup otomatis dari DP terjadwal
- Cocok untuk pekerja/kost yang rutin laundry

**UC-7: Express vs Regular**
| Layanan | Turnaround | Harga |
|---------|-----------|-------|
| Regular | Next day (max 24 jam) | Normal |
| Express | Same day (6-8 jam) | Premium (+30-50%) |

**UC-8: B2B Bulk — Hotel / Resto / Laundry Shop Overflow**
- Hotel/resto/laundry shop kirim overflow cucian via DP
- MO dengan kapasitas besar menangani volume tinggi
- Pricing beda (per kg, volume pricing)

**UC-9: Multi-DP Route untuk MO**
- MO ambil cucian dari 3-5 DP terdekat dalam satu rute
- Platform optimize routing untuk efisiensi

**UC-10: Locker Drop Point (Self-Service)**
- Loker dengan QR code di lokasi strategis (minimarket, apartemen)
- Customer drop sendiri, MO scan buka loker
- 24/7, tanpa staff DP

---

## 4. Order Lifecycle & Status

```
DROP → PICKUP → WASH → RETURN → READY → DONE
  ↓       ↓       ↓       ↓        ↓        ↓
  DP   MO ambil  MO cuci MO antar  DP siap  Cust ambil
```

### Status Flow

| Status | Actor | Description |
|--------|-------|-------------|
| `MENUNGGU_AMBIL` | DP | Cucian sudah di DP, nunggu MO ambil |
| `DIAMBIL` | MO | MO sudah ambil cucian dari DP |
| `DICUCI` | MO | Sedang dicuci |
| `SIAP_DIANTAR` | MO | Sudah selesai, siap diantar ke DP |
| `DIANTAR` | MO / Sistem | Dalam perjalanan ke DP |
| `SIAP_DIAMBIL` | DP | Cucian sudah di DP, menunggu customer pickup |
| `SELESAI` | Customer | Customer sudah ambil |
| `DIBATALKAN` | — | Order dibatalkan (alasan: dll) |
| `KOMPLAIN` | Customer | Ada masalah, masuk review |

---

## 5. SOP Framework (untuk Drop Point & MO)

### SOP Drop Point
1. Terima cucian dari customer
2. Timbang berat (kg) di depan customer
3. Konfirmasi jenis layanan & harga
4. Catat di app (foto cucian optional)
5. Simpan cucian di tempat bersih, pisah per order
6. Serahkan ke MO saat diambil (cocokkan order ID)
7. Terima kembali dari MO (cek kondisi)
8. Serahkan ke customer (verifikasi identitas)

### SOP Machine Owner
1. Terima notifikasi order
2. Ambil cucian dari DP dalam waktu X jam (SLA)
3. Cuci sesuai standar (pisah putih/warna, suhu sesuai)
4. Keringkan + setrika (jika layanan setrika)
5. Lipat dan packing rapi
6. Kembalikan ke DP dalam waktu Y jam (SLA)
7. Jika ada masalah (kotor tidak hilang, robek), laporkan via app

### Dispute Categories & Resolution Framework (Draft — need discussion)

| # | Kategori | Contoh | Pelapor |
|---|----------|--------|---------|
| D1 | **Barang Rusak** | Baju robek, kancing copot, warna luntur | Customer |
| D2 | **Barang Hilang** | Ada item hilang setelah dicuci | Customer / DP |
| D3 | **Keterlambatan** | MO telat ambil/antar, melebihi SLA | Customer / DP |
| D4 | **Kualitas Cuci** | Masih kotor, bau, tidak setrika | Customer |
| D5 | **Selisih Timbang** | Berat tidak sesuai di pickup vs drop | Customer / MO |
| D6 | **Pembayaran/Saldo** | Gagal bayar, refund belum masuk | Semua |
| D7 | **Perilaku** | MO/DP tidak ramah, jam tutup tidak sesuai | Semua |

**Catatan:** Detail SOP resolusi, batas waktu komplain, matrix ganti rugi, dan escalation flow perlu di-finalisasi setelah diskusi lanjutan.

---

## 6. Business Model & Pricing

### Revenue Streams

| Stream | Dari | Model |
|--------|------|-------|
| **Commission per order** | MO | Potongan sekian % dari harga layanan |
| **Service fee per order** | Customer | Fee platform kecil per transaksi |
| **Subscription DP** | DP | Biaya bulanan untuk jadi mitra DP |
| **Subscription MO** | MO | Biaya bulanan untuk akses order |

### Payment Flow

```
          Customer
             │
             ▼
         Platform ──► Machine Owner
             │
             ▼
         Drop Point (fee referral)
```

- **Non-cash (preferred):** Customer bayar via app → Platform tahan → Split ke MO + DP setelah order selesai
- **Cash (allowed):** Customer bayar ke DP → Platform catat sebagai utang DP → Otomatis potong saldo DP

### Proposed Commission

| Jenis | Platform | MO | DP |
|-------|----------|-----|-----|
| Cuci Kering | 10-15% | 60-65% | 20-25% |
| Cuci Setrika | 10-15% | 60-65% | 20-25% |
| Express | 10-15% | 65-70% | 15-20% |
| B2B Bulk | 5-10% | 75-80% | 10-15% |

### Pricing Range (Platform-Controlled)

| Layanan | Min Price | Max Price | Notes |
|---------|-----------|-----------|-------|
| Cuci Kering | Rp 5.000/kg | Rp 8.000/kg | Per kg |
| Cuci Setrika | Rp 7.000/kg | Rp 12.000/kg | Per kg |
| Express | +50% dari regular | — | 6-8 jam |
| Minimum order | Rp 15.000 | — | Per transaksi |

---

## 7. Market Potential & Financial Projections

### 7.1 Market Sizing

| Metrik | Nilai | Sumber |
|--------|-------|--------|
| Pasar laundry online Indonesia | ~USD 1.1 miliar (Rp 17-18T) | Ken Research 2026 |
| Home & laundry care market | Rp 115 Triliun (CAGR 3.65%) | Investor.id / Kompas 2024 |
| Pertumbuhan industri laundry | 12-15%/tahun | ASLI |
| Anggota ASLI (Asosiasi Laundry Indonesia) | 1.800+ across 21 provinsi | Kemenkop UKM 2025 |
| Tenaga kerja terserap | 34.000+ | Liputan6 2025 |
| Rata-rata harga kiloan (2026) | Rp 6.000-10.000/kg | Cikadu.id |
| Pertumbuhan anggota ASLI | ~20%/tahun | Kemenkop UKM |

**Key Insight:** Pasar besar dan tumbuh konsisten. Belum ada platform dengan model drop point + machine owner. Kompetitor existing (Sukucuci, D-Laundry, Iziloh, QnC) mostly pakai model pickup-delivery langsung atau POS untuk laundry shop.

### 7.2 Financial Projections — 3 Skenario

**Core Assumptions:**

| Asumsi | Nilai |
|--------|-------|
| Rata-rata order value (incl. service fee) | Rp 25.000 |
| Berat rata-rata per order | 3 kg |
| Net platform revenue per order (after gateway & split) | Rp 3.000 |
| Subscription DP/MO (mulai bulan 4) | Rp 50.000/bln per mitra |
| Ops cost (VPS, API, domain, dll) | Rp 700K-1,5jt/bln |
| Build period | Bulan 1-2 (0 revenue) |

---

#### Skenario A: Pessimistic (Slow Adoption)

Word of mouth lambat, DP/MO terbatas, hanya 1 kecamatan.

| Bulan | Orders | Trans Rev | Subs | Total Rev | Ops Cost | Net Cash | Cumulative |
|-------|--------|-----------|------|-----------|----------|----------|------------|
| 1-2 | 0 | 0 | 0 | 0 | Rp 1,4jt | -Rp 1,4jt | -Rp 1,4jt |
| 3 | 20 | Rp 60rb | 0 | Rp 60rb | Rp 700rb | -Rp 640rb | -Rp 2,04jt |
| 4 | 50 | Rp 150rb | Rp 500rb | Rp 650rb | Rp 700rb | -Rp 50rb | -Rp 2,09jt |
| 5 | 80 | Rp 240rb | Rp 600rb | Rp 840rb | Rp 750rb | +Rp 90rb | -Rp 2,0jt |
| 6 | 150 | Rp 450rb | Rp 800rb | Rp 1,25jt | Rp 800rb | +Rp 450rb | -Rp 1,55jt |
| 7 | 250 | Rp 750rb | Rp 1,0jt | Rp 1,75jt | Rp 850rb | +Rp 900rb | -Rp 650rb |
| 8 | 350 | Rp 1,05jt | Rp 1,2jt | Rp 2,25jt | Rp 900rb | +Rp 1,35jt | +Rp 700rb |
| 12 | 600 | Rp 1,8jt | Rp 1,5jt | Rp 3,3jt | Rp 1,1jt | +Rp 2,2jt | +Rp 8,6jt |

- **Monthly break-even:** Bulan 5
- **Cumulative break-even:** Bulan 8
- **Revenue Month 12:** ~Rp 3,3jt/bln

---

#### Skenario B: Realistic (Expected)

Adopsi stabil, referral dari early adopters, ekspansi ke 2-3 kecamatan.

| Bulan | Orders | Trans Rev | Subs | Total Rev | Ops Cost | Net Cash | Cumulative |
|-------|--------|-----------|------|-----------|----------|----------|------------|
| 1-2 | 0 | 0 | 0 | 0 | Rp 1,4jt | -Rp 1,4jt | -Rp 1,4jt |
| 3 | 50 | Rp 150rb | 0 | Rp 150rb | Rp 700rb | -Rp 550rb | -Rp 1,95jt |
| 4 | 150 | Rp 450rb | Rp 600rb | Rp 1,05jt | Rp 750rb | +Rp 300rb | -Rp 1,65jt |
| 5 | 300 | Rp 900rb | Rp 800rb | Rp 1,7jt | Rp 800rb | +Rp 900rb | -Rp 750rb |
| 6 | 500 | Rp 1,5jt | Rp 1,0jt | Rp 2,5jt | Rp 900rb | +Rp 1,6jt | +Rp 850rb |
| 7 | 750 | Rp 2,25jt | Rp 1,2jt | Rp 3,45jt | Rp 1,0jt | +Rp 2,45jt | +Rp 3,3jt |
| 8 | 1.000 | Rp 3,0jt | Rp 1,4jt | Rp 4,4jt | Rp 1,1jt | +Rp 3,3jt | +Rp 6,6jt |
| 12 | 2.000 | Rp 6,0jt | Rp 2,2jt | Rp 8,2jt | Rp 1,5jt | +Rp 6,7jt | +Rp 28,9jt |

- **Monthly break-even:** Bulan 4
- **Cumulative break-even:** Bulan 6
- **Revenue Month 12:** ~Rp 8,2jt/bln

---

#### Skenario C: Optimistic (Fast Adoption)

Viral effect, DP/MO antre daftar, coverage cepat meluas ke 5+ kecamatan.

| Bulan | Orders | Trans Rev | Subs | Total Rev | Ops Cost | Net Cash | Cumulative |
|-------|--------|-----------|------|-----------|----------|----------|------------|
| 1-2 | 0 | 0 | 0 | 0 | Rp 1,4jt | -Rp 1,4jt | -Rp 1,4jt |
| 3 | 100 | Rp 300rb | 0 | Rp 300rb | Rp 700rb | -Rp 400rb | -Rp 1,8jt |
| 4 | 400 | Rp 1,2jt | Rp 800rb | Rp 2,0jt | Rp 800rb | +Rp 1,2jt | -Rp 600rb |
| 5 | 800 | Rp 2,4jt | Rp 1,2jt | Rp 3,6jt | Rp 1,0jt | +Rp 2,6jt | +Rp 2,0jt |
| 6 | 1.500 | Rp 4,5jt | Rp 1,6jt | Rp 6,1jt | Rp 1,2jt | +Rp 4,9jt | +Rp 6,9jt |
| 7 | 2.500 | Rp 7,5jt | Rp 2,0jt | Rp 9,5jt | Rp 1,4jt | +Rp 8,1jt | +Rp 15,0jt |
| 8 | 3.500 | Rp 10,5jt | Rp 2,4jt | Rp 12,9jt | Rp 1,7jt | +Rp 11,2jt | +Rp 26,2jt |
| 12 | 5.000 | Rp 15,0jt | Rp 3,5jt | Rp 18,5jt | Rp 2,8jt | +Rp 15,7jt | +Rp 84,0jt |

- **Monthly break-even:** Bulan 4
- **Cumulative break-even:** Bulan 5
- **Revenue Month 12:** ~Rp 18,5jt/bln

---

### 7.3 Summary Perbandingan

| Metrik | Pessimistic | Realistic | Optimistic |
|--------|------------|-----------|------------|
| Orders/bln (M-12) | 600 | 2.000 | 5.000 |
| Revenue M-12 | Rp 3,3jt/bln | Rp 8,2jt/bln | Rp 18,5jt/bln |
| Cumulative break-even | Bulan 8 | Bulan 6 | Bulan 5 |
| Modal cash max (dibakar) | ~Rp 2,1jt | ~Rp 2,0jt | ~Rp 1,8jt |
| ARR (annual run rate M-12) | Rp 40jt | Rp 98jt | Rp 222jt |

**Key Takeaway:** Modal cash sangat kecil karena bootstrapped + 2 dev. "Modal" terbesar adalah opportunity cost waktu dev (~Rp 25-40jt biaya hidup selama 3-5 bulan build + pilot). Risiko finansial rendah.

---

## 8. Competitive Landscape

### Direct Competitors

| Competitor | Model | Coverage | Notes |
|------------|-------|----------|-------|
| **Sukucuci** | Pickup-delivery | Jabodetabek | Asset-heavy, own fleet + laundry |

### Indirect Competitors

| Competitor | Model | Gap |
|------------|-------|-----|
| **Laundry Shop tradisional** | Walk-in | Terbatas secara lokasi, jam operasional |
| **Laundry kiloan rumahan** | By referral | Tidak terstandarisasi, cakupan sempit |
| **Gojek/Grab** | Bisa diminta beliin | Bukan dedicated laundry solution |

### Competitive Gap

**Tidak ada platform yang menghubungkan:**
- Banyak drop point (convenience)
- Banyak machine owner (kapasitas terdistribusi)
- Dengan sistem rating + SOP + pricing terstandarisasi

---

## 9. Technical Architecture

### Stack

| Layer | Teknologi | Biaya |
|-------|-----------|-------|
| Mobile App (Android) | Kotlin / Flutter | $0 |
| Backend API | Go (Fiber/Hono) | $0 |
| Database | PostgreSQL + Redis | $0 (self-host VPS) |
| Queue | RabbitMQ / Redis Stream | $0 |
| Push Notification | Firebase Cloud Messaging | $0 |
| Maps / Location | Google Maps API / OpenStreetMap | ~$0-50/bln |
| VPS | DigitalOcean / Vultr $12-24/bln | $12-24 |
| CDN | Cloudflare Free | $0 |

### High-Level Architecture

```
┌──────────────┐     ┌──────────────────┐     ┌───────────────┐
│  Customer App │────▶│                  │◀────│    MO App      │
│  (Android)    │     │   Backend API    │     │   (Android)    │
└──────────────┘     │   (Go + Redis)   │     └───────────────┘
                     │   + PostgreSQL   │
┌──────────────┐     │                  │     ┌───────────────┐
│  DP App       │────▶│  + Cloud Tasks  │◀────│  Admin Web    │
│  (Android)    │     └──────────────────┘     │  (Dashboard)  │
└──────────────┘                                └───────────────┘
```

### Role & Menu Breakdown per App (MVP)

**Customer App:**
| Menu | Fungsi |
|------|--------|
| Home | Peta + list DP terdekat, filter jarak/layanan |
| Buat Order | Pilih DP, pilih layanan, konfirmasi drop |
| Track Order | Timeline status real-time |
| Riwayat | History order + detail transaksi |
| Wallet | Top-up, history transaksi, refund |
| Profile | Edit profil, settings |

**Drop Point App:**
| Menu | Fungsi |
|------|--------|
| Dashboard | Order pending hari ini, notifikasi |
| Buat Order | Input cucian (timbang, layanan, foto), submit ke sistem |
| Daftar Order | List order masuk & keluar, filter status |
| Scan QR | Scan QR MO (ambil/antar) + scan QR customer (pickup) |
| Riwayat | History transaksi + earning |
| Wallet | Saldo, setoran cash, penarikan |

**Machine Owner App:**
| Menu | Fungsi |
|------|--------|
| Dashboard | Order available di area, queue order saya |
| Ambil Order | Pilih order, scan QR DP, status → DIAMBIL |
| Proses | Update status DICUCI → SIAP_DIANTAR |
| Antar | Scan QR DP, status → SIAP_DIAMBIL |
| Riwayat | History transaksi + earning |
| Wallet | Saldo, penarikan |

**Admin Dashboard (Web):**
| Menu | Fungsi |
|------|--------|
| Dashboard | Metrics real-time (volume, revenue, active DP/MO) |
| Kelola Order | Search, filter, edit status, force-resolve |
| Kelola User | Approve/flag/suspend DP & MO |
| Dispute | List komplain, assign, resolve, catat keputusan |
| Reports | Export data, revenue summary |

---

## 10. MVP Scope

### MUST HAVE (MVP)

| Fitur | Platform | Priority |
|-------|----------|----------|
| Auth (login/register) | All | P0 |
| Cari DP terdekat (list/map) | Customer | P0 |
| Order lifecycle (drop → pickup → wash → return → ready → done) | All | P0 |
| QR-based order handover (DP ↔ MO) | DP + MO | P0 |
| Status tracking | Customer | P0 |
| Push notification tiap status change | All | P0 |
| Rating & review | Customer | P0 |
| Wallet + payment (non-cash) | All | P0 |
| SOP compliance checklist | DP + MO | P0 |

### NICE TO HAVE (Post-MVP)

| Fitur | Alasan Skip |
|-------|-------------|
| AI auto-assign optimization | Butuh data dulu |
| Locker self-service | Hardware investment |
| Subscription model | Validasi dulu |
| B2B bulk | Butuh volume |
| Multi-language / EN | Indonesia dulu |
| Live chat support | Manual dulu via WA |
| Analytics dashboard advanced | Basic dulu |

### MVP Build Sequence (Estimasi: 2 Dev)

| Phase | Durasi | Output |
|-------|--------|--------|
| **Phase 1: Foundation** | Week 1-2 | VPS, CI/CD, DB, Auth, Wallet |
| **Phase 2: Core Flow** | Week 3-4 | Order lifecycle, QR handover, Status tracking |
| **Phase 3: Mobile Apps** | Week 5-8 | Customer App + DP App + MO App (Android) |
| **Phase 4: Launch Prep** | Week 9-10 | Testing, Admin dashboard, Landing page, Pilot di 1 area |

---

## 11. Open Questions (Need Discussion)

- [ ] **Nama platform** — belum ditentukan
- [ ] **Pricing final** — persentase komisi peran masih estimasi
- [ ] **Minimum order** — apakah ada minimum kg atau Rp?
- [ ] **SLA time** — berapa jam maksimal MO ambil dari DP? Maksimal cuci?
- [ ] **Pickup distance** — seberapa jauh MO boleh ambil dari DP? Radius?
- [ ] **DP verification** — siapa yang boleh jadi DP? Cukup daftar atau butuh visit?
- [ ] **MO verification** — perlu verifikasi lokasi & mesin? Atau cukup KTP?
- [ ] **Cash handling** — bagaimana mekanisme setoran cash DP ke platform?
- [ ] **Dispute resolution** — SOP komplain: barang rusak/hilang, keterlambatan
- [ ] **Launch area** — mulai dari 1 kecamatan mana? Bandung? Jaksel? Jatinangor?
- [ ] **Payment gateway** — pakai Xendit/Midtrans? Atau QRIS manual?
- [ ] **Dispute SOP detail** — timeframe komplain (24 jam?), batas ganti rugi, escalation flow
- [ ] **Ganti rugi barang rusak/hilang** — batas maksimal MO ganti rugi? Skema asuransi?
- [ ] **SLA MO** — maksimal jam ambil dari DP? Maksimal waktu cuci + return?
- [ ] **Cash handling SOP** — setoran DP, rekonsiliasi, sanksi keterlambatan setor

---

## 12. Next Steps

1. Finalize nama platform
2. Validasi dengan 10-20 target user (pemilik laundry, pemilik toko, customer)
3. Tentukan launch area (1 kecamatan)
4. Finalize pricing & commission
5. Finalize dispute SOP & escalation matrix
6. Detailkan SOP operasional (hukum & logistik)
7. Mulai build Phase 1: Foundation (Week 1-2)

---

*Dokumen ini draf awal — akan di-update setelah diskusi lanjutan.*
