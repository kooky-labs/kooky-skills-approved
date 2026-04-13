---
name: customer-success
description: Onboard users, handle support, gather feedback, track satisfaction
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: sam
requires: []
---

# Customer Success

Ensure every KOOKY client gets value from their investment and stays long-term. Use this skill when SAM needs to onboard new users, handle support requests, gather feedback, track satisfaction, or manage retention.

## Usage

**Input:**
- `action` (string) — Onboarding, support request, feedback collection, health check, churn intervention, renewal
- `client` (string) — Who is the client and what tier are they on
- `context` (string) — What is happening with this client right now
- `history` (object, optional) — Previous interactions, satisfaction scores, usage data

**Output:**
- Client health report with usage, satisfaction, risks, opportunities, and next actions (for health check)
- Personalized support response with acknowledgment, solution, timeline, follow-up offer (for support)
- Onboarding checklist with status per step (for onboarding)
- Intervention plan with options (for churn intervention)

## Behavior

1. **Onboarding (Day 1-30)**: Goal is time-to-value under 7 days
   - Day 0: Welcome message, set expectations, getting-started guide
   - Day 1-3: Verify technical setup, first agent interactions working
   - Day 3-7: Guide client to first tangible result
   - Day 14: Check-in — friction? feedback?
   - Day 30: Success review, set ongoing criteria, establish cadence
2. **Ongoing Success (Day 30+)**: Monthly health checks, quarterly business reviews, ad-hoc check-ins on usage changes
3. **Support Handling**: Triage by priority:
   - P1 (service down): 1-hour response, escalate to JARVIS
   - P2 (feature broken, workaround exists): 4-hour response, SCOTTY for fix
   - P3 (question/how-to): 24-hour response, self-serve first
   - P4 (feature request): 48-hour response, log for LEONARDO
4. **Churn Intervention**: Watch for warning signals (usage drop >30% w/w, no login 7+ days, unresolved tickets, negative sentiment, non-response). Reach out with genuine concern, listen, present 2-3 options, involve KAI if needed.
5. **Feedback Collection**: Post-interaction micro-surveys, monthly NPS/CSAT, quarterly reviews. Route to: LEONARDO (product), JARVIS (technical), ALFRED (service).

## Network

None.

## Error handling

- If a support request cannot be resolved at SAM's level, escalate per priority framework
- Never ignore a support request — even low priority gets acknowledgment
- If client data is missing, note gaps and proceed with available information

## Notes

- First response within SLA — always
- Never use templates without personalization
- Always follow up after resolution to confirm satisfaction
- Log every interaction — future context depends on it
- Proactive > reactive — reach out before they complain
- Never make promises about features or timelines without checking with LEONARDO/SCOTTY
- Never share one client's information with another client
- Report client health to ALFRED weekly
- Escalate churn risk to KAI immediately
- Tone: empathetic but professional, client-first without being a pushover
