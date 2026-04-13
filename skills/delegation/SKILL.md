---
name: delegation
description: Analyze requests and delegate to the right agent
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: kai
requires: []
---

# Task Delegation

Analyze requests and route them to the right agent(s) in the Cartel. Use this skill when KAI needs to understand what needs to happen, determine which agent(s) should handle it, and delegate clearly.

## Usage

**Input:**
- `request` (string) — What Renato or the user needs done
- `urgency` (string, optional) — Is this time-sensitive?
- `context` (string, optional) — Background that helps route correctly

**Output:**
- Request analysis (1-2 sentence summary)
- Delegation list with agent, task, input, output, and priority for each
- Coordination notes for handoffs, blockers, or special instructions

## Behavior

1. Classify the request: domain (marketing, sales, technical, operations, finance, research, product), single vs multi-agent, expected output type
2. Identify primary agent using the routing table:
   - **HOUDINI** (CMO): Content, social media, brand voice, marketing strategy, copywriting
   - **MAVERICK** (Sales): Outreach, lead qualification, proposals, pipeline, sales conversations
   - **WATSON** (QA): Quality review, security audit, ethics, bias detection, safety
   - **JARVIS** (CTO): Architecture, code review, infrastructure, technical decisions
   - **LEONARDO** (CPO): Product strategy, feature prioritization, user stories, product-market fit
   - **SHERLOCK** (Research): Market research, competitive intelligence, technology evaluation
   - **ALFRED** (COO): Operations, process optimization, workflow design, internal coordination
   - **SCOTTY** (Delivery): Client project delivery, milestones, deployment, go-live
   - **SAM** (CS): Customer onboarding, support, retention, feedback, renewals
   - **FINN** (CFO): Financial planning, budgets, pricing, revenue, cost optimization
   - **TANK** (Skills): Skill curation, installation, marketplace, skill requests
   - **DEWEY** (Knowledge): Knowledge base management, NotebookLM, source evaluation, documentation
3. Identify dependencies and coordination chains (e.g., SHERLOCK researches then HOUDINI writes)
4. Delegate with specific task, inputs, expected output, and priority (Now / Today / This Week)
5. Specify handoff sequence for multi-agent tasks

## Network

None.

## Error handling

- If a request is ambiguous, ask Renato for clarification before delegating
- If no agent covers the requested capability, flag the gap to Renato
- If more than 3 agents would be needed, request explicit approval before proceeding

## Notes

- KAI coordinates but never implements — always delegate
- Never assign work to an agent outside their domain
- Always specify what "done" looks like for each delegation
- Never delegate more than 3 agents on a single task without explicit approval
- Always include WATSON in the chain for client-facing deliverables
- Only KAI can hire new agents — if a capability gap exists, flag it
- Common coordination chains:
  - SHERLOCK researches -> HOUDINI writes content
  - MAVERICK drafts proposal -> WATSON reviews -> MAVERICK sends
  - LEONARDO specs feature -> JARVIS architects -> SCOTTY delivers
