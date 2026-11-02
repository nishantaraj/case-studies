# Application Portal: one front door for every digital programme

## Context
Each digital programme used to have its own site, its own form, its own payment link and its own follow-up routine. The company ran many of them at once. Adding a new programme meant rebuilding the same plumbing, and nobody could see the whole funnel in one place.

## What I built
One applications, checkout and automation system that every programme site plugs into, with a single admin console on top.

| Layer | What it does |
|---|---|
| Catalogue | A programme is one row and an intake (cohort) is one row, owned by a partner. The same catalogue drives the apply page, the pay page and every partner site that shows dates and seats. Other sites read it through versioned APIs and never keep a copy |
| Form builder | A launch wizard that creates the form, the programme row and the cohort rows together. Forms are schemas with per-form settings: branding, seat caps, option-based pricing, conditional questions |
| Custom checkout | The server calculates the amount and sends the card request. The browser only holds a one-time submission token. Pay-first and apply-first journeys end on the same application row, so there are no orphan or duplicate payments |
| Promo engine | Percent or fixed codes scoped to programmes or cohorts, with usage caps, validity windows and per-email limits. Validated and redeemed on the server, and safe to replay |
| Payment webhook | The only writer of payment state. Signature-checked, idempotent, and it parks anything it cannot match for review instead of guessing |
| Communication engine | Email and WhatsApp, driven by application and payment status (see below) |
| Admin console | Applications, payments, payment links, promo codes, forms, catalogue, mentors, leads and automation settings, with roles enforced on the server as well as in the screens |

## From application to conversion, automated
1. An application triggers an instant confirmation. Programmes that need review get an "under review" message instead.
2. A payment-pending ladder starts: a nudge within minutes, then reminders spaced across the first week, then further cycles until shortly before the programme starts. Only the most recent due stage is ever sent, so a delayed job never fires a stale reminder.
3. A payment cancels the ladder and sends a receipt. Someone who paid first gets a link to complete the application.
4. Residential and event programmes have their own drip: review, interview, offer letter, then reminders, driven from an admin queue.
5. Instalment plans have numbered links, scheduled collection, failure notices and an internal overdue digest.

## Safety on every send
- A guard stops the same template going twice to the same student.
- A global kill switch for automated email, plus per-programme and per-stage switches.
- A circuit breaker: repeated send failures pause all sending until someone looks.
- A shared WhatsApp blocklist, per-programme stop lists, and unsubscribe links that work.
- Every email and message is logged and stitched to the student, so the admin console shows a single timeline of leads, applications, payments, messages and visits.

## Measurement
Attribution is frozen at first touch. Each payment records its own touch separately, append-only. The console reports every reminder stage on its own, and shows revenue that followed automated reminders. The method and its limits are in [Application-To-Payment-Journey](Application-To-Payment-Journey.md).

## Decisions worth noting
- **Prices are calculated on the server.** The browser never sends an amount.
- **Derive, don't store.** Seats left, live status and apply links are computed from the catalogue, never copied.
- **The contract is a document.** The rules for programme links and the catalogue operating manual are written to be handed to partner platforms and to AI agents.
- **Plans next to code.** Architecture decisions are kept in a running log with the reason beside each one.

## How it connects
It sits on the shared platform described in [Platform-Estate-Architecture](../02-Data-And-Backend/Platform-Estate-Architecture.md). The learner portal reads its applications to enrol students. The finance console reads its payments. The agents and the affiliate platform use its promo and payment-link engine.

## A note on numbers
No volumes, prices or conversion rates are given on purpose. They are company data.
