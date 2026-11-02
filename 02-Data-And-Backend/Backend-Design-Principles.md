# Backend design principles

## Context
The company's data lives in two Postgres databases on Supabase. One is the central spine for people, organisations, applications, payments, consent and outreach. The other backs the program sites, the LMS and the finance layer. Between them, edge functions handle intake, checkout, payment webhooks, reconciliation, and email and WhatsApp sends.

This page is the set of rules I apply when I add to either one.

## Principles

**Inbound data is a claim.** Anything that arrives from a form, a webhook or an import lands in a landing table first, with a unique key on the source and the sender's own idempotency key. It is copied into a real table only after validation. Rejected identities go to a quarantine area instead of being deleted, so someone can look at them later.

**Replays must be harmless.** Webhooks are retried and scripts are re-run. Payments are unique on provider and provider payment id, so the same event arriving twice changes nothing.

**Money is an integer plus a currency.** Amounts are stored in minor units with an explicit currency code. Nothing is converted at rest. Refunds are their own rows linked to the payment, so the payment stays a historical fact.

**A payment that cannot be matched is flagged, not guessed.** Rows carry a needs-review flag, and a person resolves them.

**Consent and suppression belong to the database.** An opt-out recorded once is honoured by every tool, because the check sits next to the data, not inside each sender.

**Access is a grant, not a role forever.** Staff have roles. Anything sensitive needs a time-limited grant with a reason, and views of sensitive records are logged.

**Row-level security is on by default.** Tables are deny-by-default and policies open specific doors. Functions that run with elevated rights get extra scrutiny.

**Migrate beside the old system.** Backups, quarantines, an id map and a run log sit in their own schema. The older projects kept running while the new one filled up.

**Every source has a code.** A source code column on inbound records, payments and refunds answers where a row came from.

## What I'd change
Write the ownership rules before the first table. Several of mine became explicit only when the first migration exposed a conflict.

## Reusable version
[supabase-backend-patterns](https://github.com/nishantaraaj-prog/supabase-backend-patterns) reproduces these ideas with invented names, plain SQL and a test suite that runs on a real Postgres.
