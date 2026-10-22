---
description: Open, update or close an experiment record. Usage /experiment <agent> "<hypothesis>" or /experiment close <EXP-id>
---

Arguments: $ARGUMENTS

- **Open:** create `memory/experiments/<EXP-id>.md` from `templates/experiment.md`. Fill hypothesis in the form "If we X, metric Y moves from A to B within T, because Z", ICE-R scores, risk class, window, success threshold, rollback. Refuse if the agent already has 3 open experiments.
- **Close:** ask the analyst for the result vs threshold; set status `won | lost | inconclusive`; write one learning line to `memory/learnings.md` with tags; if this pattern is now confirmed 3 times, open a PR proposing it as a rule in `playbook/` or the agent's role file.
