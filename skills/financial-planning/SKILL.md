---
name: financial-planning
description: Budget analysis, revenue projections, cost optimization, pricing strategy
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: finn
requires: []
---

# Financial Planning

Provide clear financial analysis that enables smart business decisions. Use this skill when FINN needs to analyze budgets, create revenue projections, optimize costs, or develop pricing strategy.

## Usage

**Input:**
- `analysis_type` (string) — Budget review, revenue projection, cost optimization, pricing analysis, financial report
- `time_period` (string) — Monthly, quarterly, annual
- `available_data` (object, optional) — Revenue figures, costs, subscriber counts, usage metrics
- `decision_context` (string) — What financial decision needs to be made
- `constraints` (string, optional) — Cash runway, funding status, growth targets

**Output:**
- Structured financial analysis matching the requested type
- Numbers with sources (not rounded estimates without basis)
- Conservative bias with optimistic assumptions flagged
- Trade-off analysis for every recommendation
- Sensitivity analysis: what changes if key assumptions are wrong
- Visual summaries (tables) for comparison

## Behavior

1. Receive analysis type and available data
2. Apply the appropriate framework:
   - **Budget Analysis**: Revenue by source, costs by category, net/burn rate/runway, observations, recommendations with expected savings
   - **Revenue Projections**: Conservative/base/optimistic scenarios, stated assumptions, key risks and upside
   - **Cost Optimization**: Top 5 cost items, necessity/alternatives/optimization for each, ROI for proposed investments
   - **Pricing Strategy**: Competitive landscape, unit economics (CAC, LTV, LTV/CAC), pricing tier models, psychological pricing, "what if we're wrong" scenario
3. Always include ranges, not single-point estimates for projections
4. State assumptions explicitly and separately from conclusions
5. Include impact analysis for cost cuts (not just savings)

## Network

None.

## Error handling

- If data is insufficient for reliable analysis, flag what additional data is needed
- Never present projections as certainty — always use ranges
- If key assumptions cannot be validated, note the uncertainty and its impact on conclusions

## Notes

- KOOKY financial context: pricing tiers $500/mo (starter) to $8,400/mo (full service), pre-revenue/early revenue stage, goal is first $10K MRR
- Infrastructure costs: Anthropic API (per-agent, per-conversation), Vercel, Supabase
- Revenue model: monthly subscription + setup fees
- Lead with numbers, not opinions — conservative by default
- Every recommendation: "this costs X, enables Y, risks Z"
- Never recommend cost cuts without assessing quality/security impact
- Never hide unfavorable numbers — Renato needs the truth
- Never make pricing recommendations without competitive context
- Escalate legal/tax questions — FINN is not a lawyer or accountant
- Report financial summaries to KAI regularly
