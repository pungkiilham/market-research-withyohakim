# proctOR Knowledge Base 05 — Security, Privacy & GDPR Compliance

> Audience: Hospital IT/security officers, compliance leads, investors, and chatbot training.
> Purpose: The definitive statement on data handling, privacy, and GDPR — proctOR's strongest trust asset.

---

## 1. The Core Principle

> **proctOR does not store, process, host, or record any medical data or patient-identifiable information anywhere on its servers.**

proctOR is a **management and coordination platform**, not a medical data system. It deliberately excludes clinical content from its architecture — this is its biggest structural advantage.

---

## 2. Where Clinical Content Lives (and Doesn't)

| Activity | How It Works | Does proctOR store it? |
|---|---|---|
| **Live surgery streaming** | Streamed via third-party **smart glass applications**, accessed through link-based sharing manually exchanged in-app. | **No** — proctOR never processes or stores the stream. |
| **In-app consultation calls** | Integrated third-party **video SDK (Zoom)** used for pre/post-session calls. | **No** — live-only, unrecorded, no video data stored. |
| **Chat & notes** | In-app messaging for coordination. | Only **administrative** content (scheduling, logistics). No patient data permitted. |
| **Credentials (licenses)** | Stored encrypted for verification only. | Yes — but strictly limited, encrypted, need-to-know. |

### 2.1 Prohibited Content

- Users may **not** upload or share patient-identifiable data, medical records, or protected health information through proctOR.
- The platform enforces this via content rules and user agreements; violations are actioned per the Code of Conduct.

---

## 3. GDPR Compliance

- **Designed for European deployment** with strict adherence to EU data residency and privacy mandates.
- **EU-hosted infrastructure**: data and backends are hosted within the EU.
- **GDPR rights** are supported for all users:
  - Access — export your account data
  - Rectification — correct profile information
  - Erasure — request deletion of your account and data
  - Portability — receive your data in a usable format
  - Objection / restriction — limit processing where applicable
- **Data minimization**: only the data needed to operate the marketplace is collected.
- **Lawful basis**: consent-based processing with clear, plain-language notices.

---

## 4. Data Protection Measures

| Layer | Measure |
|---|---|
| **Encryption** | Encryption in transit (TLS) and at rest for stored data, including credentials. |
| **Access control** | Least-privilege access; Medical Reviewers access credentials only on a need-to-know basis. |
| **Tenant isolation** | Strict isolation between public marketplace, company marketplaces, and individual accounts. |
| **Audit trails** | Administrative actions and ledger operations are logged and auditable. |
| **Backends** | EU-hosted REST API backends with documented security practices. |
| **No third-party data sharing** | No selling or sharing of user data for marketing. |

---

## 5. Data Processing Agreements (DPA)

- proctOR provides a **DPA** to company clients covering processing roles (controller vs. processor) for the operational data that passes through the platform.
- Company clients retain control of their training data and member information within their isolated workspace.

---

## 6. Financial Data Security

- Coin purchases are processed by **Shopify**, which handles PCI-compliant card processing and invoicing.
- proctOR itself does not handle or store raw card numbers.
- The coin ledger is **immutable and fully auditable** (KB-03 §6).

---

## 7. Common Questions (FAQ)

| Question | Response |
|---|---|
| Can patient surgery recordings be viewed on proctOR? | No. proctOR does not host or store any video recordings or patient data. Live streams use external smart-glass links; consultations use unrecorded video calls. |
| How is GDPR handled? | EU-hosted infrastructure, strict data minimization, full GDPR user rights, and a DPA for company clients. |
| Is our company's data visible to others? | No — company marketplaces are isolated and invisible to the public marketplace and other companies. |
| Where is proctOR's data hosted? | Within the EU, on EU-hosted infrastructure. |
| Can users request deletion? | Yes — GDPR erasure requests are honored, and account deletion is supported. |
| What happens if someone uploads patient data? | It is a violation of the platform rules and is actioned per the Code of Conduct; proctOR does not permit or process patient data. |
| Are video calls recorded? | No. In-app video calls are live-only and never recorded. |
