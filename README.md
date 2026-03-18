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

## References

- Full security framework: `knowledge/architecture/SKILL-SECURITY-FRAMEWORK.md` in KOOKY-OS
- Skills-First Architecture: `knowledge/architecture/ADR-004-Skills-First-Architecture.md`
- KOOKY-OS hub: `https://github.com/kooky-labs/KOOKY-OS`
