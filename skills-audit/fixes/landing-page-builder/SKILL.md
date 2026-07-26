---
name: landing-page-builder
description: Turn any offer into a complete, deployable landing page — copy, structure, and build — in Mikke's Vibe Align voice. Use for lead magnet opt-in pages, webinar registration pages, sales pages, and service pages for Vibe Align consulting, SUDSync, or Vixta Voice. Trigger on "build a landing page," "make an opt-in page," "sales page for [offer]," "registration page," "squeeze page," "turn this offer into a page," or when perfect-webinar-builder needs its registration page built. Produces a draft page and preview deploy only — never a production deploy without explicit approval.
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
| Service page | Book a call (Vibe Align consulting / SUDSync / Vixta Voice) | Medium: diagnosis-led |

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
  framing (diagnose the real problem, prescribe the fix). Credibility line
  where relevant: "Clinician-built. Compliance-ready."
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

## Step 4 — Ship (guardrailed)

- Deploy as a **Vercel preview** and return the link.
- Production deploys, custom domains, or connecting real form endpoints /
  payment links require the user's explicit go-ahead on the final version,
  in this conversation. No exceptions.

## Hand-offs

- Webinar assets beyond the registration page → perfect-webinar-builder
- Post-launch promotion → linkedin-hook-writer + vibealign-content
- A/B headline variants → generate 5, ranked, with reasoning
