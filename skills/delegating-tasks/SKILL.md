---
name: delegating-tasks
description: Analyzes incoming requests and routes them to the appropriate agent(s) with clear task definitions. Use when a request arrives and needs to be broken down, routed, or coordinated across multiple agents.
---

# Task Delegation

Analyze requests and route them to the right agent(s). This skill handles request classification, agent selection, dependency ordering, and handoff coordination.

## When to Use

- A new request arrives that needs routing to one or more agents
- A multi-step task requires coordination across agents
- Determining which agent owns a capability

## Agent Routing Table

| Agent | Domain |
|-------|--------|
| HOUDINI (CMO) | Content, social media, brand, marketing strategy |
| MAVERICK (Sales) | Outreach, leads, proposals, pipeline |
| WATSON (QA) | Quality review, security audit, bias detection |
| JARVIS (CTO) | Architecture, code, infrastructure, technical decisions |
| LEONARDO (CPO) | Product strategy, features, user stories |
| SHERLOCK (Research) | Market research, competitive intel, tech evaluation |
| ALFRED (COO) | Operations, process optimization, workflows |
| SCOTTY (Delivery) | Client delivery, milestones, deployment |
| SAM (CS) | Onboarding, support, retention, feedback |
| FINN (CFO) | Financial planning, budgets, pricing |
| TANK (Skills) | Skill curation, installation, marketplace |
| DEWEY (Knowledge) | Knowledge bases, documentation, source evaluation |

## Process

1. Classify the request: domain, single vs. multi-agent, expected output type.
2. Select the primary agent from the routing table.
3. Identify dependencies and coordination chains.
4. Delegate with: specific task, inputs, expected output, priority (Now / Today / This Week).
5. For multi-agent tasks, specify the handoff sequence.

## Common Coordination Chains

- SHERLOCK researches -> HOUDINI writes content
- MAVERICK drafts proposal -> WATSON reviews -> MAVERICK sends
- LEONARDO specs feature -> JARVIS architects -> SCOTTY delivers

## Constraints

- Always delegate -- never implement directly.
- Never assign work outside an agent's domain.
- Always specify what "done" looks like for each delegation.
- Limit to 3 agents per task without explicit approval.
- Always include WATSON in the chain for client-facing deliverables.
