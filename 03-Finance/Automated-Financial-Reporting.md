# Automated financial reporting

## Context
Reports that someone builds by hand are late, inconsistent and the first thing to slip when the team is busy. The goal was a reporting rhythm that runs without anyone, at the level of detail each reader needs.

## The reporting rhythm

| Cadence | Report | Reader |
|---|---|---|
| Daily | Application report: new applications by programme type, programme, cohort, school, country and city, plus a text version ready to paste into chat | Founders, operations, sales |
| Daily | Payment summary: today's payments with a programme and cohort breakdown showing gross, processor charges and net | Wide operations list |
| Daily | Payment report: month-to-date revenue split by programme type, with programme-wise detail beneath each | Founders only |
| Weekly | Full financial overview | Founders |
| Quarterly | Quarterly report with a programme-wise profit and loss breakdown | Founders |

Daily reports run from time-driven Apps Script triggers. Each also has an ad hoc date-range run for questions that do not fit the schedule.

## How the daily reports stay correct
- **A programme master drives everything.** Programme type, response source and active status come from one register. Nothing is hard-coded in the scripts.
- **Three kinds of source are handled.** Form sheets, database-synced sheets and web-form sheets. Rows are de-duplicated.
- **Several payment sources become one view.** Card payments, bank transfers and a second processor are matched to programmes by programme code first, then by looser matching. Refunds are matched to their original payment. Settlements and internal transfers are excluded so nothing is counted twice.
- **Currencies are converted once** to a single reporting currency.
- **Unknowns are named, not hidden.** Payments with an unknown or conflicting programme are listed by name in the email, so the register can be fixed at the source. A manual audit tool exists for this and is deliberately never put on a trigger.
- **Scheduled sync jobs in the database** refresh the application, payment, refund and programme-code sheets every hour, so the reports read current data.

## The weekly and quarterly layers
They rely on the same convention as the books and the console: one programme code on every row. That is what makes a programme-wise profit and loss possible, including deferred advance fees, foreign-exchange effects and allocated overhead. See [Programme-Code-Convention](Programme-Code-Convention.md) and [Financial-Streamlining-And-Reporting](Financial-Streamlining-And-Reporting.md).

## Reusable version
[programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting) shows the programme-wise profit and loss calculation with invented data. [apps-script-daily-ops-toolkit](https://github.com/nishantaraaj-prog/apps-script-daily-ops-toolkit) shows the daily snapshot pattern.

## A note on numbers
No figures appear here. Recipients and sheet identifiers are kept out of the public material.
