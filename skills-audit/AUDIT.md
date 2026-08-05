# Vibe Align — Skills & Plugin Audit (July 2026)

Full audit of the claude.ai account's skill ecosystem: 27 custom account
skills, 31 plugin installs (~19 unique), plus built-in/session skills.
Plugin-internal skills were identifiable by plugin name only from this
environment; auditing their bodies requires an interactive claude.ai session
or access to their source repos.

## Inventory by category

**A. Brand identity & voice:** brand-lanes, dear-vibe-align, anti-slop,
content-research-writer · plugins: brand-voice (×2), mikke-social-content-v3,
vibe-persuasion

**B. Content production & distribution:** linkedin-hook-writer,
seo-blog-post-writer · plugins: searchfit-seo, marketing (×2)

**C. Sales, offers & funnel:** ideal-client-avatar-builder,
lead-research-assistant, perfect-webinar-builder · plugins: sales,
small-business (×2)

**D. Product & build:** prd-writer, brainstorming, skill-creator,
mcp-builder, setting-up-mcps, web-artifacts-builder · plugins:
product-management (×2), engineering, design (×2)

**E. Research & QC:** notebooklm, crosscheck, learn · plugins:
bigdata-com (×2), data (×2), enterprise-search (×2)

**F. Documents & visuals (stock):** docx, pptx, pdf, xlsx, doc-coauthoring,
internal-comms, canvas-design, theme-factory, brand-guidelines · plugin:
pdf-viewer

**G. Business ops plugins:** finance (×2), legal (×2), human-resources,
operations, productivity (×2), cowork-plugin-management

## Key findings

### 1. Effectiveness
- Seven skills/plugins compete for the same "write content" triggers →
  non-deterministic skill selection. Fix: brand-lanes as master router
  (see fixes/brand-lanes/SKILL.md).
- seo-blog-post-writer references skills that don't exist on this account
  (Email Newsletter Writer, Crosspost, SEO Audit) — dangling imports.
- 12 duplicate plugin installs add trigger noise (see CLEANUP-CHECKLIST.md).
- linkedin-hook-writer should learn from actual Blotato post analytics.
- skill-creator's eval/benchmark mode is unused — run it on the top 5
  revenue-relevant skills.

### 2. Security & risk
- 🔴 Voice contamination: anti-slop enforces "Ryan's voice" and
  seo-blog-post-writer targets ryandoser.com — imported from another
  creator's suite. The QC layer was calibrated to the wrong brand.
- 🟠 Autonomous publishing surface: content skills + Blotato/Gmail/Vercel
  with no mandatory per-piece human approval (see
  fixes/approval-gate-snippet.md).
- 🟠 notebooklm stores persistent Google auth for browser automation.
- 🟠 crosscheck sends content to OpenAI/Google via OpenRouter — data egress.
- 🟡 Prompt-injection path: scraped transcripts flow toward publish-ready
  output; guard added in the seo-blog-post-writer rewrite.
- 🟡 lead-research-assistant has no CAN-SPAM/GDPR guardrails.
- 🟡 Three connectors need re-authentication.

### 3. Social content insights encoded in the stack
- Dear Vibe Align's letter→diagnosis→prescription structure is a franchise
  format; reader submissions are a zero-effort topic queue.
- Hook-first truncation focus is the right LinkedIn model; use all 8–10
  generated variants across reposts.
- The stack itself is a serialized content pillar ("skill #7 of 100").
- The avatar→webinar→hooks trio implies a webinar-anchored content calendar.

### 4. What makes this stack unique
- A governance layer (router → voice → format) instead of loose utilities.
- ICA as a queryable role-play project, incl. buying committees.
- Multi-model adversarial QC (crosscheck) + source-grounded research
  (notebooklm).
- Full-funnel closure under one voice system, already part-productized
  (versioned plugins).

### 5. Workflow combinations
1. Offer Validation Gauntlet: brainstorming → ICA role-play rejection →
   perfect-webinar-builder → dear-vibe-align ads → crosscheck.
2. Content Flywheel: video → blog → newsletter → hooks → anti-slop →
   Blotato → analytics feed back into hooks.
3. Column Production Line: letter → column → branded visual → hooks.
4. Lead-Gen Loop: lead research → ICA scoring → voice-matched Gmail drafts.
5. Client Brand-OS Builder: interview → client ICA → skill-creator builds
   the client's own router/voice/anti-slop plugin (productized service).

### 6. Product ideas
1. "Brand OS" installable plugin / setup service (fastest to revenue).
2. Synthetic-customer SaaS (Supabase + Vercel already connected).
3. The AI Ecosystem Guide as an interactive gated directory (this repo).
4. Anti-slop as a micro-product (extension/API).
5. "Skill Audit" as a $2–5k consulting offer.

## Impact-ranked recommendations
1. Fix voice contamination (this fix pack).
2. Master router + dedupe plugins (this fix pack).
3. Approval gates on all publishing paths (this fix pack).
4. Ship the Client Brand-OS productized service.
5. Wire Blotato analytics into linkedin-hook-writer.
