---
title: Upload Modal Close During Active Upload
status: In Progress
priority: Medium
type: Design
area: Upload Documents
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/13/26 (Original #45)*

When the user clicks Close while files are still pending or uploading, what should happen? Options considered:
1. Cancel in-progress uploads — abort the API calls, discard incomplete files, only keep completed ones
2. Warn the user — show a confirmation dialog ("Uploads are still in progress/have not started. Close anyway?") before closing
3. Let uploads continue in background (what was started, what was not started will be lost) — close the modal but let uploads finish silently
4. Prevent closing — disable Close/X while uploads are active

**Resolution (Design):**
- Warn the user with confirmation dialog
- Let uploads continue in background for what was started; what was not started will be lost
- 2/23: Need to make the "Close Anyway" not the primary button on the modal (switch buttons)
