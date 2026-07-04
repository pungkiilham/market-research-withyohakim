# Strategy Review & Brainstorm
## Laundry Marketplace Platform
### Version 0.1
### July 2026

---

# Purpose

This document is **not a replacement** for the Product Plan.

Instead, this document contains strategic observations, possible risks, alternative approaches, and ideas discovered after reviewing the current product concept.

The goal is to challenge assumptions before development begins.

---

# Executive Summary

The current platform proposes a three-sided marketplace connecting:

- Customer
- Drop Point (DP)
- Machine Owner (MO)

Unlike traditional online laundry services, this model separates customer-facing operations from washing operations.

Instead of every laundry shop handling everything, the platform distributes work among specialized participants.

This is the strongest differentiation of the product.

However, several assumptions should be validated before implementation.

---

# Observation 1
## This is NOT another laundry app

Many competitors build:

Customer
↓

Laundry Shop

↓

Customer

Our proposed model becomes:

Customer
↓

Drop Point

↓

Machine Owner

↓

Drop Point

↓

Customer

This changes the platform from being a booking application into a logistics and capacity marketplace.

This distinction should become the core company positioning.

Instead of saying:

> "Find nearby laundry."

The platform could position itself as:

> "The operating system for distributed laundry services."

---

# Observation 2
## The primary customer may not be consumers

Current product positioning assumes that customers are the first target.

This assumption may not be correct.

Machine Owners experience a larger pain point.

Common problems:

- expensive washing machines
- idle capacity
- inconsistent order volume
- dependence on walk-in customers

Example:

Laundry Capacity

100 kg/day

Actual Orders

35 kg/day

Unused Capacity

65 kg/day

The marketplace can monetize unused capacity.

Instead of selling laundry,

the platform sells:

> Washing Capacity.

This changes the marketing strategy significantly.

Current Message

"Find laundry nearby."

Alternative Message

"Earn more from your washing machines."

---

# Observation 3
## Drop Point responsibilities may be too heavy

Current DP responsibilities:

- receive clothes
- weigh
- inspect
- create order
- store clothes
- hand over
- receive from MO
- return to customer
- collect payment

This is already close to operating a small laundry business.

Question:

Would convenience stores, kiosks, or neighborhood shops be willing to perform this much work?

Possible solution:

Create multiple DP levels.

---

### DP Level 1
Agent

Responsibilities

- receive package
- return package

No weighing.

No pricing.

No inspection.

Lowest barrier to entry.

---

### DP Level 2
Standard Drop Point

Responsibilities

- weighing
- inspection
- storage
- customer interaction

Current proposed model.

---

### DP Level 3
Professional Partner

Target:

- apartments
- hotels
- offices
- campuses

Can process larger volume and business customers.

---

# Observation 4
## Subscription may slow adoption

Current revenue:

- commission
- subscription

Early marketplaces usually avoid subscriptions.

Reason:

Partners only want to pay after receiving value.

Alternative approach:

Free registration.

Platform earns from transaction commissions.

Future premium services:

- priority order access
- analytics
- insurance
- featured listing
- faster withdrawal
- premium support

---

# Observation 5
## Trust is missing from the product plan

Marketplace success depends heavily on trust.

Technology alone is insufficient.

Recommended Trust Framework

---

Identity

- KTP verification
- selfie verification
- machine verification
- business verification

---

Quality

- before washing photos
- after washing photos
- digital weight record
- QR sealed laundry bags

---

Protection

- damaged clothes policy
- lost clothes compensation
- refund mechanism
- optional insurance

---

Reputation

Suggested public metrics

- rating
- completion rate
- on-time percentage
- complaint ratio
- repeat customer rate

Trust becomes one of the biggest competitive advantages.

---

# Observation 6
## Capacity Marketplace

One exciting opportunity is exposing available washing capacity.

Example

Machine Owner A

Capacity

80 kg/day

Booked

45 kg

Remaining

35 kg

Platform automatically routes orders toward available capacity.

Benefits

- better utilization
- shorter turnaround
- fairer distribution
- scalable matching algorithm

