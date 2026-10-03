---
name: ghl-ai-builder
description: >
  Full browser takeover of GoHighLevel to build what the GHL MCP can't: funnels and
  sites via Funnel & Website AI (Build mode), complete workflows via Workflow AI
  Builder, plus AI Studio projects — all driven through Claude in Chrome inside the
  user's GHL account. Use this skill whenever the user asks to build a funnel, landing
  page, website, workflow, or automation in GHL/HighLevel, use the AI funnel builder,
  use Workflow AI, use AI Studio, connect forms or calendars to an AI-built page, or
  take over the browser/screen to work inside GoHighLevel. Also trigger on "Funnel AI",
  "Website AI", "Workflow AI", "Build with AI", "GHL AI builder", "build the whole
  funnel for me", "auto-create workflows", or any request to clone/improve a site with
  GHL's AI tools. Also trigger when a GHL form isn't creating contacts, a funnel form
  isn't working, leads aren't coming through a page, or a workflow won't fire — the AI
  builders produce fake forms and hallucinated references, and this skill documents the
  fixes. The GHL MCP handles data (contacts, conversations, opportunities, payments) —
  it CANNOT create funnels or workflows. Everything build-related runs through the
  browser.
---

# GHL AI Builder — Funnels + Workflows (Browser-Control SOP)

Operating manual for building funnels, pages, AND workflows with GoHighLevel's AI builders via Claude in Chrome. Grounded in HighLevel's official docs and changelog plus a full end-to-end field run (funnel + form + workflow) on **2026-07-17**.

**If you read one thing, read Rule Two.** The AI builds forms that look perfect and capture nothing, and workflows that reference forms and tags that don't exist. Everything else here is secondary.

## Rule zero — MCP for data, browser for builds

The official GHL MCP server covers contacts, conversations, calendars, opportunities, payments, locations, and custom fields (~21 tools; `/mcp/anthropic/v2` has the widest coverage). It CANNOT create funnels, sites, or workflows — those endpoints don't exist in the MCP surface. Division of labor:
- **GHL MCP** (if connected): look up contacts, verify a form submission landed, check opportunities/pipelines, read conversations. Use it for verification steps — faster and more precise than screenshots.
- **Browser (Claude in Chrome)**: everything else — Funnel & Website AI, Workflow AI Builder, AI Studio, form/calendar wiring, settings.

GHL is a web app. Use **Claude in Chrome tools** (`mcp__claude-in-chrome__*`) — navigate, computer (screenshot/click/type/scroll), find, form_input. Desktop computer-use can't click browsers (read-only tier). Load all Chrome tools in ONE ToolSearch call before starting.

## Rule one — universal guardrails

- NEVER click Publish (funnel OR workflow), connect a domain, or push anything live without explicit confirmation from the user. A published workflow fires real emails/SMS to real contacts — treat workflow Publish exactly like funnel Publish.
- **Confirm the sub-account before building.** Many users run agencies with multiple client accounts. URL pattern: `https://app.gohighlevel.com/v2/location/{locationId}/dashboard` — or the agency's white-label domain (`https://{white-label-domain}/v2/location/{locationId}/dashboard`). Ask which account/location if it isn't obvious. Location IDs change per client; the process never does.
- **Ask for brand details before the first build**: primary color, accent color, font, and any brand rules. Don't invent a brand.
- Login/2FA is the user's job — hand control back if a login screen appears. Never ask for or store credentials.
- Workflows that send to real contacts get built in DRAFT and tested with a test contact before the user approves publish.

## Which builder — decision table

| Ask | Tool | Where |
|---|---|---|
| Funnel, landing page, sales page, opt-in, website | **Funnel & Website AI, Build mode** (DEFAULT) | Sites → Funnels → Build with AI |
| Workflow, automation, follow-up sequence, nurture | **Workflow AI Builder** | Automation → Workflows → Build using AI |
| Quiz, custom booking flow, storefront, interactive app | **AI Studio** (only if asked) | Left nav → AI Studio |

