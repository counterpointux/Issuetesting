---
title: Replace Hardcoded Colors with Theme Variables
status: Open
priority: High
type: Bug
area: Theme System
assigned: Unassigned
created: 2026-04-02
---

Multiple components use hardcoded hex colors instead of CSS custom properties, breaking dark theme support.

**Affected components in `moat.css`:**
- Connect button: `#000000`, `#333333`, `#4B5563` (lines ~1185-1206)
- Modal danger button: `#DC2626`, `#B91C1C` (lines ~2252-2258) — should use `var(--moat-error)`
- Protocol indicators: `#00ff00`, `#ff0000` (lines ~2285-2290) — neon colors clash with theme
- Code preview border: `#007bff` (line ~2308) — not in design system
- Code change description: `#333` (line ~2338)
- Status card colors: `#007bff`, `#28a745`, `#ffc107` (lines ~2355-2367) — legacy Bootstrap palette

All of these should reference the existing `--moat-*` CSS variables so they respond correctly to light/dark theme toggling.
