# Product Plan: OmniWA — WA Official API + AI Context Engine

**Tim:** 2 Developer (Bootstrapped)
**Tanggal:** Juli 2026

---

## 1. Executive Summary

**Problem:** 64 juta UMKM di Indonesia bergantung pada WhatsApp sebagai channel komunikasi utama. Semakin besar bisnis, semakin kewalahan handle chat pelanggan. Solusi yang ada cuma dua: (1) manual pakai WA Business app (gratis tapi gak scalable), atau (2) pakai Qontak/Wati (official tapi mahal, Rp 350K-1.3Jt/bln). Di tengah, gak ada. Fonnte/Kirimi/Wablas ada di harga murah tapi unofficial (risiko banned tinggi dari Meta).

**Solusi:** OmniWA — WA Official API + AI Context Engine. Satu platform dengan dua produk:
- **OmniWA API:** WA Official API termurah untuk developer (Rp 100K/bln, 0% markup)
- **OmniWA Chat:** Staff AI yang bisa ngobrol kaya manusia buat UMKM (Rp 50-150K/bln)

**Target Pasar:** Developer Indonesia + UMKM yang 50-200 chat/hari.

**Revenue Model:** Subscription bulanan + pay-per-use API.

**Edge:** Satu-satunya produk yang menggabungkan **WA Official + AI Context Engine + harga di bawah Rp 200K/bln**.

---

## 2. Product Architecture

```
┌──────────────┐     ┌──────────────────────────────────┐
│  Customer     │────▶│          OmniWA Engine            │
│  (WhatsApp)   │     │                                    │
└──────────────┘     │  ┌──────────────────────────────┐  │
                     │  │  1. Intent Detection (NLU)    │  │
                     │  │  2. Context Memory (session)  │  │
                     │  │  3. Knowledge Retrieval (RAG) │  │
                     │  │  4. Sentiment Analysis        │  │
                     │  │  5. Response Generation (LLM) │  │
                     │  │  6. Action Execution          │  │
                     │  │  7. Human Handoff             │  │
                     │  └──────────────────────────────┘  │
                     └──────────────────────────────────┘
                               │
                               ▼
                     ┌──────────────────┐
                     │  OmniWA Dashboard │
                     │  (Owner/Admin)    │
                     └──────────────────┘
```

---

## 3. AI Context Engine — Advanced Conversational Agent

Bukan auto-reply keyword biasa. Ini AI agent dengan kemampuan:

| Fitur | Level | Description |
|-------|-------|-------------|
| **Konteks Lintas Session** | Advance | Inget percakapan sebelumnya — bahkan kalo customer balik besok |
| **Knowledge Retrieval** | Advance | Paham katalog produk, FAQ, SOP bisnis dari data yang diupload owner |
| **Intent Understanding** | Advance | Bukan cuma cocok keyword — paham maksud kalimat natural ("kalo beli 2 ada diskon?") |
| **Sentiment Detection** | Advance | Detek emosi customer (frustasi/senang/bingung) → adjust tone respon |
| **Smart Handoff** | Advance | Tau kapan harus transfer ke manusia (komplain >2x, negosiasi harga, AI gak confident) |
| **Tone Customization** | Medium | Bisa diset formal / santai / casual per bisnis |
| **Action Execution** | Medium | Generate link pembayaran, catat order, kirim resi otomatis |

### Bedanya dengan Auto-Reply Biasa

| Dimensi | Auto-Reply (Fonnte/Wablas) | OmniWA Context Engine |
|---------|---------------------------|----------------------|
| Pola respon | Keyword → Template | Natural language → AI-generated |
| Memory | Gak inget percakapan | Inget full history per customer |
| Pemahaman | Cocok kata kunci | Paham intent + konteks |
| Emosi | Gak peduli | Detek sentiment, adjust tone |
| Handoff | Manual | Otomatis kalo perlu |
| Evolusi | Statis | Belajar dari interaksi |

---

## 4. Use Case — Skenario Nyata

### Skenario A: Toko Fashion (UMKM, 100-200 chat/hari)

