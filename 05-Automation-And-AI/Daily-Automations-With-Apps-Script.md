# Daily automations with Apps Script

## Context
A lot of operations work lives in spreadsheets, and a lot of it is the same check done every morning. Google Apps Script is the lightest way to take that check away from a person without introducing a new system.

## What exists
A register of Apps Script automations, every one bound to a sheet, with a deployment status for each. In broad groups:

| Group | Examples |
|---|---|
| Reporting | A daily application report and daily payment reports for founders and operations. See [Automated-Financial-Reporting](../03-Finance/Automated-Financial-Reporting.md) |
| Campaign analytics | Reports pulled from three email-sending tools into sheets |
| People and communication | Auto-emails after form submissions, birthday and anniversary emails, welcome, handover and goodbye emails for staff |
| Documents | A bulk certificate and letter generator |
| Conversion | A masterclass conversion tracker |
| AI | Gmail replies drafted by an AI model against a persona, held for review, and an engine that captures replies back into the sheet |
| Visibility | Recurring checks of how the organisations appear in AI answers |

Behind the reports, scheduled database jobs refresh the application, payment, refund and programme-code sheets every hour.

## Principles behind the toolkit
- Settings live in Script Properties, never as constants in the code, so a test copy and the real sheet differ only by configuration.
- A job that sends something logs what it sent, so running it twice never sends twice.
- A programme register drives the logic. Nothing about a specific programme is written into a script.
- Unknowns are reported by name instead of being dropped silently.

## Reusable version
[apps-script-daily-ops-toolkit](https://github.com/nishantaraj/apps-script-daily-ops-toolkit) has the daily snapshot email, the idempotent staged reminders and a duplicate-safe CSV importer, written from scratch.
