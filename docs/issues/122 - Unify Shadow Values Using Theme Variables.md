---
title: Unify Shadow Values Using Theme Variables
status: Open
priority: Medium
type: Bug
area: Theme System
assigned: Unassigned
created: 2026-04-02
---

Sidebar shadows are hardcoded `rgba(0, 0, 0, 0.1)` while other components correctly use `var(--moat-shadow)` / `var(--moat-shadow-lg)`.

**Hardcoded (should use variables):**
- Right sidebar: `-2px 0 12px rgba(0, 0, 0, 0.1)`
- Left sidebar: `2px 0 12px rgba(0, 0, 0, 0.1)`
- Bottom dock: `0 -2px 12px rgba(0, 0, 0, 0.1)`

**Already using variables (correct):**
- Comment box: `0 4px 24px var(--moat-shadow-lg)`
- Action buttons: `0 1px 2px var(--moat-shadow)`

Migrate the sidebar shadows to use theme variables so they adapt in dark mode.