Eventually the platform becomes a marketplace for capacity rather than simply laundry services.

---

# Observation 7
## Order Assignment

Avoid allowing Machine Owners to freely choose orders.

Reason:

Partners naturally cherry-pick the easiest jobs.

Suggested approach:

Algorithmic assignment.

Assignment Score

=

Distance

+

Remaining Capacity

+

Rating

+

On-time Performance

+

Acceptance Rate

Benefits

- fair distribution
- predictable customer experience
- easier SLA management

---

# Observation 8
## Flexible Pricing

Current proposal uses minimum and maximum pricing.

Potential issue:

Laundry prices differ significantly between cities.

Recommendation

Platform suggests price ranges instead of enforcing them.

Machine Owners choose pricing.

Algorithm warns when prices are significantly above or below market.

---

# Observation 9
## MVP may still be too large

Current MVP contains:

- wallet
- payment
- push notification
- QR
- maps
- rating
- admin dashboard

This is ambitious for two developers.

Suggested MVP

Customer

- register
- choose DP
- track order

Drop Point

- create order
- handover
- pickup confirmation

Machine Owner

- accept order
- update status

Admin

- dispute handling
- partner management

Everything else can wait.

---

# Observation 10
## Solve the Marketplace Cold Start

The biggest challenge is acquiring all three participant groups simultaneously.

Suggested priority

Phase 1

Machine Owners

↓

Phase 2

Drop Points

↓

Phase 3

Customers

Without supply, customer acquisition becomes ineffective.

---

# Observation 11
## Metrics That Matter

Suggested KPIs

Supply

- Active Machine Owners
- Active Drop Points

Demand

- Monthly Active Customers
- Repeat Customers

Marketplace

- Order Acceptance Rate
- Order Completion Rate
- Average Turnaround Time
- Complaint Ratio
- SLA Compliance

Business

- GMV
- Revenue
- Revenue per Order
- Customer Acquisition Cost
- Lifetime Value

Operations

- Machine Utilization
- Average Capacity Remaining
- Average Orders per Machine

---

# Strategic Alternative

Instead of launching immediately as a three-sided marketplace,

consider three evolutionary stages.

---

Stage 1

Laundry Operating System

Build software for laundries.

Goal

Acquire supply.

Learn operations.

Generate early revenue.

---

Stage 2

Capacity Sharing

Allow laundries to exchange overflow orders.

Goal

Build network effects.

Validate routing.

---

Stage 3

Customer Marketplace

Introduce customers and Drop Points.

Supply already exists.

Marketplace launches with lower cold-start risk.

---

# Long-Term Vision

Current Product

Marketplace for laundry orders.

Future Platform

Infrastructure for laundry operations.

Possible future expansion

- commercial laundry
- hotel laundry
- restaurant linen
- apartment laundry
- university laundry
- hospital laundry
- industrial uniforms
- laundry financing
- machine rental
- detergent marketplace
- predictive maintenance
- AI demand forecasting

The long-term opportunity extends far beyond consumer laundry.

---

# Key Questions For Team Discussion

## Business

- Who is our first paying customer?
- Who experiences the biggest pain today?
- Should subscriptions exist at launch?
- What is our strongest competitive advantage?

---

## Operations

- Is the DP workflow too complicated?
- Should there be multiple DP levels?
- Should all orders be algorithmically assigned?

---

## Product

- Is the MVP too large?
- Which features can be delayed?
- How do we build trust into every transaction?

---

## Growth

- How do we solve the marketplace cold-start problem?
- Which city should become the first pilot?
- What creates a defensible network effect?

---

# Final Thoughts

The proposed platform has the potential to become more than a laundry application.

Its strongest opportunity lies in becoming the operating infrastructure for distributed laundry capacity.

If executed correctly, the platform could evolve into the standard network connecting independent laundry operators, Drop Points, and customers across Indonesia.

The greatest challenge is not software development.

The greatest challenge is designing incentives, trust, and marketplace liquidity.


# Funding Strategy, Financial Planning & Revenue Potential

## Philosophy

The goal is **not to raise as much money as possible**.

The goal is to raise **just enough capital to reduce the biggest business risks** while keeping founder ownership high.

