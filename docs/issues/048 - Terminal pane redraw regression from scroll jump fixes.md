---
title: Terminal pane redraw regression from scroll jump fixes
status: In Progress
priority: High
type: Bug
area: Terminal
assigned: Unassigned
created: 2026-04-01
---

Some of the scroll jump fixes introduced a regression where terminal panes don't reliably redraw their content in Claude Code sessions. The terminal rendering can become stale or incomplete, likely due to the scroll-preserving fit utility or related changes interfering with xterm.js redraw cycles.
