---
title: Standardize Button Styles Across Extension
status: Open
priority: High
type: Improvement
area: Extension UI
assigned: Unassigned
created: 2026-04-02
---

There are 5+ distinct button style variations in `moat.css` with inconsistent padding, font-size, height, and border-radius:

| Button | Padding | Font-size | Height | Border-radius |
|--------|---------|-----------|--------|---------------|
| Comment actions | `6px 14px` | `12px` | `32px` | `6px` |
| Moat actions | `6px` | `14px` | `32px` | `6px` |
| Tab buttons | `6px 10px` | `11px` | auto | `4px` |
| Bottom tab buttons | `8px 12px` | `12px` | auto | `8px` |
| Connect confirm | `6px 18px` | `12px` | `32px` | `6px` |
| Empty connect | `6px 20px` | `12px` | `32px` | `6px` |
| Modal buttons | `10px 20px` | `14px` | inherited | `6px` |

Define 2-3 button size tiers (small, default, large) and apply them consistently. Tab buttons in the bottom dock shouldn't differ from the sidebar tab buttons.
