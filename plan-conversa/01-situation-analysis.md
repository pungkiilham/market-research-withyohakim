# Situation Analysis — Conversa + Proctor

> Last updated: 2026-07-25
> Purpose: Honest assessment of where we stand, the ethical trap, and available paths forward.

---

## 1. The Cast

| Person | Role | Relationship |
|---|---|---|
| **You** | PM + full-stack, co-founder Conversa | Employee at Diginergy |
| **Yohakim** | Developer, co-founder Conversa | Also works on Proctor via Diginergy |
| **Robin** | Your boss at Diginergy | Controls Proctor engagement, not involved in Conversa |
| **Tobias** | Founder of Proctor App | Diginergy client, potential Conversa investor/customer |

---

## 2. Current State

### Proctor App (Diginergy)
- €30K spent on MVP (already built)
- €15K ongoing at Diginergy for Phase 1 completion
- Complex app: Zoom SDK, multi-role, coin wallet, Shopify, calendar sync, company module
- Robin pushing Odoo as payment gateway over your objection
- Yohakim is the developer on this project

### Conversa
- MVP built: web widget, knowledge base, Gravija engine, memory, handoff, console, billing
- Zero users, zero revenue
- Needs funding to operate and grow

### Relationship with Tobias
- You've already hinted at frustrations with Robin to Tobias
- Tobias knows you and Yohakim can deliver
- Tobias needs a chatbot for Proctor

---

## 3. The Core Dilemma

```
You work at Diginergy
    ↓
Tobias is a Diginergy client (€15K active)
    ↓
You want Tobias to fund Conversa
    ↓
BUT: If you ask him to move Proctor work to you directly
     → That's poaching a client from your employer
     → Major ethical red flag for Tobias too
     → Could backfire badly with Robin if discovered
    
AND: If you only pitch Conversa as a separate product
     → Tobias might not have budget beyond the €15K
     → Harder to close
```

---

## 4. The Robin Problem (Context)

From what you've shared, the friction with Robin isn't personal — it's structural:

| Issue | Robin's View | Your View | Who's Right? |
|---|---|---|---|
| UI/UX depth | Stop at mockup, use common sense | Need detailed design for complex app | **You** — Proctor has Zoom, multi-role, payments. "Common sense" doesn't cover edge cases. |
| Dev approach | Simple CRUD, ship fast | Complex app needs proper architecture | **You** — Medical marketplace + Zoom SDK + payment = not a CRUD app |
| Odoo as payment gateway | Odoo has modules, manual approve for cashout | Stripe/PayPal direct is more secure and simpler | **You** — Odoo is an ERP, not a payment processor. For a platform handling mentor payouts with German tax compliance, Stripe Connect or similar is the correct choice. Odoo manual approval adds operational overhead and risk. |

**Reality check:** Robin's "simplify everything" approach makes sense for small projects. Proctor is not a small project. Your pushback is justified.

But here's the hard truth: **Robin is still your boss.** And Tobias hired Diginergy, not you personally.

---

## 5. Tobias's Perspective (Investor Lens)

If I were Tobias, here's what I'd think:

**What I know:**
- I spent €30K on Proctor MVP
- I'm paying €15K to Diginergy for more work
- The PM (you) and developer (Yohakim) seem competent
- The PM has hinted that Robin makes questionable decisions
- I need a chatbot for my platform

**What concerns me:**
- "You're asking me to move money from your employer to you directly — what happens if Robin finds out?"
- "If you're willing to poach Diginergy's client, would you poach mine later?"
- "Can you actually deliver both Proctor work AND Conversa?"
- "What's the legal structure? Do you have a company?"

**What I like:**
- I know you, we've worked together
- Conversa is already built — cheaper than building from scratch
- I need a chatbot anyway
- You understand my business

---

## 6. The Ethical Path Forward

There are only three clean ways to do this:

### Path A: Separate Engagement (Recommended)
Keep Proctor at Diginergy. Pitch Conversa as a **new, separate project**:

