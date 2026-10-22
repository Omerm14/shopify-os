# Autonomy — how agents earn the right to act alone

Autonomy is granted per agent, not to the system as a whole. Each agent's current level and track record live in `state/autonomy.yaml`. Only the Owner changes a level upward. The auditor can lower it.

## 1. Risk classes (classify every action)

| Class | Meaning | Examples |
|-------|---------|----------|
| **R0 Read** | No change anywhere | Pull reports, read tickets, research suppliers, draft analysis |
| **R1 Reversible, internal** | Changes visible only to us, undo in one step | Tag orders, draft an email, draft a product page, create an unpublished ad |
| **R2 Reversible, external** | Customers or spend affected, but undo is quick and loss is capped by guardrails | Publish a page, start/scale an ad within caps, send a campaign, templated CS reply, refund under cap |
| **R3 Costly or hard to reverse** | Commits money or reputation beyond caps | Purchase order, price change, new supplier, new channel, discount above cap, big budget shift, policy change |
| **R4 Owner only** | Never done by an agent, at any level | Bank/payout details, account ownership, legal agreements, hiring/firing, loans, legal or regulatory replies, deleting data |

Protective actions (pause, hold, hide, stop) are **always allowed** regardless of class, and must be logged and announced within 1 hour.

## 2. Levels

| Level | Name | What the agent does | Owner's role |
|-------|------|---------------------|--------------|
| **L0** | Observe | Reads and reports | Reads reports |
| **L1** | Propose | Prepares every action fully; executes only after approval | Approves each action |
| **L2** | Act within caps | Executes R1 and capped R2 alone, notifies; asks for R3 | Reviews daily digest, can roll back |
| **L3** | Manage by exception | Executes R1–R2 alone, escalates only anomalies and R3 | Reads exceptions + weekly review |
| **L4** | Envelope owner | Also executes R3 inside a pre-approved envelope (e.g. monthly budget, PO within forecast ±10%) | Sets envelopes monthly, audits |

## 3. Matrix — may the agent act without approval?

| | R0 | R1 | R2 | R3 | R4 |
|---|---|---|---|---|---|
| L0 | yes | no | no | no | never |
| L1 | yes | after approval | after approval | after approval | never |
| L2 | yes | yes | yes, within caps, notify | after approval | never |
| L3 | yes | yes | yes | after approval | never |
| L4 | yes | yes | yes | yes, inside envelope; else approval | never |

## 4. Promotion (Owner decides; promotion is itself R3)

An agent may be proposed for the next level when **all** are true:

- At least 4 weeks at the current level
- At least 30 decisions at the current level
- 90%+ of its proposals approved **without edits** over the last 30
- Zero guardrail breaches in that window
- KPIs it owns did not regress vs the baseline it inherited
- Its rollback path was tested at least once
- The auditor signs off in the weekly review

## 5. Demotion (automatic)

- Any guardrail breach → down one level, open an incident
- Two rollbacks within 7 days → down one level
- Owned KPI in red for 2 consecutive weekly reviews → down one level
- Kill switch → all agents treated as L0 until cleared

## 6. Hand-off timeline (target, not promise)

| Phase | When | Business stage | Typical levels | Owner time |
|-------|------|----------------|---------------|-----------|
| A — Build the track record | Days 0–30 | Validate | All L0–L1 | Approves everything, ~1 h/day |
| B — First hands off | Days 30–90 | Launch | analyst, scout, creative L2; media-buyer L2 with tight caps; care L2 on templates | Daily digest ~20 min |
| C — Exception management | Months 3–9 | Scale | Most agents L2–L3 | Digest 10 min + weekly review 1 h |
| D — Envelopes | Month 9+ | Systemize → Empire | Ops, finance, media-buyer L3–L4 within envelopes | Monthly board meeting + R4 only |

The Owner's job at phase D: capital allocation, new brands, partnerships, and everything in R4.
