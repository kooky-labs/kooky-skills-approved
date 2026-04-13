---
name: product-design
description: Define features, prioritize backlog, write user stories, design user flows
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: leonardo
requires: []
---

# Product Design

Make product decisions that maximize user value with minimal complexity. Use this skill when LEONARDO needs to define features, prioritize the backlog, write user stories, or design user flows.

## Usage

**Input:**
- `request_type` (string) — Feature definition, backlog prioritization, user story, user flow design
- `problem_statement` (string) — What user problem are we solving (required)
- `user_segment` (string) — Which ICP segment (displaced professional, solopreneur, small business owner)
- `existing_context` (string, optional) — What we already have, current user experience
- `constraints` (string, optional) — Technical limitations, timeline, budget, dependencies

**Output:**
- Clear problem statement (never skipped)
- Proposed solution with scope defined (must-have, should-have, won't-have)
- User stories with acceptance criteria
- Prioritization rationale (ICE framework)
- Dependencies and risks
- Size estimate (small/medium/large)

## Behavior

1. Validate the problem: What is the pain point? Evidence it is real? How big? Cost of inaction?
2. Explore solutions: generate 2-3 approaches, evaluate smallest shippable version of each
3. Define scope with explicit exclusions: Must have / Should have / Won't have (this version)
4. Set success criteria: what metric moves, by how much, measurement timeline
5. Write user stories in format: "As a [user], I want to [action], So that [outcome]" with acceptance criteria, out-of-scope items, dependencies, and size
6. For backlog prioritization, apply ICE framework: Impact (1-10) x Confidence (1-10) x Ease (1-10) / 10
7. For user flows: happy path first, then decision points, error states, entry/exit points, data requirements

## Network

None.

## Error handling

- If no problem statement is provided, request one before proceeding
- If evidence for the problem is missing, flag it and recommend validation steps
- If scope creep is detected, explicitly name what is being excluded and why

## Notes

- KOOKY product context: Voice AI interview turns into a complete online business
- Target user: non-technical professionals building AI-powered businesses
- Pricing tiers: $500/mo (starter) to $8,400/mo (full service)
- Key insight: users want outcomes, not tools; they want a business, not an AI platform
- Never build a feature without a validated problem
- Never define scope without naming what is excluded
- Never write acceptance criteria that cannot be tested
- Never prioritize based on who is asking loudest — use the framework
- Hand off to JARVIS for technical feasibility, HOUDINI for GTM, SHERLOCK for market research
- Size estimates only: small / medium / large — never time estimates
