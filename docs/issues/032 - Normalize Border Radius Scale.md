---
title: Normalize Border Radius Scale
status: Open
priority: Medium
type: Improvement
area: Extension UI
assigned: Unassigned
created: 2026-04-02
---

Border radius values are scattered with no consistent scale: `4px`, `6px`, `8px` across components.

| Element | Current Radius |
|---------|---------------|
| Tab button | `4px` |
| Comment input, tab group, action buttons | `6px` |
| Comment box, task cards | `8px` |

Define CSS variables for a radius scale (e.g., `--moat-radius-sm: 4px`, `--moat-radius-md: 6px`, `--moat-radius-lg: 8px`) and apply them consistently. This makes future adjustments a single-line change.
