---
name: call-debrief
description: Process a client or sales call transcript into structured business assets — CRM update, action items, follow-up draft, proposal inputs, voice-of-customer language, and proof candidates. Use after any recorded call when the user says "debrief this call," "process this transcript," "here's the transcript from my call with [name]," or pastes/links a transcript. Pairs with sales-call-prep (before the call) the way a clinical note pairs with an intake. Never sends follow-ups or updates external systems without per-item approval.
---

# Call Debrief — one transcript in, six assets out

Every recorded call is paid-for business intelligence. This skill makes
sure none of it evaporates.

## Input

A transcript (pasted, file, or Notion meeting-note link) plus who the call
was with and the call type: discovery / sales / delivery / check-in.

## Output — always in this order

1. **CRM update block** — ready to paste into the client's row/page:
   stage, products discussed (SUDSync / Vibe Align consulting / Vixta
   Voice), budget signals, decision process, named stakeholders, next step
   with date.
2. **Action items** — theirs and Mikke's, each with an owner and a date.
   Flag anything Mikke promised on the call; those are commitments, not
   suggestions (Leila Hormozi rule: deliver what you promise).
3. **Follow-up draft** — in Mikke's voice, referencing specifics from THIS
   call, one clear next step. Draft only; never send.
4. **Proposal inputs** — if the call was discovery/sales: their problem in
   their exact words, scope signals, objections raised, fee context.
   Formatted as the input block proposal-builder expects.
5. **VOC entries** — verbatim quotes worth keeping: frustrations, desired
   outcomes, objection language, words they use for their problems. Tagged
   for the customer-voice-research language bank. First-party quotes beat
   scraped Reddit threads every time.
6. **Proof candidates** — any stated result, win, or praise → flag for
   case-study-builder with consent status DRAFT-ONLY until written
   permission exists.

## Compliance guardrails (non-negotiable)

- **Consent check first.** If the transcript doesn't show recording was
  announced/consented, flag it before processing. Mikke sells compliance;
  her own records must model it.
- **PHI firewall.** If a transcript contains patient-level information
  (names, identifiable treatment details from a BH program's clients),
  STOP: excerpt nothing patient-level into CRM/VOC/proof outputs, flag the
  section, and recommend the source recording live only in a
  BAA-covered system. Business intelligence never includes PHI.
- Client-identifying details follow case-study-builder's de-identification
  rules the moment they leave the CRM context.
- This skill updates nothing external on its own: CRM blocks, follow-ups,
  and VOC entries are drafts until Mikke approves each.

## Hand-offs

- Before the next call with this client → sales-call-prep (feed it the CRM
  block)
- Proposal requested → proposal-builder (feed it output #4)
- Proof with consent → case-study-builder
- Patterns across many calls → customer-voice-research (quarterly: "what
  are my actual clients saying" beats "what is Reddit saying")
