---
name: content-strategy
description: Plan content calendars, suggest topics, align with business objectives
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: houdini
requires: []
---

# Content Strategy Planning

Design content strategies that build KOOKY's audience through authentic build-in-public storytelling. Use this skill when HOUDINI needs to plan content calendars, suggest topics, define content mix, or align content efforts with business objectives.

## Usage

**Input:**
- `time_horizon` (string) — Weekly plan, monthly calendar, or quarterly strategy
- `objectives` (string) — Business goal content serves (audience growth, lead gen, product launch, brand awareness)
- `active_platforms` (string) — Which platforms are active (X primary, LinkedIn, TikTok, Instagram)
- `current_metrics` (object, optional) — Follower count, engagement rate, impressions
- `recent_events` (string, optional) — Business events that can become content (launches, wins, failures, decisions)
- `constraints` (string, optional) — Available production capacity, Renato's availability for recording

**Output:**
- Weekly plan: table with Day/Platform/Pillar/Topic/Format/Notes + engagement focus areas
- Monthly calendar: week-by-week themes, key content pieces, metric targets, production schedule
- Quarterly strategy: narrative arc, platform evolution, pillar adjustments, collaboration targets, resource requirements

## Behavior

1. Receive time horizon, objectives, and platform information
2. Apply content pillar allocation: Founder's Journey (40%), Behind-the-Scenes Ops (25%), Case Studies & Proof (20%), AI Landscape Hot Takes (15%)
3. Plan against default weekly rhythm: Monday (recap), Tuesday (behind-the-scenes thread), Wednesday (case study), Thursday (hot take), Friday (Day X update)
4. Prioritize platforms: X (primary, 2-3 threads/week + daily singles), TikTok (3-4 videos/week), LinkedIn (2-3 posts/week), Instagram (selective cross-post)
5. Apply engagement targets per platform and timeframe
6. Account for content repurposing — one good piece becomes 3-4 platform-native posts
7. Leave room for reactive content (responding to industry news, real-time moments)
8. Return structured plan with production requirements

## Network

None.

## Error handling

- If no recent events are available, focus on evergreen pillar content and flag the gap
- If production capacity is limited, reduce volume and prioritize highest-impact platforms
- If metrics are unavailable, use default engagement targets as baselines

## Notes

- Quality over volume — fewer posts with more impact beats daily filler
- Every planned piece must pass the authenticity test
- Never plan content that requires Renato to fabricate experiences
- Never prioritize volume over quality
- Content calendar is a guide, not a mandate — skip anything that is not genuinely interesting
- Engagement targets: X followers +300/30d, +1,500/90d; X thread impressions 50K/30d, 300K/90d
- Collaboration targets: daily engagement with key accounts (@julianweisser, @aisolopreneur, @gregisenberg, @DeRonin_, @levelsio)
- 70/30 rule on X: 70% engaging with others' content, 30% original
