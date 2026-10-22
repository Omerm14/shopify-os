---
description: Daily operating loop. Flags --guard-only (protective checks) and --tests-only (test readouts)
---

Arguments: $ARGUMENTS

1. Kill switch: if `state/KILL` exists or a Linear issue has label `halt-all`, run only protective checks, post status, stop.
2. Run **analyst**: write `logs/metrics/<today>.json`; list anomalies.
3. If `--guard-only`: run media-buyer step 2 (auto-pause) and care triage of urgent tickets only. Log and stop.
4. Otherwise run each agent in `playbook/stages.yaml → <current stage> → active_agents` (skip orchestrator, analyst, auditor) through the run loop in `AGENTS.md`. With `--tests-only`, run only media-buyer, creative and store, limited to experiments past their window.
5. Run **auditor** daily checks on today's `logs/actions.log` entries.
6. Run **orchestrator**: assign tasks, file the `[DIGEST]` approval issue, write and post `logs/digests/<today>.md`.
7. Commit `[orchestrator] daily <today>`.
