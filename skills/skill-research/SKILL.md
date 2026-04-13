---
name: skill-research
description: Research and discover skills from community registries and Claude Code for agent adoption
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: sherlock
requires: []
---

# Skill Research

Discover, evaluate, and recommend skills from external sources for adoption by KOOKY OS agents. Use this skill when SHERLOCK needs to find existing skills that can enhance agent capabilities instead of building from scratch.

## Skill Discovery Sources

### 1. Online Registries
- **skills.sh** — Community registry with 1000s of skills, install counts and ratings
- **awesome-openclaw-skills** (github.com/VoltAgent/awesome-openclaw-skills) — Curated list of vetted skills
- **GitHub search** — Search for SKILL.md files, Claude Code skills, agent skills

### 2. Claude Code Global Skills
- Located at `~/.claude/skills/` on development machines
- Battle-tested skills already in use (brainstorming, copywriting, frontend-design, etc.)
- Many map directly to agent needs

## Usage

**Input:**
- `search_query` (string) — Capability or domain to search for (e.g., "SEO audit", "email marketing", "image generation")
- `target_agent` (string, optional) — Which agent this skill would be for (e.g., "houdini", "maverick")
- `depth` (string) — Quick scan (check top results) or deep dive (thorough evaluation)

**Output:**
- Structured report with:
  - Skills found (name, source, install count if available, description)
  - Relevance assessment per agent (which agents would benefit)
  - Compatibility assessment (will it work with Managed Agents?)
  - Security flags (any concerns for WATSON to investigate)
  - Recommendation: adopt, adapt, or skip — with reasoning

## Behavior

1. **Scope the search:** Understand what capability is needed and which agent(s) would use it
2. **Search all sources:**
   - Query `skills.sh` registry by keyword
   - Check `awesome-openclaw-skills` curated list
   - Search GitHub for SKILL.md files matching the capability
   - Scan Claude Code global skills for relevant matches
3. **Evaluate each candidate:**
   - Does it match the needed capability?
   - Is it compatible with Managed Agents (no local-only dependencies)?
   - What's the trust level? (Official kooky-labs, curated, community, experimental)
   - Install count / community adoption signal
   - Code quality (if source available)
   - Any security red flags? (eval, shell exec, network calls to unknown domains)
4. **Produce recommendation:**
   - Rank candidates by fit
   - Flag any for WATSON security review
   - Suggest which agent(s) should receive each skill
   - Note if the skill needs adaptation for KOOKY OS context
5. **Hand off:**
   - Pass recommended skills to WATSON for security vetting
   - After WATSON approves, TANK converts to SKILL.md format and pushes to `kooky-skills-approved`

## Network

- `skills.sh` — skill registry search
- `github.com` — repo search, skill file retrieval
- Public internet — for evaluating skill documentation and source code

## Error handling

- If no skills found for a query, report "no matches" with suggestions for alternative search terms
- If a skill looks promising but has security concerns, flag it for WATSON rather than dismissing
- If a skill requires dependencies not available on Managed Agents, note it as "requires adaptation"

## Notes

- **Skills-First Principle (ADR-004):** Always search for existing skills before creating new ones
- **Trust levels:** Official (kooky-labs) > Curated (>10K installs) > Community (>1K) > Experimental (<1K)
- **Never install directly** — all skills go through WATSON security vetting first
- **Claude Code skills** are high-value targets — they're already proven in production
- Report findings to the requesting agent (usually KAI or TANK), not directly to users
- Include the skill's GitHub URL or registry link so WATSON can audit the source
- Every recommendation must have a reasoning — no "just because it looks good"
