# Stack, access and credentials

**Principle:** each agent gets the narrowest access its current level needs. Write scopes are added only when an agent reaches L2 for that system. Tokens live in the runtime's secret store (environment variables), never in this repo, never in memory or logs.

## Runtime

| Piece | Choice | Notes |
|-------|--------|-------|
| Agent runtime | Claude Code, headless (`claude -p "/daily"`) on a schedule | Subagents from `.claude/agents/`, loops from `.claude/commands/` |
| Scheduler | Cron / GitHub Actions / Claude scheduled tasks | Times in `os/cadence.yaml` |
| Source of truth | This Git repo | Every run commits; history = audit trail |
| Approvals & tasks | Linear (team EMP) | `os/approval-protocol.md` |
| Notifications | Slack `#empire-ops` | Digest, approvals, incidents |

## Systems by phase

| System | Purpose | Phase | Day-0 access | Added later |
|--------|---------|-------|-------------|-------------|
| Shopify Admin GraphQL (custom app token) | Products, orders, inventory, analytics | day-0 | `read_products`, `read_orders`, `read_inventory`, `read_analytics` | `write_products` (store L2), `write_inventory` (ops L2), `write_discounts` (store L2, capped) |
| Shopify CLI + theme | Theme edits on a duplicate theme | day-0 | Dev/duplicate theme only | Publish rights at store L2 |
| Shopify Dev MCP / AI Toolkit | Docs, GraphQL schema, code validation for building | day-0 | No store access needed | — |
| Storefront MCP (`<store>/api/mcp`) | Test how AI shopping agents see the catalog | launch | Read | — |
| Shopify Flow | Automations (tags, alerts, routing) | launch | Owner builds | store L2 proposes flows |
| Meta Marketing API | Ads | validate | Read insights | Create/edit/pause at media-buyer L1→L2 (pause always) |
| Google Ads, TikTok Ads | Ads | scale | Read | Same pattern |
| GA4 | Sessions, funnels, AI-referral segment | validate | Read | — |
| Klaviyo or Shopify Email | Email/SMS | launch | Read + draft | Send at lifecycle L2 |
| Helpdesk (Gorgias, Zendesk or Shopify Inbox) | Care | launch | Read + draft | Reply at care L2 |
| Image/video generation | Creatives | validate | Generate only | — |
| Google Sheets / Drive | Finance models, supplier sheets | validate | Read/write a dedicated folder | — |

## Access never granted to any agent

Payment methods, bank and payout details, Shopify staff/owner settings, app installs, domain and DNS, tax settings, ad account billing. These are R4 (`os/guardrails.yaml → owner_only_r4`).

## AI shopping channels

Shopify syndicates products to AI shopping surfaces through its catalog. Agents read the **catalog data**, not the theme, so the store agent's catalog checklist matters more than design for this channel. Availability differs by country; re-check the store's sales-channel settings in the quarterly review.
