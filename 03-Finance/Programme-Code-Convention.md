# Programme code convention

## Problem
A program run exists in several places at once: the accounting system, the application form, the response sheet, the payment link, the database, the dashboard. If each names it differently, every report starts with a translation step.

## The convention
Each program run gets one code, assigned once, built from four parts:

| Part | Meaning |
|---|---|
| Type | Camp, competition or fellowship |
| Partner | Who the program is run with |
| Programme | Which program in the family |
| Cohort | The run, usually as a year and month |

The code is the join key. It is the tracking value in the books, the metadata on every payment, the key that maps a response sheet to its program, and the column that lets a dashboard group correctly.

## How it is used
- Every batch gets its own code, including programs that run several batches a year.
- A registry maps each code to its application sheet and its program and payment links.
- Payment metadata carries the code, so a payment can be matched to its program.
- The books use it as the tracking value, which is what makes per-program profitability possible.


The invented-data version of this lives in [programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting).
