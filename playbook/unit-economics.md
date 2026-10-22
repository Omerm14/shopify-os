# Unit economics — the formulas every agent uses

Same math as the "Unit economics" tab of the Shopify Empire Playbook. If an agent's number disagrees with these formulas, the formulas win.

## Per order

```
net_price        = list_price × (1 − avg_discount)
payment_fees     = net_price × fee_rate + fixed_fee            # plan dependent, see below
returns_cost     = net_price × return_rate
contribution     = net_price − landed_cogs − shipping_and_packaging − payment_fees − returns_cost
profit_per_order = contribution − cpa

breakeven_cpa    = contribution                                 # max you can pay per order
breakeven_roas   = net_price / contribution
gross_margin     = (net_price − landed_cogs) / net_price
```

**Landed COGS** = supplier price + freight to the destination market + customs duty and tariffs (US: check current China tariffs; de minimis no longer applies) + import VAT if not reclaimed (EU) + local handling, per unit. VAT charged to customers is excluded from `net_price`.

## Health bands per order

| Profit per order as % of net price | Status | Agent behavior |
|------------------------------------|--------|----------------|
| ≥ 12% | Healthy | Media-buyer may scale within caps |
| 0–12% | Thin | No scaling; store/ops/finance look for margin |
| < 0 | Losing | Auto-pause scaling; orchestrator opens a margin experiment |

## Shopify plan fees (2026, USD)

| Plan | Monthly | Annual (per month) | Shopify Payments online | Extra fee with outside gateway |
|------|---------|--------------------|------------------------|-------------------------------|
| Basic | 39 | 29 | 2.9% + 30¢ | 2% |
| Grow | 105 | 79 | 2.7% + 30¢ | 1% |
| Advanced | 399 | 299 | 2.5% + 30¢ | 0.6% |
| Plus | from ~2,300 | contract | negotiated | 0.2% |

If the store runs on an outside gateway, `fee_rate = gateway_rate + extra_fee`. Finance re-checks the cheapest plan monthly (stage task Y6).

## Growth model assumptions (used in forecasts)

- New customers per month = ad_spend / cac_new
- Repeat orders per month = Σ cohort_size × monthly_repeat_rate × 0.88^(age in months − 1)
- Monthly profit = revenue × margin_before_ads − ad_spend − fixed_costs
- Cash needed = −min(cumulative profit). Finance must keep cash ≥ 1.5 × cash needed before approving a growth plan.
