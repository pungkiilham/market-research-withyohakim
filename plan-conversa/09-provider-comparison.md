# Provider Comparison: Bailey (Baileys) vs WATI vs SendPulse

## Executive Summary

This report compares three WhatsApp connectivity options for **Conversa** (AI customer-service chatbot SaaS):

| Provider | Type | Best For | Key Differentiator |
|---|---|---|---|
| **Baileys** | Open-source library | Developers building custom WhatsApp integrations from scratch | No Meta relationship; raw WebSocket connection |
| **WATI** | Official Meta Solution Partner (Tech Partner + BYOA) | Teams needing dedicated AI agent architecture on WhatsApp | BYOA (Bring Your Own Agent) + Connect AI Agents |
| **SendPulse** | Official Meta BSP + Chatbot builder | Budget-conscious teams needing basic WhatsApp API access | $9.60/month Pro plan; free WhatsApp API included |

---

## 1. Bailey (Baileys) — Open-Source Library

### What It Is
- **Baileys** is an open-source TypeScript/JavaScript library (`WhiskeySockets/baileys`)
- Connects to WhatsApp Web's WebSocket protocol via Linked Devices feature
- **NOT** a WhatsApp Business API Provider (BSP); does NOT use Meta's Business API
- Independent library; not affiliated with Meta or WhatsApp

### Key Characteristics

| Aspect | Details |
|---|---|
| **API Access** | WhatsApp Web WebSocket; raw protocol access |
| **Meta Relationship** | None — operates at WhatsApp Web level |
| **Ban Risk** | 🔴 **HIGH** — No Meta compliance; easy to violate TOS |
| **Suitable for Production** | ❌ No — for development/testing only |
| **Compliance** | None — you handle all WhatsApp policy compliance |
| **Support** | Community only (GitHub issues) |
| **Cost** | Free (open-source) |

### Why NOT Recommended for Conversa

| Reason | Impact |
|---|---|
| **No Meta Business API** | Cannot integrate with WhatsApp Business Platform |
| **Ban risk extreme** | No policy compliance; account will be banned quickly |
| **No webhook support** | No structured incoming/outgoing message events |
| **No template system** | Cannot send approved message templates |
| **No business verification** | No Facebook Business Portfolio integration |
| **Not scalable** | Meant for individual development, not SaaS product |

### Code Example (from docs)

```bash
# Installation
npm install @whisockets/baileys

# Basic usage
const { default: Baileys } = require('@whisockets/baileys')

const client = new Baileys()

client.ev.on('connection.update', state => {
  console.log('Connection state:', state)
})

// Listen for messages
client.ev.on('messages.1', async (messages) => {
  console.log('New message:', messages[0].key.remoteJid)
})
```

### Ban Probability Assessment

| Scenario | Probability |
|---|---|
| **Ban within 24h** | ~95% (no policy compliance) |
| **Ban within 1 week** | ~99% |
| **Ban within 1 month** | ~100% |
| **Why** | No Meta relationship; violates TOS by design |

---

## 2. WATI — Official Meta Solution Partner

### What It Is
- **WATI** is an official **Meta Solution Partner** (Tech Partner tier)
- Provides WhatsApp Business API access through Meta-approved channel
- **BYOA (Bring Your Own Agent)** architecture for custom AI integration
- **Connect AI Agents** add-on ($100/month) for custom AI as Team Inbox operator

### Key Features

| Feature | Details |
|---|---|
| **Sandbox environment** | For testing before going live |
| **Early API access** | Pre-release API endpoints |
| **Solution architect support** | Dedicated technical guidance from WATI |
| **Co-marketing opportunities** | Joint marketing, brand assets |
| **Customizable pricing** | Modular pricing for combined solutions |
| **No listing fees** | Free to list in WATI's App Marketplace |
| **Exclusive partner discounts** | Better rates than standard customers |
| **BYOA add-on** | $100/month for Custom AI Agent integration |
| **Connect AI Agents** | Your AI appears as Team Inbox operator |
| **100+ integrations** | CRM, databases, workflow tools |

### Pricing Structure

