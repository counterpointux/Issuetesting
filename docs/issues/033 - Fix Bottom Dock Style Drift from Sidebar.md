---
title: Fix Bottom Dock Style Drift from Sidebar
status: Open
priority: Medium
type: Bug
area: Extension UI
assigned: Unassigned
created: 2026-04-02
---

The bottom dock position has styling overrides that cause it to visually drift from the left/right sidebar versions:

- **Tab buttons**: `12px` font / `8px 12px` padding / `8px` radius in bottom, vs `11px` font / `6px 10px` padding / `4px` radius in sidebar
- **Icon sizes**: Right sidebar overrides `.float-icon` to `10px` (from the default `12px`), inconsistent with bottom dock
- **Duplicated rules**: Several selectors are repeated for `.float-moat-bottom` variants that could share styles with the sidebar

The three dock positions should share a single base style with only layout-specific overrides (direction, shadow direction, width vs height).
