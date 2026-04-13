---
name: researching-skills
description: Discovers and evaluates skills from community registries, marketplaces, and existing installations for potential agent adoption. Use when searching for existing skills to fill a capability gap before building from scratch.
---

# Skill Research

Find existing skills from external sources rather than building from scratch. Covers registry search, compatibility assessment, security flagging, and adoption recommendations.

## When to Use

- An agent needs a new capability and an existing skill might already cover it
- Scouting registries and marketplaces for useful skills
- Evaluating whether a community skill is safe and compatible

## Discovery Sources

- **skills.sh** -- Community registry with install counts and ratings.
- **GitHub search** -- Search for SKILL.md files and agent skill repositories.
- **Claude Code global skills** (`~/.claude/skills/`) -- Battle-tested skills already in production use.

## Process

1. Scope the search: what capability is needed, which agent(s) would use it.
2. Search all sources by keyword and capability match.
3. Evaluate each candidate:
   - Does it match the needed capability?
   - Is it compatible with the target platform (no local-only dependencies)?
   - Trust level: Official > Curated (>10K installs) > Community (>1K) > Experimental (<1K).
   - Code quality and documentation.
   - Security red flags: eval, shell exec, network calls to unknown domains.
4. Rank candidates by fit. Flag any needing security review.
5. Recommend: adopt as-is, adapt for context, or skip -- with reasoning for each.

## Output Format

- Skills found: name, source, install count, description
- Relevance and compatibility assessment per candidate
- Security flags for review
- Recommendation per skill: adopt / adapt / skip with reasoning

## Constraints

- Never install directly -- all skills go through security vetting first.
- Every recommendation must include reasoning, not just "looks good."
- Include the skill's source URL so security can audit it.
- If no skills match, report "no matches" with alternative search term suggestions.
