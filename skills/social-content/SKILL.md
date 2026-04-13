---
name: social-content
description: Write platform-native social media posts for X, LinkedIn, TikTok, and Instagram
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: houdini
requires: []
---

# Social Content Creation

Create platform-native social media posts that build KOOKY's audience through authentic build-in-public storytelling. Use this skill when HOUDINI needs to write social media content for any platform (X, LinkedIn, TikTok, Instagram).

## Usage

**Input:**
- `topic` (string) — What happened, what decision was made, what result occurred
- `platform` (string) — X (thread or single tweet), LinkedIn, TikTok script, or Instagram
- `content_pillar` (string, optional) — Founder's Journey (40%), Behind-the-Scenes Ops (25%), Case Studies & Proof (20%), AI Landscape Hot Takes (15%)
- `day_number` (integer, optional) — Current day in the "building a zero-human company" series
- `raw_material` (string, optional) — Voice notes, screenshots, real numbers, decisions from Renato

**Output:**
- Post content ready to copy-paste, with platform label
- Character count for X posts
- Notes on timing or engagement strategy
- Suggested reply-tweet content (for X)

## Behavior

1. Receive topic, platform, and optional context
2. Select appropriate content pillar if not specified
3. Format content according to platform-specific rules:
   - **X single tweets**: Under 280 characters, no external links in main tweet
   - **X threads**: Numbered parts (1/, 2/, 3/), 3-7 tweets max, hook-first opening, end with question
   - **Serialized format**: "Day [X] of building a zero-human company." + one concrete thing + optional question
   - **LinkedIn**: Professional tone, line breaks every 1-2 sentences, hook first line, 150-300 words, 3-5 hashtags
   - **TikTok scripts**: Hook in first 3 seconds, face-to-camera, 45-90 seconds, visual cues, conversational language
   - **Instagram Reels**: Cross-post from TikTok selectively, separate caption text
4. Apply brand voice: direct, specific, honest, aspirational without hype
5. Verify content passes authenticity test: "Could any other company post this exact thing?" If yes, rewrite
6. Return formatted output with character count and engagement notes

## Network

None.

## Error handling

- If no real data is available for claims, flag it and ask Renato rather than fabricating
- If content fails the authenticity test, rewrite with more specific, KOOKY-unique details
- If platform constraints cannot be met (e.g., too much content for a single tweet), suggest splitting or reformatting

## Notes

- Never fabricate numbers or results
- Never use corporate jargon: "leverage", "synergy", "disrupt", "paradigm"
- Never add emoji spam — one or two max per post, zero is fine
- Never write "Thread:" or "THREAD" as a prefix
- Always attribute the voice to Renato, not to KOOKY generically
- Engagement targets: reply rate >2% (30-day), >3% (90-day)
- Weekly rhythm: Monday (recap), Tuesday (behind-the-scenes), Wednesday (case study), Thursday (hot take), Friday (Day X update)
- Best X posting windows: 9-11am EST or 6-8pm EST
