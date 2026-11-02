# Operating model: before and after

## Context
Learn with Leaders runs several student programs with a small team. Each program began as its own form, its own response sheet, its own payment links, and a person who knew how to reconcile them. That works for two programs. It stops working at eight.

## Before and after

| Area | Before | After |
|---|---|---|
| Data | A sheet per program, the same school spelled several ways | One central database. People, organisations, applications and payments are separate entities with explicit links |
| Inbound data | Form responses collected in per-program sheets | Lands in one place first, treated as a claim until validated |
| Payments | Payment links with no program or student attached, matched by hand | Custom checkout that carries a program code, a payment webhook, and a reconciliation job |
| Follow-up | Manual and inconsistent | Staged reminders, measured stage by stage |
| Finance | Reconciled by hand per program | One coded program taxonomy shared by the books, the database and the reports, with per-program tracking |
| Reporting | Built by hand | A daily snapshot to the founders and a weekly financial report that run themselves |
| After enrolment | A gap once a student had paid | A learner portal and LMS reading from the same database |
| Leads | Qualified by hand, a lot of manual time | Agents and meeting analysis, with guardrails, feeding the same data |
| New programs | Built case by case | A platform readiness checklist that a new program site is built against |

## The thread through all of it
Every change follows the same order. Get the data into one trusted place. Put money through it with identifiers that survive. Make reports read from it. Only then automate the follow-up, and measure each stage so the automation can be questioned.

## Where a person stays in the loop
Payments the system cannot match confidently are flagged for review. Agents go through approval stages before they send on their own. Refunds are recorded as their own events. The aim is to make people's decisions better informed, not to remove them.

## Where each piece is written up
- Data and backend: [02-Data-And-Backend](../02-Data-And-Backend/)
- Finance: [03-Finance](../03-Finance/)
- Product: [04-Product](../04-Product/)
- Automation and AI: [05-Automation-And-AI](../05-Automation-And-AI/)
- Process design: [06-Process-Design](../06-Process-Design/)

## A note on numbers
This page has none on purpose. Volumes, revenue and conversion rates are company data. Where figures are cleared for publication they will be added to the relevant case study.
