---
name: managing-knowledge
description: Organizes knowledge bases, evaluates source quality, enforces documentation standards, and identifies knowledge gaps. Use when adding sources, auditing documentation health, or maintaining information currency.
---

# Knowledge Management

Maintain well-organized, accurate, current knowledge bases. Covers source evaluation, documentation structure, gap analysis, and deprecation workflows.

## When to Use

- Evaluating a new source for inclusion in a knowledge base
- Auditing documentation for staleness or gaps
- Organizing or restructuring knowledge base content
- Deprecating outdated documents

## Process

### Source Evaluation

Score each source 1-5 on five weighted dimensions:
- **Authority** (25%): Creator credentials, peer review, institutional backing.
- **Accuracy** (25%): Evidence support, factual errors, cross-source alignment.
- **Currency** (20%): Publication date, ongoing relevance.
- **Relevance** (15%): Direct applicability to the organization's needs.
- **Depth** (15%): Thoroughness, actionable detail.

Minimum score for inclusion: 3.0 weighted average. Verdict: INCLUDE / EXCLUDE / CONDITIONAL.

### Documentation Standards

- `knowledge/agent-notes/` -- Daily findings (`YYYY-MM-DD-<topic-slug>.md`)
- `knowledge/architecture/` -- ADRs and system design (`ADR-NNN-<title>.md`)
- `knowledge/guides/` -- How-to documents
- `knowledge/research/` -- Research outputs

### Maintenance Cadence

- Daily: Process new notes, tag, cross-reference.
- Weekly: Review for outdated content.
- Monthly: Gap analysis.
- Quarterly: Full audit, archive deprecated content.

### Deprecation

Mark as needs-review, notify owner, allow a grace period, archive (never delete), update referencing documents.

## Constraints

- Never add sources without evaluation.
- Never delete knowledge permanently -- archive deprecated content.
- Never skip cross-referencing -- isolated documents lose value.
- Flag critical knowledge gaps immediately rather than waiting for scheduled review.
