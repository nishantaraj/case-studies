# Financial streamlining and reporting

## Context
A multi-currency, multi-program business collects money through card payments and bank transfers, spends it across programs, and still has to answer a founder asking how one program is doing. For a long time that answer meant stitching sheets together.

## What I built
- **Books designed for programs.** A multi-currency setup in Xero with a chart of accounts that handles advance fees received, foreign-exchange gain and loss, and programme delivery costs. Cash taken before delivery is held as a liability, not counted as earned.
- **Per-program tracking.** A tracking category tags revenue and cost to a specific program run, so profitability can be read per program and per cohort, not just for the company.
- **A shared program code.** One code identifies a program run in the books, the response sheets, the payment metadata and the database. See [Programme-Code-Convention](Programme-Code-Convention.md).
- **A finance layer in the database.** Vendors and bills, overhead categories and allocations, program budgets, exchange rates, travel expenses, payment matches, and mirrors of the accounting invoices and payments.
- **A finance console.** An internal app with cash position, a founder snapshot, profitability by program, overheads, budgets and travel expenses.
- **Reports that arrive.** A daily snapshot email to the founders and a weekly financial report.

## How the pieces connect
In outline: payment events come from the payment provider, are matched to applications in the database and tagged with the program code, and are mirrored against the accounting records. The finance console and the reports read from that tagged data.

## Decisions worth noting
- Advance fees are a liability until delivered, so a program's margin is not flattered by cash that has not been earned.
- Profitability is tracked per program run, not only per company.
- Foreign exchange has its own accounts, so currency movement does not hide inside program results.

## Reusable version
[programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting) is a runnable illustration with invented data: coded transactions, monthly exchange rates, straight-line recognition of advance fees, overhead allocation and an exceptions list for rows that cannot be coded. It is my sketch of the idea, not the company's implementation.

## A note on numbers
No amounts appear here. Revenue, cost and cash figures are company data and stay with the company.
