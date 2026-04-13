---
name: copywriting
description: Write marketing copy: headlines, body copy, CTAs, email subject lines
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: houdini
requires: []
---

# Marketing Copywriting

Write clear, compelling marketing copy that converts. Use this skill when HOUDINI needs to write copy for landing pages, emails, ads, product descriptions, or sales materials.

## Usage

**Input:**
- `copy_type` (string) — headline, subhead, body copy, CTA, email subject line, email body, ad copy, product description, tagline
- `context` (string) — Where the copy will appear (landing page, email, ad platform, product UI)
- `audience_segment` (string) — Which ICP segment (displaced professional, solopreneur, small business owner)
- `desired_action` (string) — What the reader should do after reading
- `tone_override` (string, optional) — Default is KOOKY brand voice
- `constraints` (string, optional) — Character limits, platform rules, A/B test variants needed

**Output:**
- Final copy formatted for its destination
- Character/word count where relevant
- 2-3 A/B variants for headlines and subject lines
- Brief rationale for key creative choices
- Any assumptions made about audience or context

## Behavior

1. Receive copy type, context, audience, and desired action
2. Apply the appropriate framework:
   - **Headlines**: Lead with outcome, use specific numbers, pattern of [Pain point] + [Unexpected solution]
   - **Body copy**: Open with empathy, one idea per paragraph, features become benefits, single clear CTA
   - **CTAs**: Action-oriented verbs ("Start building", "Get your AI team"), match commitment level to context
   - **Email subject lines**: Under 50 characters, curiosity gap or specific benefit, 2-3 variants minimum
   - **Email body**: One purpose per email, first sentence earns the second, PS line for secondary CTA, plain text for cold outreach
3. Apply brand voice: direct, specific, honest, aspirational without hype
4. Run quality checks: read-aloud test, specificity test, "so what?" test
5. Generate A/B variants for headlines and subject lines
6. Return formatted copy with rationale

## Network

None.

## Error handling

- If audience segment is unclear, state assumptions and flag for confirmation
- If character limits conflict with necessary messaging, provide both a short and long version
- If claims cannot be verified, flag them rather than including unverified assertions

## Notes

- Core value proposition: "AI took your job? Let AI build you a new one."
- Power words: build, own, launch, automate, replace, earn, scale
- Banned words: leverage, synergy, disrupt, paradigm, revolutionary, game-changing, unlock
- Never make claims about results KOOKY cannot verify
- Never use fear-based copy ("You'll be left behind")
- Never promise specific income or financial outcomes
- Never disparage competitors by name
- Always write in a way that Renato would actually say it
