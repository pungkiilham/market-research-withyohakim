# Context — Market Research & Product Plan

## Research History

### 1. Market Research: API Provider Business Indonesia
- **File:** `market-research-report.md`
- **Scope:** Market sizing, competitive landscape, pricing, roadmap API Provider umum (KYC + WA API + Utility)
- **Status:** ✅ Completed

### 2. Product Plan: OmniWA — WA Official API + AI Context Engine
- **File:** `plan-wa-context-engine.md`
- **Concept:** Pivot dari API Provider umum → fokus ke WA Official API + Context Engine (AI conversational agent untuk UMKM)
- **Dual Product:**
  - **OmniWA API** — WA Official API proxy untuk developer (Rp 100K/bln)
  - **OmniWA Chat** — AI context engine untuk UMKM (Rp 50-150K/bln)
- **Decoy APIs:** Regional data, IP geo, exchange rate, AI gateway — gratis, bikin platform keliatan lengkap
- **Key Differentiator:** Satu-satunya yang menawarkan WA Official + AI Context Engine + harga di bawah Rp 200K/bln
- **Status:** ✅ Draf awal selesai

## File Structure

```
market-research-api-provider/
├── market-research-report.md      # Riset awal (API Provider umum)
├── plan-wa-context-engine.md      # Product plan OmniWA (14 sections)
└── context.md                     # File ini — checkpoint status
```

## Last Discussion Points

- **Context Engine Level:** Advanced AI agent (bukan auto-reply keyword biasa) — conversation memory, RAG dari data bisnis, sentiment-aware, smart handoff
- **Target Persona:** Developer + UMKM (50-200 chat/hari)
- **Pricing Anchor:** Rp 150K/bln — 2.3x lebih murah dari Qontak termurah
- **MVP Build Effort:** ~16-22 hari untuk 2 dev

## Next Steps (when continue)

1. Validate idea with 10-20 target users (UMKM + developer)
2. Decide final product name (OmniWA or else)
3. Finalize MVP scope
4. Start building Phase 1: Foundation
5. Build Phase 2: Context Engine
6. Launch

## Open Questions (to discuss later)

- [- ] Product name finalization
- [- ] LLM provider choice (GPT-4o-mini vs Claude vs local)
- [- ] Pricing finalization
- [- ] Specific feature for MVP vs post-MVP