Instead of immediately seeking a multi-billion Rupiah investment, the company should progress through several validation stages.

Each funding round should prove one major assumption before raising the next round.

---

# Funding Roadmap

| Phase | Objective | Duration | Estimated Budget | Success Metric |
|--------|-----------|----------|-----------------:|---------------|
| Phase 0 | Customer Discovery & Validation | 1 Month | Rp 10–20 Million | Interview 50–100 potential users & partners |
| Phase 1 | MVP Development | 2–3 Months | Rp 30–80 Million | Functional Android MVP ready |
| Phase 2 | Pilot Launch (1 District) | 3–6 Months | Rp 100–200 Million | Product-Market Fit validation |
| Phase 3 | City Expansion | 6–12 Months | Rp 500 Million–1.5 Billion | Sustainable operations in one city |
| Phase 4 | Multi-City Expansion | Year 2+ | Rp 2–10 Billion | Regional expansion |

---

# Phase 0 – Customer Discovery

## Objective

Validate whether the marketplace solves a real problem.

### Activities

- Interview 30–50 customers
- Interview 20–30 Machine Owners
- Interview 20 Drop Point candidates
- Observe daily laundry operations
- Validate pricing expectations
- Validate commission expectations
- Understand biggest operational pain points

### Estimated Cost

| Item | Estimated Cost |
|------|---------------:|
| Transportation | Rp 5 Million |
| Food & Meetings | Rp 3 Million |
| Incentives for Interviewees | Rp 7 Million |
| Miscellaneous | Rp 5 Million |

**Estimated Total**

**Rp 10–20 Million**

---

# Phase 1 – MVP Development

## Objective

Build the minimum product capable of running real transactions.

### Scope

Customer App

- Registration
- Order Tracking

Drop Point App

- Create Order
- QR Handover

Machine Owner App

- Accept Order
- Update Status

Admin Dashboard

- User Management
- Order Monitoring
- Dispute Resolution

### Estimated Cost

| Item | Estimated Cost |
|------|---------------:|
| VPS & Infrastructure | Rp 5 Million |
| Domain & Services | Rp 2 Million |
| Test Devices | Rp 10 Million |
| Miscellaneous | Rp 15 Million |

**Estimated Total**

**Rp 30–80 Million**

*(Assuming development is performed by the founders.)*

---

# Phase 2 – Pilot Launch

## Objective

Validate Product-Market Fit within one district.

### Suggested Pilot Scale

| Metric | Target |
|--------|-------:|
| District | 1 |
| Drop Points | 10 |
| Machine Owners | 30 |
| Customers | 300–500 |

### Budget Allocation

| Item | Estimated Cost |
|------|---------------:|
| Marketing Campaign | Rp 50 Million |
| Referral Rewards | Rp 40 Million |
| Operations | Rp 30 Million |
| Customer Support | Rp 20 Million |
| Insurance Reserve | Rp 20 Million |
| Contingency | Rp 40 Million |

**Estimated Total**

**Rp 100–200 Million**

---

# Phase 3 – City Expansion

## Objective

Expand after proving Product-Market Fit.

### Target Scale

| Metric | Target |
|--------|-------:|
| Drop Points | 100+ |
| Machine Owners | 300+ |
| Customers | 10,000+ |

### Estimated Budget

| Category | Estimated Cost |
|----------|---------------:|
| Hiring | Rp 300 Million |
| Marketing | Rp 400 Million |
| Operations | Rp 300 Million |
| Technology | Rp 100 Million |
| Working Capital | Rp 400 Million |

**Estimated Total**

**Rp 500 Million–1.5 Billion**

---

# Suggested Initial Fundraising

Instead of raising billions immediately,

consider raising:

## Pre-Seed

**Rp 300 Million**

### Budget Breakdown

| Category | Budget |
|----------|---------:|
| MVP Completion | Rp 50 Million |
| Operations | Rp 50 Million |
| Marketing | Rp 80 Million |
| Referral Program | Rp 40 Million |
| Legal & Administration | Rp 20 Million |
| Infrastructure | Rp 10 Million |
| Emergency Reserve | Rp 50 Million |

