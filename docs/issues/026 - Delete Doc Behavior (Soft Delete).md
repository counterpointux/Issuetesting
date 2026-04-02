---
title: Delete Doc Behavior (Soft Delete)
status: Open
priority: Medium
type: Design
area: Review Documents Wizard
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/24/26 (Original #84)*

How Delete Doc works in Clear Docs: Clear Docs uses soft delete exclusively. When a document is "deleted," it is marked with IsTrash = true in the database and moved to the Recycle Bin. There is no permanent/hard delete available to users. Trashed documents remain in the database indefinitely — no auto-purge or retention policy.

**How It Works:**
- Right-click a document (or use the "More..." button) -> select "Move to Recycle Bin"
- Confirmation dialog appears: "Are you sure you would like to send the following documents to the Recycle Bin?"
- Document is marked with IsTrash = true
- A document version record is created with ActionType = MovedToTrash for audit
- Document disappears from the main tree
- A background Hangfire job syncs the deletion to BytePro/LOS

**Resolution:** Requirements.MD matches Clear Docs. XD NOTE: Original design intent was to follow Clear Docs approach to docs.
