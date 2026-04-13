---
name: designing-products
description: Defines features, prioritizes backlogs, writes user stories, and designs user flows using structured frameworks. Use when making product decisions -- scoping a feature, prioritizing work, or validating a problem.
---

# Product Design

Make product decisions that maximize user value with minimal complexity. Covers feature definition, backlog prioritization, user stories, and user flow design.

## When to Use

- Defining a new feature or scoping a product change
- Prioritizing a backlog of work
- Writing user stories with acceptance criteria
- Designing user flows (happy path, errors, edge cases)

## Process

1. **Validate the problem**: What is the pain point? What evidence exists? How big is it? What is the cost of inaction?
2. **Explore solutions**: Generate 2-3 approaches. Evaluate the smallest shippable version of each.
3. **Define scope**: Must have / Should have / Won't have (this version). Always name exclusions explicitly.
4. **Set success criteria**: What metric moves, by how much, over what timeline.
5. **Write user stories**: "As a [user], I want to [action], so that [outcome]" with acceptance criteria, out-of-scope items, dependencies, and size (small / medium / large).
6. **Prioritize** (if applicable): ICE framework -- Impact (1-10) x Confidence (1-10) x Ease (1-10) / 10.
7. **Design user flows** (if applicable): Happy path first, then decision points, error states, entry/exit points.

## Output Format

- Problem statement (never skip this)
- Proposed solution with explicit scope (must-have, should-have, won't-have)
- User stories with acceptance criteria
- Prioritization rationale if multiple items
- Dependencies and risks
- Size estimate: small / medium / large (never time estimates)

## Constraints

- Never build a feature without a validated problem.
- Never define scope without naming what is excluded.
- Never write acceptance criteria that cannot be tested.
- Never prioritize based on who is asking loudest -- use the framework.
