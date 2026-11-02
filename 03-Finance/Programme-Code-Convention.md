# Programme code convention

## Problem
A programme run exists in several places at once: the accounting system, the application form, the response sheet, the payment link, the database, the dashboard. If each names it differently, every report starts with a translation step.

## The convention
Each programme run gets one code, assigned once, built from four parts:

| Part | Meaning |
|---|---|
| Type | Camp, competition or fellowship |
| Partner | Who the programme is run with |
| Programme | Which programme in the family |
| Cohort | The run, usually as a year and month |

The code is the join key. It is the tracking value in the books, the metadata on every payment, the key that maps a response sheet to its programme, and the column that lets a dashboard group correctly.

## How it is used
- Every batch gets its own code, including programmes that run several batches a year.
- A registry maps each code to its application sheet and its programme and payment links.
- Payment metadata carries the code, so a payment can be matched to its programme.
- The books use it as the tracking value, which is what makes per-programme profitability possible.


The invented-data version of this lives in [programme-finance-reporting](https://github.com/nishantaraaj-prog/programme-finance-reporting).
