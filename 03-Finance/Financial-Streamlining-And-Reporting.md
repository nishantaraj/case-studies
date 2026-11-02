# Financial streamlining and reporting

## Context
A multi-currency, multi-programme business collects money through card payments and bank transfers, spends it across programmes, and still has to answer a founder asking how one programme is doing. For a long time that answer meant stitching sheets together.

## What I built
- **Books designed for programmes.** A multi-currency setup in Xero with a chart of accounts that handles advance fees received, foreign-exchange gain and loss, and programme delivery costs. Cash taken before delivery is held as a liability, not counted as earned.
- **Per-programme tracking.** A tracking category tags revenue and cost to a specific programme run, so profitability can be read per programme and per cohort, not just for the company.
- **A shared programme code.** One code identifies a programme run in the books, the response sheets, the payment metadata and the database. See [Programme-Code-Convention](Programme-Code-Convention.md).
- **A finance layer in the database.** Vendors and bills, overhead categories and allocations, programme budgets, exchange rates, travel expenses, payment matches, and mirrors of the accounting invoices and payments.
- **A finance console.** An internal app with cash position, a founder snapshot, profitability by programme, overheads, budgets and travel expenses. See [Finance-Console](Finance-Console.md).
- **Reports that arrive.** Daily application and payment reports, a weekly full financial overview and a quarterly report with a programme-wise profit and loss. See [Automated-Financial-Reporting](Automated-Financial-Reporting.md).

## How the pieces connect
In outline: payment events come from the payment provider, are matched to applications in the database and tagged with the programme code, and are mirrored against the accounting records. The finance console and the reports read from that tagged data.

## Decisions worth noting
- Advance fees are a liability until delivered, so a programme's margin is not flattered by cash that has not been earned.
- Profitability is tracked per programme run, not only per company.
- Foreign exchange has its own accounts, so currency movement does not hide inside programme results.

## Reusable version
[programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting) is a runnable illustration with invented data: coded transactions, monthly exchange rates, straight-line recognition of advance fees, overhead allocation and an exceptions list for rows that cannot be coded. It is my sketch of the idea, not the company's implementation.

## A note on numbers
No amounts appear here. Revenue, cost and cash figures are company data and stay with the company.
