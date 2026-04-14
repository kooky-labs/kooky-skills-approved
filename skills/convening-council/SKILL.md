---
name: convening-council
description: Convene a multi-agent council for high-stakes decisions. Uses callable_agents to gather parallel perspectives, runs an adversarial counter-argument pass, synthesizes a decision, and writes one row to the `decisions` table. Use for architectural, security, strategic, or multi-domain calls — not for simple or time-sensitive tasks.
---

# Convening a Council

For high-stakes decisions where a single agent's answer is not enough. This skill is a protocol, not infrastructure. It uses existing tools (`callable_agents`, REST `plan.log_action`, REST `decisions.create`) to produce one auditable row in the `decisions` table.

## When to Use

Use council for questions with real downside if wrong:

| Category | Trigger examples |
|----------|------------------|
| `architectural` | Two or more valid technical approaches; hard to reverse |
| `security` | Installing a non-verified skill; exposing a new endpoint; auth change |
| `strategic` | Pricing change, positioning shift, hire/fire, partnership commitment |
| `multi_domain` | Requires cross-functional judgment (marketing + sales + technical) |

## When NOT to Use

- Simple tasks with one correct answer
- Time-sensitive operations (council takes longer)
- Implementation work (one agent should build)
- Questions where the user's preference is the answer — escalate to approval, not council

## Protocol

### 1. Frame the question

Write it in one sentence. No leading language. Include context the agents need but not your preferred answer.

Bad: *"Shouldn't we just use Stripe since it's obviously better?"*
Good: *"Select payment processor for KOOKY OS client billing. Requirements: subscriptions, metered usage, pause/resume, LATAM card support. Budget for platform fees < 3.5%."*

### 2. Pick 2-4 agents

Include domain owners, plus at least one outsider perspective. Using fewer than 2 defeats the purpose. Using more than 4 produces mush.

Common compositions:

| Question type | Panel |
|---------------|-------|
| Architectural | JARVIS + WATSON + one domain owner |
| Security | WATSON + JARVIS + TANK |
| Strategic | KAI + HOUDINI + MAVERICK |
| Skill install | WATSON + TANK + SHERLOCK |
| Pricing / GTM | MAVERICK + HOUDINI + FINN |

### 3. Parallel proposal pass

Use `callable_agents` to ask each panelist the same question in parallel. Give each:
- The question verbatim
- The same context
- An instruction: *"Give your recommendation and the reasoning behind it. Be specific. Do not hedge."*

Log each response to `plan_actions` with `category='council_response'` as it arrives.

### 4. Adversarial counter pass

After responses come in, pick the strongest recommendation. Route it to a designated red-team agent (default: WATSON; for WATSON's own recommendation use JARVIS) with this instruction:

> *"Find the strongest counter-argument to this recommendation. Not a hedge — a specific failure mode, missed assumption, or scenario where this is clearly wrong. If you cannot find one, say so."*

This is where real signal appears. Consensus without dissent is groupthink.

### 5. Rebuttal (optional, one round only)

If the counter-argument is substantive, give the original agent one chance to rebut or revise. One round, no loops.

### 6. Synthesize and decide

Write the `decisions` row. Required fields:

| Field | Content |
|-------|---------|
| `title` | Short name for the decision |
| `category` | From the table above |
| `decision` | The chosen path, one paragraph |
| `rationale` | Why this over alternatives |
| `alternatives` | JSON array: each option considered + why rejected |
| `strongest_objection` | The adversarial counter-argument, verbatim |
| `evidence` | JSON array of `{session_id, message_range, note}` pointers |
| `decided_by` | `council:<comma-separated agent codes>` |
| `protocol` | `council` or `adversarial` |
| `routes_to_approval` | `true` if human sign-off needed |

### 7. Route

- Low-impact + high-agreement → implement directly
- High-impact OR unresolved dissent → set `routes_to_approval=true`; appears in Approvals sidebar for user review

## Constraints

- One council row per decision. Do not open a second council on the same question without new information.
- `strongest_objection` must be populated. An empty objection means the counter-pass was skipped — not acceptable.
- Never invite more than 4 agents. Group output quality degrades fast.
- Council does not replace the user. For reversible decisions inside an agent's domain, the agent decides. For high-stakes + strategic, escalate.
- Do not retry a council. If the first pass was bad, diagnose why; don't rerun hoping for a different answer.

## Anti-patterns

- **Consensus theater.** Asking agents to "vote" or rate confidence produces noise. Ask for reasoning, not scores.
- **Stacking the panel.** Inviting only agents likely to agree defeats the purpose. Include at least one outsider.
- **Running council for user preferences.** "What color should the button be?" is not a council question. Ask the user.
- **Skipping the adversarial pass.** Proposal-only councils are just averaged opinions.
- **Using council to avoid accountability.** One agent should still own the decision. Council informs; it does not dilute responsibility.

## Output

One row in `decisions`. Full deliberation transcript accessible via `evidence` pointers (session_id + message_range) which deep-link into the Anthropic session view. No separate council storage.
