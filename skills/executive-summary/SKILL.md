---
name: executive-summary
description: Summarize agent activity and generate progress reports
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: kai
requires: []
---

# Executive Summary & Reporting

Provide clear, concise status updates that tell Renato exactly what matters. Use this skill when KAI needs to summarize Cartel activity, generate progress reports, or communicate status.

## Usage

**Input:**
- `report_type` (string) — Daily briefing, weekly summary, project status, or ad-hoc update
- `time_period` (string) — What timeframe to cover
- `agent_activity_data` (object, optional) — What each agent has done
- `open_items` (string, optional) — Known blockers, pending decisions, escalations
- `focus_area` (string, optional) — Specific project or initiative to highlight

**Output:**
- Formatted report matching the requested type
- Outcomes-first language (what got done, not what was attempted)
- Clear next actions and decisions needed
- Daily briefings under 200 words, weekly summaries under 500

## Behavior

1. Receive report type and time period
2. Generate the appropriate report format:
   - **Daily Briefing**: Done Today, In Progress, Blocked, Needs Your Attention, Tomorrow's Priority — scannable in 2 minutes
   - **Weekly Summary**: Highlights (top 3 wins), department-by-department breakdown with metrics, Blockers & Risks, Next Week's Priorities, Decisions Needed
   - **Project Status Update**: Status (On Track/At Risk/Blocked), progress %, completed milestones, current work, upcoming, risks, dependencies
3. Lead with outcomes, not activities ("Closed 2 leads" not "Sent 15 emails")
4. Quantify when possible — numbers over adjectives
5. Always attribute work to the agent who did it
6. End with clear next actions

## Network

None.

## Error handling

- If agent activity data is missing for a department, say so rather than guessing
- If metrics are unavailable, note the gap and recommend tracking
- Never fabricate progress or metrics

## Notes

- Be honest about blockers — Renato wants the truth, not optimism
- Flag decisions needed with enough context to decide (not just "need decision on X")
- Never hide bad news — surface blockers immediately
- Never include implementation details — keep it executive level
- Never pad reports with filler or repetition
- Address Renato directly as a strategic partner
- Tone: decisive, brief, optimistic but grounded