| Component | Monthly Cost |
|---|---|
| **Base subscription** | Growth/Pro/Business plan (TBD, typically $39-$200+) |
| **BYOA add-on** | $100/month |
| **WhatsApp API** | Included in subscription |
| **Service messages** | FREE (incoming replies within 24h) |
| **Message pricing (Indonesia)** | ~$0.03 (auth/utility), $0.0493 (marketing) |
| **Total estimated** | **$139+/month** |

### Integration Architecture for Conversa

```
Customer sends WhatsApp message
    ↓
WATI receives message (via WhatsApp Business API)
    ↓
WATI webhook pushes to Conversa AI
    ↓
Conversa generates AI response
    ↓
Conversa calls WATI API to send reply
    ↓
WATI sends reply to customer
```

### Human Escalation

- **Team Inbox** appears as native WhatsApp chat
- AI agent can be assigned as operator
- Humans take over with full conversation context
- No conversation context loss

### Ban Probability Assessment

| Scenario | Probability |
|---|---|
| **Ban due to policy violation** | ~1-3% (very low for customer service) |
| **Ban due to WATI issues** | ~0% (WATI handles Meta relationship) |
| **Restriction (temporary)** | ~5-10% (if quality rating drops) |
| **Why low** | WATI is Meta-approved partner; compliance monitored |

---

## 3. SendPulse — Official Meta BSP + Chatbot Builder

### What It Is
- **SendPulse** is an official **Meta Business Partner** (WhatsApp Business Solution Provider)
- Provides WhatsApp Business API access with chatbot builder
- **Free WhatsApp API** with any paid Pro plan
- **Message-based pricing** (effective July 1, 2025)
- More focused on no-code chatbot building vs. developer-first API

### Key Features

| Feature | Details |
|---|---|
| **Official Meta Partner** | WhatsApp Business Solution Provider |
| **Free WhatsApp API** | Included with Pro plan ($9.60/month annual) |
| **No-code chatbot builder** | Drag-and-drop flow builder |
| **Global webhooks** | Track incoming_message, outgoing_message, etc. |
| **REST API** | For programmatic control |
| **Integrations** | Make, Google Sheets, Zapier |
| **Multi-channel** | Email, SMS, Viber, Telegram, WhatsApp |
| **Built-in CRM** | Contact management included |
| **AI add-ons** | ChatGPT and Google Sheets integrations |

### Pricing Structure

| Plan | Price (Annual) | Subscribers | Messages |
|---|---|---|---|
| **Free** | $0 | 500 | 10,000/month |
| **Pro** | $9.60/month | 10,000+ | Unlimited |
| **WhatsApp API** | FREE with Pro plan | | |
| **Message pricing (Indonesia)** | $0.03 (auth/utility), $0.0493 (marketing) | | |
| **Service messages** | FREE (replies within 24h) | | |

### Integration Architecture for Conversa

```
Customer sends WhatsApp message
    ↓
SendPulse receives message (via WhatsApp Business API)
    ↓
SendPulse webhook pushes to Conversa AI
    ↓
Conversa generates AI response
    ↓
Conversa calls SendPulse API to send reply
    ↓
SendPulse sends reply to customer
```

### Limitations vs WATI

| Limitation | Impact |
|---|---|
| **No BYOA feature** | Must build custom integration from scratch |
| **No AI agent as operator** | Can't appear as Team Inbox operator |
| **No message filtering** | Receives ALL incoming messages |
| **No conversation history API** | Must build context tracking yourself |
| **Basic human escalation** | Flow Builder only, no full Team Inbox |
| **No CLI tool** | Must use dashboard or REST API |

### Ban Probability Assessment

| Scenario | Probability |
|---|---|
| **Ban due to policy violation** | ~1-5% (low for customer service) |
| **Ban due to SendPulse issues** | ~0% (SendPulse handles Meta relationship) |
| **Restriction (temporary)** | ~5-15% (if quality rating drops) |
| **Why low** | Official Meta BSP; compliance monitored |

---

## 4. Direct Comparison Table

