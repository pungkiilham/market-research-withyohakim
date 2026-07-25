# 22 — Product Requirements Document (PRD) — Whole Product

> **Purpose:** the product-level requirements for the entire platform — what the
> product must do for its users, across all channels and phases, written without
> technical implementation detail. Companion to the
> [BRD (doc 21)](./21-brd.md): the BRD says *why this business*, this PRD says
> *what the product must do*.
>
> For engineering-depth specs see [doc 10](./10-prd-mvp-chatbot.md) (MVP web
> chatbot), [doc 11](./11-prd-context-engine.md) (knowledge engine), and the
> build plans (docs 12, 19, 20).
>
> Working name: **Conversa** · Owner: mikahoy045@gmail.com · Last updated: 2026-07-24

---

## 1. Product Summary

Conversa gives a business **one AI agent** that answers its customers on the
**website**, on **WhatsApp**, and inside **Odoo** — trained on the business's own
content and data, remembering every returning client, escalating to a human when
needed, and reporting everything in one console.

The product experience in one sentence per audience:

- **For the business owner:** "I signed up, uploaded my docs, pasted one line on
  my site — and my customers get instant, correct answers day and night."
- **For the end customer:** "It answered my actual question, it remembered me
  from last time, and when I asked for a person, a person came."
- **For the agency:** "I run this for all my clients under my own brand."

## 2. Goals & Success Metrics

| Goal | Metric | Target |
|---|---|---|
| Fast time-to-value | Signup → bot live on website | < 15 minutes self-serve |
| Answers customers can trust | Answer grounded-in-source rate; hallucination reports | Grounded by default; citations available |
| Real workload relief | Deflection (resolved without human) | Majority of conversations |
| Recognition that feels human | Returning clients recalled correctly | Recall precision monitored per tenant |
| Expansion | Tenants on ≥2 channels; plan upgrades | Growing quarter over quarter |
| Sustainable economics | Gross margin per conversation | 70%+ blended (managed mode) |

## 3. Personas

| Persona | Who | What they need from the product |
|---|---|---|
| **Owner Olivia** | SMB owner | Live in minutes, cheap, "just works", never miss an after-hours lead |
| **Support Sam** | Support lead at a SaaS | Deflection, easy embed, transcripts, analytics, clean handoff to the team |
| **Agency Alex** | Agency owner | White-label, multi-tenant management, margin |
| **Odoo Omar** | Runs his business on Odoo | AI on Odoo Live Chat that knows his data and remembers repeat customers |
| **End customer** | The tenant's customer | Correct answers instantly, in their language, a human on request |
| **Platform operator** | The SaaS team (us) | Tenant overview, platform model keys, revenue view, safe operations |

## 4. Scope

### In scope (across releases)

- Knowledge ingestion (documents, FAQs, catalogs) with automatic freshness.
- Governed read-only access to the tenant's database as an answer source.
- Grounded, guardrailed, multilingual conversations with per-client memory.
- Rich media in and out (images, voice notes with transcription/spoken replies, video, files).
- Channels: embeddable web widget → WhatsApp (official and gateway modes) → Odoo.
- Live human handoff with a real agent inbox and notifications.
- Contacts (leads → customers) captured from conversations.
- Tenant console: setup, knowledge, playground, conversations, contacts, analytics, team, billing.
- Platform operator console: tenants, platform model keys, revenue overview.
- Plans, trial, metering by conversation, managed vs BYOK model modes.
- Later: internal Assistant bot type, skills library, white-label/reseller mode.

### Out of scope (deliberate non-goals)

- Real-time telephony / live phone calls (voice = asynchronous audio messages).
- WhatsApp broadcast/marketing blasts, group chats, catalogs/commerce flows.
- Building a general-purpose agent platform — the product is a business chatbot.

## 5. Functional Requirements

Priorities: **P0** = must have for the phase it ships in · **P1** = should have ·
**P2** = later. Phase = when it reaches customers (see §7).

