# Doser Stack Integration — decisions and the merge prompt

Decisions (Mikke, July 2026): compile-first. Where the stack overlaps
existing skills, keep the stack version and fold in whatever ours did
better. Landing pages, GEO, and carousels go to the stack. Daily social
stays with the lane-aware claude.ai set.

## Paste this to Claude Code in the ai-skills-stack folder

```
Apply these integration decisions:

1. Landing Page Designer.md — append this guardrail block at the end:
"## Guardrails (do not remove)
- Deploy previews only. Production deploys, custom domains, or live form
endpoints require Mikke's explicit approval of the final version.
- Form action URLs stay as clearly marked TODO placeholders until Mikke
names the real endpoint.
- Client proof appears only with a consent status: NAMED (written consent
on file) or DE-IDENTIFIED. No status = don't use it.
- Credibility comes from Mikke's 14 years in behavioral health. Never
attach compliance promises to products."

2. GEO AI Search Optimizer.md — add a query-sourcing step: buyer
questions come from the customer-voice-research language banks (real
quotes from BH program directors, therapists, group practice owners).
Map them: compliance/audit questions → SUDSync pages, automation
questions → Vibe Align consulting, intake/phone questions → CADENCE.

3. Social Media Graphics Generator.md — replace its generic carousel
approach with the Vibe Align carousel system: 1080x1080 HTML rendered to
PNG, dark and light themes, 6 frameworks (Educational, Framework,
Before/After, Listicle, Story, Quote/Stat), 8 slide types. Brand colors
and type come from Brand Kit Builder output.

4. SEO Blog Post Writer.md — personalize it: target site vibealign.co,
voice per voice-guide.md, internal links point at CADENCE, SUDSync, and
AI Readiness Assessment pages.

5. LinkedIn Post Writer.md and Social Media Manager Skill.md — add a
header note: "DORMANT: daily social is owned by vibealign-content and
mikke-social-content-v3 on claude.ai. Use this file only when Mikke names
it explicitly."

6. Auto-Improve Skill.md — convert from passive to on-demand. New rule:
it runs ONLY when Mikke says "tune it up" about a skill or an output.
It reviews against voice-guide.md and the skill's own standards, then
proposes specific improvements as suggestions. It never edits files
without her OK. Passive background scoring: off.

Report each file changed when done.
```

## The rule to remember

**"Tune it up."** Say it about any skill or any output, on any machine.
Claude reviews it against voice-guide and standards and proposes
improvements. Suggestions only, no silent edits. One phrase, no slash
commands to remember.

## Ownership map after integration

| Territory | Owner |
|---|---|
| Daily social posts, lanes, hooks, columns | claude.ai set: brand-lanes → vibealign-content / mikke-social-content-v3 / linkedin-hook-writer / dear-vibe-align |
| SEO articles, listicles, comparisons, content strategy | Doser stack SEO skills |
| Email: newsletters, sequences, sales emails, CTAs | Doser stack email skills |
| Video scripts, captions, YouTube/podcast packaging | Doser stack video/YouTube skills |
| Landing pages, web design, CRO | Copy + conversion architecture: Doser stack (Landing Page Designer, with guardrails). Visual build + design audit: Hallmark (~/.claude/skills/hallmark, from nutlope/hallmark; fork kept at vibe-onomy/hallmark). Conversion audit: CRO Skill. Flow: Designer writes → Hallmark builds → CRO audits conversion → hallmark audit audits design. |
| Lead magnets | Doser stack Lead Magnet Creator |
| Design: brand kit, logos, graphics, carousels, infographics | Doser stack design skills (carousels use the Vibe Align system) |
| Sales calls: prep, debrief, coaching | Mikke's set: sales-call-prep / call-debrief / sales-call-coach |
| Proof, VOC, competitive intel, compliance checks | Mikke's set |
| Voice enforcement | stack anti-slop (personalized) + AI Critic as final gate |
| Dormant | stack LinkedIn Post Writer, Social Media Manager, Open Source pack (5 files), passive Auto-Improve |
