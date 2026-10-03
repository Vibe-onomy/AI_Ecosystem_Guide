# Skills Audit — Fix Pack 1 (Voice Integrity + Routing)

This folder contains ready-to-apply fixes from the July 2026 skills audit.
Nothing in here changes automatically — each fix is applied by you in
claude.ai → Settings → Capabilities → Skills (or by re-uploading the skill).

## What's in this pack

| File | What it fixes | Priority |
|------|---------------|----------|
| `fixes/anti-slop/SKILL.md` | Skill was enforcing "Ryan's voice" on Mikke's content | 🔴 1 |
| `fixes/seo-blog-post-writer/SKILL.md` | Skill wrote for ryandoser.com in Ryan's voice; dangling references to skills that don't exist on this account | 🔴 1 |
| `fixes/brand-lanes/SKILL.md` | Promotes brand-lanes to the master content router so writing skills stop competing for the same triggers | 🟠 2 |
| `fixes/approval-gate-snippet.md` | Paste-in guardrail for any skill that can publish externally (Blotato, Gmail, deploys) | 🟠 3 |
| `CLEANUP-CHECKLIST.md` | Duplicate plugins to uninstall + connector re-auth list | 🟠 2 |
| `AUDIT.md` | The full audit report, for the record | — |

## How to apply a skill fix

1. Open claude.ai → Settings → Capabilities → Skills.
2. Find the skill by name (e.g. `anti-slop`).
3. Replace its SKILL.md content with the version in `fixes/<skill>/SKILL.md`,
   or delete the old skill and upload the new folder as a .zip.
4. If the original skill had extra reference files you still want, keep them —
   these rewrites only replace the main SKILL.md.

## Important note on the rewrites

The original skill *bodies* live on your claude.ai account and were not
readable from this session — only their names and trigger descriptions were.
The rewritten files below are complete, working replacements built from your
documented brand voice (direct, witty, authority-forward, zero AI slop,
"business therapy" framing). Before applying, skim each one and add any
specific rules from the originals you want to preserve.
