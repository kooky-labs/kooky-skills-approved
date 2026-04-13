---
name: automating-operations
description: Maps operational workflows, classifies steps by automation potential, and designs optimized target-state processes. Use when a process is manual, slow, or error-prone and needs automation analysis.
---

# Operations Automation

Design operational workflows that run smoothly with minimal manual intervention. Covers current-state mapping, automation classification, target-state design, and implementation planning.

## When to Use

- A manual or slow process needs automation analysis
- Designing a new workflow from scratch
- Optimizing an existing workflow with bottlenecks or handoff failures

## Process

1. **Map current state**: Document every step, identify manual steps, handoffs, decision points, delays, and bottlenecks.
2. **Classify each step**:
   - Automate fully: No human judgment needed, deterministic outcome.
   - Automate with oversight: Agent handles it, human reviews output.
   - Human-in-the-loop: Requires human judgment or approval.
   - Cannot automate: Physical action or external dependency.
3. **Design target state**: Optimized workflow with triggers, handoffs, completion criteria, and error handling for each step.
4. **Create implementation plan**: What to build, migration path, rollback plan, ownership assignment.

## Output Format

- Current state map with steps, handoffs, and bottlenecks
- Automation classification per step
- Target state workflow diagram
- Implementation plan with migration and rollback

## Workflow Documentation Template

Each workflow should specify: name, owner, trigger, frequency, SLA, and steps with owners and step types (automated / oversight / human / manual).

## Constraints

- Never automate something you do not understand manually first.
- Never design a workflow without mapping current state.
- Every step must have defined error handling.
- Always include a human escalation path for edge cases.
- Prefer idempotent operations -- running a step twice should not cause harm.
- Every workflow must have a single owner.
