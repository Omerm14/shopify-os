# The Flywheel

Two flywheels turn together. The **business flywheel** makes money. The **learning flywheel** makes the agents better at turning the first one, which is what lets the Owner step out.

## 1. Business flywheel

```
  Find a winning product ──▶ Test creatives cheaply ──▶ Lower CAC
          ▲                                               │
          │                                               ▼
  More product ideas &       ◀── More data, reviews ◀── More customers
  margin for testing              & repeat buyers
```

| Spoke | What turns it | Owner agent | Metric that proves it is turning |
|-------|---------------|-------------|----------------------------------|
| Winning product | Scoring rubric + cheap demand tests | scout | Products passing the stage-1 gate |
| Creative volume | 5–10 new creatives/week, structured angles | creative | Creatives tested / week, hit rate |
| Lower CAC | Fast kill/scale decisions on tests | media-buyer | CPA vs breakeven CPA, MER |
| Conversion | Product page and offer experiments | store | Conversion rate, AOV |
| Repeat & reviews | Flows, post-purchase, review requests | lifecycle, care | 90-day repeat rate, review count |
| Margin | Supplier terms, shipping, bundles | ops, finance | Contribution margin after ads |
| Reinvestment | Cash freed for tests and stock | finance, orchestrator | Test budget as % of profit, runway |

Each turn should make the next one cheaper: winning angles feed the next creative batch, buyer questions feed product pages, repeat buyers lower blended CAC, and margin funds more tests.

## 2. Learning flywheel (the agent system)

```
 Sense ──▶ Decide ──▶ Act ──▶ Measure ──▶ Learn ──▶ Memory
   ▲                                                   │
   └──────────── better priors, fewer approvals ◀──────┘
```

1. **Sense** — pull metrics (`playbook/metrics.yaml`), read queues, read memory.
2. **Decide** — compare with the stage gate; choose ≤3 actions. Every non-routine action is written as a hypothesis: *"If we X, metric Y moves from A to B within T, because Z."*
3. **Act** — classify R0–R4, act or request approval.
4. **Measure** — after the test window in `os/guardrails.yaml → min_test_runtime_hours`, record the result against the hypothesis.
5. **Learn** — one-line learning in `memory/learnings.md`, tagged so others find it (`#creative #hook #price`).
6. **Memory** — learnings become defaults: a pattern confirmed 3 times is proposed (via PR) as a rule in `playbook/` or a role file.

**Approvals are training data.** When the Owner edits or rejects a proposal, the agent records why in `memory/decisions.md`. The approval-without-edits rate is the main signal for promotion (`os/autonomy.md §4`).

## 3. The experiment engine

The unit of progress is an experiment (`schemas/experiment.schema.json`, `templates/experiment.md`).

- Every agent keeps **at least one and at most three** experiments open.
- Experiments are ranked with ICE-R: Impact (1–5) × Confidence (1–5) ÷ (Effort (1–5) × Risk (1–5)).
- A test that cannot reach a decision within 14 days is too small or too vague; rewrite it.
- Results are one of: `won`, `lost`, `inconclusive`. Inconclusive is a result; log it and move on.
- Never rerun a `lost` test without stating what is different.

## 4. Who talks to whom

```
                 Owner
                   ▲  approvals, digest, incidents
                   │
             orchestrator ◀──── auditor (independent checks)
      ┌──────┬─────┼──────┬──────┬───────┐
   scout  creative media  store lifecycle care   ops   finance
                   buyer
                   ▲
               analyst (single source of numbers for everyone)
```

- The **analyst** is the only agent that computes KPIs; others read `logs/metrics/`.
- The **auditor** never acts on the business. It checks other agents' actions against guardrails and scores them for promotion.
- Agents hand work to each other by opening a Linear issue assigned to the target agent's label, never by editing each other's files.
