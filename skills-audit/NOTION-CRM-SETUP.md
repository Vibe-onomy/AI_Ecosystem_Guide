# Client Tracking — extend what exists (revised after reviewing Vixta Hub)

Original version of this doc proposed two new databases. Withdrawn: the
**👥 Vixta Clients** database (in Vixta Hub) already does the revenue side
better than the generic proposal — Status pipeline (Lead → Onboarding →
Active → Paused → Churned), Plan tiers (Catch/Core/Clear/Complete), Setup
Fee, Monthly MRR, Maintenance + Compliance Fee, Annual Revenue and Tax
Year Revenue formulas, GHL subaccount, portal relations, and a Discovery
Call page template. Do not duplicate it.

What it's missing is everything the call-recording workflow needs. Paste
the prompt below into a claude.ai chat (Notion connector on) to close the
gaps.

---

Please update my Notion database "👥 Vixta Clients" (inside the Vixta Hub
page) by ADDING these properties. Do not change or remove any existing
properties, formulas, or templates.

1. "State" (text) — client's US state; determines call-recording consent
   rules
2. "Recording Consent" (select): on file / verbal only / not yet
3. "Proof Consent" (select): named OK / de-identified only / none
4. "Next Step" (text)
5. "Next Step Date" (date)
6. "Source" (select): referral / content / outreach / webinar / other
7. "Calls" (relation) — link to my sales analysis database that holds my
   sales and discovery call transcripts [I'll point you at it — ask me
   for the link if you can't find it by searching "sales analysis"]

Then, in my sales analysis / call transcripts database, ADD these
properties if they don't already exist (again, change nothing that's
already there):
1. "Client" (relation back to 👥 Vixta Clients, two-way with the "Calls"
   property above)
2. "Call Type" (select): discovery / sales / delivery / check-in / other
3. "Consent Announced" (checkbox)
4. "Debrief Status" (select): raw / debriefed / follow-up sent

---

## Why these specific fields

- **State + Recording Consent:** MN is one-party consent, but prospects in
  CA/WA/FL etc. are all-party states. The universal fix is announcing the
  recording every time; the field keeps the record.
- **Proof Consent:** feeds case-study-builder's NAMED / DE-IDENTIFIED /
  DRAFT-ONLY gate directly from the client row.
- **Next Step + Date:** the one thing every CRM needs and most Notion
  client lists lack — makes "stalled deals" a filterable view.
- **Calls relation + Debrief Status:** transcripts stop floating free;
  "raw" calls become a to-process queue for the call-debrief skill.

## Notes

- SUDSync and Vibe Align consulting clients: replicate this pattern when
  those pipelines have live customers — same fields, per-product hub, or
  promote Vixta Clients to a shared Clients DB with a "Product"
  multi-select. Decide when it's real, not before.
- Mikke confirmed sales/discovery calls contain no PHI. The call-debrief
  skill's PHI firewall stays in place anyway — it matters for *delivery*
  calls with active BH clients, where a client may describe a patient
  situation mid-call.
