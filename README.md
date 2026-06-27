<div align="center">
  <img src="assets/banner.png" width="100%" alt="Mohammed Ain Tomar — Backend Engineer"/>
</div>

<br/>

<div align="center">

<a href="https://getinvoicebot.com">
<img src="https://img.shields.io/badge/getinvoicebot.com-live-10B981?style=flat&labelColor=111827" alt="InvoiceBot"/>
</a>

<a href="mailto:contact@aintora.com">
<img src="https://img.shields.io/badge/contact@aintora.com-111827?style=flat&logo=gmail&logoColor=EA4335" alt="Email"/>
</a>

<a href="https://linkedin.com/in/mohammed-ain-tomar">
<img src="https://img.shields.io/badge/LinkedIn-111827?style=flat&logo=linkedin&logoColor=3B82F6" alt="LinkedIn"/>
</a>

</div>

---

# Backend Engineer

I build backend systems that automate real business operations through REST APIs, relational databases, background job architectures, and production deployments on Linux.

Based in Morocco. Targeting backend engineering opportunities in Germany from 2026.

I enjoy designing software that is reliable, maintainable, and built to solve real business problems.

---

# Featured Project — InvoiceBot

> Production SaaS that automates invoice reminder workflows for small businesses.

🌐 **Live:** https://getinvoicebot.com

Small businesses lose revenue because invoice follow-ups are often manual, inconsistent, and time-consuming.

InvoiceBot removes that entire workflow.

Once an invoice is created, reminder scheduling, payment tracking, subscription management, and email delivery happen automatically without human intervention.

---

## Architecture

```text
                         ┌─────────────────────────────┐
                         │        Flask REST API        │
Client ── HTTPS ────────►│                             │
                         │ Authentication              │
                         │ Business Logic              │
                         │ Invoice Management          │
                         │ Payment Webhooks            │
                         └──────────┬──────────────────┘
                                    │
              ┌─────────────────────┼──────────────────┐
              ▼                     ▼                  ▼
       ┌─────────────┐    ┌──────────────────┐  ┌──────────────────┐
       │ PostgreSQL  │    │ APScheduler      │  │ Lemon Squeezy    │
       │             │    │                  │  │                  │
       │ Users       │    │ Reminder Jobs    │  │ Subscriptions    │
       │ Invoices    │    │ Polling Engine   │  │ Billing Events   │
       │ Reminders   │    │ Status Checks    │  │ Webhooks         │
       └─────────────┘    └────────┬─────────┘  └──────────────────┘
                                   │
                                   ▼
                          ┌──────────────────┐
                          │ Brevo SMTP       │
                          │                  │
                          │ Transactional    │
                          │ Email Delivery   │
                          └──────────────────┘

                    Hosted on Render · Linux · Production
```

---

## Engineering Decisions

### APScheduler over cron

The reminder engine requires direct access to application state and database connections. Running APScheduler inside the Flask application eliminates process startup overhead while allowing scheduled jobs to reuse existing SQLAlchemy sessions.

### Lemon Squeezy over Stripe

Stripe merchant payouts are unavailable in Morocco. Lemon Squeezy operates as a Merchant of Record, handling taxation, subscriptions, and payouts across MENA without requiring a foreign company.

### PostgreSQL enum-based invoice states

Invoice lifecycle states (`draft → sent → reminded → overdue → paid`) are modeled as PostgreSQL enums with controlled application-level transitions. This guarantees deterministic reminder scheduling and prevents invalid state changes.

### SMTP abstraction

Brevo SMTP provides inexpensive transactional email delivery at the current scale. The email layer is abstracted, making migration to another provider straightforward if future volume requires it.

---

# Technologies I Work With

| Layer           | Technology              |
| --------------- | ----------------------- |
| Language        | Python                  |
| Backend         | Flask                   |
| Database        | PostgreSQL · SQLAlchemy |
| Authentication  | JWT                     |
| Background Jobs | APScheduler             |
| APIs            | REST                    |
| Email           | Brevo SMTP              |
| Payments        | Lemon Squeezy           |
| Infrastructure  | Linux · Docker · Git    |
| Deployment      | Render                  |

---

# Current Focus

* PostgreSQL internals (indexing, query planning, EXPLAIN ANALYZE)
* Docker and production container workflows
* System design for distributed backend architectures
* German language (TELC B1 → targeting B2)

---

# GitHub Activity

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Mohammed18-19&show_icons=true&hide_border=true&title_color=3B82F6&icon_color=8B5CF6&text_color=64748B&bg_color=00000000&hide=stars&count_private=true&hide_rank=true"/>

<br/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Mohammed18-19&layout=compact&hide_border=true&title_color=3B82F6&text_color=64748B&bg_color=00000000"/>

</div>

---

# Featured Repositories

* 🚀 **InvoiceBot** — Production SaaS for automated invoice reminder workflows
* 💼 **Portfolio** — Personal portfolio showcasing backend engineering projects

---

<div align="center">

<a href="https://github.com/Mohammed18-19/InvoiceBot">InvoiceBot</a> • <a href="https://github.com/Mohammed18-19/Portfolio">Portfolio</a> • <a href="https://linkedin.com/in/mohammed-ain-tomar">LinkedIn</a> • <a href="mailto:contact@aintora.com">Email</a>

</div>

<br/>

<div align="center">
<sub>Open to Backend Engineering roles and Ausbildung Fachinformatiker Anwendungsentwicklung opportunities in Germany.</sub>
</div>
