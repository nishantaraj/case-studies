# Application-to-payment journey

## Context
A student applies to a program, then has to pay to confirm a seat. Many applicants never complete the payment step.

## Problem
Follow-ups were manual and inconsistent. Payment links carried no program or student details, so matching a payment to the right application meant guesswork.

## What I built
1. Form submission goes through a single intake step into the central database.
2. A confirmation email goes out immediately.
3. Staged reminders follow: shortly after submission, then on days 2, 5, and 7, with extended windows after that.
4. A custom checkout replaced plain payment links. It captures student name, school, and a hidden program code as metadata.
5. A payment webhook records the payment, and a reconciliation job matches it to the application.
6. A confirmation email goes out after payment.

## How I measured it
The admin console reports each reminder stage separately: how many were sent, how many unique applicants were reached, and how many paid afterward.

Two things came out of that view:
- The early reminder stages converted best.
- The extended windows sent the most email for the least return, which made them the first candidate to trim.

## A note on claims
"Paid after a reminder" is not the same as "paid because of a reminder." Many applicants pay before any reminder is sent, and some reminded applicants would have paid anyway. The clean way to separate the two is a holdout test: withhold reminders from a small random slice of new applicants and compare. That test is on my list.

## What I'd change
I'd have built the stage-level measurement before the reminders, not after. It would have shaped the schedule from day one.
