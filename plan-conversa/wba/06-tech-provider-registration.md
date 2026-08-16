# 06 — Tech Provider Registration (WhatsApp Business API)

> **Purpose:** Self-serve registration as a Meta Tech Provider to onboard tenants via Embedded Signup.
> **Use case:** Each tenant links their own WA number to Conversa; Conversa receives inbound messages and replies (customer service). Pass-through billing: tenant pays Meta for API, Conversa charges its subscription separately.
> **Entity:** CV Estro Hutama (verified via NIB/NPWP + akta + bank statement).
> **Time to status:** Days (self-serve, no application).

---

## 1. Prerequisites (before you start)

| Item | Requirement | Status |
|---|---|---|
| **CV Estro Hutama verified business portfolio** | NIB + NPWP + akta notaris + business bank statement. Name/address/phone must exactly match across portfolio, email domain, and website. Same-domain email required — **no Gmail**. | ? |
| **Fresh dev number** | Must NOT be active on consumer WhatsApp or the WhatsApp Business App. Consider a second SIM/number for production once the PT forms. | ? |
| **Public webhook endpoint** | HTTPS/SSL-facing server with a URL. Required for inbound messages from all tenants (one endpoint; route by `phone_number_id`/`waba_id`). Verify token for validation. | ? |
| **Facebook Login for Business config** | Create in App Dashboard → **Use cases** → **Customize** → **WhatsApp Embedded Signup** template. Save the `config_id`. This is the button tenants click to connect their WA number. | ? |
| **Allowed domains + OAuth redirect URIs** | Add your domain(s) to the Meta App settings → **Allowed domains**. Set valid OAuth redirect URIs for the Login flow. | ? |
| **Two demo videos for App Review** | (1) Send a message from your app received in WhatsApp. (2) Create a message template in your app. These are required to get advanced access to `whatsapp_business_messaging` + `whatsapp_business_management`. Prepare draft descriptions now. | ? |

> **Tip:** Start the business verification (Step 1a) immediately — it takes 2–5 days. Meanwhile, set up the Meta App and Facebook Login for Business config. They're independent.

---

## 2. Step 1 — Create Meta Business Portfolio & Verify

1. Go to `business.facebook.com` → log in → **Create a Business Portfolio** (or use existing one).
   - **Portfolio name:** `CV Estro Hutama` (must match your registered entity exactly).
   - Add your company email (matching the website domain). No Gmail.
2. **Start business verification**:
   - In the portfolio → **Settings** → **Business** → **Verified Meta Business Suite**.
   - Provide: business name, address, phone number, email, website.
   - Confirm connection method: "I manage this business."
   - **Upload docs:** NIB + NPWP + akta notaris + business bank statement.
   - **Why:** Name/address/phone across portfolio, email domain, and website must match exactly. If the site is `conversa.ai`, the footer should show the relationship (e.g., "Conversa — a service of CV Estro Hutama").
   - **Review time:** 2–5 business days (up to 14). If rejected: check for name mismatch, expired docs, low-quality scans.
3. **Confirm portfolio admin**.
   - Add a shared/admin account (not personal) that will manage assets and generate system user tokens.

> **Output:** A verified Meta Business Portfolio under CV Estro Hutama. Keep the portfolio ID — you'll need it for the Meta app and Tech Provider onboarding.

---

## 3. Step 2 — Create Meta App + WhatsApp use case

1. Go to `developers.facebook.com/apps` → **Create App** (or use existing).
   - App type: **Business**.
   - Display name: `Conversa` (or your brand).
   - Contact email: your@conversa.ai (matching the portfolio).
2. **Add the WhatsApp use case**:
   - In the App Dashboard → **Use cases** → click the pencil icon → **Customize**.
   - Select **WhatsApp** → **Next**.
   - This enables the WhatsApp section in the dashboard.
3. **Configure Facebook Login for Business**:
   - Still in the App Dashboard → **Set up** → **Facebook Login for Business**.
   - Choose **WhatsApp Embedded Signup** template.
   - This gives you a **`config_id`** — embed this in your Conversa console for the "Connect WhatsApp" button.
   - Set **Allowed domains** (your website domain) and **Valid OAuth redirect URIs**.
4. **Note your app ID and app secret**.
   - Go to **Basic Settings** → copy **App ID** and **App Secret**. You'll need these to exchange the Embedded Signup code for a business token.

> **Output:** A Meta App (e.g., `236484624622562`) with WhatsApp use case enabled, Facebook Login for Business config (`config_id`), and saved app credentials.

---

## 4. Step 3 — App Review: Advanced access (the gate)

This is the critical step that grants you the ability to send/receive messages on tenants' behalf.

