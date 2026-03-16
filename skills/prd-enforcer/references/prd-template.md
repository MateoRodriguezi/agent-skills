# PRD Template (prd-enforcer)

## Context (quantified problem)
- What is happening?
- Where in the journey?
- Evidence: baseline metric(s), time window, sample size
- Why now?
- Data sensitivity: what PII, financial, or credential data is involved? (if none, state "N/A")

## Objective (measurable)
- Primary objective metric: baseline → target by date
- Secondary metrics (guardrails): e.g., failure rate, support tickets, fraud rate

## Scope
### In scope
- Concrete deliverables (screens, APIs, flows, experiments)
### Out of scope
- Explicitly excluded items

## Technical Landscape
How the feature runs in production — enough context to evaluate effort, dependencies, and risks.

### Deployment model
- How is this deployed? (e.g., containers on ECS/K8s, serverless Lambda, monolith, static site)
- Environment(s): staging, production, multi-region?

### Key services & infrastructure
- Databases (e.g., PostgreSQL, DynamoDB, Redis)
- Message queues / event buses (e.g., SQS, Kafka, RabbitMQ)
- Storage (e.g., S3, GCS)
- Caching layers (e.g., Redis, Memcached, CDN)
- Auth providers (e.g., Cognito, Auth0, internal SSO)

### External integrations
- Third-party APIs (payment processors, KYC providers, notification services)
- Webhooks received or sent
- Partner/vendor dependencies

### Technology stack
- Language / framework / runtime (e.g., Node.js + Express, Python + FastAPI, Go)
- Relevant libraries or SDKs

### Data flow summary
- Where does data enter? (API, webhook, batch import, user input)
- Where does it get processed? (service, queue, worker)
- Where does it persist? (DB, cache, external system)

> Tip: a simple "data enters via X → processed by Y → stored in Z" is enough. This is not an architecture doc.

## Success Metrics
For each metric:
- Definition
- Baseline
- Target
- Time window
- Source of truth
- Owner

## Dependencies & Constraints
- Teams, vendors, compliance approvals
- Country/rail/platform constraints
- Security review or approvals needed (if feature handles sensitive data or exposes new endpoints)

## Risks & Mitigations
- Risk, impact, likelihood
- Mitigation and owner

Example risks to consider:
- Business risk: adoption lower than expected → mitigation: phased rollout with early signal metrics
- Data exposure risk: unauthorized access to user balances or PII → mitigation: validate ownership on every request, rate-limit sensitive endpoints

## Rollout Plan
- Phases (Alpha/Beta/GA)
- Gating criteria (including, for sensitive features: access control review complete, abuse scenarios documented)
- Timeline
- Owners
- Rollback plan

## Post-launch Monitoring
- Dashboards/queries
- Alerts and thresholds
- Review cadence
- Incident/responder path
- For features with financial or identity impact: alerts for anomalous patterns (unusual spikes, unexpected geos, auth failure bursts)
