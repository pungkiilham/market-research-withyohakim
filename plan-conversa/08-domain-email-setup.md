# 08 — Domain, Email & Meta Verification Setup (Estro Website)

> **Purpose:** Document the complete process for connecting Estro's custom domain, fixing email domain mismatch, and preparing for Meta Business verification.
> **Entity:** CV Estro Hutama
> **Website:** Vercel deployment (published)
> **Domain Provider:** Biznet
> **Current Email:** Gmail (needs upgrade for Meta compliance)
> **Status:** ⚠️ Gmail blocker identified — requires Google Workspace/Zoho Mail upgrade

---

## 1. Problem Summary

| Issue | Impact | Severity |
|---|---|---|
| **Gmail email** (`estro@gmail.com`) | Meta business verification **requires** same-domain email (`estro.co.id`). Gmail will cause rejection. | 🔴 **CRITICAL** — must fix before Meta submission |
| **Website domain** (`www.estro.co.id`) | Custom domain adds credibility for Meta and visitors. Currently on Vercel `*.vercel.app`. | 🟡 **HIGH** — recommended but Meta primary check is business docs |
| **Nameservers** | Currently Biznet; can point to Cloudflare or use Biznet DNS directly. | 🟡 **MEDIUM** — affects website professionalism and Meta domain claim |

---

## 2. Required Actions — Priority Order

### 🔴 Phase 1: Fix the Gmail Blocker (MUST DO FIRST)

Meta will reject business verification if your contact email is Gmail/Yahoo/Outlook. You need a domain-matched email.

| Option | Provider | Steps | Cost (monthly) | Time |
|---|---|---|---|---|
| **Google Workspace** | Google | 1. Go to workspace.google.com<br>2. Register company account<br>3. Add domain `estro.co.id`<br>4. Create emails: `admin@estro.co.id`, `contact@estro.co.id`<br>5. Verify domain ownership (DNS TXT record)<br>5. Migrate any existing Gmail data | $6–$12/user | 1–2 days |
| **Zoho Mail** | Zoho | 1. Go to zohomail.com<br>2. Register<br>3. Add domain `estro.co.id`<br>4. Verify via DNS TXT record<br>5. Create email boxes | $1–$3/user | 1 day |
| **Self-hosted mail** | Your server | 1. Install mail server (Postfix/Dovecot)<br>2. Configure DNS MX records<br>3. Create email boxes<br>2. Maintain spam/security | Free (if you have server) | 2–3 days + ongoing maintenance |

**Recommendation:** **Google Workspace** — most familiar, best integration, professional suite included (Docs, Calendar, Meet).

#### Google Workspace Setup Checklist

- [ ] Register at workspace.google.com
- [ ] Select "Business Starter" ($6/user/month) — sufficient for email + suite
- [ ] Enter your company name and domain: `estro.co.id`
- [ ] Verify domain ownership: Add TXT record to Biznet DNS (Value provided by Google)
- [ ] Create email boxes: `admin@estro.co.id`, `contact@estro.co.id` (at minimum)
- [ ] Update any team members' emails from Gmail to the new Workspace emails
- [ ] Test sending/receiving emails

---

### 🟡 Phase 2: Connect Website Domain (Recommended)

Connect your Biznet domain to Vercel for a professional `www.estro.co.id` website.

#### Option A: Using Cloudflare (Recommended — simpler DNS management)

1. **In Biznet:** Change nameservers to Cloudflare's:
   - `ns1.cloudflare.com`
   - `ns2.cloudflare.com`
   - (Go to Biznet → Domain Settings → Nameservers → Replace with Cloudflare NS)

2. **In Cloudflare:**
   - Add your domain `estro.co.id`
   - **DNS Records:**
     - `CNAME` `www` → `your-project.vercel.app` (Target)
     - `TXT` `@` → `google-site-verification=...` (if claiming Google Search Console — optional)
     - Optional: `MX` records if you're using Google Workspace (auto-populated after Phase 1)
   - **SSL/TLS** → "Full" (or "Full (strict)" if you have Vercel origin cert)
   - **Proxy Status** → **Orange Cloud** (on) — this activates HTTPS via Let's Encrypt

