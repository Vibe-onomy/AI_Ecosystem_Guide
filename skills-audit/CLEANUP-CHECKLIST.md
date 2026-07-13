# Cleanup Checklist — duplicates, re-auth, and dangling references

Work top to bottom. Everything here is done in claude.ai settings, takes
about 15 minutes total, and requires no code.

## 1. Uninstall duplicate plugins (12 duplicates found)

You have two installed copies of each plugin below — likely the same plugin
installed from two marketplaces. Duplicates double trigger-matching noise
and can feed Claude two conflicting versions of the same instructions.

In claude.ai → Settings → Capabilities → Plugins, keep ONE copy of each and
uninstall the other (if version/source differs, keep the newer or
official-marketplace copy):

- [ ] small-business (2 copies)
- [ ] brand-voice (2 copies) ← most important; this one shapes your voice
- [ ] product-management (2 copies)
- [ ] bigdata-com (2 copies)
- [ ] finance (2 copies)
- [ ] legal (2 copies)
- [ ] enterprise-search (2 copies)
- [ ] data (2 copies)
- [ ] design (2 copies)
- [ ] marketing (2 copies)
- [ ] productivity (2 copies)

## 2. Re-authenticate connectors

Three connected MCP servers currently fail auth, so their tools are dead
weight until re-authorized. In claude.ai → Settings → Connectors, look for
any connector showing a "needs authentication / reconnect" state and re-auth
it. (Server IDs are internal; the settings page shows the friendly names.)

- [ ] Re-auth connector 1
- [ ] Re-auth connector 2
- [ ] Re-auth connector 3

## 3. Apply the skill fixes from this pack

- [ ] Replace `anti-slop` with `fixes/anti-slop/SKILL.md` (kills the
      "Ryan's voice" contamination)
- [ ] Replace `seo-blog-post-writer` with
      `fixes/seo-blog-post-writer/SKILL.md` (retargets ryandoser.com →
      vibealign.co, removes references to skills you don't have, adds
      transcript injection guard)
- [ ] Replace `brand-lanes` with `fixes/brand-lanes/SKILL.md` (master router)
- [ ] Paste `fixes/approval-gate-snippet.md` into any skill inside
      `mikke-social-content-v3` that can call Blotato

## 4. Audit other imported skills for the same contamination

`anti-slop` and `seo-blog-post-writer` were imported from another creator's
suite. Check whether these were too, and fix any "Ryan"/ryandoser.com
references inside their bodies:

- [ ] `perfect-webinar-builder`
- [ ] `lead-research-assistant`
- [ ] `ideal-client-avatar-builder`
- [ ] anything inside `mikke-social-content-v3` that was adapted from
      templates

## 5. Widen GitHub access (so the next audit can read skill source)

- [ ] github.com → Settings → Applications → Claude → Repository access →
      grant the vibe-onomy repos you want auditable
- [ ] When starting a Claude Code web session, select those repos as sources

## 6. Optional but recommended

- [ ] Decide whether `brand-guidelines` (applies ANTHROPIC's branding)
      should stay enabled — risky if it fires during client deliverables
- [ ] Run `skill-creator`'s eval/benchmark mode on `anti-slop` and
      `brand-lanes` after replacing them, to confirm triggering improved
