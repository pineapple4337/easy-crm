# MAJU CRM — Google Sheets CSV export

Changed: `app.js`, `index.html`.

Adds four export buttons in Help & administration → Importing and exporting. Each exports a flat, UTF-8 BOM CSV with friendly column headings: Partners, Cases, Conversations (one row per discussion), and Engagements. Partner IDs and Case IDs are retained for cross-sheet references. Long notes are CSV-quoted; potentially dangerous spreadsheet formulas are neutralised. No Firestore writes or changes to stored data. `index.html` increments the JavaScript cache version.

## Suggested Google Sheets setup

Create a spreadsheet with four tabs: Partners, Cases, Conversations, Engagements. For each tab, use File → Import → Upload → Replace current sheet (not the entire spreadsheet). Then freeze row 1, turn on Data → Create a filter, enable alternating colours, wrap text for Notes/Objective, format date columns as dates, and use conditional formatting for Tier 1 / overdue cases. Keep IDs as plain text. URLs can be clicked when Google Sheets recognises them.

CSV exports are snapshots and not a lossless CRM backup: use Export backup (JSON) for restoration. No automatic syncing with Google Sheets.
