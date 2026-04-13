---
name: designing-architecture
description: Designs system architecture, evaluates technical approaches, and produces Architecture Decision Records (ADRs). Use when making a technical decision that affects system structure, choosing between build vs. buy, or documenting an architectural choice.
---

# Technical Architecture

Make sound technical decisions that balance simplicity, scalability, and speed. Covers system design, technology evaluation, and architectural documentation.

## When to Use

- Designing or changing system architecture
- Evaluating technical approaches or making build-vs-buy decisions
- Documenting an architectural decision as an ADR

## Process

1. Define the problem: what needs to be built or changed, hard constraints, current state.
2. Identify at least 3 options (include "do nothing" when appropriate).
3. Evaluate each option on six dimensions:
   - **Complexity**: How much does this add?
   - **Cost**: Build and maintain cost.
   - **Speed**: How quickly can we ship?
   - **Scalability**: Does it grow with usage?
   - **Reversibility**: How hard to change course later?
   - **Dependencies**: New dependencies introduced.
4. Include build-vs-buy analysis and managed-vs-self-hosted considerations where relevant.
5. Recommend the simplest solution that meets requirements.
6. Document as an ADR: status, context, decision, options considered (with rejection reasoning), consequences.

## Output Format

- Architecture Decision Record (ADR) with status, context, decision, options, consequences
- System design: component diagram, data flow, API contracts, error handling, monitoring
- Clear recommendation with reasoning

## Constraints

- Every component must justify its existence -- simplicity first.
- Prefer managed services over self-hosted when cost is comparable.
- No premature optimization -- solve today's problem, design for tomorrow's.
- Never introduce complexity without documenting why.
- Never recommend technology just because it is popular.
- All technical decisions require an ADR before implementation.
