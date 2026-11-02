# Finance console: business intelligence for founders

## Context
Founders needed to answer questions like "which programmes earn their keep, what is our cash position, and where did the overhead go" without a finance analyst assembling it by hand each time.

## What I built
An internal finance console on its own schema in the shared database, plus a broader founder view that pulls the other platforms together.

| Area | What it does |
|---|---|
| Cash position | A cash-basis view that is deliberately independent of how revenue is attributed to programmes |
| Founder snapshot | Revenue and cost by category, school and region |
| Profitability | A per-programme ledger and a report view with budgets, an expense inspector and mentor costs |
| Overheads | Categories, entries and allocation across programmes |
| Programme codes | The registry where codes are created, programme status is managed, and cancellations and restores are recorded |
| Payments and reconciliation | Card and bank ledgers, matched to programme codes, with items parked for review |
| Vendor portal | A restricted role where a vendor can upload a bill and see only their own |
| Travel and budgets | Travel expenses and programme budgets |
| Founder 360 | One dashboard across sales, admissions, applications, revenue, finance, programmes and research, with a PDF statement extractor and a question-and-answer assistant |

## Design decisions
- **Two reporting bases.** "By programme" attributes everything to the programme's start month. "By month" uses actual dates. The screen always says which one is on.
- **Transfers are not income.** Money moving between the card processor and the bank is tracked as a transfer, so it is never counted twice.
- **Overhead is apportioned exactly.** Indirect cost is spread across the year's programmes by revenue share, rounded so the parts add up to the whole. Manual allocations override. Rows with unrecognised codes are excluded so they cannot distort profit.
- **One currency path.** Convert to a single base currency once, then to the display currency. Refunds keep their sign.
- **The browser never touches the database.** Role-checked server functions are the single entry, and the roles are owner, admin, viewer and vendor.
- **Syncs are replay-safe.** Bank and wallet rows arrive from sheets pushed by scripts and are keyed on the bank's own reference, never on a row number. Each sync keeps an audit log and a needs-review count. Failed rows are isolated so one bad row cannot stop a batch.
- **Accounting mirror.** Invoices and payments are pulled from the accounting system when it is connected.

## How AI is used
- A founder brief and a graded programme report, generated from pre-aggregated figures, with instructions that every claim must cite the numbers supplied and nothing may be invented.
- Vendor bills: a PDF becomes a draft. The model may pick a programme code only from the real list. The draft carries mismatch flags and a confidence score and starts as pending, so a person confirms it.

## Reusable version
[programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting) reproduces the profit-and-loss logic with invented data and tests. [Financial-Streamlining-And-Reporting](Financial-Streamlining-And-Reporting.md) covers the books behind it, and [Automated-Financial-Reporting](Automated-Financial-Reporting.md) the reports that arrive without anyone building them.

## A note on numbers
No amounts appear here. Cash, revenue, cost and profit are company data.
