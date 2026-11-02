# Unified data architecture

## Context
Learn with Leaders runs several student programmes. Each one started with its own form, its own response sheet, and later its own set of tables. Payments came from Stripe links and bank transfers, and people appeared under different names in different places.

## Problem
Nobody could answer a simple question like "how many students from this school applied across all programmes, and how many paid?" without stitching sheets together by hand. Duplicates were everywhere, and the same school showed up under several spellings.

## What I built
A single central database with a few firm rules:

- Everything inbound lands in one place first. A row there is a claim, not a fact. It becomes a fact only after validation.
- People, organizations, applications, and payments are separate entities with explicit links, so one student or school can be traced across programmes.
- Money is stored as minor units plus a currency code. Nothing is converted at rest. Refunds are their own records instead of status text inside a payment row.
- Applications from the older per-programme tables sync into one unified table on a schedule that is safe to re-run.
- Every source carries a code, so any lead, application or payment can be traced back to where it came from.
- Access is role-based. Elevated access comes as a time-limited grant with a recorded reason, and every view of sensitive data is logged.

How the later platforms share this database is in [Platform-Estate-Architecture](Platform-Estate-Architecture.md).

## Decisions worth noting
- I kept the older project running while the new one filled up, rather than doing a single cutover. It cost some duplicated effort and avoided a risky weekend.
- Consent and suppression live in the database, not in each tool, so an opt-out is honored everywhere.

## Result
Cross-programme questions that took hours of sheet work became queries. Reports, dashboards, and automations now read from the same source.

## What I'd change
I'd write the data-ownership rules before the first table. Several of them only became explicit after the first migration surfaced conflicts.
