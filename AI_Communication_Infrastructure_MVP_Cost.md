
# AI Communication Infrastructure - MVP Cost Estimate

> Estimates are for an MVP serving approximately **100 paying companies**. Prices are indicative and should be validated against your chosen cloud provider and AI vendor.

## Assumptions

- 100 tenants
- ~300 conversations/day/company
- WhatsApp + REST API
- Multi-tenant SaaS
- High availability is not yet required

## Fixed Infrastructure

| Component | Recommendation | Est. USD / Month |
|---|---|---:|
| API Servers | 2× 4 vCPU / 8 GB | 80 |
| PostgreSQL | Managed | 60 |
| Redis | Cache & Sessions | 30 |
| Qdrant | Self-hosted | 30 |
| RabbitMQ | Queue | 20 |
| Object Storage | Cloudflare R2 / S3 | 20 |
| Monitoring | Grafana + Prometheus | 20 |
| Logging | BetterStack / Self-host | 25 |
| CDN | Cloudflare Pro | 25 |
| Email | Resend / SendGrid | 20 |
| Backup | Database & Files | 20 |
| CI/CD | GitHub + Registry | 20 |
| Domain & DNS | Domain | 2 |

**Estimated Fixed Cost:** **USD 372 / month**

## Variable Costs

| Item | Pricing Model |
|---|---|
| AI inference | Per token / request |
| WhatsApp | Per conversation (Meta pricing) |
| SMS (optional) | Per message |
| Payment gateway | Per transaction |
| External integrations | Depends on provider |

## Example AI Budget

| Scenario | USD / Month |
|---|---:|
| Light usage | 100 |
| Medium usage | 300 |
| Heavy usage | 800 |

## Monthly Operating Cost

| Scenario | Fixed | AI | Total (USD) |
|---|---:|---:|---:|
| Lean MVP | 372 | 100 | 472 |
| Growth | 372 | 300 | 672 |
| Scale | 372 | 800 | 1,172 |

## Suggested Pricing

| Plan | Monthly Price (IDR) |
|---|---:|
| Starter | 499,000 |
| Growth | 1,499,000 |
| Business | 2,999,000 |
| Enterprise | Custom |

## Example Unit Economics

Assume:
- 100 customers
- Average subscription: IDR 1,500,000/month

Revenue:
- IDR 150,000,000/month

Approximate operating cost:
- USD 672/month ≈ IDR 11,000,000 (exchange-rate dependent), excluding WhatsApp conversation fees and payment processing.

Approximate gross margin before salaries, marketing, taxes, and office expenses:
- Around **92–93%**.

## Costs Not Included

- Engineering salaries
- Customer support
- Sales & marketing
- Legal and accounting
- Taxes
- Office expenses
- Disaster recovery
- Enterprise SLA

## Recommendation

Keep the fixed infrastructure lean and focus on reducing AI inference costs by:
1. Routing simple requests to rules instead of an LLM.
2. Caching repeated answers.
3. Using smaller models for intent classification.
4. Sending only complex conversations to larger models.
5. Letting customers connect and pay for their own WhatsApp Business account when possible.
