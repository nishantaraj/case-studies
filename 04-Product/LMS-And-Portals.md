# Learner portal and LMS

## Context
Once applications and payments ran through one system, the next gap was what happens after a student enrols.

## What I built
One home for students, mentors and admins across every cohort. It went live with its first cohort.

**Students** get a dashboard, their programmes with sessions, recordings, resources, submissions, mentor feedback and certificates, a session calendar with a join button, announcements, moderated community chat, a help centre, and feedback forms with a reward for completing them. A rewards vault holds loyalty and effort credit, referrals and redemptions.

**Mentors** have a separate sign-in with a read-only view of their own cohorts, their sessions, student submissions and anonymised feedback. They see student data only through functions that leave out payment and parent details. Access ends the moment a mentor is removed from a cohort.

**Admins** manage programmes, cohorts, mentor groups and sections, sessions (with bulk upload), attendance, enrolments, certificates, feedback, announcements, community moderation, events, message templates, support tickets and the rewards vault.

## The enrolment engine
Enrolment is not a button someone presses. A scheduled reconciliation compares applications and payments with enrolments, plans the changes, and applies them through one function that writes the state and an audit row in the same transaction.

- Enrol on payment, unenrol on refund, move on a cohort change.
- Switches off by default, a dry-run mode, a cap on changes per run, and a guard that raises an alert on a sudden wave of refunds.
- Manual overrides can be pinned so the engine leaves them alone.
- New students enter a paced onboarding queue with caps and cooldowns. An existing account is reused by email.

## Other decisions worth noting
- **Admin first.** I built the admin side before the student side. The team needed visibility before students needed a portal, and it exposed data problems early.
- **One database.** The portal reads the same central data as everything else, so enrolment and payment status cannot drift apart.
- **Immutable history.** Enrolment events and the rewards ledger cannot be edited or deleted. The browser can never write credit or certificates.
- **Attendance is evidence.** Join clicks and recording views count as attendance alongside staff marks.
- **Community safety.** Phone numbers and contact details in chat are caught by the database, and an AI summary helps moderators.
- **A help assistant** answers student questions from a bundled knowledge file.

## Also built on the same pattern
A student leadership programme platform with gated levels, one task unlocked at a time, admin review and scoring, and referral analytics read from shared data. A public student website with a catalogue-driven programme finder and a consent-gated AI concierge that answers only from the live catalogue, discloses that it is an AI, and has rate and spend limits.

## What I'd change
I'd involve a few students earlier. The first cohort found rough edges that a short pilot would have caught.
