# Day 0 → Day 14 — getting the flywheel turning

Owner time: about 3 hours on day 0, then ~1 hour per day.

## Day 0 — Owner setup (≈3 h)

- [ ] Create a private GitHub repo from this folder; push.
- [ ] Fill the `OWNER` fields in `state/business.yaml` (currency, home market, monthly ad envelope, product brief).
- [ ] Linear: create team **SHOP**, labels `needs-approval`, `halt-all`, `agent:<name>` for each agent; workflow states Proposed → Approved / Rejected / Expired → Done.
- [ ] Slack: create `#shopify-os`; connect Linear and GitHub notifications.
- [ ] Shopify: create the store (or a development store while validating); create a custom app with **read-only** scopes from `integrations/stack.md`; store the token as an environment secret.
- [ ] Meta Business: ad account with a spending limit equal to the validate-stage envelope (set the limit in Meta itself as a second safety net).
- [ ] In Claude Code inside the repo: run `/day-0`.

## Days 1–3 — Product shortlist (scout, finance)
- Review the shortlist in `memory/decisions.md`. Approve up to 3 products for sample orders (R3).
- Owner orders samples (payments are R4).

## Days 3–7 — Test assets (store, creative, media-buyer)
- Approve the test page and 3–5 creative angles.
- Approve the test campaign within the daily cap.
- Schedule the loops in `os/cadence.yaml`: `daily-morning`, `daily-evening`, `weekly-review`.

## Days 7–14 — Demand test
- Read the morning digest; approve or edit in the `[DIGEST]` issue.
- Every edit and rejection gets a reason in one line. That is how the agents learn your judgment.
- Day 14: orchestrator proposes go / iterate / kill per product (task V8).

## What "done" looks like at day 30
- One product with 10+ paid orders, or a clear kill with learnings logged
- 30+ proposals decided per active agent, unchanged-approval rate measured
- First weekly reviews in `logs/weekly/`
- First promotion candidates (likely analyst and scout to L2)
