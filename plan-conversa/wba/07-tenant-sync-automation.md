# 07 — Tenant Sync Automation (WhatsApp Business API)

> **Purpose:** Document the automation levels for onboarding tenants as a Tech Provider.
> **Scope:** Fully automated server-to-server steps, semi-automated tenant onboarding, and the one-time manual per-tenant setup.
> **Automation tier:** Tier 1 (code exchange, webhooks, PIN registration, messaging) after initial Tech Provider setup.
> **Entity:** CV Estro Hutama (Tech Provider).

---

## 1. Automation Overview

| Automation Layer | What's Automated | What's Manual | Effort After Setup |
|---|---|---|---|
| **Tier 1 — Core flow** | Code exchange (`code` → `business_token`), webhook subscription (`/subscribed_apps`), phone number registration (`/register` with PIN), inbound message reception, outbound message sending | Tenant clicks "Connect WhatsApp" → finishes Meta popup → confirms 6-digit PIN sent to their WA | ~5 minutes per tenant (click + PIN confirm). Zero API calls needed from tenant after flow starts. |
| **Tier 2 — Onboarding script** | One-click server script that takes `tenant_id` + `code` + IDs and runs all 3 API calls automatically | None (still requires the `code` from the frontend, but automates the API sequence) | 1–2 days dev work; eliminates the "forward code to server" manual step |
| **Tier 3 — Portfolio auto-creation** | System creates Meta Business Portfolio on behalf of tenant via Graph API | Not possible via Graph API without tenant portal interaction | Not currently possible — tenant must create portfolio once via `business.facebook.com` (≈5 min) |

> **Your current state:** **Tier 1** is fully live. Every new tenant takes ~5 minutes total (click + PIN confirm). This is sufficient for 1k–10k in 6 months.

---

## 2. The Fully Automated Flow (Tier 1)

This is the core automated process that runs after a tenant clicks "Connect WhatsApp" in the Conversa console.

### Phase A — Tenant side (one action)

1. Tenant clicks **Connect WhatsApp** in Conversa console.
2. Meta popup opens → tenant logs into their Meta account → selects their business portfolio → adds their WA number (fresh or from WhatsApp Business app).
3. Meta posts `WA_EMBEDDED_SIGNUP` event back to the spawning window:
   ```
   { waba_id, phone_number_id, business_portfolio_id, code }
   ```
   ⚠️ **`code` expires in 30 seconds.**
4. Tenant's frontend forwards `code` + IDs to your server **immediately**.

> **Note:** Steps 1–4 are the only manual per-tenant actions. After step 4, everything is server-to-server.

### Phase B — Server side (fully automated, 3 API calls)

All calls use `Authorization: Bearer <SYSTEM_USER_ACCESS_TOKEN>` (your system token from Tech Provider onboarding).

**Call 1 — Exchange code → business token:**
```
GET graph.facebook.com/v25.0/oauth/access_token
    ?client_id=<APP_ID>&client_secret=<APP_SECRET>&code=<CODE>
```
→ Returns the **tenant's business token** (customer-scoped; scoped to that tenant only). Store this token — you'll use it for all subsequent send/receive operations for this tenant.

**Call 2 — Subscribe to webhooks on the tenant's WABA:**
```
POST graph.facebook.com/v25.0/<WABA_ID>/subscribed_apps
```
→ Now every inbound WhatsApp message for this tenant is delivered to **your webhook endpoint**. You don't need to make further API calls to receive messages.

**Call 3 — Register the tenant's phone number:**
```
POST graph.facebook.com/v25.0/<PHONE_NUMBER_ID>/register
    { "messaging_product": "whatsapp", "pin": "<6-digit PIN>" }
```
→ A 6-digit PIN is sent to the tenant's WhatsApp number. The tenant taps **Confirm** on their phone. Your server records the registration as soon as the PIN is validated.

### Phase B — Live messaging (fully automated, forever)

