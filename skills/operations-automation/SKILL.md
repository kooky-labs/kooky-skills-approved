---
name: operations-automation
description: Design operational workflows and identify automation opportunities
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: alfred
requires: []
---

# Operations Automation

Make KOOKY's operations run smoothly with minimal manual intervention. Use this skill when ALFRED needs to design operational workflows, identify automation opportunities, or optimize internal processes.

## Usage

**Input:**
- `process` (string) — What operational workflow needs attention
- `current_state` (string) — How this works today (or "doesn't exist yet")
- `pain_points` (string) — What is broken, slow, or manual
- `stakeholders` (string) — Who is involved (agents and/or humans)
- `volume` (string) — How often this process runs (daily, weekly, per-client, ad-hoc)
- `tools_available` (string, optional) — Available systems (n8n, Supabase, Anthropic Managed Agents, NotebookLM)

**Output:**
- Current state map with steps, handoffs, bottlenecks
- Automation classification per step (fully automated / automated with oversight / human-in-the-loop / cannot automate)
- Target state workflow with triggers, handoffs, completion criteria, error handling
- Implementation plan with migration path and rollback plan

## Behavior

1. Map current state: document every step, identify manual steps/handoffs/decision points, note delays/errors/bottlenecks
2. Classify each step for automation potential:
   - **Automate fully**: No human judgment needed, deterministic outcome
   - **Automate with oversight**: Agent handles it, human reviews output
   - **Human-in-the-loop**: Requires human judgment or approval
   - **Cannot automate**: Physical action or external dependency
3. Design target state: optimized workflow with triggers, handoffs, completion criteria, error handling
4. Create implementation plan: what to build, migration path, rollback plan, ownership assignment
5. Document using workflow format: name, owner, trigger, frequency, SLA, steps with owners and types

## Network

None. (Workflows may reference n8n, Supabase, or Anthropic APIs but this skill itself makes no network calls.)

## Error handling

- Every step in a designed workflow must have defined error handling
- Always include a human escalation path for edge cases
- Prefer idempotent operations — running a step twice should not cause harm

## Notes

- Common KOOKY workflows:
  - Client Onboarding: SAM -> SCOTTY -> JARVIS -> WATSON -> SAM
  - Content Publishing: SHERLOCK -> HOUDINI -> WATSON -> HOUDINI
  - Lead Processing: MAVERICK -> KAI -> MAVERICK -> SCOTTY -> SAM
  - Skill Installation: TANK -> WATSON -> KAI -> TANK -> WATSON
- Automation tools: n8n (visual orchestration), Anthropic Managed Agents (cognitive tasks), Supabase (data/triggers), Cron (time-based)
- Every workflow must have a single owner
- Never automate something you do not understand manually
- Never design a workflow without mapping current state first
- Coordinate with JARVIS for technical implementation, SCOTTY for delivery workflows
- Report operational status to KAI