```
Customer: "kak, baju merah ukuran L masih ada?"
AI:      "Halo kak! Baju merah ukuran L masih ready, 
          Rp 149.000 aja. Mau warna lain juga ada: hitam,
          putih, navy. Katalog bisa dicek di sini ⬇️"
          [link katalog]
...
Customer: (besok) "kemarin aku nanya baju merah, 
          pesen 1 dong"
AI:      "Baik kak, baju merah ukuran L Rp 149.000.
          Langsung aja atau mau ditambah item lain? 
          Kalo via link pembayaran bisa transfer ke: ⬇️"
```

### Skenario B: Developer / Agency

Dev pake OmniWA API buat build chatbot custom buat klien:
- Endpoint: `/v1/ai/chat`
- Body: `{ "phone": "628xxx", "message": "...", "context_id": "..." }`
- Response: real-time AI-generated reply with context

---

## 5. Target Market & Demand Validation

### Market Size

| Metrik | Data |
|--------|------|
| WhatsApp users Indonesia | 112M+ |
| UMKM Indonesia | 64-65 juta |
| UMKM sudah go-digital | 25 juta (target 30 juta) |
| Global WA Business API Market | $2.34B (2024) → $19.13B (2033) |
| CAGR | 24.7% |
| Orang RI chat bisnis via WA per minggu | 88% (tertinggi global) |

### Demand Signal — 3 Tren

1. **Migrasi Unofficial → Official:** Meta makin ketat banned account pake Fonnte/Wablas/Kirimi. Ratusan ribu pengguna cari alternatif official yang affordable. Tapi pilihan cuma: api.co.id (raw API, no context engine) atau Qontak/Wati (mahal).

2. **UMKM Butuh "Staff AI":** 70% UMKM masih di tahap awal digitalisasi. Gak punya budget buat tim CS, tapi chat masuk numpuk. Solusi yang ada (WA Business app) cuma bisa handle <100 chat/hari secara manual.

3. **AI Chatbot Adoption Meningkat:** 60% perusahaan yang pakai WA API bakal implement AI automation by 2026. UMKM juga mulai sadar — lihat dari banyaknya artikel "chatbot UMKM" yang bermunculan.

### Gap Analysis

```
                  RAW API ONLY ◄──────────────► AI CONTEXT ENGINE
                         │                            │
   MAHAL           Twilio, Qontak API              Qontak (Rp 350K-1.8Jt)
   (> Rp 300K)                                     Wati ($39-79)
                                                    Chakra Chat ($12.49)
                         │                            │
                         │                            │
   MURAH          api.co.id (Rp 100K)          → KAMU: OmniWA (Rp 150K) ←
   (< Rp 200K)        (Official)                (Official + AI Engine)
                         │                            │
                    Fonnte/Kirimi/Wablas         Fonnte/Kirimi/Wablas
                    (Rp 25-175K) ⚠️               (Rp 25-175K) ⚠️
                    Unofficial                   Unofficial
```

**Gap:** Tidak ada pemain yang menggabungkan **WA Official + AI Context Engine + harga < Rp 200K/bln**.

---

## 6. Competitive Landscape

| Provider | Official WA | Context Engine | Harga/bln | Target | Risiko Ban |
|----------|------------|---------------|-----------|--------|-----------|
| **Fonnte** | ❌ Unofficial | ✅ Auto-reply | Rp 25-175K | UMKM | 🔴 Tinggi |
| **Wablas** | ❌ Unofficial | ✅ Auto-reply + multi-agent | Rp 100-500K | UMKM | 🔴 Tinggi |
| **Kirimi** | ❌ Unofficial | ✅ AI Agent + Team Inbox | Rp 29-99K | UMKM | 🔴 Tinggi |
| **api.co.id** | ✅ Official | ❌ Raw API only | Rp 100K | Developer | ✅ Aman |
| **Qontak** | ✅ Official | ✅ CRM + Team Inbox | Rp 350K-1.8Jt | Mid-market | ✅ Aman |
| **Wati** | ✅ Official | ✅ Chatbot + Broadcast | $39-79 (Rp 625K-1.3Jt) | SMB Global | ✅ Aman |
| **Chakra Chat** | ✅ Official | ✅ Basic CRM + AI Agent | $12.49 (Rp 195K) | SMB Global | ✅ Aman |
| **→ OmniWA** | **✅ Official** | **✅ AI Context Engine** | **Rp 50-150K** | **UMKM + Dev** | **✅ Aman** |

