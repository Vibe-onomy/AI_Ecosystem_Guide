# Client Tracking — final scope (per Mikke, July 2026)

System of record confirmed:
- **👥 Vixta Clients** (Vixta Hub) — clients, packages, MRR, tax-year
  revenue formulas. Already strong; do not restructure.
- **Sales Call Intelligence** — sales + discovery call transcripts flow in
  via Notion's meeting transcription. (Not currently visible to the Claude
  Notion connector — share the page with the connector if Claude sessions
  should read/write it.)
- Consent: handled by Notion's transcript flow at recording time; no CRM
  consent fields needed.

## The one approved change

Paste into a claude.ai chat with Notion connected:

---

Please update my Notion database "👥 Vixta Clients" (inside the Vixta Hub
page) by ADDING two properties, changing nothing else — no existing
properties, formulas, or templates:

1. "Next Step" (text)
2. "Next Step Date" (date)

---

Optional, recommended when convenient: a two-way relation between Sales
Call Intelligence and 👥 Vixta Clients (property "Client" on the calls
side, "Calls" on the client side) so each client row shows its call
history. Ask for it in the same chat if wanted.

## Useful views after the fields exist

- Vixta Clients filtered: Next Step Date ≤ today → the "what do I do this
  morning" list
- Vixta Clients filtered: Next Step empty AND Status = Lead/Onboarding →
  stalled deals needing a decision
