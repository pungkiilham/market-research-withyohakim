# proctOR Knowledge Base 02 — Sessions, Scheduling & Calendar Sync

> Audience: Mentors, mentees, company admins, and chatbot training.
> Purpose: Full detail on how preceptorship and proctorship sessions are created, booked, scheduled, and cancelled.

---

## 1. The Two Session Models

proctOR supports two complementary remote-surgical-support models:

| Feature | **Preceptorship** | **Proctorship** |
|---|---|---|
| **What it is** | A mentor *offers* structured teaching/guidance sessions on a skill or procedure. | A mentee *requests* live help for a specific case, skill, or procedure. |
| **Who initiates** | The **Mentor** publishes an offer. | The **Mentee** publishes a request for help. |
| **Who chooses** | Mentees book the published offer (first-come, capacity permitting). | Mentees invite multiple candidate mentors and select one (or more). |
| **Capacity** | Mentor defines how many participants a session accepts. | Mentee controls how many mentors participate. |
| **Payout** | Reserved coins release to the mentor on confirmation of completion. | Each participating mentor is paid individually for their contribution. |

---

## 2. Creating a Session

### 2.1 Mentor → Preceptorship Offer

The Mentor provides:
- Session title & description (procedure, skills covered)
- Specialty & subspecialty tags
- Date/time slot(s) with duration (typical 30–90 min)
- **Participant capacity** (1:1 or small group)
- Session price in coins
- Optional prerequisites for participants

**Booking rule:** Once an offer is published, mentors **cannot reject bookings**. The calendar sync and availability settings are the mentor's protection against double-booking.

### 2.2 Mentee → Proctorship Request

The Mentee provides:
- Procedure / skill they need help with
- Description of the case and what support is needed (without any patient-identifiable data — see KB-05)
- Preferred timing and time zone
- Coin budget for the session
- Option to invite specific verified mentors or open it to matching

Candidates respond via chat, the mentee negotiates details, and selects the mentor(s).

---

## 3. Booking & Scheduling Mechanics

### 3.1 Booking Flow

1. Mentee finds an offer or a mentor's profile via search.
2. Mentee selects a time slot within the mentor's published availability.
3. On booking, coins are **reserved in escrow** from the mentee's wallet.
4. Both parties receive an in-app notification + calendar invite.
5. Session appears in the **Schedule** tab of both users.

### 3.2 Two-Way Calendar Sync

- proctOR offers **two-way synchronization** with Google Calendar, Microsoft Outlook, and Apple iCal.
- Booked sessions are written into the doctor's external calendar; the doctor's external calendar availability is respected when proposing slots.
- Sync prevents conflicts and reduces no-shows — a core value prop for practicing surgeons with packed schedules.

### 3.3 Time Zones (EU-First)

- Sessions are displayed in the **user's local time zone** automatically.
- Scheduling surfaces show the counterpart's time zone to avoid confusion.
- The platform is designed for **cross-European time zones** (e.g., a mentor in Berlin mentoring a mentee in Paris or Madrid with no coordination overhead).

---

## 4. Running the Session

### 4.1 Live Remote Guidance

- **Live procedure feeds** are streamed via third-party **smart glass applications** using link-based access manually shared in-app. proctOR does not host, process, or store the stream.
- **Pre/post-session consultation** uses the integrated video-call SDK (Zoom) for quick calls. These are live-only and **never recorded**.
- In-app chat supports messaging, file notes (no patient data), and coordination before/after sessions.

### 4.2 Confirmation of Completion

- At the end of the session, the **mentor confirms completion** in-app.
- Confirmation releases the reserved coins from escrow into the mentor's wallet.
- Both parties are then prompted to leave a **rating and review** (mandatory).

---

## 5. Cancellation & Refund Policy

| Scenario | Result |
|---|---|
| **Mentee cancels > 24 hours before start** | 100% of reserved coins refunded to mentee wallet. |
| **Mentee cancels < 24 hours before start** | 0% refund — reserved coins are forfeited (released to mentor as compensation for held time). |
| **Mentor cancels (any timing)** | Full refund of reserved coins to the mentee wallet, regardless of timing. |
| **Both agree to cancel** | Full refund to mentee wallet. |
| **Refund currency** | Refunds are credited **only as coins**, never converted back to cash automatically. |

### 5.1 No-Show Handling

- If a mentee does not join at the scheduled time, the same cancellation window logic applies (treated as a <24h cancellation).
- Repeated no-shows are reflected in the user's reputation profile.

---

## 6. Common Questions (FAQ)

| Question | Response |
|---|---|
| Can a mentor reject a booking? | No. Published preceptorship offers accept bookings automatically up to capacity. Two-way calendar sync prevents conflicts. |
| What if a mentor is double-booked? | Calendar sync blocks overlapping availability, so double-booking should not occur. If a conflict happens, the mentor cancels and the mentee is fully refunded. |
| Can a group session have several mentees? | Yes — the mentor sets participant capacity, and group preceptorships are supported. |
| Is the session recorded? | No. Live surgery feeds use external smart-glass links and consultations use unrecorded video calls. Nothing is stored on proctOR. |
| How do I change my availability? | Update your availability settings; two-way sync updates your external calendars and vice versa. |
| What time zone are sessions shown in? | Always your local time, with the counterpart's zone shown to avoid confusion. |