### Key Competitor Weaknesses

| Kompetitor | Kelemahan Utama |
|-----------|----------------|
| **Fonnte/Wablas/Kirimi** | Unofficial — risiko banned tinggi, gak bisa centang biru, gak ada SLA |
| **api.co.id** | Cuma raw API — gak ada context engine, gak bisa dipake UMKM non-teknis |
| **Qontak** | Mahal (Rp 350K+) — pricing gak cocok buat UMKM kecil |
| **Wati** | Global product — bahasa Indonesia kurang, support lokal terbatas, markup per pesan 10-20% |
| **Chakra Chat** | Global product, belum fokus ke Indonesia, fitur AI terbatas |

---

## 7. Pricing Strategy

### Pricing Principles
- Under-cut mid-range competitors 50-70%
- Revenue per customer: Rp 50-150K/bln (mix Lite + Pro)
- Anchor ke Rp 150K — masih 2.3x lebih murah dari Qontak termurah (Rp 350K)
- API developer pricing flat Rp 100K — compete langsung dengan api.co.id

### Tier Pricing

| Tier | Target | Harga/bln | Fitur |
|------|--------|-----------|-------|
| **Free** | Dev testing | Rp 0 | 1.000 pesan/bln, akses semua decoy APIs, context engine basic (no AI) |
| **API Dev** | Developer | Rp 100K | WA Official API + all decoy APIs + webhook + docs |
| **OmniWA Lite** | UMKM kecil | Rp 50K | WA Official + auto-reply keyword + broadcast terbatas |
| **OmniWA Pro** | UMKM medium | **Rp 150K** | **AI context engine full: memory + RAG + sentiment + handoff** |
| **OmniWA Enterprise** | Bisnis besar | Custom | Multi-agent, custom LLM, SLA, dedicated support |

### Decoy APIs (Free / Included)

Untuk bikin platform keliatan lengkap, bundle gratis di semua tier:

| API | Monetisasi |
|-----|-----------|
| Regional Data Indonesia | Gratis unlimited (akuisisi) |
| IP Geolocation | Gratis (1000/hr) |
| Exchange Rate | Gratis unlimited |
| AI Gateway (GPT/Claude) | Free tier 1000 token/hr |

---

## 8. Build Sequence — MVP Roadmap

### Fase 1: Foundation (Minggu 1-2)

| Minggu | Task | Output |
|--------|------|--------|
| 1 | Setup VPS + Docker + CI/CD | Infra siap deploy |
| 1 | Auth system (API Key) + Billing wallet | Register, top-up, deduction |
| 1 | WA Official Cloud API integration | Kirim & terima WA via API |
| 2 | Decoy APIs (Regional, IP Geo, Exchange Rate) | Free tier siap |
| 2 | Dokumentasi API + Postman collection | Dev bisa coba langsung |
| 2 | Dashboard basic (usage, billing, API keys) | Self-serve portal |

### Fase 2: Context Engine Level 1 (Minggu 3-4)

| Minggu | Task | Output |
|--------|------|--------|
| 3 | LLM integration + conversation memory | AI bisa ngobrol dengan context |
| 3 | Knowledge retrieval system (RAG) | Upload catalog/FAQ → AI paham data bisnis |
| 3 | OmniWA Chat dashboard (Konfigurasi AI) | Owner bisa set knowledge base + tone |
| 4 | Auto-connect WA number (embedded signup) | User daftar + connect WA dalam 5 menit |
| 4 | Broadcast + template management | Kirim promosi ke customer |
| 4 | Testing + bug fixing | Production ready |

### Fase 3: Launch (Minggu 5-6)

| Minggu | Task | Output |
|--------|------|--------|
| 5 | Launch ke komunitas developer (Discord, Telegram) | Developer acquisition |
| 5 | Launch ke grup UMKM / forum bisnis | End-user acquisition |
| 5 | Blog SEO: "Staff AI WhatsApp termurah 2026" | Organic traffic |
| 6 | Feedback loop + fix | Iteration |
| 6 | Monitor infra + cost | Optimasi LLM cost |

### Fase 4: Advance (Minggu 7-12)

