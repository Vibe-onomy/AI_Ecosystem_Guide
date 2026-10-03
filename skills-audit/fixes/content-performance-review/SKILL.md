---
name: content-performance-review
description: Read-only analytics review that closes the content feedback loop. Pulls post performance from Blotato (top posts, per-post analytics), diagnoses what's working and what isn't, and prescribes the next content moves — updating the proven-hooks reference so linkedin-hook-writer learns from real results. Use when the user says "how is my content doing," "content review," "what worked this month," "which posts hit," "review my analytics," or on a recurring weekly/monthly content review. This skill NEVER posts, schedules, edits, or deletes anything.
---

# Content Performance Review — the feedback loop

Most content systems are open-loop: publish, hope, repeat. This skill
closes the loop so every post makes the next one smarter.

## Step 1 — Pull (read-only)

Via Blotato: `blotato_list_top_posts` and `blotato_get_post_analytics` for
the review window (default: last 30 days; weekly if asked). If analytics
tools are unavailable, ask the user to paste platform screenshots/exports
instead — never fabricate numbers.

## Step 2 — Diagnose (the biz-therapy read)

Report in this order, numbers first:
1. **Top 3 posts** — and the specific reason each worked (hook pattern,
   topic, format, timing), not "it resonated."
2. **Bottom 3** — same specificity. A good post that died at the hook is a
   different diagnosis than a weak topic that never had a chance.
3. **Pattern read across the window** — which lane (per brand-lanes),
   which format (column, carousel, hook-led post), which topic cluster is
   pulling; what the audience is telling us they want more of.
4. **One honest flag** — the thing the numbers say that Mikke might not
   want to hear. This section is mandatory.

## Step 3 — Prescribe

- 3 concrete next moves for the coming week/month, each tied to a finding
  ("Secret #2-style compliance myths outperformed everything 3:1 — make it
  a monthly franchise").
- **Update the hook bank:** append this window's winning hooks (verbatim,
  with their numbers) to the proven-hooks reference used by
  linkedin-hook-writer, so hook generation is trained on YOUR winners,
  not generic patterns.

## Guardrails

- Strictly read-only: never create, schedule, edit, boost, or delete posts.
- Report metrics exactly as the API returns them; small samples get called
  small ("2 posts is a hint, not a trend").
- No vanity framing — reach without pipeline movement gets said plainly.

## Hand-offs

- Prescriptions → brand-lanes (routing) → vibealign-content / dear-vibe-align
- Winning topics that deserve long-form → content-research-writer or
  seo-blog-post-writer
- A win worth bragging about → case-study-builder (yes, your own content
  results are proof too)