- **Receive:** Customer messages arrive at your webhook endpoint as JSON payloads. Parse `phone_number_id` and/or `waba_id` to route to the correct tenant → feed into your Conversa bot → generate a reply.
- **Send** (inside 24h customer-service window, free-form text):
  ```
  POST graph.facebook.com/v25.0/<PHONE_NUMBER_ID>/messages
  Authorization: Bearer <TENANT_BUSINESS_TOKEN>
  { "messaging_product": "whatsapp", "to": "<customer_phone>", "type": "text",
    "text": { "body": "..." } }
  ```
- **Send** (outside 24h window, via approved template):
  ```
  POST graph.facebook.com/v25.0/<WABA_ID>/message_templates
  Authorization: Bearer <TENANT_BUSINESS_TOKEN>
  { "messaging_product": "whatsapp", "to": "<customer_phone>", "template": { "name": "your_template_name", "language_code": "en_US" } }
  ```

---

## 2. Tenant Onboarding: Manual vs Automated

| Step | Tenant Action | Automation Level | Notes |
|---|---|---|---|
| **Create Meta Business Portfolio** | Register at `business.facebook.com` (name, address, phone, email, website) | ⚠️ Manual (1× per tenant) | Required before the flow starts. Takes ~5 min. Cannot be auto-via API. |
| **Click "Connect WhatsApp"** | Calls `FB.login()` with your `config_id` | ✅ Fully automated | Part of the Embedded Signup integration in your console. |
| **Finish Meta popup** | Login + portfolio + number selection | ✅ Fully automated | Meta handles the flow; tenant just makes choices. |
| **Forward `code` + IDs to server** | Copies/forwards the `code` from the Meta event to your server | ⚠️ Manual (30 seconds) | The only per-tenant manual step after the popup. Could be automated with Tier 2 script. |
| **PIN confirmation** | Receives 6-digit PIN on WhatsApp → taps Confirm | ✅ Fully automated | PIN is sent by Meta; tenant taps Confirm; your server records the registration. |
| **Live messaging** | Receives/replies to customer messages | ✅ Fully automated | Webhook delivers messages; your bot replies via API. |

> **Summary:** After the tenant's **one-time** Meta Business Portfolio creation (≈5 min), **every subsequent step is automated**. New tenants take ~5 minutes total.

---

## 3. Tier 2 — One-Click Onboarding Script (Optional)

If you want to eliminate the "forward `code` + IDs to server" manual step, you can build a simple server-side script.

### Script inputs
- `tenant_id` (your internal ID)
- `code` (from the Embedded Signup event)
- `app_id` / `app_secret` (your Meta app credentials)
- `waba_id` / `phone_number_id` (from the event)

### Script actions (3 API calls in sequence)
1. `POST /oauth/access_token` → exchange `code` → store `business_token`
2. `POST /<waba_id>/subscribed_apps` → subscribe webhooks
3. `POST /<phone_number_id>/register` → `{pin: "123456"}` → register phone

### Example (Node.js / Python)
```javascript
// Pseudo-code: run all 3 calls sequentially
await exchangeCode(code);      // → stores business_token
await subscribeWebhook(waba_id); // → webhooks active
await registerPhone(phone_number_id, pin); // → phone registered
```

### Benefit
- Your ops team clicks "Onboard Tenant" in your internal tool → script runs 3 API calls → tenant is live.
- Eliminates the manual "forward code to server" step.
- **Effort:** 1–2 days dev work.

---

## 4. Tier 3 — Portfolio Auto-Creation (Not Currently Possible)

You might wonder: *Can your system create the tenant's Meta Business Portfolio automatically?*

**Answer:** **No, not via the public Graph API.** Meta requires the user to go through the portal verification flow (`business.facebook.com`) to create a portfolio. This is a security/identity-verification gate.

**Workaround:**
- Provide a "Create Portfolio" button in your onboarding flow that links directly to `business.facebook.com`.
- Guide the tenant through the 5-minute signup.
- After that, the normal Tier 1 automated flow takes over.