| Minggu | Task | Output |
|--------|------|--------|
| 7-8 | Sentiment analysis integration | AI detek emosi customer |
| 7-8 | Smart handoff to human | Auto-transfer kalo AI gak yakin |
| 9-10 | Multi-agent / team inbox | Multiple admin handle chat dari satu nomor |
| 11-12 | Analytics dashboard | Volume chat, response time, conversion |

---

## 9. Revenue Projection

### Asumsi Dasar
- 64 juta UMKM sebagai target pasar (OmniWA Chat)
- Developer sebagai target sekunder (OmniWA API)
- Konversi free → paid: 5-10%
- Rata-rata revenue per paid customer: Rp 100K/bln (mix Lite + Pro)
- LLM cost per customer: ~Rp 10-20K/bln (dengan optimasi)

### 3 Skenario

| Metrik | Konservatif | Moderat | Agresif |
|--------|-------------|---------|---------|
| **Month 1** | 10 paid | 20 paid | 50 paid |
| **Month 3** | 50 paid | 150 paid | 400 paid |
| **Month 6** | 200 paid | 600 paid | 1.500 paid |
| **Month 12** | 500 paid | 2.000 paid | 5.000 paid |

### MRR Projection

| Skenario | Month 1 | Month 3 | Month 6 | Month 12 | ARR Year 1 |
|----------|---------|---------|---------|----------|-----------|
| **Konservatif** | Rp 1Jt | Rp 5Jt | Rp 20Jt | Rp 50Jt | **$3.7K** |
| **Moderat** | Rp 2Jt | Rp 15Jt | Rp 60Jt | Rp 200Jt | **$14.8K** |
| **Agresif** | Rp 5Jt | Rp 40Jt | Rp 150Jt | Rp 500Jt | **$37K** |

### Break-even Analysis

| Item | Biaya |
|------|-------|
| VPS (2 instance) | $15-20/bln (~Rp 250-350rb) |
| Domain | ~$1/bln (~Rp 15rb) |
| LLM API (OpenAI/Anthropic) | ~Rp 10-20K per customer |
| Total fixed | ~Rp 300-400rb/bln |
| **Customers needed to break-even** | **~5-8 customer** (Lite + Pro mix) |

---

## 10. Risk Assessment

### Risk Matrix

| Risiko | Dampak | Probabilitas | Mitigasi |
|--------|--------|-------------|----------|
| **api.co.id copy context engine** | TINGGI — kehilangan diferensiasi | SEDANG | Mereka culture developer-first, end-user product bukan core. Tapi siap-siap pivot ke fitur lebih advance (AI agent) |
| **LLM cost ga sesuai revenue** | SEDANG | SEDANG | Optimasi prompt caching, pake local LLM untuk simple query, upgrade pricing kalo perlu |
| **Adopsi UMKM rendah** | TINGGI | SEDANG | Fokus content marketing + edukasi. Bikin tutorial "Coba gratis 14 hari" |
| **Meta ubah kebijakan API** | TINGGI | RENDAH | Pake Cloud API langsung dari Meta, bukan via BSP. Diversifikasi ke channel lain (Telegram, Instagram) |
| **Akurasi AI rendah (hallucination)** | SEDANG | SEDANG | RAG dari data bisnis yang diupload. Grounding ke knowledge base, bukan pure LLM |
| **Kompetitor turun harga** | SEDANG | RENDAH | Qontak udah mahal dari sononya — susah turun drastic. api.co.id Rp 100K udah batas bawah |

### Top 3 — Action Plan

**Risk #1: api.co.id copy fitur**
- ✅ Mereka developer-first company — kecil kemungkinan bikin end-user AI dashboard
- ✅ Bedakan dengan: AI agent yang lebih advanced (bukan auto-reply biasa)
- ✅ Build switching cost: data customer, conversation history, knowledge base tenant

**Risk #2: LLM cost bikin margin tipis**
- ✅ Cache response untuk FAQ yang sering ditanyakan
- ✅ Fallback ke local LLM (Llama 3, Mistral) untuk request simple
- ✅ Target margin kotor: 60%+ setelah optimasi