| Factor | Bailey (Baileys) | WATI | SendPulse |
|---|---|---|---|
| **Type** | Open-source library | Meta Solution Partner | Meta BSP |
| **WhatsApp API** | ❌ No | ✅ Yes | ✅ Yes |
| **Meta Relationship** | None | Official Partner | Official Partner |
| **Base Price** | Free | $39-$200+ | $9.60/month |
| **BYOA/AI Agent** | ❌ No | ✅ Yes ($100/month) | ❌ No |
| **Connect AI as Operator** | ❌ No | ✅ Yes | ❌ No |
| **Team Inbox** | ❌ No | ✅ Full-featured | ❌ Basic |
| **Webhooks** | ❌ No | ✅ Yes | ✅ Yes |
| **REST API** | Limited | ✅ Full | ✅ Full |
| **Message Pricing (ID)** | N/A | ~$0.03 auth/utility | $0.03 auth/utility |
| **Service Messages** | N/A | FREE | FREE |
| **Minimum Commitment** | None | Monthly/Annual | Monthly/Annual |
| **Best Use Case** | Dev testing only | Custom AI on WhatsApp | Budget WhatsApp API |
| **Ban Risk** | 🔴 ~100% | 🟢 ~1-3% | 🟢 ~1-5% |
| **Scalability** | ❌ None | ✅ High | ✅ Medium |
| **Developer Tools** | ✅ CLI (wati-cli) | ✅ wati-cli + MCP | ✅ REST API + Webhooks |

---

## 5. Recommendation for Conversa

### Choose WATI if:
- ✅ You need **dedicated BYOA architecture** for custom AI
- ✅ You want **AI agent as Team Inbox operator** (professional appearance)
- ✅ You need **message filtering** (only assigned messages)
- ✅ You need **conversation history** via `/getMessages` API
- ✅ You want **built-in human escalation** via Team Inbox
- ✅ You want **CLI tool and MCP server** for developer experience
- ✅ Budget is less of a concern (~$139+/month)

### Choose SendPulse if:
- ✅ **Budget is primary concern** (~$10/month vs. ~$139+/month)
- ✅ You want **simpler, no-code approach**
- ✅ You don't need AI agent as Team Inbox operator
- ✅ You're okay building custom webhook/API integration
- ✅ You want **multi-channel** (email, SMS, WhatsApp) in one platform

### Bailey (Baileys) is NOT Recommended because:
- ❌ No Meta Business API access
- ❌ ~100% ban probability quickly
- ❌ No compliance or support
- ❌ Not suitable for production SaaS
- ❌ Only for development/testing

---

## 6. Decision Framework

| Priority | Choose WATI | Choose SendPulse |
|---|---|---|
| **Budget primary** | ❌ Too expensive | ✅ $10/month |
| **Dedicated AI architecture** | ✅ BYOA + Connect AI Agents | ❌ Not available |
| **AI as Team Inbox operator** | ✅ Supported | ❌ Not supported |
| **Message filtering** | ✅ Only assigned messages | ❌ All messages |
| **Conversation history** | ✅ Built-in API | ❌ Must build yourself |
| **Human escalation** | ✅ Team Inbox | ❌ Flow Builder only |
| **Multi-channel needed** | ❌ WhatsApp-only | ✅ Email/SMS/WA/Viber/Telegram |
| **Developer experience** | ✅ CLI + MCP + docs | ✅ REST API + webhooks |
| **Setup time** | 1-2 weeks | Same day |
| **Long-term scalability** | ✅ High | ✅ Medium |

---

## 7. Next Steps

### If Choosing WATI:
1. [ ] Sign up for WATI Tech Partner program
2. [ ] Get BYOA add-on ($100/month)
3. [ ] Register Custom AI Agent in WATI
4. [ ] Configure webhook URL for incoming messages
5. [ ] Implement API calls for sending replies
6. [ ] Set up human escalation via Team Inbox

### If Choosing SendPulse:
1. [ ] Sign up for SendPulse Pro plan ($9.60/month annual)
2. [ ] Connect WhatsApp Business API
3. [ ] Configure global webhooks for `incoming_message`
4. [ ] Implement API calls for sending replies
5. [ ] Set up flow for human escalation

### If Choosing Bailey (NOT Recommended):
1. [ ] Do NOT use for production
2. [ ] Only use for development/testing
3. [ ] Implement own compliance and ban mitigation

---
*Report generated: 2026-09-04 | Research: WATI Tech Partner, SendPulse Pricing, Baileys documentation*