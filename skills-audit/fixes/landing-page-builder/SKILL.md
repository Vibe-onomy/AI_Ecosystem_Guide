---
# ⚠️ SUPERSEDED (July 2026): merged into the Doser stack's Landing Page Designer + CRO Skill. Guardrails ported via STACK-INTEGRATION.md. Kept for history — do not install.
name: landing-page-builder
description: Turn any offer into a complete, deployable landing page — copy, structure, and build — in Mikke's Vibe Align voice. Use for lead magnet opt-in pages, webinar registration pages, sales pages, and service pages for Vibe Align consulting, SUDSync, or CADENCE. Trigger on "build a landing page," "make an opt-in page," "sales page for [offer]," "registration page," "squeeze page," "turn this offer into a page," or when perfect-webinar-builder needs its registration page built. Produces a draft page and preview deploy only — never a production deploy without explicit approval.
---

# Landing Page Builder — Vibe Align

One input (the offer), one output (a page that converts). This skill owns
the full chain: positioning → copy → structure → build → preview.

## Step 1 — Diagnose the page type

| Type | Goal | Length |
|---|---|---|
| Lead magnet opt-in | Email capture | Short: hook, 3 bullets, form |
| Webinar registration | Registrations (pairs with perfect-webinar-builder) | Short-medium: promise, 3 secrets teaser, urgency |
| Sales page | Purchase decision | Long-form: full offer stack |
| Service page | Book a call (Vibe Align consulting / SUDSync / CADENCE) | Medium: diagnosis-led |

If the offer itself is fuzzy, stop and pressure-test it against the ideal
client avatar first (ideal-client-avatar-builder project) before writing
a single headline.

## Step 2 — Copy (frameworks Mikke already sells with)

- **Donald Miller / StoryBrand:** customer is the hero, Mikke is the guide.
  The headline names THEIR problem, not the product.
- **Hormozi offer stack:** value equation, stack the deliverables, name the
  price anchor, risk reversal.
- **Voss:** the CTA is one clear ask. One page, one action. No competing
  buttons.
- **Voice:** Vibe Align — direct, witty, authority-forward, business-therapy
  framing (diagnose the real problem, prescribe the fix). Credibility comes
  from Mikke's 14 years inside behavioral health, including compliance and
  audit work — that expertise is fair game in bios and "who builds this"
  sections. But never attach compliance to the products as a promise: no
  "Compliance-ready," no "keeps you compliant," nothing implying the
  product or Mikke carries liability for the buyer's compliance. Products
  get factual statements only (HIPAA-compliant, BAA included, tracks
  regulatory updates).
- Every draft passes through the anti-slop rules before it's shown.

Section order for long-form: Hook (their problem, their words) → Diagnosis
(what's actually going on) → Prescription (the offer) → Stack (what's
included) → Proof (results, credentials — only what's true) → Objections
(top 3, answered plainly) → CTA (one action, repeated) → FAQ.

## Step 3 — Build

- Single-file responsive HTML (mobile-first), styled via theme-factory /
  brand palette; follow web-design-guidelines rules.
- SEO: meta title ≤60 chars, description ≤155, Open Graph tags (or hand to
  seo-meta-agent when available).
- Forms: placeholder action URL clearly marked `TODO` — never wire a live
  endpoint without the user naming it.

## Step 4 — CRO review (run on every page before it ships)

Score the draft against this checklist and fix what fails:

1. **5-second test:** does the above-the-fold view answer "what is this,
   who is it for, what do I do next" without scrolling?
2. **One CTA, repeated:** a single action, restated after each major
   section. No competing buttons, no "learn more" next to "book a call."
3. **Friction audit:** every form field must justify itself — name + email
   for opt-ins, nothing more. Each extra field costs conversions.
4. **Specificity beats adjectives:** swap every "transform/unlock/empower"
   for a number, a timeframe, or a named deliverable.
5. **Objection placement:** the top objection gets answered *before* the
   first CTA, not buried in the FAQ.
6. **Proof proximity:** a proof block (case-study-builder output) sits
   directly beside the claim it supports, not in a separate section.
7. **Mobile thumb test:** CTA reachable and readable on a phone; no
   horizontal scroll; text ≥16px.
8. **Speed sanity:** single-file page, compressed images, no external
   font/script dependencies that block render.

Report the score (pass/fix per item) with the draft — don't silently fix
copy the user has already approved; flag it.

## Step 5 — Ship (guardrailed)

- Deploy as a **Vercel preview** and return the link.
- Production deploys, custom domains, or connecting real form endpoints /
  payment links require the user's explicit go-ahead on the final version,
  in this conversation. No exceptions.

## Hand-offs

- Webinar assets beyond the registration page → perfect-webinar-builder
- Post-launch promotion → linkedin-hook-writer + vibealign-content
- A/B headline variants → generate 5, ranked, with reasoning