**Risk #3: UMKM gak mau bayar**
- ✅ Free tier 14 hari — tanpa card, langsung cobain
- ✅ Content marketing: "Hemat 20 jam/minggu, Rp 5K/hari aja"
- ✅ Referral program: ajak teman, gratis 1 bulan

---

## 11. Demand Deep-Dive

### Market Size & Growth

| Metrik | Data | Sumber |
|--------|------|--------|
| Global WA Business API Platform | $2.34B (2024) → $19.13B (2033) | Growth Market Reports |
| CAGR | 24.7% | Growth Market Reports |
| API adoption growth | 5.400% (2019-2024) | MobileSquared |
| WA users Indonesia | 112M+ (#3 global) | Meta |
| UMKM Indonesia | 64-65 juta | Kemenko |
| Orang RI chat bisnis via WA/minggu | 88% (tertinggi global) | Meta |
| UMKM sudah go-digital | 25 juta (target 30 juta) | Wamendag 2025 |
| WA Business Summit 2025 | Meta fokus besar ke Indonesia | Gizmologi |

### Validasi Demand — Competitor Traction

| Competitor | Traction | Implikasi |
|-----------|----------|-----------|
| **api.co.id WA API** | 2 juta hits dalam 60 hari, 100+ perusahaan dalam 30 hari | Demand WA API TERBUKTI besar |
| **Fonnte** | >2.000 device terdaftar, ratusan ribu pesan/hari | Ratusan ribu UMKM udah pake unofficial → siap migrasi |
| **Qontak** | Salah satu BSP terbesar di RI, SEO dominan | Pasar WA API udah mature, bukan early adopter lagi |
| **Wati** | 8.000+ bisnis global, $39-79/bln | Global validation: orang MAU bayar buat WA platform |

### 3 Demand Driver Utama

**Driver #1: Gelombang Migrasi Unofficial → Official**
Meta makin agresif banned unofficial WA API. Fonnte sendiri di websitenya bilang:
> "Fonnte tidak bertanggung jawab terkait banned dari whatsapp... tidak akan pernah bisa memberikan SLA yang fixed karena layanan unofficial."

Ratusan ribu UMKM yang currently pake Fonnte/Wablas/Kirimi butuh tempat baru. Pilihan mereka:
1. **api.co.id** — resmi, murah (Rp 100K), tapi cuma raw API (gak ada dashboard, gak ada auto-reply)
2. **Qontak/Wati** — resmi, ada fitur, tapi MAHAL (Rp 350K-1.3Jt)
3. **OmniWA** — **resmi, ada AI context engine, Rp 150K** ← celah

**Driver #2: UMKM Butuh "Staff AI", Bukan Cuma API**
Dari riset Panduan Usaha 2026:

| Skala UMKM | Solusi Saat Ini | Gap |
|-----------|----------------|-----|
| Solo, <50 chat/hari | WA Business app (gratis) ✅ | OK |
| Tim 2-5, 50-200 chat/hari | Qontak Rp 500K-2Jt or manual | **GAP BESAR** — gak ada yang di tengah |
| Tim 5+, 200+ chat/hari | Qontak Pro / Custom | Enterprise, bukan target |

UMKM 50-200 chat/hari adalah **sweet spot** OmniWA. Mereka udah kewalahan manual, tapi belum sanggup Qontak. Solusi yang ada cuma dua ekstrem — gratis (manual) atau mahal (enterprise).

**Driver #3: AI Chatbot Adoption Lagi Peak**
- 69% konsumen lebih suka chatbot buat pertanyaan simple
- 64% customer bilang 24/7 service adalah kebutuhan
- 60% perusahaan WA API bakal implement AI automation by 2026
- 45% pekerja Indonesia udah pake AI tools personally (Populix)
- Topik "chatbot UMKM" trending di Google Indonesia — banyak yang cari

### Demand Estimation

| Channel | Target | Estimasi Volume |
|---------|--------|----------------|
| Migrasi Fonnte → Official | UMKM pengguna unofficial | Ratusan ribu orang |
| Organic search "WA API murah" | Developer + UMKM | >10.000 search/bln |
| SEO "AI chatbot UMKM" | UMKM digital-aware | >5.000 search/bln |
| Referral + word of mouth | UMKM komunitas | Viral potensial |
| **Total addressable lead/month** | | **~15.000-30.000** |

---

## 12. MVP Wise — Apa yang Dibangun & Apa yang Dilewati

### Prinsip MVP
1. **Build yang bikin WOW doang** — AI context engine yang inget konteks + paham data bisnis
2. **Skip yang "nice to have"** — kirim ke fase berikutnya
3. **Gunakan existing tools** — jangan build custom model. Pake OpenAI/Anthropic API
4. **Landing page first** — validasi sebelum build penuh

### MVP Scope

| Komponen | Build / Skip | Alasan |
|----------|-------------|--------|
| **WA Official API proxy** | ✅ BUILD | Core product — must have |
| **Auth + billing wallet** | ✅ BUILD | Must have — orang bayar |
| **Decoy APIs** (regional, ip geo, etc) | ✅ BUILD | Effort rendah (1-2 hari) — bikin platform keliatan lengkap |
| **Basic dashboard** (usage, billing) | ✅ BUILD | Self-serve portal |
| **AI Context Engine** | ✅ BUILD | **Main differentiator** |
| **Knowledge Retrieval (RAG)** | ✅ BUILD | Upload catalog/FAQ → AI paham |
| **Conversation memory** | ✅ BUILD | Inget konteks lintas session |
| **Auto-connect WA number** | ✅ BUILD | User experience kunci |
| **Dokumentasi API** | ✅ BUILD | Developer trust signal |
| **Landing page + free trial** | ✅ BUILD | Akuisisi |

| **Sentiment analysis** | ❌ SKIP | Bisa pake prompt sederhana dulu |
| **Smart handoff** | ❌ SKIP | Build setelah validasi |
| **Multi-agent / team inbox** | ❌ SKIP | Fase 3 |
| **Analytics dashboard** | ❌ SKIP | Fase 3 |
| **Broadcast campaign** | ❌ SKIP | Fase 3 |
| **Mobile app** | ❌ SKIP | Jauh banget — web dulu |
| **Custom NLP model** | ❌ SKIP | Pake LLM API existing |

### Technical Stack MVP

| Layer | Teknologi | Biaya |
|-------|-----------|-------|
| Backend | Go (Fiber/Hono) | $0 |
| Database | PostgreSQL + Redis | $0 (self-host di VPS) |
| LLM | GPT-4o-mini (OpenAI API) | ~$2-5/1M token — murah |
| Vector/RAG | ChromaDB (lightweight) | $0 |
| WA API | Meta Cloud API langsung | $0 (free tier testing) |
| VPS | DigitalOcean $12/bln | $12 |
| Frontend | React + Tailwind | $0 |
| Docs | Nextra (VitePress) | $0 |

### Estimasi Effort MVP (untuk 2 dev)

| Area | Estimasi Effort |
|------|----------------|
| Infra + CI/CD + Auth + Billing | 3-4 hari |
| WA API Proxy + Decoy APIs | 3-4 hari |
| Dashboard basic | 3-4 hari |
| AI Context Engine (memory + RAG + LLM) | 5-7 hari |
| Auto-connect WA + landing page + trial | 2-3 hari |
| **Total MVP** | **~16-22 hari** |

### Trade-off Paling Kritis: LLM Cost vs Quality

| Opsi | Cost/bulan (100 UMKM) | Quality | Rekomendasi |
|------|----------------------|---------|-------------|
| GPT-4o-mini | ~$20-50 (Rp 300-750K) | ✅ Good enough | **MVP — recommended** |
| GPT-4o | ~$100-300 (Rp 1.5-4.5Jt) | 🏆 Best | Fase scale-up |
| Claude 3 Haiku | ~$10-30 (Rp 150-450K) | ✅ Good | Alternatif lebih murah |
| Local LLM (Llama 3 8B) | ~$5-10 (VPS upgrade) | ⚠️ Medium | Setelah traffic besar |

**MVP choice:** GPT-4o-mini. Cukup murah, performa bagus buat casual chat.

---

## 13. Strategi Marketing (Zero Budget)

### Dual-Audience Strategy

Karena produk punya dua tipe pengguna, strategi marketing harus beda:

| Audience | Where They Hang Out | What They Care About |
|----------|-------------------|---------------------|
| **Developer** | GitHub, Telegram/Discord dev group, Dicoding, Postman | Dokumentasi, API quality, pricing, reliability |
| **UMKM** | Grup WA, Facebook UMKM, YouTube, TikTok | Gampang dipake, harga murah, hasil langsung |

### Developer Acquisition (Channel #1)

| Channel | Taktik | Impact |
|---------|--------|--------|
| **GitHub** | Open source library Go/JS/Python — "Official WA API client termudah" | HIGH — developer trust signal |
| **Technical Blog** | "Cara migrate dari Fonnte ke Official WA API dalam 10 menit" — di Dev.to, Medium | HIGH — SEO + authority |
| **Komunitas Telegram/Discord** | Join grup developer Indonesia, subtle promo lewat jawaban bermanfaat | MEDIUM — personal |
| **Postman** | Public workspace dengan collection siap pakai | MEDIUM — dev tools |
| **Dicoding** | Submit workshop materi "WA API + AI untuk pemula" | MEDIUM — reach 1M+ dev |
| **SEO Blog** | "Official WA API termurah 2026", "WA API Indonesia", "Perbandingan harga WA API" | HIGH — organic traffic |

### UMKM Acquisition (Channel #2)

| Channel | Taktik | Impact |
|---------|--------|--------|
| **Grup WA UMKM** | Join 10-20 grup UMKM besar, tawarin free trial untuk 5 orang pertama | HIGH — conversion langsung |
| **YouTube Shorts** | "Staff AI Rp 5K/hari — setting 5 menit" — demo visual | MEDIUM-HIGH — reach besar |
| **Content Blog** | "Cara hemat 20 jam/minggu dengan AI WhatsApp" — SEO friendly | MEDIUM — organic |
| **Facebook UMKM** | Post di grup Facebook UMKM Indonesia | MEDIUM — reach besar |
| **Testimoni** | Minta user pertama bikin video testimoni, bagi ke grup | HIGH — social proof |
| **KOL micro** | Cari 3-5 UMKM dengan followers kecil tapi engaged, kasih free lifetime | MEDIUM — trust |

### SEO Content Pillars

| Pillar | Target Keyword | Search Volume Estimasi |
|--------|---------------|----------------------|
| **Harga termurah** | "official wa api murah" | >5.000/bln |
| **Migrasi** | "alternatif fonnte", "pindah dari wablas" | >3.000/bln |
| **AI chatbot** | "ai chatbot wa umkm", "staff ai whatsapp" | >2.000/bln |
| **Perbandingan** | "qontak vs wati", "harga wa api indonesia" | >5.000/bln |

### Viral Loop

```
User daftar free tier (1.000 pesan/bln)
        ↓
User pake, hasilnya bagus
        ↓
User invite teman → dapet bonus 500 pesan
        ↓
Teman daftar → siklus berulang
        ↓
User mencapai limit free → auto upgrade ke paid
```

### AIDA Funnel

| Stage | Taktik |
|-------|--------|
| **Attention** | "Bales chat WA otomatis pake AI cuma Rp 5K/hari — resmi dari Meta" |
| **Interest** | "Coba gratis 14 hari, tanpa kartu kredit. Setup 5 menit." |
| **Desire** | "Toko A: dulu 3 jam/hari bales chat, sekarang 15 menit. Hemat Rp 2Jt/bulan." |
| **Action** | "Daftar sekarang → langsung bisa dipake." |

### Growth Metrics Target

| Metrik | Target Month 1 | Target Month 3 |
|--------|---------------|---------------|
| Free signup | 200 | 2.000 |
| Paid conversion | 10 (5%) | 100 (5%) |
| Developer signup | 50 | 500 |
| MRR | Rp 2Jt | Rp 15Jt |

---

## 14. Next Steps

1. **Validate with 10-20 target users** (UMKM + developer) — tanya pain point, willingness to pay
2. **Decide product name** — OmniWA atau nama lain yang lebih klik
3. **Finalize scope Phase 1** — fitur apa yang MUST HAVE vs NICE TO HAVE
4. **Build Phase 1: Foundation** — Minggu 1-2
5. **Build Phase 2: Context Engine** — Minggu 3-4
6. **Launch** — Minggu 5-6
