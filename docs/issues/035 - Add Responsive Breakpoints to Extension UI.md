---
title: Add Responsive Breakpoints to Extension UI
status: Open
priority: Low
type: Improvement
area: Extension UI
assigned: Unassigned
created: 2026-04-02
---

`moat.css` contains zero `@media` queries. All widths are fixed:

- Sidebar: `320px` (won't fit on phones)
- Comment box: `300px` (could overflow on small viewports)
- Bottom dock: fixed `152px` height

The extension injects into any page, including mobile browsers. At minimum, add a breakpoint that collapses the sidebar into a full-width bottom sheet on narrow viewports.
