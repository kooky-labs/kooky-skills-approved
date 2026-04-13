# kooky-skills-approved

Curated, vetted skills for KOOKY Cartel bots. Every skill in this repo has passed a manual security review before being listed here.

---

## What this repo is

KOOKY bots run on a skills-first architecture — all bot capabilities are implemented as discrete, installable skills. This repository is the official approved registry: if a skill is here, it has been reviewed and is safe to install on Cartel infrastructure.

Skills **not** in this repo require full security vetting before installation. See [VETTING.md](./VETTING.md) for the checklist and `knowledge/architecture/SKILL-SECURITY-FRAMEWORK.md` in KOOKY-OS for the full framework.

---

## Skill structure

Each skill lives under `skills/<skill-name>/` and follows this layout:

```
skills/
  <skill-name>/
    SKILL.md        # Required — YAML frontmatter + instructions
    run.sh          # Optional — executable script (chmod 755)
    README.md       # Optional — human-readable documentation
```

`SKILL.md` frontmatter:

```yaml
---
name: skill-name
description: One-line description of what this skill does
version: 1.0.0
author: kooky-labs
requires: []        # system deps, e.g. ["ffmpeg", "python3"]
---
```

---

## How to install a skill

```bash
skill install kooky-labs/kooky-skills-approved@<skill-name>
```

Example:

```bash
skill install kooky-labs/kooky-skills-approved@voice-transcription
```

The installer fetches `skills/<skill-name>/SKILL.md` from this repo and registers the skill with the bot runtime.

---

## How to contribute a skill

1. Fork this repo
2. Copy `skills/_template/` to `skills/<your-skill-name>/`
3. Fill in `SKILL.md` and (if needed) `run.sh`
4. Open a pull request
5. A reviewer will work through [VETTING.md](./VETTING.md) before merging

Skills that fail any critical check in VETTING.md will be rejected.

---

## Pre-installed skills

All base skills for the KOOKY Cartel agent fleet. Each skill is assigned to a specific agent.

| Skill | Agent | Description |
|-------|-------|-------------|
| [social-content](skills/social-content/SKILL.md) | HOUDINI (CMO) | Write platform-native social media posts for X, LinkedIn, TikTok, and Instagram |
| [copywriting](skills/copywriting/SKILL.md) | HOUDINI (CMO) | Write marketing copy: headlines, body copy, CTAs, email subject lines |
| [content-strategy](skills/content-strategy/SKILL.md) | HOUDINI (CMO) | Plan content calendars, suggest topics, align with business objectives |
| [sales-outreach](skills/sales-outreach/SKILL.md) | MAVERICK (Sales) | Write personalized cold outreach for LinkedIn and email |
| [lead-qualification](skills/lead-qualification/SKILL.md) | MAVERICK (Sales) | Evaluate and score incoming leads against ICP criteria |
| [quality-review](skills/quality-review/SKILL.md) | WATSON (QA) | Review content, code, and deliverables for quality standards |
| [skill-security-audit](skills/skill-security-audit/SKILL.md) | WATSON (QA) | Vet skills for security before installation |
| [delegation](skills/delegation/SKILL.md) | KAI (CEO) | Analyze requests and delegate to the right agent |
| [executive-summary](skills/executive-summary/SKILL.md) | KAI (CEO) | Summarize agent activity and generate progress reports |
| [technical-architecture](skills/technical-architecture/SKILL.md) | JARVIS (CTO) | Design system architecture and evaluate technical approaches |
| [mcp-integration](skills/mcp-integration/SKILL.md) | JARVIS (CTO) | Build MCP server tools, define schemas, connect external services |
| [product-design](skills/product-design/SKILL.md) | LEONARDO (CPO) | Define features, prioritize backlog, write user stories, design user flows |
| [operations-automation](skills/operations-automation/SKILL.md) | ALFRED (COO) | Design operational workflows and identify automation opportunities |
| [market-research](skills/market-research/SKILL.md) | SHERLOCK (Research) | Research competitors, market trends, and produce structured analysis |
| [financial-planning](skills/financial-planning/SKILL.md) | FINN (CFO) | Budget analysis, revenue projections, cost optimization, pricing strategy |
| [skill-management](skills/skill-management/SKILL.md) | TANK (Skills) | Curate, validate, and install skills; manage skill marketplace |
| [delivery-management](skills/delivery-management/SKILL.md) | SCOTTY (Delivery) | Track client deliverables, manage timelines, coordinate agent handoffs |
| [customer-success](skills/customer-success/SKILL.md) | SAM (CS) | Onboard users, handle support, gather feedback, track satisfaction |
| [knowledge-management](skills/knowledge-management/SKILL.md) | DEWEY (Knowledge) | Organize and maintain knowledge bases, ensure information currency |

---

## References

- Full security framework: `knowledge/architecture/SKILL-SECURITY-FRAMEWORK.md` in KOOKY-OS
- Skills-First Architecture: `knowledge/architecture/ADR-004-Skills-First-Architecture.md`
- KOOKY-OS hub: `https://github.com/kooky-labs/KOOKY-OS`
