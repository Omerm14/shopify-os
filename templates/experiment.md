---
id: EXP-YYYYMMDD-agent-1
agent:
status: proposed
hypothesis: "If we ..., <metric> moves from <A> to <B> within <T> days, because ..."
metric:
baseline:
target:
min_sample: "100 clicks per variant and 48h"
window_days: 7
ice_r: {impact: 3, confidence: 3, effort: 2, risk: 1}
risk_class: R2
budget:
rollback: ""
opened: YYYY-MM-DD
closed: null
result_value: null
learning: null
tags: []
---

## Setup
What exactly changes, where, for whom. Variant names.

## Result
Filled by the analyst at close: numbers per variant, sample size, confidence in plain words.

## Learning
One sentence a future agent can act on. Copy it to `memory/learnings.md` with tags.
