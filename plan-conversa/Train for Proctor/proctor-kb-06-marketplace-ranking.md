# proctOR Knowledge Base 06 — Marketplace, Matching & Reputation

> Audience: Mentors, mentees, marketplace managers, and chatbot training.
> Purpose: How users discover each other, how reputation drives visibility, and how proctOR learns market demand.

---

## 1. Search & Discovery

- Users search the marketplace by:
  - **Specialty / subspecialty** (e.g., orthopedics, minimally invasive surgery)
  - **Procedure or skill** (e.g., laparoscopic cholecystectomy)
  - **Mentor name** or institution
  - **Availability** and **time zone**
- Filtering options: session model (preceptorship vs. proctorship), price range, rating threshold, verified status, language.

### 1.1 Public Profiles

- Every verified mentor has a public profile showing:
  - Name, specialty, credentials, and verified badge
  - Average rating and review count
  - Completion rate and session count
  - Availability and languages

---

## 2. Ratings & Reviews

- **Mandatory for both parties** after every completed session.
- Users rate on key dimensions (clarity, punctuality, communication, expertise) and leave a written review.
- Reviews are **deterministic and tamper-proof** — a user cannot delete or edit a rating given.

---

## 3. Reputation & Ranking Algorithm

Mentor visibility is determined by a **simple, deterministic ranking** using transparent metrics:

| Signal | Why it matters |
|---|---|
| **Average rating** | Direct quality signal |
| **Completion rate** | Reliability — share of booked sessions actually completed |
| **Session count** | Experience and marketplace participation |
| **Response time** | Responsiveness to messages and requests |

- Higher-ranked mentors appear first in search and get more booking volume.
- Because the ranking is deterministic and transparent, users understand exactly what to improve.
- New mentors start with a "new" status and build ranking through completed, well-rated sessions.

---

## 4. Trust & Safety Signals

- Every profile is **verified** before they can transact (KB-01).
- Reviews and completion rates are visible to counterparties before booking.
- Repeated no-shows or cancellations degrade the user's ranking.

---

## 5. Demand-Led Growth (Ticket System)

- When a mentee searches for a specialty/procedure that has **no available mentors**, proctOR logs an automated **demand ticket** in the Operator Dashboard.
- This gives proctOR **real-time market demand data**:
  - Which specialties are underserved
  - Which regions/countries have demand
  - Which procedures surgeons are asking for
- Operators use demand tickets to **recruit in-demand specialists** and close the supply gap.

### 5.1 Why This Matters

- Growth is **demand-driven**, not guesswork — proctOR recruits exactly where the market signals need.
- It turns the marketplace into a self-improving flywheel: more demand → targeted recruitment → better coverage → more users.

---

## 6. The Matching Flywheel

1. Underserved specialty search → **demand ticket logged**
2. proctOR recruits and verifies mentors in that specialty
3. Supply appears → mentees book → ratings build → visibility grows
4. More activity attracts more mentors and mentees → network effects compound

---

## 7. Common Questions (FAQ)

| Question | Response |
|---|---|
| How do mentors get ranked? | By a deterministic mix of average rating, completion rate, session count, and response time. |
| Can I delete a bad rating? | No — ratings are mandatory and tamper-proof. Both parties can respond in a comment thread. |
| How do I get found as a new mentor? | Complete sessions with high ratings and fast responses; ranking builds automatically. |
| What if no mentor exists for my specialty? | Your search logs a demand ticket, and proctOR prioritizes recruiting mentors in that specialty. |
| Are ratings anonymous? | Reviews are shown with the reviewer's role context; abusive reviews are subject to review by proctOR. |
| Is my reputation tied to a specific specialty? | Reputation is tracked per role and per specialty, so your mentoring record in one field doesn't conflate with another. |
