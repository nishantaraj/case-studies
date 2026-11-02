# Case studies

Write-ups of systems I designed and built at Learn with Leaders, an EdTech company running several student programmes, where I am Head of AI Product Automations & Strategy. The source code is the company's, so these cover the problem, the design, the trade-offs, and what I'd change.

Start with [the operating model, before and after](01-Organisation-Reshaped/Operating-Model-Before-And-After.md), then read whichever area interests you.

## Index

| Folder | Case study | In one line |
|---|---|---|
| [01-Organisation-Reshaped](01-Organisation-Reshaped/) | [Operating model, before and after](01-Organisation-Reshaped/Operating-Model-Before-And-After.md) | How the company moved from a sheet per programme to one trusted system |
| [02-Data-And-Backend](02-Data-And-Backend/) | [Unified data architecture](02-Data-And-Backend/Unified-Data-Architecture.md) | Eight-plus programmes, one database, one set of rules for incoming data |
| | [Platform estate architecture](02-Data-And-Backend/Platform-Estate-Architecture.md) | One shared database, a schema per platform, one catalogue and one student id |
| | [Backend design principles](02-Data-And-Backend/Backend-Design-Principles.md) | The rules I apply to every table, webhook and migration |
| [03-Finance](03-Finance/) | [Financial streamlining and reporting](03-Finance/Financial-Streamlining-And-Reporting.md) | Programme-coded books, deferred revenue, and reports that arrive on their own |
| | [Finance console](03-Finance/Finance-Console.md) | Cash position, programme profitability and founder intelligence in one place |
| | [Automated financial reporting](03-Finance/Automated-Financial-Reporting.md) | Daily, weekly and quarterly reports, down to programme-wise profit and loss |
| | [Programme code convention](03-Finance/Programme-Code-Convention.md) | One identifier across the books, the forms, the payments and the database |
| [04-Product](04-Product/) | [Application portal](04-Product/Application-Portal.md) | One front door for every digital programme, with checkout and automated follow-up |
| | [Application-to-payment journey](04-Product/Application-To-Payment-Journey.md) | Forms, staged reminders, custom checkout, and reconciliation |
| | [Learner portal and LMS](04-Product/LMS-And-Portals.md) | Student, mentor and admin portals with an enrolment engine |
| | [Affiliate platform](04-Product/Affiliate-Platform.md) | Partner and school portals with attribution, earnings and payouts |
| | [Lovable build portfolio](04-Product/Lovable-Build-Portfolio.md) | Every platform in one table, and the habits that keep them coherent |
| [05-Automation-And-AI](05-Automation-And-AI/) | [AI calling agents](05-Automation-And-AI/AI-Calling-Agents.md) | Region and programme agents with consent, suppression and kill switches |
| | [AI lead agents and reporting](05-Automation-And-AI/AI-Lead-Agents-And-Reporting.md) | Agents that have to earn the right to send, and reports nobody builds by hand |
| | [Daily automations with Apps Script](05-Automation-And-AI/Daily-Automations-With-Apps-Script.md) | The checks a person used to do every morning |
| [06-Process-Design](06-Process-Design/) | [Building processes from scratch](06-Process-Design/Building-Processes-From-Scratch.md) | From unwritten habit to a rule people actually follow |

## Runnable companions
Original code with invented data, for the patterns described above:

- [supabase-backend-patterns](https://github.com/nishantaraj/supabase-backend-patterns): landing layer, money in minor units, consent, grants, an append-only audit log, and tests that run on real Postgres.
- [programme-finance-reporting](https://github.com/nishantaraj/programme-finance-reporting): programme-coded profit and loss with deferred revenue and multi-currency.
- [payment-reconciliation-template](https://github.com/nishantaraj/payment-reconciliation-template): matching payments to applications idempotently.
- [apps-script-daily-ops-toolkit](https://github.com/nishantaraj/apps-script-daily-ops-toolkit): daily snapshot, staged reminders, duplicate-safe CSV import.

## Scope
No company code, student data, partner names, prices or financial figures appear anywhere in this repository. Earlier work from Excelerate (internship operations automation) is summarised in my [profile README](https://github.com/nishantaraj/nishantaraj).
