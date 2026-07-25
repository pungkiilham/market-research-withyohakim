# 21 — Business Requirements Document (BRD)

> **Purpose:** a single, pitch-ready recap of the entire product — what it is, every
> function it delivers, who it's for, how it makes money, and where it stands today.
> Written for investor and client conversations; consolidates docs 01–20.
>
> Product working name: **Conversa** (final name pending — see doc 07 §9).
> Owner: mikahoy045@gmail.com · Last updated: 2026-07-24

---

## 1. Executive Summary

**Conversa** is a multi-channel conversational AI platform for SMBs. A business
signs up, uploads its knowledge (documents, FAQs, catalogs) or connects its
database, and within minutes has one AI agent answering customers on its
**website**, on **WhatsApp**, and inside **Odoo** — grounded in the business's own
data and **remembering every returning client like a human would**.

> **One-line pitch:** Give any business a single AI chatbot that answers customers
> on their website, WhatsApp, and Odoo — trained on their own content, remembering
> every client — live in minutes, billed per usage.

Three structural differentiators, all owned in-house:

1. **One brain, many channels** — knowledge, persona, memory, and analytics are
   authored once and reused on every channel. Competitors force businesses to
   stitch single-channel tools together.
2. **Per-client memory** — the in-house knowledge engine (**Gravija**, distilled
   from our Context Engine) stores each client's history, so returning customers
   are recognized and conversations continue where they left off. Most
   competitors' bots forget the user after every session.
3. **Graph-aware retrieval on an engine we own** — answers are assembled from
   *connected* information (service → location → hours → payment), not naive
   top-k text similarity. Owning the engine means better answers, no per-query
   managed-RAG vendor fees, and a widening data moat.

**Status:** the core platform and web channel are **built and deployed** (private
beta stage); WhatsApp is fully specified and next in the build queue; Odoo and
white-label follow. Section 8 details built vs. planned.

---

## 2. Problem Statement

Businesses juggle customer conversations across disconnected tools: a website
with no chat (or a rigid rule bot), a WhatsApp number answered manually and
slowly after hours, and an ERP/helpdesk that knows the customer but can't talk.
Knowledge is duplicated per channel, answers drift, after-hours coverage is
poor, and hiring more agents doesn't scale.

**There is no single, affordable AI layer that serves customers consistently
across web, WhatsApp, and the business's own systems — trained on the business's
own knowledge, deployable without an engineering team.** Conversa is that layer.

---

## 3. Business Objectives

| Objective | Measure (north star) |
|---|---|
| Fast activation | % of signups live on ≥1 channel; time-to-live < 15 min self-serve |
| Multi-channel expansion | % of customers using ≥2 channels |
| Real support deflection | % of conversations resolved without human handoff |
| Healthy unit economics | Gross margin per conversation (target 70%+ on text) |
| Compounding revenue | Net revenue retention via usage, channels, and seats |

---

## 4. Target Market & Users

- **Segment A — WhatsApp-first SMBs (primary):** clinics, real estate, education,
  local retail/e-commerce, travel & hospitality — businesses losing leads to slow
  or after-hours responses.
- **Segment B — Web/SaaS support (secondary):** SaaS products, content and
  knowledge sites, internal help desks needing an embeddable grounded bot.
- **Segment C — Agencies & resellers (channel):** digital agencies wanting a
  white-label conversational product to resell.
- **Segment D — Odoo users:** businesses on Odoo ERP/CRM wanting AI on their
  Live Chat/Helpdesk grounded in Odoo data.

**Go-to-market:** global product from day one (multilingual engine, multi-currency,
CDN-served widget); **Indonesia is the launch beachhead** (WhatsApp-heavy, fast SMB
digital adoption), with an EU presence from the start (distributed team, GDPR-aware
design). Motion is product-led self-serve, amplified by agency/BSP partnerships and
sales-assisted for Odoo and larger accounts.

---

## 5. Product Functions (the full recap)

Everything below is **one core engine** exposed through thin channel adapters.

### 5.1 Knowledge & Grounding

