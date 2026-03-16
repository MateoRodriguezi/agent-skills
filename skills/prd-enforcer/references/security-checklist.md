# Risk Assessment Checklist (prd-enforcer reference)

A lightweight checklist the skill consults internally when evaluating PRD completeness.
This is not exposed to the PM — it guides the skill's assessment logic.

---

## 1. Data Classification

When the feature handles user data, classify what's involved:

| Category | Examples |
|---|---|
| PII | Name, email, phone, national ID, address |
| Financial | Balances, transactions, payment methods, bank accounts |
| Credentials | Passwords, API keys, tokens, recovery codes |
| Internal | Admin configs, feature flags, internal system data |

If the PRD doesn't mention what data the feature touches, flag it as an **Important** gap in the Context section.

---

## 2. Three Questions (simplified risk lens)

For any feature that handles sensitive data or exposes new endpoints, these three questions should be answerable from the PRD:

1. **Can someone impersonate another user through this feature?**
   → If yes, the PRD should address authentication controls in Risks & Mitigations.

2. **Can someone modify data they shouldn't have access to?**
   → If yes, the PRD should address data integrity controls (ownership validation, input validation).

3. **Can someone access or see data they shouldn't?**
   → If yes, the PRD should address access control and data exposure limits.

If the feature clearly involves one of these scenarios and the PRD doesn't address it, flag as **Important** in Risks & Mitigations.

---

## 3. Abuse Case Prompt

When evaluating Decision Readiness (Step 4), consider:

> "If someone used this feature with the worst possible intent, what could they do?"

Examples by feature type:
- **Payments/transfers:** Send money to themselves from another account, exploit rounding errors, abuse refund flows
- **User profiles/data:** Access other users' data by manipulating IDs, scrape user information at scale
- **APIs/integrations:** Abuse rate limits, exfiltrate data through API responses, use the endpoint as an amplification vector
- **Content/messaging:** Spam, phishing, impersonation of other users

If the PRD describes a feature with obvious abuse potential and doesn't mention it → flag as **Important**.

---

## 4. Guardrail Metrics by Feature Type

When checking metrics (Step 2), look for operational guardrails appropriate to the feature:

| Feature type | Expected guardrail metrics |
|---|---|
| Payments / transactions | Fraud rate, chargeback rate, unusual amount patterns |
| Authentication / login | Auth failure rate, account lockout rate, unusual geo patterns |
| User data access | Access rate anomalies, bulk access patterns |
| APIs / integrations | Error rate spikes, unusual request volumes, response size anomalies |
| Content / messaging | Report rate, spam detection rate, block rate |

These are business-health guardrails, not security metrics. They protect revenue and user trust.

---

## 5. Rollout Gating for Sensitive Features

When checking rollout (Step 5), features that handle sensitive data or payments should confirm before GA:

- [ ] Access controls reviewed (who can access what)
- [ ] Abuse scenarios documented and mitigated
- [ ] Monitoring/alerts in place for anomalous patterns
- [ ] Rollback plan accounts for data integrity (not just feature flags)

If the feature is clearly sensitive and the rollout plan lacks these → flag as **Important** in Rollout.

---

## 6. Technical Landscape as Risk Context

The **Technical Landscape** section is critical for accurate risk assessment. It lets you scope risks to what actually applies:

| Technical Landscape says... | Risk assessment implication |
|---|---|
| Serverless (Lambda/Cloud Functions) | Discard host-level threats; focus on function permissions, cold start auth, event injection |
| Containers (ECS/K8s) | Consider container escape, image supply chain, network policies |
| API Gateway in front | Rate limiting likely built-in; focus on auth config and CORS policy |
| NoSQL database (DynamoDB, MongoDB) | Discard SQL injection; consider NoSQL injection, access policy misconfig |
| SQL database (PostgreSQL, MySQL) | Consider SQL injection, connection pooling, credential rotation |
| Redis/Memcached for caching | Consider cache poisoning, unauthenticated access, data expiration |
| Third-party payment processor | Focus on webhook validation, idempotency, reconciliation |
| Message queues (SQS, Kafka) | Consider message replay, poison messages, dead letter handling |
| No file upload | Discard file upload attack surface entirely |

When Technical Landscape is present, use it to **narrow and focus** the risk assessment rather than applying a generic threat catalog. When absent, flag it — generic risk assessment produces too many false positives.
