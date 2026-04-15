---
title: Parallel execution dashboard
status: Open
priority: Medium
type: Feature
area: Sessions
assigned: Unassigned
created: 2026-03-27
---

A birds-eye view of all active Claude sessions across projects.

- Dedicated dashboard view (sidebar or keyboard shortcut) showing all running sessions in a compact card layout
- Each card shows: project name, attached issue, current tool being used (from title detection), session duration, activity indicator
- Activity states: thinking, executing a tool, waiting for user input (`Y/n` prompt), idle at prompt
- Click a card to jump directly to that session's terminal pane
- Cards color-coded or grouped by project
- Build a shared `SessionStateDetector` service that classifies PTY output into states — reusable by notifications and queue system
- Could be a panel overlay (like quick switcher) or a first-class view