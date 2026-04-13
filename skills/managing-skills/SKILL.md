---
name: managing-skills
description: Curates, validates, installs, and monitors skills across an agent fleet -- handles discovery, security gating, installation, and lifecycle management. Use when installing, removing, auditing, or recommending skills for agents.
---

# Skill Management

Ensure every agent has the right skills, installed safely, at the right scope. Covers skill discovery, evaluation, installation, monitoring, and removal.

## When to Use

- Installing or removing a skill on an agent
- Auditing which skills are installed and whether they are still needed
- Searching for or recommending skills to fill a capability gap
- Reviewing the skills registry for conflicts or duplicates

## Process

1. **Discovery**: Monitor capability gaps. Scout marketplace periodically. Accept skill requests from team members.
2. **Evaluation**: Initial screening -- does it fill a real gap? Is there overlap with existing skills? Is it well-documented? Is the source reputable?
3. **Security Gate**: Submit to security review. Classify as Tier A (internal/curated) or Tier B (community/marketplace). Never install without security approval.
4. **Installation**: Install via API. Update skills registry. Verify skill works. Document the installation.
5. **Monitoring**: Track usage and effectiveness. Flag unused skills for removal. Monitor for conflicts. Schedule periodic re-audits for Tier B skills.

## Output Format

- **Install**: Installation report with verification checklist.
- **Recommend**: Skill recommendation with rationale and alternatives.
- **Audit**: Registry inventory with usage, conflicts, and recommendations.
- **Search**: Gap analysis with candidate skills and fit assessment.

## Constraints

- Never install without security audit approval.
- Never install duplicate functionality -- check for overlaps first.
- Never modify a skill after security approval without re-audit.
- Always update the skills registry after any change.
- Monitor context bloat -- more skills means more instructions per agent.
- Remove unused skills quarterly -- skills should earn their place.
