---
description: Monthly close and stage-gate check - P&L, cash, gate status, autonomy promotions, next month's envelopes
---

1. **finance**: month close, 13-week cash forecast, proposed envelopes for next month (ad budget, PO budget, refund budget).
2. **analyst**: evaluate the current stage's `exit_gate` over the last 14 days; mark each condition pass/fail with values.
3. **auditor**: list agents eligible for promotion under `os/autonomy.md §4` with evidence.
4. **orchestrator**: one R3 issue per decision for the Owner: (a) advance stage or not, (b) each promotion, (c) envelopes. Update `state/business.yaml` only after approval.
5. Commit `[orchestrator] stage-gate <YYYY-MM>`.