| Function | What it delivers |
|---|---|
| Document ingestion | Upload PDFs, DOCX, TXT, CSV, FAQs, catalogs, policies; organize, version, delete from the console |
| Owned RAG pipeline (Gravija) | Extract → chunk → embed → index → retrieve, per tenant, on our own engine — no third-party RAG fees |
| Graph-aware retrieval | Hybrid semantic + lexical search fused and boosted by an entity graph — answers connect related facts instead of quoting the nearest paragraph |
| Automatic freshness | A watcher re-indexes on every add/update/delete, so answers always reflect current content |
| Source citations | Every answer stays traceable to the source document |
| Multilingual by default | BGE-M3 multilingual embeddings — one knowledge base serves customers in their language |
| Governed database access | The bot can query the tenant's live database (**PostgreSQL, MySQL, MongoDB**) for orders, stock, bookings — read-only, deny-by-default, per-tenant table/column allow-lists, fully logged |

### 5.2 Per-Client Memory (headline differentiator)

| Function | What it delivers |
|---|---|
| Long-term client memory | Each client's past conversations, preferences, and issues are stored and recalled on every new session — the bot "remembers you" |
| Query-aware recall | Memory retrieval is relevance-ranked with time decay, scoped strictly to the client within the tenant |
| Entity graph recall | Memory links client → orders → tickets → preferences for graph-expanded context |
| Cross-channel identity | The same client on web, WhatsApp, and Odoo can map to one continuous memory |
| Privacy controls | Memory on by default with per-client opt-out and true deletion (`forget` removes vectors, not just flags) — designed for GDPR and Indonesia's PDP Law |

### 5.3 Conversation Engine & Safety

| Function | What it delivers |
|---|---|
| LLM orchestration | Persona + business config + retrieved knowledge + memory + history assembled per turn |
| Model tiering | Cheap/fast model for simple turns, stronger model for hard ones — the biggest cost lever |
| Managed or BYOK models | Tenants run on platform keys (managed) or bring their own provider key at a discounted plan price |
| Scope guardrail | Detects off-topic requests and steers back to the business's domain — never improvises out of scope |
| Content guardrail | Blocks unsafe/abusive content with per-tenant policy; unsafe signals trigger human handoff |
| Confidence fallback | Low confidence → honest "I'm not sure" or escalation, not a guess |
| Prompt-injection defense | Critical because the bot can reach databases and tools |
| Rate limiting & abuse protection | Per tenant, on every endpoint |

### 5.4 Rich Media (all channels, both directions)

Inbound: images, voice notes (transcribed), video, files. Outbound: images,
spoken audio replies (TTS), video, files. Turn-based chat — not telephony — which
keeps cost low and quality high.

### 5.5 Human Handoff — live agent (built)

| Function | What it delivers |
|---|---|
| Conversation state machine | `bot → handoff pending → agent active → resolved`; the bot goes silent the moment a human steps in |
| Escalation triggers | Explicit request, unsafe content, low confidence, plan capacity |
| Live agent inbox | `/console/live` — pending/active queues, full transcript, agent reply with agent name shown to the customer |
| Tenant notifications | Email immediately; Firebase push to the console (notification only — transcripts never leave our backend) |
| Customer-side continuity | Widget polls for agent replies; email fallback if the visitor has left |

### 5.6 Channels

**Web chatbot widget (built, live):**
- One `<script>` line — identical for every stack (WordPress, Shopify, Wix,
  Webflow, React/Next, plain HTML). No SDK, no build step.
- Origin-locked publishable key (`pk_…`) + short-lived tokens; secret keys never
  touch the browser. Served from a public CDN host (`conversa-bot.com`).
- Streaming token-by-token replies, typing indicator, markdown rendering,
  brandable theme, lead capture, handoff.

**WhatsApp AI bot (specified — next build):**
- Same brain, same memory, same handoff on the tenant's WhatsApp number.
- **Dual connection modes:** official Meta Cloud API with Embedded Signup
  ("automagic" onboarding in minutes) *or* a self-hosted gateway mode (QR pairing,
  ~60s to live, no Meta fees) behind an explicit tenant risk acknowledgment.
