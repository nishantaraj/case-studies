# Lovable build portfolio

## Context
The company's internal and student-facing software is built with Lovable on top of Supabase. I designed the architecture and the product logic, and used AI to build quickly. This page is the catalogue: what exists, what each platform is for, and the habits that keep a lot of apps from turning into a mess. The code is the company's, so descriptions are generic.

## The platforms

| Platform | What it is | Deep dive |
|---|---|---|
| Application Portal | One front door for every digital programme: catalogue-driven forms, custom checkout, promo engine, automated email and WhatsApp reminders, and the central admin console | [Application-Portal](Application-Portal.md) |
| Learner Portal and LMS | Cohorts, student, mentor and admin portals, certificates, a rewards vault, and an enrolment engine | [LMS-And-Portals](LMS-And-Portals.md) |
| Finance console | Cash position, founder snapshot, programme profitability, overheads, budgets, vendor bills and the programme-code registry | [Finance-Console](../03-Finance/Finance-Console.md) |
| Founder 360 | One view across sales, admissions, applications, revenue, finance, programmes and research | [Finance-Console](../03-Finance/Finance-Console.md) |
| Effort First | An agent workspace that deploys AI calling agents by region and programme, with consent-gated follow-up | [AI-Calling-Agents](../05-Automation-And-AI/AI-Calling-Agents.md) |
| Affiliate platform | Affiliate, school and admin portals with attribution, earnings and payouts | [Affiliate-Platform](Affiliate-Platform.md) |
| Student leadership platform | A gated, task-by-task programme with admin review and referral analytics | [LMS-And-Portals](LMS-And-Portals.md) |
| Student website | A catalogue-driven programme finder with a consent-gated AI concierge | [LMS-And-Portals](LMS-And-Portals.md) |
| Programme and fellowship sites | A family of brand sites built from one readiness checklist. They read the shared catalogue and promo engine and keep only their own pages | [Application-Portal](Application-Portal.md) |
| Research access portal | Staff-only sign-in and approvals for a private research data store | n/a |

## How they are built
- React, TypeScript, Vite and Tailwind with shadcn components, TanStack Query for data, Recharts for charts.
- Supabase for auth, Postgres with row-level security, storage and edge functions. Stripe as the card rail.
- One shared database estate with a schema per platform. See [Platform-Estate-Architecture](../02-Data-And-Backend/Platform-Estate-Architecture.md).
- One shared catalogue of partners, programmes and cohorts. Other apps read it and never keep their own copy.

## Habits that keep it coherent
- **Plans before code.** Each project keeps dated plan files and a running decision log, so the reason for a change sits next to the change.
- **Idempotent webhooks and replay-safe reconciliation.** The same payment event twice changes nothing.
- **Campaign data is frozen at first touch.** Attribution recorded when someone first arrives is not overwritten later.
- **One student id across platforms.** A student is one person whichever app they are in.
- **Suppression is shared.** A blocked WhatsApp or email address is blocked everywhere.
- **A circuit breaker on email.** Repeated send failures pause all sending until someone looks.
- **Time is stored in UTC.**
- **Tests on the logic that moves money.** Allocation, currency and code handling have automated tests.