Default to Funnel & Website AI in Build mode. Do NOT use AI Studio and do NOT use Assist mode unless the user explicitly asks. AI Studio projects can NEVER move into standard Funnels/Websites; no order forms/payments there. AI Studio is free until Sept 1, 2026, then usage pricing kicks in.

---

# RULE TWO — THE AI BUILDS FAKE FORMS. ALWAYS REPLACE THEM.

**This is the single highest-impact thing in this document. Field-verified 2026-07-17.**

Funnel AI renders the lead capture form as a **Custom Code element** — raw HTML that looks perfect and does nothing. It has no submit handler, creates no contact, records no submission, and never appears in Sites → Forms. A client would ship this page and silently lose every lead.

**How it was proven:** filled the AI's form on the live preview → clicked submit → no success message → zero contacts created (verified twice via MCP and the Contacts UI) → no form in Sites → Forms → clicked the element in the builder and the settings panel read **"Custom Code."**

**The same failure class applies to Workflow AI**, which invents references to forms, tags, and merge fields that don't exist. See Part B.

**The fix — never skip it:**
1. Build the real form FIRST: **Sites → Forms → Create form → Start from Scratch**. It pre-loads First Name / Last Name / Phone* / Email* plus two A2P consent checkboxes.
2. Add fields from the left rail. Dropdowns live under **Choice Elements → Single Dropdown**. Drag onto the canvas, then set Label / options / Required in the right-hand panel.
3. Edit the submit button's text in the **right panel's "Text" box** — typing on the canvas button does nothing.
4. Save. Confirm it appears in Sites → Forms with today's timestamp.
5. In the page builder: click the AI's fake form → confirm the panel says "Custom Code" → delete it → click the empty column's **+ Add** → **Forms And Surveys** → **Add Existing Form** → pick your form.
6. Re-test on the preview. A real GHL form auto-formats the phone number as you type and shows a success message on submit. That's your proof it's genuinely wired.

**Expect a styling regression.** The real form element renders with default styling, losing the AI's navy card. Restyle via the element's Styles tab, or prompt the Build box to restyle the section around it. Function first, then looks.

**Cheaper alternative when the design doesn't matter:** prompt the AI to build the page *without* a form section, then drop the real form element in. Saves deleting good-looking markup.

---

# PART A — FUNNEL / PAGE BUILD LOOP (field-tested)

1. **Navigate** to the location dashboard URL. Screenshot; confirm the sub-account name in the top-left switcher.
2. Left nav → **Sites** → **Funnels** tab → blue **Build with AI** button (top right, next to "+ New funnel"). This creates a new untitled funnel and opens the page builder with the **Ask AI** panel on the left.
3. Panel defaults to **Assist**. Click **Build** (second tab). Build mode = suggestion chips + "Plan, build, modify anything..." prompt box.
4. **Write the prompt as ONE continuous prose paragraph — NO numbered lists, NO newlines.** This is the single most important rule. Field-tested: a multi-line numbered prompt hung the builder in an "Analyzing website / Reproducing sections / Sourcing and mirroring images from source" loop for 20+ minutes with an empty canvas. The identical content as flat prose generated a complete 10-section page in ~5 minutes.
5. Click into the box, type the prompt, then **click the purple send button** — don't rely on Enter. The box grows as chips render (Goal / Target Audience / Offer / Tone / Color / Layout), so re-screenshot to find the send button's current position before clicking.
6. **Verify the send**: the prompt becomes a sent bubble with parsed chips. If the text is still in the input, click send again at its new coordinates.
7. **Watch the pipeline. Healthy signals:** "Thought for Ns" → "Creating design tokens and visual theme" → per-section build cards ("Building Hero Section (1/10)"…"— Done") → "Writing content for N sections" → "Preparing image specifications" → "Running final checks" → canvas renders, page auto-renames from "Untitled", autosave flips ON. **Hung signals:** to-dos titled "Analyzing website / Reproducing sections / Sourcing and mirroring images" cycling with the canvas stuck on "Start Creating your Funnel Page".
8. **If hung ~10 min: refresh the page URL.** Nothing is lost if the canvas never rendered. After refresh, re-confirm the panel is still on Build (it usually is — see Browser-driving notes) and re-submit as prose.
9. **Poll with screenshots every ~60s.** Never navigate away or re-prompt mid-generation. Expect ~5 min for a full page with images.
10. **Review top to bottom** (scroll + screenshot). Iterate via chat in the same Build box. The AI auto-generates SEO titles/meta — verify them before any publish talk.
11. **Test integrations** — submit a real form entry / booking, verify the contact lands in CRM. Non-negotiable before delivery. **This is the step that catches the fake form (Rule Two).**
12. **Stop before Publish.** The user confirms every publish, every time.

