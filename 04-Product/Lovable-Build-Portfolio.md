# Lovable build portfolio

## Context
The company's internal and student-facing software is built with Lovable on top of Supabase. This page is the catalogue: what exists, how it is put together, and the habits that keep a lot of small apps from turning into a mess. The code is the company's, so descriptions are generic.

## What exists

| Area | What it does |
|---|---|
| Application portal | Configurable application and webinar forms, a custom form builder that replaces a third-party form tool, payment links, promo codes, instalment plans, a payments dashboard, email and WhatsApp flows, campaign attribution, and admin roles |
| Learner portal and LMS | Cohorts, a mentor portal, certificates, feedback, moderated community chat, a loyalty vault with referrals, and an enrollment engine |
| Finance console | Cash position, a founder snapshot, profitability by program, overheads, budgets and travel expenses |
| Lead and outreach tools | A lead command centre, email, WhatsApp and calling campaigns, and AI analysis of meetings |
| Partner growth | An affiliate portal with referral tracking, a link shortener that preserves campaign parameters, and a research-data dashboard |
| Program sites | A family of program and fellowship sites built from one readiness checklist, plus a unified student website |

## How they are built
- React, TypeScript, Vite and Tailwind with shadcn components, TanStack Query for data, Recharts for charts.
- Supabase for auth, Postgres with row-level security, storage and edge functions. Stripe for checkout.
- One shared catalogue of partners, programs and cohorts, maintained in one admin console. Other apps read it and never keep their own copy.

## Habits that keep it coherent
- **Plans before code.** Each project keeps dated plan files, so the reason for a change is recorded next to the change.
- **Idempotent webhooks and replay-safe reconciliation.** The same payment event twice changes nothing.
- **Campaign data is frozen at first touch.** Attribution recorded when someone first arrives is not overwritten later.
- **One student id across platforms.** A student is one person whichever app they are in.
- **Suppression is shared.** A blocked WhatsApp or email address is blocked everywhere.
- **A circuit breaker on email.** Repeated send failures pause all sending until someone looks.
- **Time is stored in UTC.**
