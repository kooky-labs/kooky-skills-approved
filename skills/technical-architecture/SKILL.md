---
name: technical-architecture
description: Design system architecture and evaluate technical approaches
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: jarvis
requires: []
---

# Technical Architecture

Make sound technical decisions that balance simplicity, scalability, and speed. Use this skill when JARVIS needs to design system architecture, evaluate technical approaches, or make build-vs-buy decisions.

## Usage

**Input:**
- `problem_statement` (string) — What technical problem needs solving
- `requirements` (string) — Functional and non-functional requirements
- `constraints` (string) — Budget, timeline, team capabilities, existing stack
- `context` (string) — What exists today, what we are integrating with
- `scale_expectations` (string) — Current and projected load/usage

**Output:**
- Architecture Decision Record (ADR) with status, context, decision, options considered, and consequences
- System design with component diagrams, data flow, API contracts, error handling, monitoring approach
- Clear recommendation with reasoning

## Behavior

1. Define the problem: what needs to be built/changed, hard constraints, current state
2. Identify at least 3 options (including "do nothing" when appropriate)
3. For each option, evaluate trade-offs:
   - **Complexity**: How much complexity does this add?
   - **Cost**: Build and maintain cost
   - **Speed**: How quickly can we ship?
   - **Scalability**: Does it scale with growth?
   - **Reversibility**: How hard to change course later?
   - **Dependencies**: New dependencies introduced
4. Include build vs. buy analysis, managed vs. self-hosted considerations
5. Recommend the simplest solution that meets requirements
6. Document as an ADR with options considered and rejected

## Network

None.

## Error handling

- If requirements are ambiguous, list assumptions and flag for confirmation
- If insufficient information to evaluate an option, note the gap rather than guessing
- If no option clearly dominates, present trade-offs and recommend based on current priorities

## Notes

- KOOKY stack: Anthropic Managed Agents (cloud-only, ADR-008), anthropic Python SDK (0.92.0+), Next.js/Vercel (Phase 3), Supabase, NotebookLM + QMD, n8n
- Cloud-only architecture — no local infrastructure recommendations (ADR-008)
- Simplicity first — every component must justify its existence
- No premature optimization — solve today's problem, design for tomorrow's
- Prefer managed services over self-hosted when cost is comparable
- Defense in depth — security at every layer
- All technical decisions require an ADR before implementation
- Never introduce complexity without documenting why
- Never recommend technology just because it is popular
