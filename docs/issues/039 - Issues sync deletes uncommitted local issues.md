---
title: Issues sync deletes uncommitted local issues
status: Resolved
priority: High
type: Bug
area: Issues Panel
assigned: Unassigned
created: 2026-04-02
---

When the issues sync runs its "pull latest from origin/main" step before a write operation, it deletes local issue files that don't exist on the remote. This means any issue created locally but not yet pushed to main gets silently wiped.

Observed: Issue #38 was created via `/issues` but disappeared after a subsequent `/issues` command triggered the sync, which overwrote the local `docs/issues/` directory from `origin/main`.

The sync should preserve locally-created files that haven't been pushed yet, or at minimum push them before pulling.
