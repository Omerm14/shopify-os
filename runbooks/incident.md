# Incidents and the kill switch

## Pull the kill switch when
- Spend is running away, wrong prices are live, messages went to the wrong people, checkout is broken, or an agent did something you did not expect and you don't know why.

## How
- **Fastest:** add label `halt-all` to any open Linear issue, or
- commit an empty file `state/KILL`.
Every agent checks both at the start of each run and goes read-only. Protective actions (pause, hold, hide) remain allowed.

## Auto-triggers (also in `os/guardrails.yaml → kill_switch`)
- Daily ad spend over cap by 10%
- 24h refund rate over 3× the 30-day average
- Checkout or payment failure

## After the switch
1. Auditor opens `INC-…` from `templates/incident.md` within 1 hour.
2. Containment: pause ads and sends, revert the last changes from `logs/actions.log` (each entry lists its rollback).
3. Owner decides when to clear: delete `state/KILL` / remove `halt-all`.
4. Within 48h: root cause and a PR that changes a guardrail, role file or tool scope so it cannot recur. The agent involved is demoted one level.

## Rollback references
| System | Rollback |
|--------|----------|
| Theme | Republish previous theme version (kept by store agent) |
| Product/price | Restore from the snapshot logged before the change |
| Ads | Pause; restore previous budget from the action log |
| Email/SMS | Cannot unsend: send correction only if the Owner approves |
| Refunds | Cannot reverse: covered by caps |
