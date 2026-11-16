# MAJU Partnerships CRM — Static HTML/JavaScript edition

No React, Vite, TypeScript, npm, or build step. Works on GitHub Pages.

## Deployment to a new GitHub repository

1. Create a new GitHub repository. Upload **the contents** of this folder to the repository root.
2. Repository Settings → Pages → Build and deployment → **Deploy from a branch**, branch `main`, folder `/ (root)` → Save.
3. Your site appears at `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/` after Pages publishes.
4. Future edits: `git add -A && git commit -m "Update CRM" && git push`.

## Connect the SAME Firebase database as your old CRM

1. Open `config.js` and paste the Firebase Web App configuration from Firebase Console → Project settings → Your apps. Do **not** paste service-account credentials.
2. Authentication → Settings → Authorized domains: add `YOUR-USERNAME.github.io` (domain only).
3. Keep your existing Firestore `members/{uid}` approvals and the included `firestore.rules` structure. The data paths are the same as the React CRM: `crm/main/partners/{id}`, `crm/main/cases/{id}`, `crm/main/meetings/{id}`.
4. On the new website, sign in using an existing approved Firebase email/password account.
5. Verify the same partner records appear. Test on two devices before retiring the React version.

The Firebase configuration is public browser configuration; database security relies on Firebase Auth and Firestore rules. Never publish service-account keys.

If `config.js` is blank, the CRM runs in localStorage demo mode. Each browser has separate data. Import `adventure-time-demo.json` using Partners → Import JSON to test.

## Google Sheets CSV

Download a sheet as File → Download → Comma-separated values (.csv). In Partners → Import CSV, choose partners/cases/updates/meetings, upload the CSV, map columns, preview, and import. Partners and cases match by name; updates and meetings append and can duplicate if imported twice. Import organisations before cases, then updates and engagements. Export a JSON backup first.

## What changed from React

This is a **new implementation** of the key workflows, not a byte-for-byte conversion. Includes dashboard, partners, case management, dated discussion updates, engagement calendar, downloadable text briefs, clickable links, CSV field mapping, JSON import/export, help, Firebase email/password login and realtime Firestore subscriptions. The calendar and CSV converter are simpler than their React equivalents; verify the workflows with dummy data before production use. Saved mapping presets and administrator account management are not implemented.

## Data safety

JSON import **replaces** the shared database when Firebase is configured. Firestore writes are per record; simultaneous edits to the same record can overwrite each other. Use backups and test with fictional data. Do not use real sensitive records until you've verified rules and approval behavior.

## Testing locally

Use a local static HTTP server (ES modules may not load from `file://`):

```sh
python3 -m http.server 5174
```

Open `http://localhost:5174`. To test Firebase login locally, add `localhost` under Firebase Authentication → Authorized domains if necessary.
