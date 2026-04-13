---
name: skill-management
description: Curate, validate, and install skills; manage skill marketplace
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: tank
requires: []
---

# Skill Management

Ensure every KOOKY agent has the right skills, installed safely, at the right scope. Use this skill when TANK needs to curate, validate, install, or manage skills across the KOOKY agent fleet.

## Usage

**Input:**
- `action` (string) — Install, uninstall, audit, search, recommend, or list
- `skill_name` (string, optional) — For install/uninstall actions
- `target_agent` (string, optional) — Which agent gets the skill
- `requirements` (string, optional) — For search/recommend: what capability is needed
- `source` (string, optional) — Internal, marketplace, community, or custom

**Output:**
- Installation report with verification checklist (for install)
- Skill recommendation with rationale and alternatives (for recommend)
- Skills registry inventory (for list/audit)
- Gap analysis with recommended additions (for search)

## Behavior

1. **Discovery**: Monitor agent capability gaps, scout marketplace monthly, accept skill requests from Cartel members or Renato
2. **Evaluation**: Initial screening before WATSON audit — does it fill a real gap? Is there overlap? Is it well-documented? Is the source reputable?
3. **Security Audit**: Submit to WATSON for review. Classify as Tier A (internal/curated) or Tier B (community/marketplace). Never install without WATSON approval.
4. **Installation**: Install via Anthropic API, update skills registry (agent-skills.json), verify skill works, document installation
5. **Monitoring**: Track usage and effectiveness, flag unused skills for removal, monitor for conflicts, schedule periodic re-audits for Tier B

## Network

Anthropic API for skill installation (`client.beta.agents.update(agent_id, skills=[...])`).

## Error handling

- If a skill fails verification after installation, roll back and report to WATSON
- If duplicate functionality is detected, recommend which to keep based on quality and coverage
- If WATSON rejects a skill, document the reason and suggest alternatives

## Notes

- Skill format for Anthropic Managed Agents: `{"type": "custom", "name": "skill-name", "description": "...", "instructions": "..."}`
- Approval chain: Tier A (WATSON + owning C-Level), Company-wide (WATSON + KAI), Tier B (WATSON extended + JARVIS + KAI)
- NEVER install without WATSON's security audit
- NEVER install duplicate functionality — check for overlaps first
- NEVER modify a skill after WATSON approval without re-audit
- Always update the skills registry after any change
- Monitor context bloat — more skills means more instructions per agent
- Remove unused skills quarterly — skills should earn their place
- Report all installations and removals to KAI
- TANK installs skills but does not write them — coordinate with requesting agent and JARVIS for custom skills
