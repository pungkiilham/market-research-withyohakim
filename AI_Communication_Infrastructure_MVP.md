# AI Communication Infrastructure MVP

## Vision

Build an AI-native communication platform that replaces repetitive sales/admin work across multiple channels.

```
WhatsApp
API
     ↓
 Communication Gateway
     ↓
 Conversation Engine
     ↓
 Context Engine
     ↓
 AI Router
     ↓
 Business Rules
     ↓
 Action Engine
     ↓
 CRM / Inventory / ERP
     ↓
 Dashboard
```

---

# MVP Scope (v1)

## Entry Points
- WhatsApp Business Cloud API
- Public REST API for developers

## Core Modules
1. Authentication & Tenant Management
2. Conversation Service
3. Context Engine
4. AI Router
5. Knowledge Base (RAG)
6. Business Rules Engine
7. Action Engine
8. Dashboard

---

# Conversation Flow

```text
Customer Message
      │
      ▼
Communication Gateway
      │
      ▼
Normalize Message
      │
      ▼
Load Company Context
      │
      ▼
Intent Detection
      │
      ├── Simple FAQ
      │      ▼
      │  Rule Engine
      │      ▼
      │   Reply
      │
      └── Complex
             ▼
      Retrieve Knowledge
             ▼
         LLM Response
             ▼
     Execute Action (optional)
             ▼
        Send Reply
```

---

# Context Engine

## Customer Context
- Name
- Previous chats
- Purchase history
- Loyalty level

## Business Context
- SOP
- Products
- Pricing
- Promotions
- Shipping rules

## Conversation Context
- Current topic
- Previous turns
- Pending actions

## External Context
- Inventory
- CRM
- ERP
- Courier

---

# AI Router

Simple requests:
- Greeting
- FAQ
- Business hours
- Store location

→ Rules Engine

Complex requests:
- Product recommendation
- Complaint
- Order modification
- Negotiation
- Multi-step conversations

→ LLM

---

# REST API (Developer)

## POST /chat

Input

```json
{
  "tenant_id":"company_a",
  "session_id":"123",
  "message":"Saya mau beli 2 pcs ukuran M"
}
```

Output

```json
{
  "reply":"Baik, stok tersedia.",
  "intent":"BUY_PRODUCT",
  "entities":{
    "qty":2,
    "size":"M"
  },
  "confidence":0.98,
  "actions":[
    "create_order_draft"
  ]
}
```

---

# Dashboard MVP

- Unified Inbox
- Human takeover
- Conversation history
- Knowledge base manager
- AI analytics
- API keys
- Team management

---

# Tech Stack

Frontend
- Next.js

Backend
- FastAPI

Database
- PostgreSQL

Cache
- Redis

Vector DB
- Qdrant

Queue
- RabbitMQ

Storage
- Cloudflare R2

AI
- OpenAI / Gemini / Anthropic (router)

Deployment
- Docker
- Kubernetes (later)

---

# Milestones

## Phase 1 (4–6 weeks)
- WhatsApp integration
- Multi-tenant auth
- Chat API
- AI reply
- Dashboard
- Knowledge base

## Phase 2 (6–8 weeks)
- Human takeover
- Analytics
- CRM integration
- Inventory integration

## Phase 3
- Instagram
- Facebook Messenger
- Telegram
- LINE

## Phase 4
- Shopee
- Tokopedia
- Lazada
- TikTok Shop

---

# Success Metrics

- < 3 sec average response
- > 80% automated replies
- > 95% uptime
- 30–50% reduction in admin workload
- Positive ROI for customers within 3 months


---

# The long-term architecture would look something like this:

                AI Commerce OS

         ┌───────────────────────┐
         │   Omnichannel Gateway  │
         │ WA • IG • FB • API     │
         │ Shopee • Tokopedia     │
         │ TikTok • Website       │
         └──────────┬─────────────┘
                    │
         Conversation Engine
                    │
              Context Engine
                    │
      ┌─────────────┼──────────────┐
      │             │              │
 Customer     Business      Memory Engine
  Memory       Rules
      │             │
      └─────── AI Router ──────────┘
                    │
      ┌─────────────┼──────────────┐
      │             │              │
 Order Agent  Sales Agent   Support Agent
 Finance Agent Inventory Agent Report Agent
                    │
              Action Engine
                    │
        CRM • ERP • Accounting • POS
                    │
             Dashboard & Analytics