## Engine notes (post-rebuild, May–Jul 2026)

The generation pipeline was rebuilt: multi-stage (thinking → design → page planner → section planner → parallel section generation), per-section "skills" (Hero, Nav, CTA, FAQ, Pricing, Testimonials, etc.), a style normalizer, and a rebuilt image pipeline (GPT + Gemini backends, split/cutout/collage compositions). Practical implications:
- First-generation quality is much higher — expect fewer iteration rounds on layout/design; focus iterations on copy and offer specifics.
- **Clone-with-changes is now first-class**: "Clone [URL] but change X" threads the customization through vision analysis and honors it in the output. Still style inspiration for legal purposes, not a pixel-perfect 1:1.
- Streaming shows per-section progress — use those cards as your health signal.
- Roadmap: multi-page generations, deeper integrations.

## High-converting prompt template (one paragraph, adapted per niche)

> "Build a high-converting lead generation page for [Business], a [niche] company serving [city/area]. Target audience is [who + pain + urgency]. Hero headline '[benefit + risk-reversal headline]' with a subheadline offering [specific $ offer], a [CTA label] button, and a click-to-call phone number. Include a trust bar ([license / review count / 24-7 proof points]), a services grid ([services list]), a why-choose-us section with [flat-rate pricing / on-time promise / satisfaction guarantee], three testimonials from [area] customers, a [$X offer] section with urgency, a lead capture form ([fields]) with button text '[action CTA]', a 5-question FAQ, and a final CTA footer. Copy style: direct response, benefit-first headlines, specific numbers, risk reversal, short punchy sentences. Design: [primary color] with [accent color] CTAs, clean white background, modern and mobile-first."

Direct-response DNA: specific dollar offer, risk reversal in the headline, proof stacked early, ONE conversion goal per page, CTA copy that says what happens ("Book My Service Call", never "Submit").

---

# PART B — WORKFLOW AI BUILDER LOOP (docs-verified 2026-07-17)

Workflow AI Builder generates complete workflows (triggers + actions + structure) from a plain-language prompt. Rebuilt April 2026 as a streaming, context-aware copilot; targeted-edit precision upgrade shipped July 10, 2026. No AI credits consumed. Labs feature — if missing, enable at Agency Settings → Labs (agency) or check Automations → Global Workflow Settings → Workflow AI (sub-account).

## Entry points (three)

1. **Automation → Workflows → "Build using AI" button** — opens a prompt modal (with voice dictation and template chips: Lead nurturing / Form automation / Email campaigns), then drops you into the builder with the generated workflow.
2. **Prompt box inside a blank workflow builder** (Create Workflow → Start from Scratch).
3. **AI chatbot sidebar inside the builder** — also handles edits to existing workflows.

If you trigger a build on a canvas that already has a workflow, the AI asks whether to start fresh or edit what's there — read the prompt and answer deliberately.

## Build loop

1. Navigate to **Automation → Workflows** in the confirmed sub-account. Screenshot.
2. Click **Build using AI**. Write the prompt with: trigger, channels, timing, conditions, content type, workflow name, and any cross-step data use. Start with action verbs: Send, Notify, Create, Update, Wait, Check if. Name the exact form in quotes.
3. Submit. **Watch the streaming progress card.** Healthy = steps advancing; done = workflow renders on canvas with a summary card listing Triggers and Actions, and the tab title changes to the workflow name.
4. **Clarifying Agent**: the AI may ask up to 3 questions when trigger/channel/timing is unspecified. Answer from the given options or type a custom response — don't skip unless the detail truly doesn't matter (skipping lets the AI guess). A fully specified prompt skips it entirely — a detailed brief generated with zero questions in a field test.
5. **Open the error/To-Do panel — the circled-check icon in the left rail.** This is non-negotiable (see "Hallucinated references" below). Work it until it reads **"Zero errors."**
6. **Verify every trigger and action config manually** (click through each node, screenshot). AI cannot test workflows — docs are explicit. Autosave applies to AI-generated workflows and AI edits.
7. **Test with a test contact** (Test workflow button, top right). Use GHL MCP to verify the contact/conversation side if connected — but see the MCP scoping caveat in Known limitations.
8. **Stop before Publish.** The workflow stays on the Draft toggle (top right). The user confirms.

