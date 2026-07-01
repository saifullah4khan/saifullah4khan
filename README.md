# Saifullah Khan

Python/Flask developer building AI-powered backend systems that automate real-world
business workflows. I like the messy parts: webhooks that retry, models that
rate-limit, and the edge cases that only show up in production.

Currently building and running **[HandleHQ](https://handlehq.net)**, a deployed
multi-tenant SaaS that replaces manual customer support handling for small and
mid-sized businesses using LLMs and REST APIs.

🎯 Exploring **Solutions Engineering, Implementation, and Associate PM** roles where
hands-on technical skills meet customer-facing problem solving. US citizen, open to
remote.

---

## HandleHQ — the product behind most of this

**[HandleHQ](https://handlehq.net)** is a deployed, multi-tenant SaaS that answers a
business's inbound customer messages with an AI agent, collects the details needed for a
support ticket or sales lead, files the ticket, and hands the owner a portal to run the
whole operation. There's a [live demo](https://app.handlehq.net/demo), no login required.

What's actually in it:

- **AI intake pipeline** — OpenAI `gpt-4o` for strict-schema field extraction and
  `gpt-4o-mini` for conversational replies, off-topic classification, and ticket
  summaries, driven by per-business intake templates across 18 verticals.
- **Multi-channel intake** — email live via SendGrid Inbound Parse, a direct message
  API, and a WhatsApp channel (Meta Cloud API, built and pending Meta verification).
- **Full ticket system** — status, priority, tags, assignee, outcome, urgent flag,
  internal notes, and AI-generated summaries, with automatic escalation of overdue
  tickets up the priority tiers.
- **Analytics** — a portal metrics dashboard (ticket volume, average first-response
  time, ROI) plus an admin funnel view across all tenants.
- **Multi-tenant data layer** — PostgreSQL via SQLAlchemy with Alembic migrations,
  Redis for cross-worker rate limiting and portal login lockout, and nightly database
  backups with a tested restore path.
- **Self-serve onboarding and billing** — a public application form, admin review,
  Stripe Checkout (setup fee plus subscription with a free trial) behind a swappable
  payment-provider abstraction, and automatic tenant provisioning on payment.
- **Three surfaces** — a marketing site, a React/Vite/Tailwind customer portal, and a
  super-admin dashboard, each on its own subdomain.
- **Production infrastructure** — gunicorn behind nginx with Let's Encrypt TLS on a VPS,
  GitHub Actions CI running a hermetic pytest suite, Dependabot, fail-closed
  HMAC-verified webhooks, CSP/HSTS, request-ID tracing, and opt-in structured JSON
  logging.

The problem it solves: most small businesses handle customer inquiries manually with no
structure or tracking. HandleHQ slots into that workflow and automates the intake,
triage, and follow-up layers end to end.

---

## Stack

| | |
|---|---|
| **Languages** | Python, C++ |
| **Backend** | Flask, REST APIs & webhooks |
| **Database** | PostgreSQL, SQLAlchemy, Alembic, Redis |
| **AI** | OpenAI (`gpt-4o` / `gpt-4o-mini`), prompt engineering |
| **Integrations** | SendGrid, Meta WhatsApp Cloud API, Stripe |
| **Infra & tooling** | gunicorn, nginx, systemd, VPS, Git, Postman, GitHub Actions CI/CD, Dependabot |

---

## A Few Things I Care About

- **Reliability over cleverness** — bounded retries, idempotency, graceful fallbacks:
  the stuff that keeps a webhook from taking down a worker.
- **Integrations that hold up** — most of my work is wiring third-party APIs together
  and handling what happens when one of them misbehaves.
- **Explaining the system, not just shipping it** — clear READMEs, architecture docs,
  and runbooks so the next person (or the customer) isn't lost.

---

## Featured Work

> _Small, focused, MIT-licensed repos, most extracted and generalized from HandleHQ's
> production code. All tested._

- **[openai-retry](https://github.com/saifullah4khan/openai-retry)** — production-grade
  retry/backoff for the OpenAI SDK; treats `insufficient_quota` as terminal via a typed
  error, with jittered exponential backoff.
- **[idempotency-keys](https://github.com/saifullah4khan/idempotency-keys)** —
  framework-agnostic helper that runs an operation at most once per key; handles the
  in-flight conflict, never caches failures, memory or Redis backends.
- **[webhook-inspector](https://github.com/saifullah4khan/webhook-inspector)** — tiny
  Flask service to receive, verify (constant-time HMAC), inspect, and replay webhooks
  while you debug an integration.
- **[flask-error-envelope](https://github.com/saifullah4khan/flask-error-envelope)** —
  consistent, typed JSON error responses for Flask APIs from a single call; never leaks
  stack traces, and sets an RFC-7231 Retry-After on 429s.
- **[sendgrid-inbound-parse-starter](https://github.com/saifullah4khan/sendgrid-inbound-parse-starter)**
  — minimal, documented Flask starter for receiving inbound email via SendGrid Inbound
  Parse.
- **[postman-to-markdown](https://github.com/saifullah4khan/postman-to-markdown)** — a
  CLI that turns a Postman collection into clean, committable Markdown API docs.

---

## Background

Before writing code full-time I spent 4 years managing operations at a medical clinic in
New York. Promoted to manager within the first year, digitized the entire workflow, and
introduced AI tools that cut administrative overhead significantly. That experience
shapes how I work: the problem first, the technology second.

---

## Get In Touch

- **Product:** [handlehq.net](https://handlehq.net) · [live demo](https://app.handlehq.net/demo)
- **Email:** saifullah4khan@gmail.com
- **LinkedIn:** [linkedin.com/in/saifullah-khan-6377b22a2](https://www.linkedin.com/in/saifullah-khan-6377b22a2/)
