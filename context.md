# Context — Market Research & Product Plan

## Research History

### 1. Market Research: API Provider Business Indonesia
- **File:** `market-research-report.md`
- **Scope:** Market sizing, competitive landscape, pricing, roadmap API Provider umum (KYC + WA API + Utility)
- **Status:** ✅ Completed

### 2. Product Plan: OmniWA — WA Official API + AI Context Engine
- **File:** `plan-wa-context-engine.md`
- **Concept:** Pivot dari API Provider umum → fokus ke WA Official API + Context Engine (AI conversational agent untuk UMKM)
- **Status:** ✅ Draf awal selesai

### 3. Conversa AI — Funding & Investor Strategy
- **Focus:** Funding pre-seed untuk Conversa (AI chatbot platform, MVP already built)
- **Target:** €15,000 SAFE round at €500K cap — Tobias (Proctor founder) first, then other angels
- **Status:** ✅ Term sheet drafted (`plan-conversa/03-funding-term-sheet.md`)
- **Next:** Pitch Tobias this week, finalize legal entity with Yohakim

### 4. Conversa AI — Reseller Program
- **Focus:** Distribution channel via agencies, software houses, freelancers
- **Commission:** $3/$10/$45 flat lifetime per client (Starter/Growth/Pro)
- **Payout:** Quarterly, no minimum
- **Status:** ✅ Program drafted (`plan-conversa/04-reseller-program.md`)

### 5. Conversa AI — WABA Registration & Meta Partner Path
- **Focus:** WhatsApp Business API (WABA) untuk channel WhatsApp (Phase 2) + daftar **langsung ke Meta sebagai partner**
- **Use case:** Customer service — tenant link nomor WA mereka ke Conversa via **Embedded Signup**, Conversa terima inbound + balas (bukan broadcasting). Billing: **pass-through** (tenant bayar Meta, Conversa tagih sub terpisah).
- **Decision:** Pakai **CV Estro Hutama** untuk Meta Business Portfolio + WABA (dev/test) + **Tech Provider** (self-serve, hari) — **cukup & cocok** untuk use case customer service. **Solution Partner TIDAK relevan** (hanya untuk bundled billing/credit line, aplikasi ke Meta, gated). Upgrade **Tech Partner** nanti jika onboarding >200 klien/minggu (1k–10k target).
- **Update 1:** Pitch Tobias sukses (2026-08-13) — web widget klinik + referral kolega/rumah sakit Jerman (Phase 2)
- **Update 2 (2026-08-15):** Daftar langsung ke Meta sebagai partner (bukan lewat BSP 360dialog/WATI). Tenant link nomor WA via **Embedded Signup**; Conversa handle chat. Detail di `05-waba-registration.md` §3–§6.
- **Status:** ✅ Research done (`plan-conversa/05-waba-registration.md`)
- **Next:** Start Tech Provider onboarding di App Dashboard; App Review (2 demo video); integrasi Embedded Signup; verification Estro; web widget klinik Tobias

## File Structure

```
market-research-api-provider/
├── market-research-report.md          # Riset awal (API Provider umum)
├── plan-wa-context-engine.md          # Product plan OmniWA
├── plan-conversa/
│   ├── 01-situation-analysis.md       # Situasi + ethical dilemmas
│   ├── 02-funding-strategy.md         # Strategi pendekatan ke Tobias
│   ├── 03-funding-term-sheet.md       # Term sheet + detail pendanaan
│   ├── 04-reseller-program.md         # Reseller program
│   ├── 05-waba-registration.md        # WABA registration + Meta partner path (CV Estro, Tech Provider → Solution Partner)
│   ├── 21-brd.md                      # BRD
│   ├── 22-prd.md                      # PRD
│   └── Conversa — AI customer service that remembers every customer.pdf
└── context.md                         # File ini — checkpoint status
```

## Current Focus: Conversa Funding + Distribution

| Item | Detail |
|------|--------|
| **Product** | Conversa — multi-channel AI chatbot (web, WA, Odoo), Gravija engine |
| **Team** | You (50%) + Yohakim (50%) |
| **Stage** | MVP built & deployed (private beta), 0 paying customers |
| **Funding Target** | €15,000 pre-seed SAFE @ €500K cap, 20% discount |
| **Primary target** | Tobias — ✅ pitched (2026-08-13); first customer (clinic web widget) + referral ke kolega/rumah sakit Jerman |
| **Reseller model** | Agencies sell to their clients, 10-15% flat lifetime commission, quarterly payout |
| **WABA entity** | CV Estro Hutama (dev/test); customers use own WABA; SAFE issuer = PT Conversa AI |
| **Key blocker** | PT Conversa AI belum dibentuk (untuk SAFE); verification Estro bisa mulai sekarang |

## Last Discussion Points

- **SAFE vs Equity:** SAFE lebih sederhana untuk pre-seed, pakai YC standard
- **Funding amount:** €15,000 (covers 12 bulan ops + WhatsApp dev + marketing)
- **Tobias approach:** Two paths — Customer First (€1,800 integration + $69/mo sub) or Bundled (€11,800 total + SAFE). ✅ Pitch done (2026-08-13): mau pakai untuk klinik (web widget dulu) + referensikan ke kolega/rumah sakit
- **German clients:** Web widget dulu (Phase 1); WhatsApp/WABA = Phase 2, tiap klinik pakai WABA sendiri (dokumen Jerman: Handelsregister/Gewerbeanmeldung/USt-ID), GDPR admin-only di WhatsApp
- **Reseller commission:** Flat $3 (Starter) / $10 (Growth) / $45 (Pro) per client/month, lifetime recurring
- **Entity:** Decided — Estro for WABA (operational), PT Conversa AI sebagai issuer SAFE. Form PT before Tobias wires money.

## Next Steps (immediate)

1. [ ] You + Yohakim: start Meta Business verification under CV Estro (see `05-waba-registration.md`)
2. [ ] You: integrate web widget untuk klinik Tobias (deliverable pertama, tanpa WABA)
3. [ ] You: prepare 15-min Conversa demo for Tobias (jika belum demo)
4. [ ] You + Yohakim: download YC SAFE template (ycombinator.com/documents)
5. [ ] Close Tobias — customer first (web), lalu SAFE
6. [ ] Recruit 2-3 reseller agencies to test the program

## Open Questions

- [ ] LLM provider choice (GPT-4o-mini vs Claude vs local)
- [ ] Pricing finalization for Conversa subscription
- [ ] When to open to other angel investors after Tobias
- [ ] Reseller tracking system (referral links vs dashboard)