> "Tobias, we built Conversa independently. It's an AI chatbot platform. You need a chatbot for Proctor. Instead of building one from scratch (€€€), let us integrate Conversa into Proctor as a separate engagement — outside Diginergy, outside Proctor contract. €X for integration + license."

**Pros:** No poaching. Clean. Tobias gets chatbot at fraction of build cost.
**Cons:** Tobias needs separate budget beyond the €15K.

### Path B: Wait + Transition
Complete the current €15K Proctor engagement at Diginergy professionally. Once it's done, then pitch Tobias directly for Phase 2 Proctor work + Conversa together.

**Pros:** Zero ethical conflict. Clean break.
**Cons:** Timing uncertainty. Conversa needs funding now.

### Path C: Open Conversation with Tobias + Robin
"Robin, Tobias needs a chatbot. We built one. Can we spin this as a separate project?"

**Pros:** Transparent. No risk of burning bridges.
**Cons:** Robin might say no, or want a cut. Unlikely to work given the friction.

---

## 7. Financial Reality Check

### What Conversa Actually Needs

| Scenario | Monthly Burn | 12-Month Total | What It Covers |
|---|---|---|---|
| **Survival** (keep day job) | ~$200 | $2,400 | Infra + LLM credits + domain |
| **Lean** (part-time focus) | ~$600 | $7,200 | Infra + LLM + basic ads + incorporation |
| **Serious** (near full-time) | ~$1,500 | $18,000 | Above + partial stipend for you/Yohakim |

### What Tobias Can Realistically Give

| Deal Type | Amount to Conversa | Tobias Gets |
|---|---|---|
| **Conversa license + integration** | €5,000–8,000 | Working chatbot integrated into Proctor |
| **Equity investment** (SAFE) | €5,000–15,000 | Equity in Conversa at pre-seed valuation |
| **Bundle** (Proctor work discount → Conversa funding) | Complex ethics | See note above |

### The €15K Reality

Tobias's €15K at Diginergy covers Proctor Phase 1 work. If you could redirect even €5K of that to Conversa, it would fund 12+ months of lean operations. But the poaching risk makes this dangerous.

---

## 8. Recommendation

### Short-term (Next 2 Weeks)
1. **Do NOT ask Tobias to move Proctor from Diginergy.** This burns trust with both Robin and Tobias.
2. **Prepare the Conversa pitch as a separate offer:**
   - "Tobias, separate from the Diginergy engagement — we built an AI chatbot platform. It's ready. Here's what it would cost to integrate into Proctor."
3. **Price it at €5,000–7,000** for integration + 12-month license.
4. If Tobias says yes, you have: first customer (case study), €5-7K revenue (12+ months runway), and zero ethical issues.

### Medium-term (2-3 Months)
1. Use Tobias as a case study to get 5-10 more customers.
2. Keep your Diginergy job until Conversa shows traction.
3. Once you have paying customers and revenue, then consider full-time.

### Long-term (6 Months)
- Revisit the conversation with Tobias about investment (not just payment)
- By then, you'll have traction to negotiate proper valuation

---

## 9. One Hard Truth

> **You cannot escape the Robin problem by going around it.**

If you poach Tobias from Diginergy:
- You might get €5-15K short-term
- But you damage your reputation with Tobias (he'll wonder if you'd do the same to him)
- You create an enemy in Robin
- You set a precedent that you're ok with cutting corners

If you pitch Conversa **as a standalone product** to Tobias:
- Clean deal
- Tobias respects you for being professional
- Robin has no claim
- You build the habit of running Conversas properly from day one

---

## 10. Open Questions

- [ ] Do you have a legal entity (PT / GmbH) for Conversa?
- [ ] Has Tobias seen a live demo of Conversa?
- [ ] What's the minimum Tobias would need to pay for you to keep Conversa running for 12 months?
- [ ] Can Yohakim handle both Diginergy Proctor work + Conversa integration simultaneously?
- [ ] What's the exit if Tobias says no?

---

*This document is meant as a realistic self-assessment, not a pitch deck. Read it before making any move with Tobias.*
