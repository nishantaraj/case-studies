# AI lead agents and reporting

## Context
Leads came in through email, forms, meetings, and outreach campaigns. Qualifying them and reporting on them took a lot of manual time.

## What I built
- Lead capture from the shared inboxes, written so a failed batch never marks messages as processed.
- An email agent that handles lead replies, trained and corrected against real conversations.
- A calling agent and campaign dialer, and a callback-request feature on the Effort First platform.
- AI analysis of meeting notes: a summary, objections, commitments, a lead score, and a suggested next step.
- Automated reports: a daily snapshot email to the founders and a weekly financial report.

## The rule I care most about
An agent does not get to send on its own because it was built. Before that, it goes through safety tests, a shadow stage where it drafts and a human compares, and a pilot. Approvals leave an audit trail, and a controls table holds runtime switches so a campaign can be stopped without a deploy. It is slower. It also means a bad agent run cannot quietly email hundreds of schools.

## Outreach guardrails
- Consent, suppression, and frequency limits are checked in the database before any send.
- Do-not-contact lists are shared across tools, not kept per tool.
- A school is locked to one program at a time, so two programs never pitch the same school.
- Message claims and brand voice rules live in a registry the agents read, instead of being retyped into prompts.

## Reusable version
The database side of these guardrails is reproduced, with invented names and tests, in [supabase-backend-patterns](https://github.com/nishantaraaj-prog/supabase-backend-patterns).

## What I'd change
I'd log human verdicts on agent outputs from the first run. Collecting them late made it harder to judge which agents deserved more freedom.
