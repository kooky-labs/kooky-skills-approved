---
name: delivery-management
description: Track client deliverables, manage timelines, coordinate agent handoffs
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: scotty
requires: []
---

# Delivery Management

Get client work delivered on time, on spec, and on quality. Use this skill when SCOTTY needs to track client project delivery, manage milestones, coordinate handoffs between agents, or ensure client work ships on time.

## Usage

**Input:**
- `client_project` (string) — Which client or project
- `action` (string) — Status update, milestone tracking, handoff coordination, go-live planning, blocker resolution
- `current_state` (string) — Where we are in the delivery process
- `timeline` (string) — Committed deadlines
- `team` (string) — Which agents are involved

**Output:**
- Project tracker with milestones, owners, due dates, status, and notes
- Blockers with impact, owner, and ETA
- Risks with likelihood, impact, and mitigation
- Next actions with owners and deadlines
- Client communication summary and schedule

## Behavior

1. Manage four delivery phases:
   - **Kickoff**: Receive handoff from MAVERICK, confirm scope/deliverables/timeline, create project tracker, assign agents, set communication cadence
   - **Execution**: Track daily progress against milestones, coordinate between agents, resolve dependency blocks immediately, run quality checks with WATSON, report to ALFRED and KAI
   - **Review & QA**: Submit to WATSON for quality review, iterate on feedback, manage client review rounds, final QA before go-live
   - **Go-Live & Handoff**: Deploy/deliver, client walkthrough, handoff to SAM for ongoing success, post-delivery retrospective
2. Track and communicate status using the project tracker format
3. Surface blockers immediately — never hide delays
4. Manage handoff protocols between agents (Sales to Delivery, Delivery to Customer Success)

## Network

None.

## Error handling

- If a milestone is at risk, surface immediately to ALFRED and KAI — do not wait for the next scheduled update
- If scope changes are requested, update timeline and confirm with KAI before accepting
- Every blocker must have an owner and an ETA — no orphaned blockers

## Notes

- Handoff from MAVERICK: receive client details, agreed scope, timeline, requirements, contract/pricing
- Handoff to SAM: provide what was delivered, known issues, client preferences, renewal timeline, expansion opportunities
- Every deliverable gets WATSON review before client sees it
- Client should never be surprised — proactive communication always
- Never promise a timeline without checking with executing agents
- Never take on scope changes without updating timeline and confirming with KAI
- Report to ALFRED (COO) for operational coordination
- Escalate to KAI for scope disputes or client escalations
- Status reporting: daily (internal), weekly (client)
