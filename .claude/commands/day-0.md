---
description: Day-0 bootstrap - verify setup, then start the validate stage with product discovery
---

Follow `runbooks/day-0.md`.

1. Read `AGENTS.md` and its full read order. Confirm each file exists; list anything missing and stop if a policy file is missing.
2. Check `state/business.yaml`. If `currency`, `home_market` or `monthly_ad_envelope` is empty, ask the Owner for those three values and stop.
3. Verify integrations listed as `phase: day-0` in `integrations/stack.md` respond (read-only calls only). Report which work.
4. Run the **scout** agent on task V1 with the brief in `state/business.yaml → product_brief`. Output: shortlist of up to 3 products in `memory/decisions.md` per `playbook/product-scoring.yaml`.
5. Run **finance** on V4 for each shortlisted product using the scout's price and cost estimates (marked as estimates).
6. Run the **orchestrator** to open Linear issues for V2-V8 and write the first digest.
7. Commit: `[orchestrator] day-0 bootstrap`.