- 24h service-window and template handling, media, per-conversation cost
  pass-through; anti-ban discipline built into the design.

**Odoo AI bot (roadmap):**
- External connector on Odoo Live Chat/Helpdesk via Odoo's API — no addon
  install. Reads/acts on Odoo records (order lookup, ticket create, CRM update)
  under the same governed allow/deny rules.

### 5.7 Contacts & CRM-lite (built)

- Widget captures name/email after first reply → stored as a **lead**.
- Per-tenant leads and customers, isolated; email match auto-promotes a lead to
  **customer**. The contact list becomes a growing asset the tenant owns.

### 5.8 Management Console (tenant-facing, built)

- Persona, tone, business hours, escalation rules.
- Knowledge base management: sources, re-index status, DB access config.
- **Playground** — test the bot on the real pipeline (retrieval, guardrails,
  memory) before going live; playground usage is free.
- Widget install page (generate snippet per site origin), test-widget preview.
- Conversations & transcripts, live inbox, contacts, analytics, usage & billing.
- Team members with roles/invites; model settings (managed vs BYOK); API keys.

### 5.9 Platform Operations (SaaS-owner console, built)

- Separate operator surface (`/admin`) with allowlist-gated access and
  Superadmin/Operator tiers; idempotent operator bootstrap on every deploy.
- Platform LLM key management (validated live, stored encrypted) powering
  managed-mode tenants.
- Tenant overview with mode-aware MRR estimate.
- Full CI/CD deploy pipeline; per-tenant data isolation throughout.

### 5.10 Analytics, Metering & Billing

- Per-conversation transcripts, resolution status, handoff rate, deflection.
- Knowledge-gaps report: what customers asked that the bot couldn't answer —
  a built-in improvement loop.
- Usage metering per tenant feeding both product limits and invoices.
- **Billable unit = conversation** (24h window; many messages = 1) — simple,
  fair, and aligned with WhatsApp's own model.
- 14-day no-card trial → paid conversion; hard-cap quota with upgrade prompt
  (no surprise bills); non-payment degrades to handoff-only mode rather than
  cutting off the tenant's customers.

### 5.11 Bot Types & Skills (design; Assistant is Phase 2)

- **Customer Service bot** — external-facing, tightly guardrailed (the default,
  built).
- **Assistant bot** — internal, employee-facing, more agentic, MCP tool support
  (Phase 2).
- **Skills** — equipable agentic tools (book appointment, check order, create
  ticket, collect lead, custom webhooks), governed by guardrails, roles, and DB
  allow/deny rules.

---

## 6. Competitive Position

The market splits into single-channel specialists and heavy enterprise suites:

| Category | Examples | Their gap |
|---|---|---|
| Web chatbot / support AI | Intercom Fin, Tidio, Chatbase, Botpress | Weak/no WhatsApp, enterprise pricing, generic top-k vector RAG, session-only memory |
| WhatsApp automation / BSPs | Twilio, WATI, Respond.io, ManyChat | Rule-flow heavy, not truly conversational, web often basic |
| Broad CX platforms | Zendesk, Freshworks, Ada | Expensive, heavy setup, overkill for SMBs |

**Positioning:** for SMBs and agencies who need to answer customers everywhere,
Conversa is a multi-channel AI agent serving web, WhatsApp, and Odoo from one
knowledge base — grounded in the business's documents *and* database, remembering
every client — deployable in minutes and priced by usage.

**Why we win:** one brain across channels · clients are remembered · graph-aware
retrieval on an owned engine (quality + margin + moat) · real data grounding with
governed DB access · live in minutes · SMB usage pricing · white-label
distribution flywheel · unified cross-channel analytics.

---

## 7. Business Model & Pricing

**Revenue streams:** subscriptions with included conversation quotas · usage
expansion · channel add-ons (WhatsApp on all paid plans) · white-label/reseller
platform fees · professional services · premium capabilities (SLA, SSO,
residency).

**Current plan structure** (subject to final pricing review):