### 5.1 Onboarding & Workspace

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| ON-1 | Self-serve signup with email verification; first login creates a named workspace | P0 | 1 ✅ |
| ON-2 | Guided path to live: add knowledge → configure persona → test → install widget | P0 | 1 ✅ |
| ON-3 | Team members with roles (owner/admin/agent) and email invites | P0 | 1 ✅ |
| ON-4 | 14-day free trial without a card; clear conversion to paid | P0 | 1 ✅ |

### 5.2 Knowledge Base

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| KB-1 | Upload and manage documents (PDF, DOCX, TXT, CSV), FAQs, catalogs; see indexing status | P0 | 1 ✅ |
| KB-2 | Changes re-index automatically — answers always reflect current content | P0 | 1 ✅ |
| KB-3 | Answers cite their sources; the tenant can trace any answer to a document | P0 | 1 ✅ |
| KB-4 | Connect a database (PostgreSQL, MySQL, MongoDB) as an answer source — read-only, with an explicit allow-list of tables/columns and deny-by-default | P1 | 1 ✅ |
| KB-5 | Knowledge-gaps report: questions the bot couldn't answer well, as an improvement to-do list | P1 | 1 ✅ |
| KB-6 | Website crawl as a source | P2 | 2+ |

### 5.3 Conversations & Answer Quality

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| CV-1 | Answers are grounded in the tenant's knowledge/data — the bot does not improvise outside it | P0 | 1 ✅ |
| CV-2 | Multilingual: customers ask in their language, one knowledge base serves all | P0 | 1 ✅ |
| CV-3 | Configurable persona, tone, and business context per bot | P0 | 1 ✅ |
| CV-4 | Off-topic requests are declined and steered back to the business's domain | P0 | 1 ✅ |
| CV-5 | Inappropriate/unsafe content is blocked; unsafe signals escalate to a human | P0 | 1 ✅ |
| CV-6 | When unsure, the bot says so or escalates — it does not guess | P0 | 1 ✅ |
| CV-7 | Rich media both ways: accept images/voice/video/files; reply with images, spoken audio, files | P1 | 1 ✅ |
| CV-8 | Suggested follow-up questions | P2 | 2+ |

### 5.4 Per-Client Memory

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| ME-1 | A returning client is recognized and the bot continues with their history in mind | P0 | 1 ✅ |
| ME-2 | Memory is strictly per client, per tenant — never leaks across either boundary | P0 | 1 ✅ |
| ME-3 | Memory recall is relevance-ranked and time-decayed — recent, pertinent facts win | P0 | 1 ✅ |
| ME-4 | A client can be forgotten on request — deletion is real and complete | P0 | 1 ✅ |
| ME-5 | The bot never asserts unverified personal facts back at the customer | P0 | 1 ✅ |
| ME-6 | The same client across web, WhatsApp, and Odoo can link to one continuous memory | P1 | 2–3 |

### 5.5 Web Widget Channel

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| WW-1 | One `<script>` line installs the widget on any website, any tech stack, no SDK | P0 | 1 ✅ |
| WW-2 | The install key is locked to the tenant's site origin; keys shown once, revocable | P0 | 1 ✅ |
| WW-3 | Streaming replies with a typing indicator and formatted (markdown) text | P0 | 1 ✅ |
| WW-4 | Brandable: colors, position, avatar, launcher | P1 | 1 ✅ |
| WW-5 | Console page generates the personalized snippet and previews the real widget before shipping | P0 | 1 ✅ |
| WW-6 | Lead capture: name/email requested after the first helpful reply | P1 | 1 ✅ |

### 5.6 WhatsApp Channel

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| WA-1 | Connect a WhatsApp number from the console — official mode via Meta's guided signup, live in minutes | P0 | 2 |
| WA-2 | Alternative gateway mode: pair any existing WhatsApp number by QR code (~60s), offered behind an explicit risk acknowledgment | P1 | 2 |
| WA-3 | Same bot, same knowledge, same memory, same handoff as the web — no separate setup | P0 | 2 |
| WA-4 | Respect WhatsApp's 24h service window; use approved templates outside it (official mode) | P0 | 2 |
| WA-5 | Media support (images, voice notes, documents) within each mode's limits | P1 | 2 |
| WA-6 | WhatsApp per-conversation fees visible to the tenant (pass-through transparency) | P1 | 2 |