---

# What This Funding Should Achieve

The first investment should NOT be measured by revenue.

It should prove that the marketplace works.

## Success Metrics

| KPI | Target |
|-----|-------:|
| Machine Owners | 20–30 Active |
| Drop Points | 10–20 Active |
| Registered Customers | 300–500 |
| Completed Orders | 500+ |
| Repeat Customer Rate | >40% |
| Complaint Rate | <5% |
| On-Time Completion | >90% |
| Positive Unit Economics | Achieved |

---

# Revenue Model

## Primary Revenue Streams

| Revenue Stream | Description | Priority |
|---------------|-------------|----------|
| Transaction Commission | Commission per completed order | High |
| Customer Service Fee | Small fee charged to customers | High |
| Premium Membership | Additional features for DP & MO | Medium |
| Featured Listing | Promote partners in search results | Medium |
| Withdrawal Fee | Instant withdrawal option | Medium |

---

## Future Revenue Opportunities

| Opportunity | Description | Potential |
|-------------|-------------|-----------|
| Laundry Supply Marketplace | Detergent, bags, packaging | High |
| Equipment Financing | Washing machine financing | Very High |
| Insurance | Laundry protection | Medium |
| Business Analytics | Premium dashboard | High |
| White-label Software | Software for laundry chains | High |
| API Integration | Enterprise integration | High |
| Working Capital Loans | Financing for partners | Very High |

---

# Revenue Projection Example

## Assumptions

| Metric | Value |
|--------|------:|
| Average Order Value | Rp 30,000 |
| Platform Revenue per Order | Rp 3,600 |
| Commission Rate | 12% |

---

## Revenue by Daily Orders

| Orders/Day | Monthly Revenue | Annual Revenue |
|------------|----------------:|---------------:|
| 100 | Rp 10.8 Million | Rp 129 Million |
| 500 | Rp 54 Million | Rp 648 Million |
| 1,000 | Rp 108 Million | Rp 1.30 Billion |
| 5,000 | Rp 540 Million | Rp 6.48 Billion |
| 10,000 | Rp 1.08 Billion | Rp 12.96 Billion |

---

# Long-Term Business Opportunity

The long-term business extends beyond laundry commissions.

Potential future ecosystem:

```
Laundry Marketplace
        │
        ├── Transaction Fees
        ├── Payment Services
        ├── Partner Subscription
        ├── Equipment Financing
        ├── Working Capital Loans
        ├── Laundry Supplies Marketplace
        ├── Insurance
        ├── Analytics Platform
        ├── API Platform
        └── White-label SaaS
```

The vision is to become the digital infrastructure for Indonesia's distributed laundry industry.

---

# Investor Readiness Checklist

Before approaching institutional investors, the company should ideally demonstrate:

| Metric | Target |
|--------|-------:|
| Active Machine Owners | 30+ |
| Active Drop Points | 15+ |
| Registered Customers | 500+ |
| Monthly Orders | 500–1,000 |
| Repeat Customer Rate | >40% |
| Marketplace Take Rate | 10–15% |
| Positive Contribution Margin | Yes |
| Product-Market Fit | Demonstrated |

---

# Risk Assessment

| Risk | Impact | Mitigation |
|------|--------|------------|
| Marketplace Cold Start | High | Acquire Machine Owners first |
| Low Customer Adoption | High | Referral campaigns & free first order |
| Low DP Participation | Medium | Simplify DP workflow & improve incentives |
| Trust Issues | High | Verification, ratings, insurance, dispute SOP |
| Operational Complexity | Medium | Launch in one district before expanding |

---

# Funding Recommendation

The recommended fundraising strategy is:

1. Bootstrap customer validation.
2. Raise a small Pre-Seed (~Rp 300 Million).
3. Achieve Product-Market Fit in one district.
4. Raise Seed funding after operational metrics are proven.
5. Expand city-by-city using validated playbooks.

The objective of the first fundraising round is **not rapid expansion**, but to reduce execution risk and demonstrate that the marketplace model is repeatable, scalable, and economically sustainable.