### 3a — Request advanced permissions

1. In the App Dashboard → **App Review** → **Permissions and Features**.
2. Click **Request advanced access** for:
   - `whatsapp_business_messaging` — send/receive messages from WhatsApp users.
   - `whatsapp_business_management` — manage phone numbers, message templates, registration, and business profiles under a WA.
3. **Submit the request**. Review takes 3–7 days typically.

### 3b — Submit demo videos (required for approval)

App Review will reject your advanced access request unless you upload two videos:

- **Video 1:** Show a message created and sent from your app, received in the WhatsApp client (mobile or web).
- **Video 2:** Show your app being used to create a message template.

**Tips for approval:**
- Both videos must clearly demonstrate the permission's use.
- Add a detailed description in the "Tell Us Why You Are Requesting" field, e.g., "As a Tech Provider, we need `whatsapp_business_messaging` to send customer-service messages on behalf of onboarded businesses, and `whatsapp_business_management` to manage their WABAs and templates."
- If rejected: fix the video content or description and resubmit.

### 3c — Outcomes

- **Approved:** You now have advanced access. Proceed to Step 4 (enable Tech Provider).
- **Rejected:** Review the rejection reason, update your videos/description, and resubmit. Common reasons: videos don't clearly demonstrate the permission, description is too vague, or the app doesn't appear to use the data in an approved manner.

> **Output:** Once approved, your Meta app has advanced access to `whatsapp_business_messaging` + `whatsapp_business_management`. This is the prerequisite for all subsequent Tech Provider steps.

---

## 4. Step 4 — Enable Tech Provider onboarding (self-serve)

Now that you have business verification + App Review approved, you can enable Tech Provider in the dashboard.

1. Go to **App Dashboard** → **WhatsApp** → **Quickstart**.
2. Scroll to the bottom — you'll see a section or button to **Start Tech Provider onboarding** (or "Become a Tech Provider").
3. **Click it.** The dashboard will guide you through:
   - Connecting your app to your **verified business portfolio** (CV Estro Hutama).
   - Assigning assets: select your app and toggle "Manage app" under Full control; select your WhatsApp account and toggle "Manage WhatsApp Business accounts."
   - **Generating your system user access token**:
     - Go to **Business Settings** → **System Users** → select your app + WhatsApp account → **Generate token**.
     - Select permissions: `business_management`, `whatsapp_business_management`, `whatsapp_business_manage_events`.
     - **Save this token** securely — you'll use it to onboard tenants and send/receive messages.
   - **Setting up webhooks** (if not already):
     - In the dashboard → **Webhooks** → subscribe to `messages`, `message_deliveries`, `message_reads`.
     - Set your verify token. All tenants' inbound messages will arrive here, routed by `phone_number_id`/`waba_id`.

> **Note:** There is **no manual application submitted to Meta**. It's self-serve: if you have business verification + App Review approved, the Tech Provider path opens in your dashboard. This is why it takes days, not weeks.

> **Output:** Tech Provider status enabled in your dashboard. You now have a **system user access token** and can onboard tenants via Embedded Signup.

---

## 5. Step 5 — Tenant onboarding flow (Embedded Signup)

Now your tenants can connect their WA numbers to Conversa. This is the WABA Sharing model (client-owned WABA, Conversa granted access).

### 5.1 Tenant side (in Conversa console)

1. Tenant clicks **"Connect WhatsApp"** → your frontend calls:
   ```
   FB.login(fbLoginCallback, {
     config_id: '<YOUR_CONFIG_ID>',
     response_type: 'code',
     override_default_response_type: true,
     extras: { setup: {} }
   })
   ```
2. Meta popup opens → tenant logs into their Meta account → selects/creates their business portfolio → adds their WA number (fresh, or existing WhatsApp Business app number via coexistence).
3. On finish, Meta posts a `WA_EMBEDDED_SIGNUP` event back to your page:
   ```
   { waba_id, phone_number_id, business_portfolio_id, code }
   ```
   ⚠️ The **`code` expires in 30 seconds.**
4. Your frontend forwards `code` + IDs to your server immediately.

### 5.2 Server-side onboarding (3 API calls)

All calls use `Authorization: Bearer <SYSTEM_USER_ACCESS_TOKEN>` (your system token from Step 4).

**Call A — Exchange code → business token** (customer-scoped, scoped to that tenant only):
```
GET graph.facebook.com/v25.0/oauth/access_token
    ?client_id=<APP_ID>&client_secret=<APP_SECRET>&code=<CODE>
```
→ Returns the tenant's **business token**. Keep this; you'll use it to send/receive messages for this tenant only.