> **Why Meta does this:** Portfolio creation involves verifying a real business entity (NIB/NPWK/akta docs). Meta doesn't allow third parties to create portfolios on behalf of users without the user completing the verification flow themselves.

---

## 5. Automation Checklist — Where You Are Now

| ✅ | Item | Status |
|---|---|---|
| **Tier 1 flow** | Code exchange → business token, webhook subscription, PIN registration, inbound/outbound messaging | ✅ Live after Tech Provider onboarding |
| **Webhook endpoint** | Public HTTPS URL + verify token, handles `messages` events, routes by `phone_number_id`/`waba_id` | ✅ Deployed |
| **DB schema** | Table storing `tenant_id ↔ waba_id, phone_number_id, business_token, display_phone_number` | ✅ Designed |
| **Tier 2 script** | One-click onboarding script (optional) | 🟡 Not yet built (1–2 days dev) |
| **Tenant portfolio creation** | Tenant creates their portfolio at `business.facebook.com` (one-time, ~5 min) | ✅ Manual (required first step) |

---

## 6. Timeline — From Zero to Automated

| Milestone | Time | Effort |
|---|---|---|
| **Tech Provider registration** | 2–5 days | Done (app review, business verification, dashboard enablement) |
| **Embedded Signup integration** | 3–5 days | Frontend `FB.login()` + `config_id` + webhook setup |
| **First tenant onboarded** | Same day as integration | 5 min (click + PIN confirm) |
| **Tier 2 onboarding script** | 1–2 weeks after Tier 1 | Dev work (optional) |
| **10 tenants onboarded** | < 1 hour total | 5 min × 10 |
| **100 tenants onboarded** | ~8 hours total | 5 min × 100 |
| **1k–10k tenants in 6 months** | Tier 1 is sufficient | No further automation needed |

---

## 7. Quick-Start Automation (What to do today)

If you want to automate the process starting today:

1. ✅ Ensure your **Tech Provider** status is live (app review approved, system token generated).
2. ✅ Have your **webhook endpoint** running and capable of receiving `messages` events.
3. ✅ Have your **DB schema** ready to store `tenant_id ↔ waba_id, phone_number_id, business_token`.
4. ✅ embed the **Connect WhatsApp** button in your Conversa console using your `config_id`.
5. 🟡 (Optional) Build a **one-click onboarding script** for your ops team (Tier 2).
6. 📤 Send the onboarding link to your first tenant (e.g., Tobias's clinic).

After step 6, every new tenant will take ~5 minutes to onboard, and all message sending/receiving is fully automated.

---

## 7. Sources

- Meta: Embedded Signup implementation (code exchange, business token, 30s TTL) — `developers.facebook.com/docs/whatsapp/embedded-signup/implementation`
- Meta: Get Started as a Tech Provider — `developers.facebook.com/docs/whatsapp/solution-providers/get-started-for-tech-providers`
- Meta: Access Tokens guide (System user tokens, Business tokens) — `developers.facebook.com/docs/whatsapp/access-tokens`
- Meta: Embedded Signup overview + onboarding customers — `developers.facebook.com/docs/whatsapp/embedded-signup`
- Meta: Webhooks for WhatsApp (messages, deliveries, reads) — `developers.facebook.com/docs/whatsapp/webhooks`

---

*Companion docs: [05 — WABA Tier & Meta Partner Path](./05-waba-tier.md) · [06 — Tech Provider Registration](./06-tech-provider-registration.md) · [CONTEXT.md](../../context.md) · [22 — PRD](./22-prd.md) §5.6 WhatsApp Channel*

---

*Automation tier definition: Tier 1 = fully server-to-server after tenant clicks "Connect WhatsApp." Tier 2 = one-click script that runs the 3 API calls. Tier 3 = portfolio auto-creation (not currently possible via API).*
