# proctOR Chatbot Demo Script — 15-Minute Tobias Pitch

> Purpose: Run this flow live with Tobias to demonstrate Conversa trained on his own product. He types the questions; the bot answers from this knowledge base. The script also notes what to highlight at each step and how to steer toward the deal.
> Tone of the demo: let the bot do the talking — Conversa is the proof. You facilitate, close.

---

## Setup (Before the Call)

- [ ] Widget installed on a proctOR-branded demo page (or the console Playground).
- [ ] Persona: "proctOR Expert Concierge" (see `proctor_chatbot_persona_and_pitch.md`).
- [ ] Knowledge sources uploaded: all `proctor-kb-01…08` docs + master KB + FAQ.
- [ ] Handoff to a human configured (agent inbox open on your side) for the escalation demo.
- [ ] Screen ready to show: the widget in a clean browser window, analytics/console in the next tab.

**Demo philosophy:** "Tobias, this is trained on your product. Ask it anything about proctOR." Then hand him the keyboard.

---

## Act 1 — Product Overview (0:00–2:30)

**You say:** *"This is Conversa, trained entirely on proctOR's own knowledge. Type whatever you'd ask about your product."*

**Sample prompts for Tobias:**
1. **"What is proctOR?"**
   → Expect: mobile-first marketplace connecting medical professionals for remote surgical support via preceptorship and proctorship.
2. **"How does it work?"**
   → Expect: verified doctors mentor/learn, sessions booked with coins in escrow, no patient data stored.

**Highlight:** Answer is grounded in *his* docs — no prompt engineering, no scripts. Note the **citations** (it points to the source document).

---

## Act 2 — User Workflow (2:30–6:00)

**Say:** *"Now let's see the real user journeys — a mentee booking, and the wallet."*

**Sample prompts:**
1. **"I'm a resident who wants to learn a new procedure. What do I do?"**
   → Expect: register → verify credentials → search specialty → book a preceptorship → coins reserved in escrow.
2. **"What happens if I cancel 5 hours before a session?"**
   → Expect: <24h cancellation = 0% refund, coins forfeited (KB-02 §5).
3. **"How does the coin system work?"**
   → Expect: 1 coin = €10, buy via Shopify, escrow on booking, released to mentor on completion.
4. **"Can I be both a mentor and a mentee?"**
   → Expect: yes — dual-role, per specialty (KB-01 §4).

**Highlight:** It understands **workflow logic** (booking → escrow → release), not just keyword matching. Memory: ask it again in a new session — *"I'm the ortho resident from before"* — and watch it continue.

---

## Act 3 — Company Module (6:00–9:00)

**Say:** *"Now the B2B side — this is what hospitals and device makers buy."*

**Sample prompts:**
1. **"Can our hospital run a private training network without other hospitals seeing our mentors?"**
   → Expect: Company Module, private invitation-only marketplace, complete isolation (KB-04 §3.2).
2. **"How do we sponsor our residents?"**
   → Expect: Company Wallet → bulk coins → atomic transfers to resident wallets.
3. **"Can a surgeon work with several hospitals?"**
   → Expect: dual membership, public + multiple company marketplaces (KB-04 §3.3).

**Highlight:** This is the **recurring SaaS** story — flat monthly fee + bulk coins. Tobias sees how institutions buy proctOR.

---

## Act 4 — Trust & Compliance (9:00–11:00)

**Say:** *"Now the part that usually kills deals — privacy."*

**Sample prompts:**
1. **"How do you handle patient privacy and GDPR?"**
   → Expect: no patient data stored by design, EU-hosted, full GDPR rights (KB-05 §3).
2. **"Are live surgery videos recorded?"**
   → Expect: no — external smart-glass links, unrecorded video calls (KB-05 §2).
3. **"How do you know mentors are real doctors?"**
   → Expect: manual credential verification by Medical Reviewers (KB-01 §3).

**Highlight:** This is proctOR's **structural moat** — zero medical data liability. The bot articulates it perfectly because it's grounded in the compliance doc.

---

## Act 5 — Human Handoff (11:00–12:00)

**Say:** *"And when the bot isn't enough, it escalates to a human — right here in my inbox."*

**Prompt:** **"I want to talk to a real person about a refund problem."**

- The bot acknowledges and hands off cleanly (it goes silent).
- You show the **live agent inbox** on screen and reply as yourself.

**Highlight:** Full conversation state machine — bot → handoff pending → agent active. This is the feature that makes enterprise clients comfortable.

---

## Act 6 — Investor Angle & Close (12:00–15:00)

**Say:** *"Want to see it from an investor's angle? It can pitch your own business model back to you."*

**Sample prompts:**
1. **"How does proctOR make money?"**
   → Expect: ~50% B2C spread + flat B2E subscription + bulk coins (KB-08 §3).
2. **"Why is this a good market to be in?"**
   → Expect: fragmented ad-hoc market, GDPR-safe architecture, demand-driven growth via tickets (KB-08 §4–5).
3. **"What's the roadmap?"**
   → Expect: Phase 1 EU/Germany launch; Phase 2 automated payouts, AI matching, self-service onboarding.

**Close (Approach A — customer first):**
> *"That's Conversa, live on your product in the demo. I can have it integrated into proctOR for €1,800, first month free, then $69–99/mo. Twelve months at standard pricing. I show you results — deflection, after-hours coverage — and in a few months I'd love to talk about something bigger."*

---

## Contingency Lines

| If Tobias says… | You say… |
|---|---|
| "Does it work on WhatsApp?" | "The same brain runs on WhatsApp — that's the next build on the roadmap. Same knowledge, same memory, same handoff." |
| "How long to set this up?" | "Under a day for integration; the knowledge base is already trained on proctOR." |
| "What does it cost to build from scratch?" | "€15–20K and months. This is live today." |
| "How is this different from a rule-based bot?" | "It answers anything in his words, grounds every answer in his docs, and remembers returning users." |
| "What about patient data going through the bot?" | "Same rule as proctOR — the bot is trained on business/process knowledge, never patient data." |

---

## After the Demo (Next Steps)

1. Send the **Phase 1 email** (see `02-funding-strategy.md`).
2. Send a short recap: what Tobias asked + what the bot answered (proof of grounding).
3. Book the integration kickoff.
4. In Month 3–4, run the **Phase 2 investment ask** with his own usage analytics.
