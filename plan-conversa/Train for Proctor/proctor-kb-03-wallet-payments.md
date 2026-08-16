# proctOR Knowledge Base 03 — Coins, Wallet & Payments

> Audience: Mentors, mentees, finance/admins, and chatbot training.
> Purpose: The complete coin economy: value, purchase, escrow, refunds, payouts, taxes, and ledger integrity.

---

## 1. The Coin System — Overview

- proctOR uses an internal digital currency called **coins**.
- **1 coin = €10** (fixed exchange ratio).
- Coins power every transaction on the platform: booking sessions, paying mentors, and sponsoring training.
- The coin ledger is **immutable and fully auditable** — every credit, reservation, release, and refund is recorded.

---

## 2. Purchasing Coins

### 2.1 How Mentees Buy Coins

- Coins are purchased **in-app** through the integrated **Shopify** checkout (invoicing handled by Shopify).
- Accepted payment methods follow Shopify's regional rails: EU cards, SEPA/alternative methods, and market-standard payment processors.
- VAT/tax handling is applied at checkout based on the buyer's country.

### 2.2 Coin Packages

- Coins are sold in bundles (e.g., starter / standard / large packs). Packs are always priced at the **€10/coin ratio**; larger packs may include a small bonus for frequent users.
- Unused coins remain in the user's wallet and do not expire (unless a company wallet policy says otherwise — see KB-04).

---

## 3. Wallet Mechanics

| Concept | Rule |
|---|---|
| **Wallet balance** | Each user holds coins in a single wallet. Coins earned vs. spent are tracked separately in the ledger. |
| **Reservation (escrow)** | On booking, coins are **reserved** from the mentee's wallet. They are held, not spent. |
| **Release** | Coins transfer to the mentor's wallet **only after the mentor confirms session completion**. |
| **Refund** | Coins return to the mentee's wallet per the cancellation policy (KB-02 §5). |
| **Company sponsorship** | Companies can transfer coins from a Company Wallet to employee/resident wallets to sponsor training (KB-04 §3). |

### 3.1 Escrow Reservation Logic

1. Mentee books session → required coins are **reserved** (deducted from available balance, held in escrow).
2. Session runs → mentor confirms completion.
3. Escrow releases → mentor wallet credited; transaction finalized in the immutable ledger.
4. If cancelled per policy → escrow returns to mentee wallet (or releases to mentor in the <24h forfeit case).

---

## 4. Mentor Payouts (Cash-Out)

- Mentors convert earned coins into fiat currency via **manual payout requests**.
- Payout flow:
  1. Mentor submits a payout request from their wallet.
  2. Request is **audited** by proctOR Finance Admins.
  3. Approved payouts are processed via a verified bank account/IBAN and completed within **defined business days** (e.g., 3–10 business days depending on destination).
- Payouts are subject to applicable taxes; proctOR provides transaction reports to support the mentor's own tax filing.
- **Automated payouts** are on the Phase 2 roadmap (KB-08 §5).

---

## 5. Commission & Platform Revenue

- **B2C (Public Marketplace):** proctOR earns a **spread/commission** of approximately **50%** between the coin purchase price (€10/coin) and the mentor's payout rate. Mentors are paid a **payout rate per coin** below the purchase price; the difference is proctOR's take.
- **B2E (Company Module):** companies pay a **flat monthly subscription** for the private marketplace, plus bulk coin package sales for sponsored mentees (KB-04 §4).

---

## 6. Ledger Integrity & Financial Security

- All financial ledger actions are **tamper-proof and auditable**, backed by EU-hosted REST API backends.
- Purchase processing is powered by **Shopify**, which handles invoicing, VAT where applicable, and the actual payment rails.
- proctOR Finance Admins control payout processing; no marketplace user can modify a ledger entry.

---

## 7. Common Questions (FAQ)

| Question | Response |
|---|---|
| How much is 1 coin worth? | 1 coin = €10. |
| Can I buy coins with a credit card? | Yes, through the integrated Shopify checkout. |
| When do coins leave my wallet? | Coins are reserved at booking and only move to the mentor after the session is confirmed complete. |
| Do coins expire? | No — personal wallet coins do not expire. Company-sponsored wallet policies may differ. |
| How do I withdraw my earnings? | Submit a payout request from your wallet; Finance Admins audit it and pay to your verified bank account. |
| Are refunds returned as cash? | No — refunds are credited strictly as coins to the wallet. |
| Who processes payments? | Shopify handles purchase/invoicing; proctOR Finance Admins handle payout audits and processing. |
| Is my wallet secure? | Yes — the ledger is immutable and auditable, hosted in EU-backed infrastructure. |
| Do I pay tax on my earnings? | You are responsible for reporting earnings per your jurisdiction; proctOR provides transaction reports to help. |
