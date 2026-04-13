---
name: quality-review
description: Review content, code, and deliverables for quality standards
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: watson
requires: []
---

# Quality Review

Ensure every deliverable that leaves KOOKY meets quality standards. Use this skill when WATSON needs to review any deliverable — content, code, agent outputs, or business materials — for quality, accuracy, and brand consistency.

## Usage

**Input:**
- `deliverable` (string) — The content, code, or material to review
- `type` (string) — content (social post, email, copy), code (implementation, integration), agent output (research, analysis), business material (proposal, deck, report)
- `author_agent` (string) — Who produced this
- `intended_audience` (string) — Who will see this
- `context` (string) — What is this for, where will it be used

**Output:**
- Structured review with verdict: PASS / PASS WITH CHANGES / FAIL
- Findings with severity levels (BLOCK, MAJOR, MINOR, NOTE)
- Specific fix recommendations for each finding
- Strengths section (always included)
- Clear next-step recommendation

## Behavior

1. Receive the deliverable and context
2. Review across five dimensions:
   - **Factual Accuracy**: Are claims verifiable? Any fabricated details? Sources cited where needed?
   - **Brand Voice Consistency**: Sounds like KOOKY/Renato? Banned words present? Passes authenticity test?
   - **Technical Accuracy** (for code): Works as intended? Security vulnerabilities? Edge cases?
   - **Bias and Safety**: Unintentional bias? Misleading statements? Promises that cannot be kept?
   - **Formatting and Presentation**: Platform-appropriate? Spelling/grammar? Clear structure?
3. Classify each finding by severity:
   - **BLOCK**: Must fix before publishing/deploying (factual errors, security issues, brand-damaging content)
   - **MAJOR**: Should fix (significant quality issues reducing effectiveness)
   - **MINOR**: Nice to fix (polish items improving quality)
   - **NOTE**: Observation (no action required but worth awareness)
4. Identify at least one strength
5. Return structured review with clear verdict and next steps

## Network

None.

## Error handling

- If the deliverable type is unclear, ask for clarification before reviewing
- If insufficient context is provided, note assumptions made during review
- Escalate legal/compliance questions to KAI — WATSON is not a lawyer

## Notes

- Default to cautious when in doubt — questioning assumptions is a feature
- Never approve something with unresolved doubts — flag the doubt
- Never rewrite the deliverable — provide specific fix instructions
- Never let personal preference override brand standards
- Never block for stylistic preferences — only for substantive issues
- Always provide at least one positive observation (strengths)
- Be specific: "This claim is unverified" not "Some claims may need checking"
- Banned words to check for: leverage, synergy, disrupt, paradigm, revolutionary, game-changing
