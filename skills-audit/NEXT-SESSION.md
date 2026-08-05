# Next laptop session — three pastes, in order

Open Claude app → Code tab → ai-skills-stack session. Then:

## Paste 1 — finish anti-slop (if the approval step wasn't completed)

```
Approved as written. Edit anti-slop.md with the two tune-up fixes (em dash
report lines + Part 6 Fabrication Rule), sync to SKILL.md, re-zip, and give
me the zip path.
```

Then: claude.ai → Settings → Capabilities → Skills → remove old anti-slop
→ upload the fresh zip.

## Paste 2 — install Hallmark

```
Run: npx skills add nutlope/hallmark
Then confirm it landed in ~/.claude/skills/hallmark/ and list its verbs.
```

## Paste 3 — retest anti-slop in a regular claude.ai chat

Use the slop test paragraph (in the audit session with Claude / or ask
Claude to regenerate one). Pass condition: every em dash reported as its
own line item, and the rewrite's proof line is a [PLACEHOLDER: real
metric + consent status] or cut — never an invented number.

## Paste 4 — package ghl-ai-builder for claude.ai

```
Package the ghl-ai-builder skill (SKILL.md is in the fix pack at
skills-audit/fixes/ghl-ai-builder/ in the AI_Ecosystem_Guide repo, or I
will paste it) as an uploadable claude.ai skill zip, same as anti-slop.
Give me the zip path.
```

Then upload at claude.ai → Settings → Capabilities → Skills. This one
lives at the ACCOUNT layer on purpose: it drives Claude in Chrome, and
browser control happens from chats/desktop, not the Claude Code terminal.

## Then tell audit-session Claude "done" so it can verify the directory.

---

Landing page flow after Hallmark is installed:
Landing Page Designer (copy + conversion architecture) → Hallmark (visual
build, 57 gates) → CRO Skill (conversion audit) → hallmark audit (design
audit). Bonus sales tool: run `hallmark audit` on a prospect's site before
a Vixta discovery call.