**Call B — Subscribe to webhooks on the tenant's WABA**:
```
POST graph.facebook.com/v25.0/<WABA_ID>/subscribed_apps
```
→ Now inbound messages for this tenant hit **your** webhook endpoint.

**Call C — Register the tenant's phone number** (two-step PIN):
```
POST graph.facebook.com/v25.0/<PHONE_NUMBER_ID>/register
    { "messaging_product": "whatsapp", "pin": "<6-digit>" }
```

**Call D — Persist the mapping** (in your DB):
```
tenant_id ↔ waba_id, phone_number_id, business_token, display_phone_number
```

### 5.3 Live messaging (per tenant)

- **Receive:** Customer messages arrive at your webhook → parse `phone_number_id`/`waba_id` → route to the right tenant → feed your Conversa bot → generate a reply.
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

> **Billing note (Tech Provider / pass-through):** At tenant onboarding, the tenant is prompted to add their **own payment method** to their WABA → Meta bills the tenant directly for API usage. Conversa charges its own subscription separately. This is the **pass-through** model.

---

## 6. Limits & scale (Tech Provider)

| Metric | Tech Provider |
|---|---|
| **New clients / rolling 7-day window** | **200** (after business verification + App Review + Access Verification complete) |
| **Total connected tenants** | No hard cap — scales with your webhook routing + DB capacity |
| **Business-initiated conversations / 24h** | 250 (unverified) → 2,000 (verified) |
| **Phone numbers per WABA** | 2 (unverified) → 20 (verified) |
| **Onboarding speed for 1k–10k in 6 months** | ✅ 1k is fine (~38/week avg). ⚠️ 5k–10k will eventually require Tech Partner upgrade (self-initiated, no application) |

### When to upgrade to Tech Partner

Once you hit these thresholds (self-initiated, no application form):
- **≥2,500 avg daily messages** (sent/received) across your business + users over last 7 days, OR
- **≥200 avg daily calls** (7-day avg) via the Calling API (new 2026 path)
- **≥10 active clients** (sent ≥1 message in last 30 days)
- **≥90% business phone number quality rating**

The upgrade raises the onboarding cap beyond 200/week and gives you the "Meta Business Partner" badge. You enable it in your dashboard once thresholds are met.

---

## 7. Quick checklist — can you start today?

- [ ] Meta Business Portfolio "CV Estro Hutama" started (verification docs submitted).
- [ ] Meta App created → WhatsApp use case → Facebook Login for Business config (`config_id` saved).
- [ ] App Review draft videos prepared (send message + create template).
- [ ] Public webhook endpoint (HTTPS/SSL) + verify token ready.
- [ ] Fresh dev number confirmed (not on any WhatsApp app).
- [ ] Allowed domains + OAuth redirect URIs configured in App settings.
- [ ] CV Estro docs match: NIB + NPWP + akta + bank statement (name/addr/phone exact across portfolio, website, email).

If 5+ items are checked → **you can start the Tech Provider onboarding today.** The self-serve flow in the App Dashboard will take you from zero to live Embedded Signup in **under a week**.

---

## 8. Sources

- Meta: Get Started as a Tech Provider — `developers.facebook.com/docs/whatsapp/solution-providers/get-started-for-tech-providers`
- Meta: Embedded Signup implementation (code exchange, business token, 30s TTL) — `developers.facebook.com/docs/whatsapp/embedded-signup/implementation`
- Meta: App Review permissions & advanced access — `developers.facebook.com/docs/whatsapp/embedded-signup/app-review`
- Meta: Access Tokens guide (Business Integration System User tokens) — `developers.facebook.com/docs/whatsapp/access-tokens`
- Meta: Upgrade to Tech Partner (eligibility: 2,500 msgs/day or 200 calls/day + 10 active clients + 90% quality) — `developers.facebook.com/docs/whatsapp/solution-providers/upgrade-to-tech-partner`
- Meta: Embedded Signup overview + onboarding customers — `developers.facebook.com/docs/whatsapp/embedded-signup`
- WhatsApp for Business: Become a Partner (tier comparison) — `whatsappbusiness.com/partners/become-a-partner`
- Meta: On-Behalf-Of ownership model deprecation (Oct 2025) — `developers.facebook.com/docs/whatsapp/solution-providers/on-behalf-of/legacy-model-deprecation`

---

*Companion docs: [22 — PRD](./22-prd.md) §5.6 WhatsApp Channel · [05 — WABA Registration & Meta Partner Path](./05-waba-registration.md) · [CONTEXT.md](../../context.md) · [03 — Funding Term Sheet](./03-funding-term-sheet.md)*
