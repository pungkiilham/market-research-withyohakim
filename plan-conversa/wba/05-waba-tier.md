# 05 — WABA: Which Tier, How to Register, 0→10k Path

> **Owner:** You + Yohakim · **Last updated:** 2026-08-15
> **Goal:** Register our own Meta path and start building the Conversa WhatsApp feature (PRD WA-1..6, Phase 2).

---

## 1. Decision

- **Use case:** **Customer service** — tenant links their own WA number to Conversa via Embedded Signup; Conversa receives **inbound** messages and **replies** (not broadcasting).
- **Use now:** **Tech Provider** — self-serve in App Dashboard, done in days, no application. Tenants link their **own** WABA via Embedded Signup.
- **Solution Partner = NOT relevant** for this use case. It only adds a credit line + bundled billing (one bill incl. API cost). We use **pass-through**: tenant pays Meta directly for API usage, Conversa charges its subscription separately. Solution Partner only if billing later changes to bundled (apply after paying tenants + PT formed).

---

## 2. Register (under CV Estro Hutama) — 6 steps

1. **Confirm Estro docs:** NIB + NPWP + akta + business bank statement — all must match the portfolio.
2. **Create Meta Business Portfolio "CV Estro Hutama" → verify.** Needs company-domain email (no Gmail).
3. **Create Meta app → WhatsApp use case → connect to the portfolio.**
4. **Enable Tech Provider:** App Dashboard → WhatsApp → Use cases → Customize → Tech Provider.
5. **App Review → Advanced access:** `whatsapp_business_messaging` + `whatsapp_business_management` (needs **2 demo videos**: send a message + create a message template).
6. **Setup for Embedded Signup:**
   - Facebook Login for Business config (`config_id`) from the "WhatsApp Embedded Signup Configuration" template
   - Public webhook endpoint (HTTPS/SSL + verify token)
   - Fresh dev number (must not be on any WhatsApp app)

---

## 3. Build the feature (PRD WA-1..6)

Tenant "Connect WhatsApp" flow (WABA Sharing model):

- `FB.login(fbLoginCallback, { config_id, response_type: 'code', override_default_response_type: true, extras: { setup: {} } })` → Meta popup → tenant picks/creates their portfolio + adds their WA number.
- Meta posts `WA_EMBEDDED_SIGNUP` event: `{ waba_id, phone_number_id, business_portfolio_id, code }` — **code expires in 30s.**
- Server side:
  1. Exchange `code` → **business token**: `GET graph.facebook.com/v25.0/oauth/access_token`
  2. Subscribe: `POST /<waba_id>/subscribed_apps`
  3. Register: `POST /<phone_number_id>/register` `{ "messaging_product": "whatsapp", "pin": "<6-digit>" }`
  4. Persist: `tenant_id ↔ waba_id, phone_number_id, business_token`
- **Send:** `POST /<phone_number_id>/messages` with the tenant's token (inside 24h window, or via approved template outside it).
- **Receive:** one webhook for all tenants → route by `phone_number_id`/`waba_id` → bot → reply.
- WA-4: 24h service window + templates · WA-6: show Meta per-message fees to the tenant (pass-through transparency — Meta bills the tenant directly, not Conversa).

---

## 4. Path: 0 → 10k linked numbers

| Stage | When | What | Why |
|---|---|---|---|
| **1. Tech Provider** | Now (days) | Embedded signup live in console; onboard first clients (client adds own payment method, Conversa charges sub on top) | Hits 100 paid users / 1 month target. 200/week cap is irrelevant at this stage |
| **2. Tech Partner** | ~after 10 active clients + 2,500 msgs/day | Self-initiated upgrade, no application | Removes onboarding cap for 1k–10k scale + official badge |
| **3. Solution Partner** | Only if billing changes to bundled | Application via Meta | Unlocks credit line → bundled billing (NOT needed for pass-through / customer-service use case) |

Note: 10k needs partner status — as a pure Tech Provider you'd be capped at ~1.2k new clients / 6 months.

---

## 5. New-client onboarding limits (per partner type)

| Partner type | New clients / rolling 7-day window | Notes |
|---|---|---|
| Plain developer (verified + App Review) | 200 | Baseline after BV + App Review + Access Verification |
| **Tech Provider** | **200** | Self-serve; no application. Total connected tenants has no hard cap — only onboarding *speed* is capped |
| **Tech Partner** | Higher (not published — granted with partner status) | Self-initiated upgrade: ≥2,500 avg msgs/day OR ≥200 calls/day + ≥10 active clients + ≥90% quality |
| **Solution Partner (BSP)** | Highest (not published — vetted/granted) | Selective application + credit line |

Implication for target 1k–10k in 6 months:
- **1k** (~38/week) → Tech Provider covers it comfortably.
- **5k–10k** (~192–385/week) → Tech Provider cap (200/week) blocks >5k; upgrade to Tech Partner when you hit volume thresholds.

---

## 6. Gotchas (one line each)

- **Fresh dedicated number** — not registered on any WhatsApp app; consider a second number for production once the PT forms.
- **Set timezone Asia/Jakarta + IDR before billing** — immutable after a line of credit. (German tenants: Europe/Berlin + EUR.)
- **One webhook endpoint per Meta app** — route all tenants' inbound by `phone_number_id`; don't create per-tenant apps.
- **Per-tenant WABA:** tenants bring their own portfolio (Tobias = proctOR GmbH); **Estro WABA = dev/test/internal only**.
- **OBO model is deprecated** (Oct 2025) — build on Embedded Signup WABA Sharing, not on-behalf-of.
- **WABA cannot be migrated between portfolios** — when PT forms, re-register the dev number under the PT.
- **WABA belongs to the tenant, not Conversa** — bundled billing only changes who pays Meta, not ownership.

---

*Companion docs: [22 — PRD](./22-prd.md) §5.6 WhatsApp Channel · [CONTEXT.md](../../context.md)*
