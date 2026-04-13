---
name: lead-qualification
description: Evaluate and score incoming leads against ICP criteria
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: maverick
requires: []
---

# Lead Qualification

Qualify leads quickly and accurately so sales effort goes to the highest-probability prospects. Use this skill when MAVERICK needs to evaluate incoming leads, score them against ICP criteria, and recommend next actions.

## Usage

**Input:**
- `lead_source` (string) — Where the lead came from (inbound form, LinkedIn engagement, referral, content download, event)
- `available_data` (object) — Name, title, company, industry, company size, any messages or interactions
- `engagement_history` (string, optional) — What they have engaged with (posts liked, content downloaded, pages visited)
- `stated_need` (string, optional) — What they said they need, if anything

**Output:**
- Structured qualification report with weighted score
- Lead tier classification (Hot/Warm/Cool/Cold)
- Recommended primary and secondary actions
- Key observations and information gaps
- Disqualification flags if any

## Behavior

1. Receive lead data and engagement history
2. Score on five dimensions (weighted):
   - **Profile Fit** (30%): Match to ICP segments (5 = displaced professional actively seeking, 1 = student/hobbyist)
   - **Intent Signal** (25%): Explicit interest level (5 = asked about KOOKY, 1 = no signal)
   - **Budget Likelihood** (20%): Ability to pay $500-$8,400/mo (5 = indicated budget, 1 = no indicators)
   - **Timing** (15%): Urgency of need (5 = active transition now, 1 = no timing signal)
   - **Engagement Quality** (10%): Interaction depth (5 = thoughtful replies, 1 = no response)
3. Calculate weighted score and assign tier:
   - **Hot** (4.0-5.0): Immediate personal outreach within 4 hours
   - **Warm** (3.0-3.9): Personalized outreach within 24 hours, add to nurture
   - **Cool** (2.0-2.9): Content nurture, monitor for intent signals
   - **Cold** (1.0-1.9): Archive, no active pursuit
4. Generate specific next-action recommendations
5. Flag competitor mentions for routing to SHERLOCK

## Network

None.

## Error handling

- If data is insufficient for a dimension, mark as "insufficient data" rather than guessing
- Never inflate scores to make a lead look better than it is
- If new information emerges after scoring, trigger reassessment

## Notes

- No lead should sit unqualified for more than 24 hours
- Never disqualify based on assumptions — note information gaps instead
- Always recommend a specific next action, even for cold leads
- Flag any lead that mentions competitors — route intel to SHERLOCK
- ICP segments: displaced professionals, solopreneurs, small business owners
- Budget range: $500-$8,400/month for AI-powered business infrastructure