3. **In Vercel:**
   - Go to Settings → Domains
   - Add `www.estro.co.id`
   - Vercel will auto-provision SSL (Let's Encrypt)
   - Visit `www.estro.co.id` → should show your website with padlock 🔒

   **Propagation:** 5–30 minutes for DNS, up to 24 hours for full global rollout.

#### Option B: Using Biznet DNS Only (No Cloudflare)

1. **In Biznet DNS:**
   - `CNAME` `www` → `your-project.vercel.app`
   - Optional: `TXT` `@` for any verification needs
2. **In Vercel:**
   - Add domain `www.estro.co.id`
   - Vercel will attempt to verify DNS TXT record
   - SSL will be provisioned if verification passes

> **Cloudflare recommended** — better UI, easier DNS management, built-in WAF, and the orange "Proxy" cloud gives you HTTPS immediately.

---

### 🟡 Phase 3: Meta Business Verification Preparation

After Phases 1 and 2 are done, you'll have:

| Requirement | Status after Phases 1–2 |
|---|---|
| **Business verification docs** (NIB/NPWP/akta/bank) | ✅ Ready (already have these) |
| **Domain-matched email** | ✅ After Phase 1 (Workspace/Zoho) |
| **Custom website domain** | ✅ After Phase 2 (Cloudflare + Vercel) |
| **Same-domain email + website** | ✅ Both now `estro.co.id` |
| **App Review (2 demo videos)** | ⏳ Still needed — record send-message + template-video |
| **Business Portfolio verification** | ⏳ Still needed — submit NIB/NPWP docs to Meta |

**Note:** After Phases 1–2, Meta will pass the domain/email checks. You can proceed with the full Tech Provider registration.

---

## 3. Complete Workflow — From Zero to Meta-Ready

| Step | Action | Owner | Time | Status |
|---|---|---|---|---|
| **1** | Purchase Google Workspace (or Zoho Mail) + add `estro.co.id` domain | You | 1 day | ⬜ Not started |
| **2** | Create email boxes: `admin@estro.co.id`, `contact@estro.co.id` | You/Google | 1 day | ⬜ Not started |
| **3** | Update all team communications to use new emails | You/Team | 1 day | ⬜ Not started |
| **4** | (Optional) Change Biznet nameservers to Cloudflare | You | 30 min | ⬜ Not started |
| **5** | In Cloudflare: Add `estro.co.id` → CNAME `www` → Vercel app → Enable Orange Cloud | You | 30 min | ⬜ Not started |
| **5** | In Vercel: Add `www.estro.co.id` → auto-SSL → verify website loads | You | 15 min | ⬜ Not started |
| **5** | Wait 15–30 min DNS propagation | — | 15–30 min | ⬜ Not started |
| **6** | Test: Visit `www.estro.co.id` → padlock 🔒 visible | You | 5 min | ⬜ Not started |
| **7** | Record 2 App Review demo videos (send message + template) | You/Team | 1–2 days | ⬜ Not started |
| **8** | Submit Meta Business Portfolio verification (NIB/NPWP/akta) | You | 2–5 days | ⬜ Not started |
| **8** | Apply for Tech Provider in Meta App Dashboard | You | 1 day | ⬜ Not started |

**Total time to Meta Tech Provider readiness:** ~2–3 weeks (if you move fast on Phase 1).

---

## 3. Quick-Start Commands — If Using Cloudflare

If you want to execute the Cloudflare setup immediately, here's the exact sequence:

```bash
# Step 1: In Biznet, note your current nameservers, then change to:
# ns1.cloudflare.com
# ns2.cloudflare.com

# Step 2: In Cloudflare (after adding domain estro.co.id):
# 1. CNAME: www → your-project.vercel.app
# 2. SSL/TLS: Full (strict optional)
# 4. Proxy: Orange cloud (on)

# Step 4: In Vercel:
# 1. Settings → Domains → Add www.estro.co.id
# 2. Wait for auto-provisioned Let's Encrypt SSL
# 3. Visit www.estro.co.id → verify padlock 🔒

# Step 5: In Google Workspace:
# 1. Add domain estro.co.id
# 2. Add DNS TXT record Value provided by Google
# 3. Create email boxes admin@estro.co.id, contact@estro.co.id
```

---

## 4. Checklist — Are You Ready for Meta Now?

| ✅ | Readiness Indicator |
|---|---|
| ☐ Google Workspace (or Zoho) active with `estro.co.id` domain |
| ☐ Email boxes created: `admin@estro.co.id`, `contact@estro.co.id` |
| ☏ CNAME `www` → Vercel app configured (Cloudflare or Biznet) |
| ☏ HTTPS padlock 🔒 visible on `www.estro.co.id` |
| ☐ 2 App Review demo videos recorded (send message + template) |
| ☐ Business docs (NIB/NPWP/akta/bank) ready for Meta submission |
| ☐ Meta Business Portfolio ready to verify |

**If 6/6 are ✅ → You're ready to submit for Meta Tech Provider registration.**

---

## 5. Sources

- Google Workspace setup guide — `workspace.google.com`
- Zoho Mail setup guide — `zohomail.com`
- Cloudflare DNS setup — `cloudflare.com/dns`
- Vercel custom domain guide — `vercel.com/docs/domains`
- Meta Business verification — `facebook.com/business/help/159334372093366`
- Meta Tech Provider onboarding — `developers.facebook.com/docs/whatsapp/solution-providers/get-started-for-tech-providers`

---

## 6. Companion Files

| File | Purpose |
|---|---|
| `05-waba-tier.md` | WABA tier decision, partner limits, 0→10k path |
| `06-tech-provider-registration.md` | Step-by-step Tech Provider onboarding |
| `07-tenant-sync-automation.md` | Tenant onboarding automation flow |
| `CONTEXT.md` | Entity/checkpoint status |

---

*Automation tier: This file documents the infrastructure setup required before Tier 1 (onboarding) can proceed. Without the domain+email fixes, Meta verification will fail.*

---

*Companion docs: [05 — WABA Tier](./05-waba-tier.md) · [06 — Tech Provider Registration](./06-tech-provider-registration.md) · [07 — Tenant Sync Automation](./07-tenant-sync-automation.md) · [CONTEXT.md](../context.md)*

---

*Automation tier: This file documents the infrastructure setup required before Tier 1 (onboarding) can proceed. Without the domain+email fixes, Meta verification will fail.*