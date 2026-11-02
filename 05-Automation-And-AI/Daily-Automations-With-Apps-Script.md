# Daily automations with Apps Script

## Context
A lot of operations work lives in spreadsheets, and a lot of it is the same check done every morning. Google Apps Script is the lightest way to take that check away from a person without introducing a new system.

## What exists
A register of Apps Script automations that covers, in broad groups:
- campaign reports pulled from email-sending tools
- HR and onboarding emails
- certificate generation
- a conversion tracker
- AI-drafted replies
- an engine that captures email replies back into the sheet

Alongside it, a short design note describes the reply-capture engine.

## Principles behind the toolkit
- Settings live in Script Properties, never as constants in the code, so a test copy and the real sheet differ only by configuration.
- A job that sends something logs what it sent, so running it twice never sends twice.

## Reusable version
[apps-script-daily-ops-toolkit](https://github.com/nishantaraaj-prog/apps-script-daily-ops-toolkit) has the daily snapshot email, the idempotent staged reminders and a duplicate-safe CSV importer, written from scratch.
