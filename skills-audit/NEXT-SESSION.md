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

## Paste 5 — install b-roll-finder (only once you're editing talking-head video)

```
Install the b-roll-finder skill: git clone https://github.com/louisedesadeleer/b-roll-finder.git
into my user folder, add a /find-broll pointer to ~/.claude/CLAUDE.md, and install
its tools for WINDOWS (not the macOS/Homebrew steps): yt-dlp, ffmpeg, imagemagick via
winget. Skip mlx-whisper (Apple-only). For transcripts, use my Tella transcripts or
the timestamps I provide; only install openai-whisper if I ask.

Then add these to the Guardrails in my fork of TASTE.md, as permanent overrides:
1. Never use yt-dlp --cookies-from-browser or my logged-in browser. Public sources only.
2. No clips from other creators' YouTube channels. Allowed sources: my own footage and
   screens, licensed stock (Pexels, Mixkit, Coverr), official government and
   association sources, screenshots of public headlines, and my own motion graphics.
3. Never show patient information, client names, or identifiable program details
   without written consent on file.
Run the onboarding questions with me before the first use; do not reuse Louise's
taste profile.
```

## Then tell audit-session Claude "done" so it can verify the directory.

---

Landing page flow after Hallmark is installed:
Landing Page Designer (copy + conversion architecture) → Hallmark (visual
build, 57 gates) → CRO Skill (conversion audit) → hallmark audit (design
audit). Bonus sales tool: run `hallmark audit` on a prospect's site before
a Vixta discovery call.
