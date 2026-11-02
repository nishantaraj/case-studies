# AI calling agents

## Context
Reaching schools and families by phone does not scale with a small team, and a badly behaved caller damages a brand quickly. The question was how to deploy voice agents that are precise about who they call, what they say and what they are allowed to do afterwards.

## What I built
An agent workspace inside the Effort First platform. Each agent is a separate unit with its own purpose, voice, language, rules and campaigns. Nothing is shared except the provider account.

| Piece | How it works |
|---|---|
| One agent per region and programme | An agent owns its campaigns, contacts, calls and messages. A new agent starts from a generic brief plus its own script and facts, so it never inherits another agent's wording |
| Region settings | Calling windows by time zone, weekdays only, cooldowns, retry gaps, attempt limits and concurrency are set per campaign. Contacts outside their window are held, not dropped |
| Language | Set per agent. A regional agent can listen first and mirror the speaker's language |
| Live facts | Dates and venues come from the shared catalogue at call time. They are never written into a script |
| Contacts | Manual entry or CSV import with column detection, phone validation and de-duplication |
| Test first | Any number can be called in a test mode that touches no counters |
| Dialer | Starts per campaign, places one paced call per tick, claims each contact atomically so nobody is called twice, and switches itself off when idle |
| Call outcomes | Each call produces a structured result: interested, send info, call back, referred, not interested, do not call, voicemail, wrong number, no human. It also records whether the contact details were confirmed and what permission was given |
| Follow-up | Email and WhatsApp with tracked links, a scheduling link and an optional discount code |

## Guardrails
- **Consent fails closed.** A follow-up goes out only after a completed human call, with explicit permission and a read-back confirmed address. Email permission never implies WhatsApp permission.
- **Suppression is checked before every dial.** A shared do-not-call list, a limit on attempts per number per week, and permanent retirement on do-not-call and wrong-number.
- **Honest voice rules.** The agent answers truthfully if asked whether it is automated, does not invent facts, dates, prices or affiliations, and stops when interrupted.
- **Kill switches at three levels.** Pause one campaign, pause one agent, or pause all outreach, which defaults to paused.
- **Never trust a webhook alone.** Call results are confirmed against the provider before anything is sent. Ambiguous send failures are parked for review, never blindly resent.
- **Staged rollout.** Test calls, then a small pilot tranche, then wider use, with the worker initially off.

## Reporting
Per-agent view of contacts, queue, calls today and captured details. A call log with transcript, recording, summary and delivery status. A captured-contacts view with filters and export. A handoff summary goes to the human lead.

## Decisions worth noting
- Agent tables sit in the central database and are reachable only through server functions.
- Every decision has a recorded reason in a log beside the code.
- Only reads and replay-safe commands are retried. A call, a send or a create is never retried automatically.
- I describe the rollout as staged. Some pilot steps still wait on owner validation, so I do not claim results at scale.

## Related
[AI-Lead-Agents-And-Reporting](AI-Lead-Agents-And-Reporting.md) covers the wider rule for how any agent earns the right to act. The database side of consent and suppression is reproduced in [supabase-backend-patterns](https://github.com/nishantaraaj-prog/supabase-backend-patterns).
