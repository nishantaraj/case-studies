# LMS and portals

## Context
Once applications and payments ran through one system, the next gap was what happens after a student enrolls.

## What I built
- An application portal for the team: every application and payment across programs in one view, with filters and status management. I later spent a sprint cleaning it up as the number of views grew.
- A learner portal and LMS where enrolled students access cohort content. It went live with its first cohort.
- Student communication automation tied to cohort milestones and session schedules.
- A custom form builder, so the team can create new forms without a third-party tool.

## In design now
- A wallet system with two kinds of credit, one for the Effort First platform and one for loyalty
- Direct enrollment, so a student can join a cohort from inside the LMS
- Migration of the remaining external apply-and-pay forms into the central system

## Decisions worth noting
- I built the admin side before the student side. The team needed visibility into applications before students needed a portal, and the admin portal exposed data problems early.
- The LMS reads from the same central database as everything else, so enrollment and payment status never drift apart.

## What I'd change
I'd involve a few students earlier. The first cohort found rough edges that a short pilot would have caught.
