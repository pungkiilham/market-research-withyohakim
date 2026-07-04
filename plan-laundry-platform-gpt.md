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