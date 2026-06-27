<div align="center">
  <img src="assets/banner.png" width="100%" alt="Mohammed Ain Tomar — Backend Engineer"/>
</div>

<div align="center">

[![Email](https://img.shields.io/badge/aintomar.mohammed200@gmail.com-111827?style=flat&logo=gmail&logoColor=EA4335)](mailto:aintomar.mohammed200@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-111827?style=flat&logo=linkedin&logoColor=3B82F6)](https://linkedin.com/in/mohammed-ain-tomar)
[![InvoiceBot](https://img.shields.io/badge/getinvoicebot.com-live-10B981?style=flat&labelColor=111827)](https://getinvoicebot.com)

</div>

---

Backend engineer focused on REST APIs, relational databases, and background job systems. I build software that automates real business operations and runs in production.

Based in Morocco. Targeting backend engineering positions in Germany from 2026.

---

## InvoiceBot

> Production SaaS that automates invoice reminder workflows for small businesses — [getinvoicebot.com](https://getinvoicebot.com)

Small businesses lose revenue to unpaid invoices. Manual follow-up is inconsistent and doesn't scale. InvoiceBot removes that dependency entirely — once an invoice is issued, the reminder lifecycle runs without human intervention.

**Architecture.**

```
                         ┌─────────────────────────────┐
                         │        Flask REST API        │
Client ── HTTPS ────────►│                             │
                         │  Auth · Business Logic       │
                         │  Invoice State · Webhooks    │
                         └──────────┬──────────────────┘
                                    │
              ┌─────────────────────┼──────────────────┐
              ▼                     ▼                  ▼
       ┌─────────────┐    ┌──────────────────┐  ┌──────────────────┐
       │  PostgreSQL  │    │   APScheduler    │  │  Lemon Squeezy   │
       │             │    │                  │  │                  │
       │ Users        │    │ Polling engine   │  │ Subscriptions    │
       │ Invoices     │    │ Reminder jobs    │  │ Billing events   │
       │ Reminders    │    │ Status checks    │  │ Webhook ingestion│
       └─────────────┘    └────────┬─────────┘  └──────────────────┘
                                   │
                                   ▼
                          ┌──────────────────┐
                          │   Brevo SMTP     │
                          │                  │
                          │ Transactional    │
                          │ email delivery   │
                          └──────────────────┘

                     Deployed on Render · Linux · Production
```

**Engineering decisions.**

*APScheduler over cron.* The reminder engine needs direct access to application state and database connections during execution. Running APScheduler in-process lets scheduled jobs reuse the existing SQLAlchemy session pool and eliminates subprocess startup overhead on every invocation.

*Lemon Squeezy over Stripe.* Stripe merchant payouts are unavailable in Morocco. Lemon Squeezy operates as Merchant of Record, handling tax obligations and payouts across MENA without requiring a foreign legal entity. Hard infrastructure constraint, not a preference.

*Invoice state as a PostgreSQL enum.* Lifecycle transitions (`draft → sent → reminded → overdue → paid`) are modeled as a native enum with application-level transition guards. Invalid state changes are structurally prevented, and reminder scheduling logic stays deterministic.

*SMTP over a hosted transactional API.* Brevo SMTP keeps per-message cost near zero at current scale. The delivery layer is abstracted behind a single interface — migrating to a higher-volume provider is a one-file change.

**Stack.**

| Layer | Technology |
|---|---|
| API | Python · Flask · REST |
| Auth | JWT |
| Database | PostgreSQL · SQLAlchemy |
| Jobs | APScheduler |
| Email | Brevo SMTP |
| Payments | Lemon Squeezy |
| Hosting | Render · Linux |

[Repository](https://github.com/Mohammed18-19/InvoiceBot) · [Live](https://getinvoicebot.com)

---

## Stack

```
Language      Python · SQL
Framework     Flask
Database      PostgreSQL · SQLAlchemy
Auth          JWT
Jobs          APScheduler
Infra         Linux · Docker · Git
Deployment    Render
```

---

## Current Focus

- PostgreSQL internals — indexing, query planning, EXPLAIN ANALYZE
- Docker — multi-stage builds, production container workflows
- System design — job queue reliability, idempotency, at-least-once delivery
- German — targeting B2, TELC B1 certified June 2026

---

<div align="center">

[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=Mohammed18-19&show_icons=true&hide_border=true&title_color=3B82F6&icon_color=8B5CF6&text_color=64748B&bg_color=00000000&hide=stars&count_private=true&hide_rank=true)](https://github.com/Mohammed18-19)

</div>

---

<div align="center">
  <sub>Open to backend engineering roles and Ausbildung Fachinformatiker Anwendungsentwicklung in Germany · <a href="mailto:aintomar.mohammed200@gmail.com">aintomar.mohammed200@gmail.com</a></sub>
</div>