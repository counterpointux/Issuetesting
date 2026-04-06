---
title: Refactor global tooltip CSS to remove position relative
status: Open
priority: Medium
type: Improvement
area: Global UI
assigned: Unassigned
created: 2026-03-30
---

The global `[data-tooltip]` CSS rule in `src/styles/global.css` sets `position: relative` on any element with a `data-tooltip` attribute. This breaks absolutely positioned elements that rely on a specific ancestor as their containing block.

**Current problem:** The resume button on issue rows uses `position: absolute` anchored to `.issue-item-header` (which has `position: relative`). Adding `data-tooltip` to the button forces `position: relative` on it, which overrides `position: absolute` and breaks the consistent right-edge positioning we achieved by removing `position: relative` from `.issue-row-inner`.

As a workaround, the resume button currently uses the native browser `title` attribute instead of the styled `data-tooltip` tooltip.

**Desired outcome:** Refactor the tooltip system so it doesn't require `position: relative` on the tooltip-bearing element. Possible approaches:

1. Use a JS-based tooltip that renders a portal (positioned via `getBoundingClientRect`) — avoids any CSS position side effects.
2. Use `position: fixed` for the `::after` pseudo-element and calculate placement with CSS custom properties set via a lightweight JS handler.
3. Create an opt-in variant class (e.g., `data-tooltip-fixed`) that doesn't set `position: relative`, for use on elements that already have explicit positioning.

**Files involved:**
- `src/styles/global.css` (lines 134–161) — tooltip CSS rules
- `src/components/Issues/Issues.css` — `.issue-resume-btn` positioning
- `src/components/Issues/GitHubIssuesView.tsx` — resume button (currently uses `title`)
- `src/components/Issues/IssueRow.tsx` — resume button (currently uses `title`)