### 5.7 Odoo Channel

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| OD-1 | Connect an Odoo instance (credentials + surface selection) from the console — no addon install | P0 | 3 |
| OD-2 | The bot answers on Odoo Live Chat / Helpdesk grounded in the same knowledge base | P0 | 3 |
| OD-3 | The bot reads/acts on Odoo records (order lookup, ticket create, CRM update) under the same allow/deny governance | P1 | 3 |
| OD-4 | Handoff routes to Odoo agents / the shared inbox | P1 | 3 |

### 5.8 Human Handoff

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| HH-1 | Escalation on explicit request, unsafe content, low confidence, or plan capacity | P0 | 1 ✅ |
| HH-2 | The moment a human takes over, the bot goes silent — they never talk over each other | P0 | 1 ✅ |
| HH-3 | Agents get a live inbox with pending/active queues, full transcript, and reply-as-agent (name shown to the customer) | P0 | 1 ✅ |
| HH-4 | The tenant is notified immediately (email; push notification to the console) | P0 | 1 ✅ |
| HH-5 | If the customer has left the page, the conversation can continue by email fallback | P1 | 1 ✅ |
| HH-6 | The bot only promises a human when the system can actually deliver one | P0 | 1 ✅ |

### 5.9 Contacts

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| CT-1 | Conversation-captured contacts stored as leads, per tenant | P1 | 1 ✅ |
| CT-2 | A lead matching a known customer email is promoted to customer automatically | P1 | 1 ✅ |
| CT-3 | Contact list is viewable/manageable in the console and isolated per tenant | P0 | 1 ✅ |

