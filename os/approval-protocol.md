# Approval protocol

How agents ask the Owner for permission, and how the answer becomes training data.

## Where

Linear team **EMP** (rename to fit). Every action that the autonomy matrix does not allow becomes an issue.

| Field | Value |
|-------|-------|
| Title | `[ACT][<agent>][R<class>] <verb> <object>` — e.g. `[ACT][media-buyer][R2] Scale ad set "Hook-B" 150→180 ILS/day` |
| Label | `needs-approval`, plus the agent label (`agent:media-buyer`) |
| Body | The action request JSON (`schemas/action-request.schema.json`) followed by a 3-line human summary |
| Due | Now + `expires_in_hours` (default 24) |

## Owner responses

| Owner does | Meaning | Agent then |
|-----------|---------|-----------|
| Moves to **Approved** | Execute exactly as written | Executes, comments result, moves to **Done** |
| Edits the body, then **Approved** | Execute the edited version | Executes edited version; logs the diff in `memory/decisions.md` as a lesson |
| Moves to **Rejected** with a comment | Do not execute | Logs the reason in `memory/decisions.md`; does not re-propose the same action for 7 days without new evidence |
| No answer before expiry | Default is **do nothing** | Marks **Expired**; re-proposes only if still relevant |

Protective actions are never queued. They are executed and then posted as `[PROTECT]` issues for visibility.

## Batching

To save the Owner's time, the orchestrator bundles all R1/R2 requests from a run into one daily issue `[DIGEST] YYYY-MM-DD approvals` with one checkbox per action. Ticked = approved, struck through = rejected. R3 requests always get their own issue.

## SLA targets

| Stage | Owner response target |
|-------|----------------------|
| validate / launch | same day |
| scale | 12 h for R2, 24 h for R3 |
| systemize+ | R3 only; 48 h |

## Measuring trust

`state/autonomy.yaml` keeps, per agent: proposals, approved unchanged, approved with edits, rejected, expired, rollbacks, breaches. The auditor updates it in the weekly review. These counters drive promotion (`os/autonomy.md §4`).
