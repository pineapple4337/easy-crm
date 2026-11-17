# MAJU CRM - Data management update

- `app.js`: Removed the Handover checklist from Help. Added Data management panel with backup export and guarded Clear all CRM data action. In Firebase mode deletes partner, case and meeting documents in batches, leaving `members` and Authentication untouched. In local mode clears only the local CRM data.
- `index.html`: Cache-busts app.js on mobile and desktop.

**Warning:** Deletion is permanent without a previously exported backup. Any approved member can perform this operation under current Firestore rules. Consider admin-only permissions before real team use.
