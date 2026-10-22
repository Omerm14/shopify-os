# Shopify OS (Empire OS)

An agent operating system for building a Shopify business from day 0, with the Owner in the loop at first and stepping out as agents earn autonomy.

- **Agents start here:** `AGENTS.md`
- **Owner starts here:** `runbooks/day-0.md`
- **The idea in one line:** every action is classified by risk (R0–R4), every agent has an autonomy level (L0–L4), and approvals are the training data that moves agents up the ladder.

## How it fits together

| Layer | Files |
|-------|-------|
| Constitution | `AGENTS.md`, `os/guardrails.yaml`, `os/autonomy.md` |
| Loops | `os/flywheel.md`, `os/cadence.yaml`, `.claude/commands/` |
| Playbook | `playbook/stages.yaml`, `metrics.yaml`, `unit-economics.md`, `product-scoring.yaml` |
| Team | `.claude/agents/` — orchestrator, analyst, auditor, scout, creative, media-buyer, store, lifecycle, care, ops, finance |
| Memory | `state/`, `memory/`, `logs/` |
| Human interface | Linear approvals (`os/approval-protocol.md`), Slack digest, kill switch (`runbooks/incident.md`) |

## Scaling to a portfolio
At stage 5 this repo becomes the **core**: `os/`, `playbook/` and `.claude/` move to a parent repo; each brand gets its own repo with `state/`, `memory/` and `logs/`, inheriting the core.