### 5.10 Console & Analytics

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| CO-1 | Playground: chat with the real bot (same pipeline as production) before going live; free, unmetered | P0 | 1 ✅ |
| CO-2 | Conversation list + full transcripts with resolution/handoff status | P0 | 1 ✅ |
| CO-3 | Analytics: conversations, deflection rate, handoffs, usage vs quota | P0 | 1 ✅ |
| CO-4 | Model settings: managed (platform keys) or BYOK (tenant's own key) with the plan price reflecting the choice | P0 | 1 ✅ |
| CO-5 | Usage page shows the effective rate and consumption transparently — no bill shock | P0 | 1 ✅ |
| CO-6 | White-label settings (brand, domain) for agency tenants | P1 | 4 |

### 5.11 Plans, Billing & Metering

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| BI-1 | Billable unit = one conversation per client per 24h window (many messages = 1) | P0 | 1 ✅ |
| BI-2 | Hard-cap quotas with an upgrade prompt — never a surprise bill | P0 | 1 ✅ |
| BI-3 | Non-payment degrades to handoff-only mode instead of cutting off the tenant's customers | P0 | 1 ✅ |
| BI-4 | Managed vs BYOK pricing (BYOK discounted; tenant pays their model provider directly) | P0 | 1 ✅ |
| BI-5 | Region-appropriate payment methods (Indonesia local rails; global cards/MoR) | P1 | 1–2 |
| BI-6 | Usage-based overage billing (beyond hard cap) | P2 | 2+ |

### 5.12 Platform Operations (SaaS owner)

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| OP-1 | Separate operator console with allowlist-gated access and role tiers (superadmin/operator) | P0 | 1 ✅ |
| OP-2 | Operator accounts provision automatically on deploy — no manual server/database work | P0 | 1 ✅ |
| OP-3 | Platform model keys registered and validated in the console, stored encrypted, powering managed-mode tenants | P0 | 1 ✅ |
| OP-4 | Tenant overview with mode-aware MRR estimate | P1 | 1 ✅ |
| OP-5 | Per-tenant cost monitoring and anomaly alerts | P1 | 2+ |

### 5.13 Bot Types & Skills (later)

| ID | Requirement | Priority | Phase |
|---|---|---|---|
| SK-1 | Skills library the bot can invoke: book appointment, check order, create ticket, collect lead | P1 | 2–4 |
| SK-2 | Custom skills via a webhook contract, governed by roles and data-access rules | P2 | 4 |
| SK-3 | Internal **Assistant** bot type for the tenant's own team — broader scope, more agentic, per-employee memory | P2 | 4 |
| SK-4 | Agency/reseller multi-tenant white-label mode | P1 | 4 |

## 6. Key User Journeys

1. **Go live (Owner Olivia):** register → verify email → name workspace → upload
   docs → set persona → try the playground → generate widget snippet → paste
   before `</body>` → first real conversation appears in the console. Target
   under 15 minutes.
2. **Customer gets help (end customer):** opens chat → asks in their own words →
   grounded, streamed answer with the business's tone → shares name/email when
   asked → returns next week and is remembered.
3. **Escalation (Support Sam):** customer asks for a human → bot goes quiet and
   confirms the request → Sam gets an email/push → opens the live inbox → replies
   as himself → resolves → bot resumes for future messages.
4. **WhatsApp connect (Phase 2):** Console → Channels → WhatsApp → guided Meta
   signup popup (or QR pairing in gateway mode) → the same bot answers the
   business's WhatsApp number.
5. **Operator day-to-day:** admin login → tenants overview and MRR → register or
   rotate platform model keys → keys validated live and stored encrypted.

## 7. Release Plan (product view)

| Release | Contents | Status |
|---|---|---|
| **Phase 1 — Web MVP** | Everything marked Phase 1 above: knowledge, memory, guardrails, widget, handoff, contacts, console, billing, operator console | ✅ Built & deployed (private beta) |
| **Phase 2 — WhatsApp** | WA-1…6, cross-channel identity start, skills v1 | Specified — next build |
| **Phase 3 — Odoo** | OD-1…4, memory across channels | Planned |
| **Phase 4 — Scale** | White-label, Assistant bot, custom skills, vertical templates, enterprise (SSO/SLA/residency) | Planned |

## 8. Non-Functional Requirements (product-level)

| Area | Requirement |
|---|---|
| Responsiveness | Replies begin streaming fast enough to feel conversational; widget stays lightweight on the tenant's site |
| Availability | The widget and channels keep serving customers even when a tenant's plan lapses (degraded handoff-only mode) |
| Isolation & privacy | Strict per-tenant isolation of knowledge, memory, contacts, transcripts; customer content never leaves the platform via third-party notifications |
| Compliance posture | Designed for GDPR and Indonesia's PDP Law: consent, retention controls, real deletion, audit trails |
| Security | Origin-locked public keys, secrets never in the browser, encrypted stored provider keys, least-privilege data access, rate limiting on all endpoints |
| Localization | Multilingual conversations from day one; console UI in English + Indonesian at launch, German next |
| Accessibility | Widget usable by keyboard and screen readers |

## 9. Assumptions & Dependencies

- LLM providers (managed keys or tenant BYOK) remain available and priced within
  the unit-economics model (doc 05).
- WhatsApp official mode depends on Meta business verification and template
  approval timelines; gateway mode carries tenant-acknowledged ban risk (doc 20).
- Odoo channel depends on tenant Odoo version/edition and API credentials.
- Market sizing and final pricing quotas to be validated before fundraising
  (docs 03 §5, 05 §4).

## 10. Open Questions

- Final product name (trademark/domain) — doc 07 §9.
- Exact conversation quotas per tier after measuring real cost per conversation.
- Whether WhatsApp/Odoo remain tier-gated or become paid add-ons.
- Self-serve password reset (currently manual; tracked as future work — doc 17).

## 11. References

| Doc | What it adds |
|---|---|
| [21 — BRD](./21-brd.md) | Business case, market, pricing, competitive position |
| [10 — PRD: MVP web chatbot](./10-prd-mvp-chatbot.md) | Engineering-depth MVP requirements |
| [11 — PRD: Context Engine](./11-prd-context-engine.md) | Knowledge/memory engine requirements |
| [12](./12-trd-web-widget.md) / [18](./18-widget-install.md) | Widget technical contract & install guide |
| [19 — Human handoff](./19-human-handoff-live.md) | Handoff build plan (built) |
| [20 — WhatsApp channel](./20-whatsapp-channel.md) | WhatsApp build plan (next) |
