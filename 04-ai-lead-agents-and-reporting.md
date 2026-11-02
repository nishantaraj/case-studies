# AI lead agents and reporting

## Context
Leads came in through email, forms, meetings, and outreach campaigns. Qualifying them and reporting on them took a lot of manual time.

## What I built
- Lead capture from the shared inboxes, written so a failed batch never marks messages as processed.
- An email agent that handles lead replies, trained and corrected against real conversations.
- A calling agent and a callback-request feature on the Effort First platform.
- AI analysis of meeting notes: a summary, objections, commitments, a lead score, and a suggested next step.
- Automated reports: a daily snapshot email to the founders and a weekly financial report.

## The rule I'm proudest of
Every agent starts with an autonomy level of zero for every segment, and the database enforces it with a constraint. An agent earns more freedom by showing good results, and sending autonomy is kept out of reach of ordinary settings. It's slower, and it means a bad agent run can't quietly email hundreds of schools.

## Outreach guardrails
- One relationship contact per school group, so a country campaign doesn't send 188 separate emails to schools of the same group
- Consent, suppression, and frequency limits checked in the database before any send
- A school locked to one program at a time, so two programs never pitch the same school

## What I'd change
I'd log human verdicts on agent outputs from the first run. Collecting them late made it harder to judge which agents deserved more autonomy.
