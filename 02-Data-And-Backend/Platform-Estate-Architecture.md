# Platform estate architecture

## Context
Over time the company ended up with many front ends: an application portal, a learner portal, a finance console, an affiliate platform, an outreach platform, a student website and a family of programme sites. Left alone, each would have grown its own database and its own idea of what a student, a programme or a payment is.

## What I built
One shared database estate with a clear division of ownership.

- **A schema per platform.** Each application owns its own schema and writes only there. A platform never writes into another platform's tables.
- **A shared catalogue.** Partners, programmes, cohorts, mentors and masterclasses live in one place, read-only for everyone else. Apps reference a cohort by id and derive status from dates. They never keep a local copy.
- **One identity.** One email is one person across every platform, so a student has a single id from application to certificate.
- **One door into the data.** Browsers never talk to the database directly. Role-checked server functions are the only way in, with allow-lists for what can be read or written.
- **Codes are minted in one place.** Programme codes are created only in the finance console, and every other system receives them. See [Programme-Code-Convention](../03-Finance/Programme-Code-Convention.md).
- **Scheduled work through the database.** Recurring jobs call server functions on a schedule. Each one is safe to run twice.
- **Migrations as files.** The SQL for the shared database is kept as dated files in each project, because the editor does not own that database.

## Why it works
| Rule | What it prevents |
|---|---|
| Write only to your own schema | One platform quietly corrupting another's data |
| Read the catalogue, never copy it | Two sites showing different dates for the same programme |
| One student id | The same person counted three times |
| Server functions as the only door | A missing access rule in a screen exposing data |
| Codes minted once | Finance and operations disagreeing about which programme a row belongs to |

## Decisions worth noting
- A payment webhook push from the payments platform to the learner portal was removed on purpose. A scheduled reconciliation compares applications with enrolments and applies only the differences. It is slower by minutes and far easier to reason about.
- Where a table's role names could not be changed, the code maps the older names instead of altering a shared definition.

## Reusable version
The patterns underneath are reproduced with invented names and runnable tests in [supabase-backend-patterns](https://github.com/nishantaraj/supabase-backend-patterns).

## Related
[Unified-Data-Architecture](Unified-Data-Architecture.md) covers the first consolidation. [Backend-Design-Principles](Backend-Design-Principles.md) lists the rules applied to every table and webhook.