| Plan | Managed (our keys) | BYOK (tenant's key) |
|---|---:|---:|
| Starter | $29/mo | $19/mo |
| Growth | $99/mo | $69/mo |
| Pro | $299/mo | $199/mo |
| Agency / Enterprise | Custom | Custom |

**Unit economics:** blended variable cost ≈ **$0.02–0.03 per conversation** on
managed keys (model tiering, capped context, semantic caching, owned
embeddings/retrieval — no per-query RAG vendor fees). Quotas are derived from a
target ~70%+ gross margin. BYOK removes model cost from our side entirely
(~90%+ margin on the platform fee) while easing customer data concerns.

**Payments by region:** Midtrans (Indonesia, IDR), Paddle (global
merchant-of-record, EU VAT), Stripe (global cards).

---

## 8. Current Status & Roadmap

| Phase | Scope | Status |
|---|---|---|
| 0 — Foundations | Multi-tenant data model, auth, CI/CD, provider abstractions, **Gravija** engine (knowledge + memory + graph) | ✅ Built — Gravija is the default engine in production |
| 1 — MVP: Core + Web | Widget, streaming, media, guardrails, memory, governed DB access, playground, contacts, billing/metering, analytics, **live human handoff**, console + admin | ✅ Built & deployed (private-beta stage) |
| 2 — WhatsApp | Dual-mode adapter (official Cloud API + gateway), shared memory/handoff/billing, Channels console | 📋 Fully specified (doc 20) — next build |
| 3 — Odoo | Live Chat/Helpdesk connector, Odoo records as governed tools | Planned |
| 4 — Scale | White-label/agency mode, Assistant bot + MCP, vertical templates, SSO/residency/SLA, advanced analytics | Planned |

Continuous workstreams: answer-quality evaluation, memory precision, guardrail
hardening, cost engineering, security review before each new surface.

---

## 9. Key Risks & Mitigations

| Risk | Mitigation |
|---|---|
| LLM cost spikes | Model tiering, semantic caching, context caps, per-tenant cost monitoring |
| Hallucination / wrong answers | Graph-grounded RAG, confidence thresholds, guardrails, human handoff |
| DB over-reach / data leakage | Read-only, deny-by-default allow-lists, parameterized queries, audit logs, injection defense |
| WhatsApp policy & ban risk | Official Cloud API as the compliant default; unofficial mode opt-in behind explicit risk acknowledgment; no broadcast blasts |
| Wrong/stale client memory | Relevance-ranked recall with decay, retention controls, true deletion, never assert unverified personal facts |
| Privacy / PII (GDPR, PDP Law) | Per-tenant isolation, encryption, configurable retention, consent + deletion, EU-residency option on roadmap |
| Commoditization | Multi-channel + owned graph engine + memory + white-label distribution = compounding moat |

---

## 10. Notes for Pitching

- **Market sizing:** the TAM/SAM/SOM framework is in doc 03 §5 — fill it with
  sourced figures (Statista / industry reports) before an investor meeting; do
  not present guessed numbers.
- **Pricing:** the plan prices above are live in the product; quotas per tier are
  still being calibrated against measured cost per conversation (doc 05 §4.1).
- **Name:** "Conversa" is a working name — trademark/domain check pending.
- **Proof points to collect from pilots:** deflection %, response-time
  improvement, after-hours leads captured, cost vs. added headcount.

### Source documents

| Topic | Doc |
|---|---|
| Vision & business model | [01](./01-vision-and-business-model.md) |
| Product modules (deep dive) | [02](./02-product-modules.md) |
| Market & competitors | [03](./03-market-and-competitors.md) |
| Pricing & unit economics | [05](./05-pricing-and-monetization.md) |
| Roadmap | [06](./06-roadmap-and-phases.md) |
| Go-to-market | [07](./07-go-to-market.md) |
| Knowledge engine (Gravija) | [09](./09-context-engine-integration.md), [16](./16-gravija.md) |
| Web widget & install | [12](./12-trd-web-widget.md), [18](./18-widget-install.md) |
| Human handoff | [19](./19-human-handoff-live.md) |
| WhatsApp channel | [20](./20-whatsapp-channel.md) |