## Hallucinated references — the #1 Workflow AI failure (field-verified 2026-07-17)

Workflow AI writes correct *structure* but **invents references to entities that don't exist**. The workflow looks perfect on the canvas and is completely inert. Every one of these was caught by the error panel in a single field test:

| What it wrote | Error | Reality |
|---|---|---|
| Trigger filter "Form is: *[your form name]*" | **"Form not found"** | The chip displayed the right name but held no valid form ID |
| Action "Add tag: keystone-lead" | **"Referenced Tag does not exist or does not belong to this location"** | Tag was never created — the picker showed "No Data" |
| `{{form.service_needed}}`, `{{form.urgency_level}}` | *(silent — no error)* | Real tags are `{{contact.service_needed}}` / `{{contact.urgency_level}}`. Form fields become **Contact → Custom Fields**, never a `form.` namespace |

**Fixes:**
- **Phantom form:** open the trigger → remove the filter chip → re-pick the form from the dropdown (binds the real ID) → Save trigger. **Close the dropdown before clicking Save** — the option list overlaps the Save button and you'll select a random form instead.
- **Phantom tag:** open the action → remove the chip → retype the tag → click **"+ Add New tag (name)"** to actually create it → Save action.
- **Merge fields:** never trust AI-written merge tags. Insert them with the **Custom values picker** (tag icon in the message toolbar) and search — it only offers fields that exist. This is also the fastest way to discover the real field name.

Fixing one error often reveals the next. Re-check the panel until it says Zero errors.

## Internal notification ≠ email

Asked for "an internal email to the owner," the AI used the **Internal notification** action with Type = **Notification** — an in-app notification, not an email to the address specified. If the client needs an actual email:
- Set **Type of notification → Email**, then **To User Type → Custom email**, then fill **To Custom Email**.
- **Switching the type WIPES the Subject and Message.** Re-enter both afterward. Set the type FIRST, then write the content, and you'll only do it once.
- **From Name / From Email left blank = account defaults.** Fine for drafts; confirm before publish.
- Other To User Types: All users, Assigned owners, Particular user.

## Editing arsenal (use instead of manual node surgery)

- **Conversational edits**: add/remove/replace/move/modify actions and triggers, rename the workflow, adjust settings, link data across steps. If/Else and Wait actions are fully editable by chat — branch logic, AND/OR operators, timeout branches, wait types.
- **Compound requests in one turn**: "rename, add a 24h wait, turn off re-entry" — executes all at once.
- **Conversational memory**: "actually make that 48 hours" works — it remembers session context.
- **Targeted + bulk edits (July 10, 2026)**: name exactly which actions/triggers to change and it touches only those; bulk copy rewrites across many actions, bulk pipeline stage swaps, bulk From Name/From Email — one instruction each.
- **Point and Edit**: for workflows with 10+ actions or ambiguous names — click Point & Edit under the AI panel's input, select nodes (click, multi-click, or Shift+drag), then describe the change. It applies ONLY to the selection.
- **Chat Mode**: brainstorm/plan without building. Design the plan with the AI, then flip Chat Mode off (or click "Continue in Build Mode") to execute. Use this for complex multi-branch automations before committing.
- **Write with AI**: inside an email/notification action, generates the message body in place.

## Workflow browser-driving notes

