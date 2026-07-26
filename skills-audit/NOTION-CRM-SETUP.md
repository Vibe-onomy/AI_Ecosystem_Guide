# Client Tracking Setup — paste this prompt into a claude.ai chat

Copy everything between the lines into a regular claude.ai chat (with the
Notion connector on) and approve the prompts it shows you.

---

Please create two new Notion databases for my client tracking system, then
link them. Create them under my workspace (I'll move them where I want
after).

DATABASE 1 — "Clients — Vibe Align CRM"
Description: System of record for live customers and active prospects
across Vibe Align consulting, SUDSync, and Vixta Voice. Updated after
every call.
Properties:
- Name (title)
- Organization (text)
- Stage (select): prospect / discovery / proposal sent / active client /
  delivery / renewal / closed lost / past client
- Products (multi-select): SUDSync / Vibe Align Consulting / Vixta Voice
- Primary Contact (text)
- Contact Email (email)
- State (text) — note: this determines call-recording consent rules
- Recording Consent (select): on file / verbal only / not yet
- Proof Consent (select): named OK / de-identified only / none
- Next Step (text)
- Next Step Date (date)
- Fee / MRR (number, dollar format)
- Source (select): referral / content / outreach / webinar / other
- Notes (text)
- Created (created time)
- Last Touched (last edited time)

DATABASE 2 — "Calls & Transcripts"
Description: Every recorded client/sales call. Fed by call recordings;
processed by the call-debrief skill into CRM updates, follow-ups, VOC
quotes, and proof candidates.
Properties:
- Name (title) — format: YYYY-MM-DD Client — call type
- Client (relation to "Clients — Vibe Align CRM", two-way, synced name
  "Calls")
- Call Type (select): discovery / sales / delivery / check-in / other
- Date (date)
- Consent Announced (checkbox)
- Contains PHI (select): no / flagged — quarantine
- Debrief Status (select): raw / debriefed / follow-up sent
- Transcript (text or file — paste transcript or attach export)
- Key Quotes (text) — VOC candidates from call-debrief
- Proof Candidate (checkbox)
- Action Items (text)

After creating both, add a board view on the Clients database grouped by
Stage, and a table view on Calls & Transcripts sorted by Date descending.

---

## After it's created

1. Point the call-debrief skill at these: when debriefing, tell Claude
   "update the CRM block for [client] in my Clients database" and it can
   write the row (in claude.ai chats where Notion edits are approved).
2. Your existing "saves" database entries labeled social proof: relate or
   migrate the client-specific ones to the matching client row so proof,
   consent status, and the source call live together.
3. Add a row to the Codi Skills & Agents Directory for call-debrief once
   the skill is installed.
