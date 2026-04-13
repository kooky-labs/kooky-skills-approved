---
name: knowledge-management
description: Organize and maintain knowledge bases, ensure information currency
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: dewey
requires: []
---

# Knowledge Management

Maintain KOOKY's collective knowledge so every agent has access to accurate, current, well-organized information. Use this skill when DEWEY needs to organize knowledge bases, evaluate sources, manage documentation, or ensure information currency.

## Usage

**Input:**
- `action` (string) — Source evaluation, knowledge base organization, documentation update, content quality scoring, gap analysis
- `domain` (string, optional) — Topic area for source evaluation
- `source` (string, optional) — URL, document, or reference to evaluate
- `knowledge_base` (string, optional) — Which knowledge base needs attention
- `requester` (string, optional) — Who needs this knowledge work done

**Output:**
- Source evaluation report with 5-criteria scores and verdict (INCLUDE/EXCLUDE/CONDITIONAL)
- Gap analysis with well-covered topics, under-documented topics, stale content, recommended additions
- Organization updates with naming conventions and cross-references applied
- Deprecation notices with migration plan for referencing documents

## Behavior

1. **Source Evaluation**: Score each source 1-5 on five dimensions (weighted):
   - **Authority** (25%): Creator credentials, peer review, institutional backing
   - **Accuracy** (25%): Evidence support, factual errors, cross-source alignment
   - **Currency** (20%): Publication date, ongoing relevance, domain changes
   - **Relevance** (15%): Direct applicability to KOOKY's needs
   - **Depth** (15%): Thoroughness, actionable detail level
   - Minimum score for inclusion: 3.0 weighted average
2. **Knowledge Base Organization**: Enforce structure standards:
   - `knowledge/agent-notes/` — Daily findings and decisions (`YYYY-MM-DD-<topic-slug>.md`)
   - `knowledge/architecture/` — ADRs and system design (`ADR-NNN-<title>.md`)
   - `knowledge/guides/` — How-to documents
   - `knowledge/research/` — SHERLOCK's research outputs
3. **Maintenance Schedule**: Daily (process new notes, tag/cross-reference), Weekly (review for outdated content), Monthly (gap analysis), Quarterly (full audit, remove deprecated)
4. **Deprecation Process**: Mark needs-review, notify owner, 2-week grace period, archive (never delete), update referencing documents
5. **NotebookLM Management**: Upload quality sources, organize by domain, maintain source inventory, remove outdated sources quarterly

## Network

None.

## Error handling

- If a source scores below 3.0, provide specific reasons and suggest better alternatives
- If a knowledge gap is critical (could affect agent decisions), flag immediately rather than waiting for scheduled review
- If a document owner is unresponsive for deprecation review, escalate to KAI

## Notes

- Every knowledge document must have: clear title, date created/updated, author/source, status (current/needs-review/deprecated), related documents
- Never add sources to knowledge bases without evaluation
- Never delete knowledge permanently — archive deprecated content
- Never skip cross-referencing — isolated documents lose value
- Coordinate with SHERLOCK for research inputs
- Report knowledge base health to JARVIS monthly
- Flag when a critical knowledge gap could affect agent decision-making