- The workflow canvas is more DOM-readable than the funnel canvas, but screenshots remain the truth for node states and the streaming card.
- The sidebar survives close/reopen — session history persists. Don't panic if the panel gets closed mid-build.
- The AI never names the platform (white-label safe) — fine to run in client-facing accounts.
- Learn Mode answers "how does X work" questions with real-time streaming — usable mid-build for capability checks.
- Left rail icons include the error/To-Do panel (circled check), execution history, and the AI panel (sparkle) — the error panel is the one that matters.

---

# PART C — FULL-STACK BUILD (funnel + workflow end-to-end)

When the user says "build the whole thing," the order is (revised 2026-07-17 from a full field run):

1. **Confirm sub-account + offer details + brand** (ask one focused question if anything's ambiguous — never assume the business).
2. **Build the real form first** (Rule Two). Doing this before the funnel means the AI's fake form is the only thing you throw away, and the workflow's form picker will find a real form to bind.
3. **Funnel** (Part A). Get the page approved visually, then swap the fake form for the real element.
4. **Test the form** — submit on the preview, confirm the contact lands. Do this BEFORE the workflow; a workflow triggered by a dead form can never fire.
5. **Workflow** (Part B), naming the exact form in the prompt — then fix every hallucinated reference until Zero errors.
6. **End-to-end test**: submit the form → confirm contact created → confirm workflow fired (Enrollment history) → verify email content rendered with real values, not raw `{{merge.tags}}`.
7. **Report to the user** with what was built, what's in draft, and what needs their publish confirmation. Never publish either piece yourself.

## The standard local-business automation recipe

For nearly every service-business client, the baseline form-fill automation is:
1. **Add a tag** (the lead-source tag — e.g. `keystone-lead`)
2. **Send the lead a confirmation email** (thanks them by first name, sets the callback expectation, restates the offer, repeats the phone number)
3. **Send the client an internal email** — "you have a new lead" — with name, phone, email, and the form's custom fields so the team can dispatch

Prompt all three in one paragraph and Workflow AI structures it correctly on the first pass. The structure is reliable; the *references* are not.

## Forms, calendars, automations in AI Studio (reference only)

- Forms/calendars are NOT auto-connected in AI Studio. Ask the chat to "Connect the form to my CRM"; if name lookup fails, paste the Form ID.
- Submissions land in Contacts and Sites → Forms → Submissions → External Forms.
- Workflow trigger for AI Studio pages: **External Tracking Event** → event "Form submission" → filter by Domain / External Form.

---

## Browser-driving notes (hard-won, funnel builder)

- The funnel canvas is iframe/canvas-heavy: `get_page_text` returns nothing and `read_page`/`find` often see a different layer — `find` on the builder has returned the Theme Builder tree instead. **Screenshots are the source of truth.** Zoom into regions to read small text.
- `wait` maxes at 10s and `scroll_amount` at 10 per call — batch multiple calls. `repeat` on scroll does not reliably repeat; issue separate calls.
- If the user resizes the window mid-session, all coordinates shift — re-screenshot before every click after any viewport change.
- **The Ask AI panel no longer resets to Assist on refresh** (corrected 2026-07-17). It keeps Build mode, full chat history, and any attached element chip. The changelog's "session continuity" is real.
- **BUG — an attached element chip silently freezes the Build input.** If you click a page element, its name (e.g. `emergency-footer`) becomes a chip above the prompt box and the box stops accepting text — the send button stays greyed and keystrokes leak to the canvas as shortcuts (they will open Layers / Quick Add panels). **Fix: click the chip's × to detach it**, then the input focuses (purple border) and accepts text. Refreshing does NOT clear the chip.
- Stop clicks don't always register while the pipeline loops — refresh is the reliable escape hatch.
- After success: autosave ON + page renamed + funnel auto-renamed in the Funnels list are your completion signals.
- Deep-linking to GHL sub-pages by guessing URLs is flaky (it can bounce you to the agency dashboard or a blank page). Navigate to a known-good page and click through the nav instead.
- Rich-text/label fields often ignore canvas typing — look for the equivalent field in the right-hand settings panel and edit there.

## Page-builder toolbar (top-left icons)

Left to right, the icons you'll actually use: **+ (Quick Add / elements)**, **Ask AI**, **Layers**, and further along a **SEO / page metadata** icon. Funnel AI auto-generates the SEO title and description — open that panel to review or clear them before any publish conversation. The Quick Add panel's left rail is where **Forms And Surveys**, Buttons, Images, Countdown Timers, Social Media Icons, and Prebuilt Sections live; this is your escape hatch whenever the AI can't build an element natively (which, for forms, is always).

## Known limitations (verified July 2026)

- **GHL MCP cannot create funnels, sites, or workflows** — no endpoints for it. Browser is the only path. (MCP also lacks notes, tags, call transcriptions.)
- **The MCP is scoped to ONE location.** Its token binds to a single sub-account, so MCP contact lookups silently return zero results when you're building in a different sub-account — which looks identical to "the form is broken." Field-verified: contacts visible in the Contacts UI returned nothing via MCP search. **When MCP and the UI disagree, trust the UI**, and confirm which location the MCP is pointed at before using it as a verification tool.
- **Funnel AI cannot build real forms** (Rule Two) — Custom Code only. Same for anything else it can't natively render: add it from the Quick Add panel or build it elsewhere in GHL and insert it.
- **Workflow AI hallucinates entity references** (forms, tags, merge fields) — see Part B. The error panel catches forms and tags; bad merge tags fail silently.
- AI Studio projects can't move into standard Funnels/Websites builders. Ever. No order forms/payments in AI Studio (roadmap). Free until Sept 1, 2026, then usage pricing.
- Multi-line prompts hang Funnel AI Build mode (Part A rule 4). Suspected cause: the parser treats structured lists as a "reproduce this website" spec.
- Workflow AI is beta: manual review required, complex configs may need hand-adjustment, AI cannot test workflows. Generation ran ~36s in a field test vs the "under 30s" claim — close enough; don't treat 40s as hung.
- Funnel AI + Workflow AI are Labs features — UI moves fast. If the screen doesn't match this doc, screenshot, adapt, and note the drift so this skill gets updated.

## What the AI is genuinely good at (don't over-correct)

Field test, HVAC/plumbing lead page, one prose prompt, ~5 minutes: used the supplied headline verbatim, built all 9 planned sections in order, invented testimonials from **real Bergen County towns** (Paramus, Hackensack, Teaneck) each tied to a specific problem, listed 12 real towns in the footer, generated a branded service van in the exact navy + orange palette, wrote unprompted risk reversal ("or your service call is free"), and added a "here's exactly what happens next" expectation list. Copy and design quality are strong — spend your review time on **wiring and references**, not rewriting the copy.

## Sources

- [Funnel & Website AI](https://help.gohighlevel.com/support/solutions/articles/155000006713-funnel-website-ai) (official support doc)
- [Workflow AI Builder: Generate and Edit Workflows with AI](https://help.gohighlevel.com/support/solutions/articles/155000006100-workflow-ai-builder) (official, mod. May 12, 2026)
- [AI Studio in HighLevel](https://help.gohighlevel.com/support/solutions/articles/155000007587-ai-studio-in-highlevel) (official)
- [Connect Forms, Calendars and Automations in AI Studio](https://help.gohighlevel.com/support/solutions/articles/155000007599-connect-forms-and-calendars-in-ai-studio) (official)
- [Changelog: AI Builder in workflows now more powerful](https://ideas.gohighlevel.com/changelog/ai-builder-in-workflows-now-more-powerful) (Apr 2026 rebuild)
- [Changelog: Funnel & Website AI — Enhanced Page Generation & Clone](https://ideas.gohighlevel.com/changelog/funnel-website-ai-enhanced-page-generation-clone) (engine rebuild)
- [Changelog: AI Studio Updates](https://ideas.gohighlevel.com/changelog/ai-studio-updates)
- [Changelog: Introducing Brand New Funnel & Website AI](https://ideas.gohighlevel.com/changelog/introducing-brand-new-funnel-website-ai)
- [HighLevel MCP Server guide](https://help.gohighlevel.com/support/solutions/articles/155000005741-how-to-use-the-highlevel-mcp-server) + [LeadConnector MCP docs](https://marketplace.gohighlevel.com/docs/other/mcp/) (MCP scope/limits)
