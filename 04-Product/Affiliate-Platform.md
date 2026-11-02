# Affiliate platform

## Context
Partners and schools were already sending students to the programmes. Tracking who sent whom, and paying fairly, was manual and trust-based.

## What I built
Three portals under one brand, on top of the shared platform.

| Portal | Who uses it | What it does |
|---|---|---|
| Affiliate partners | Individuals and organisations who refer students | Dashboard, programmes, promo codes, payment links, earnings, payouts, performance, a leaderboard and resources |
| School partners | Invited schools | Dashboard, students, programmes, payments and announcements |
| Admin | The team | Partners, schools, applications with attribution, payouts and admins |

## How attribution and earnings work
- A partner gets real promo codes and payment links. They are created in the central checkout and tagged to the partner, so the checkout honours them.
- Earnings are calculated from actual redemptions and link payments, multiplied by a commission rate that depends on the programme format.
- Admins move payouts through processing, paid or cancelled in a ledger.
- Admin views show which partner or school code each application came from, filterable by platform.
- The leaderboard shows first name and initial only. Metrics that could not be measured properly were removed rather than faked.

## Decisions worth noting
- **Calculated, not copied.** Earnings are read from the central records, so they cannot drift from what the checkout recorded.
- **A single, narrow write.** The platform is read-only against the central system except for creating the promo codes and links a partner needs. The price floor on those is enforced on the server.
- **Named database functions only.** The server calls fixed, validated functions and never builds ad hoc queries. Every argument is checked before use.
- **Access is checked twice**, in the server function and again in the database.

## Related
[Application-Portal](Application-Portal.md) provides the checkout. [Platform-Estate-Architecture](../02-Data-And-Backend/Platform-Estate-Architecture.md) explains the shared data.

## A note on numbers
Commission rates, earnings and partner counts are company data and are not published.
