---
title: Inconsistent Animation Timing and Easing
status: Open
priority: Low
type: Improvement
area: Extension UI
assigned: Unassigned
created: 2026-04-02
---

Animations use a mix of durations and easing functions with no shared pattern:

| Animation | Duration | Easing |
|-----------|----------|--------|
| Header notification | `0.4s` | `ease` |
| Toast notification | `0.3s` | `ease` |
| Floating card | `2.5s` | `cubic-bezier(0.25, 0.46, 0.45, 0.94)` |
| Settling card | `0.8s` (shadow: `1.2s`) | `ease-out` |
| Comment shake | `0.5s` | `ease-in-out` |
| Tab hover | `0.2s` | `ease` |

Consider defining a few timing tokens (e.g., `--moat-duration-fast: 0.2s`, `--moat-duration-normal: 0.3s`) and standardizing easing to reduce visual noise.
