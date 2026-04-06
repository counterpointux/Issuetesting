---
title: Make Composer the primary terminal input with output-only terminal
status: Open
priority: Medium
type: Feature
area: Terminal
assigned: Unassigned
created: 2026-04-02
---

Suppress direct keyboard input to the terminal pane and make the PaneComposer the primary (and only) way to send input to Claude. The terminal becomes an output-only display.

### Motivation

The Composer provides a better editing experience — multi-line, Cmd+Enter to send, image paste, voice input. Making it the default input removes the awkward dual-input model where users aren't sure whether to type in the terminal or the Composer.

### Implementation

Use xterm.js `disableStdin` option to make the terminal output-only. All input routes through the PaneComposer, which already sends text to the PTY via `terminal-input` events.

### Open question: slash command highlighting

Claude Code's ink UI shows autocomplete/highlighting for slash commands as you type character-by-character. Two approaches:

**A) Accept the tradeoff** — Composer sends complete text on Enter. No incremental highlighting, but slash commands still work. Simplest approach.

**B) Stream keystrokes from Composer** — Forward each keystroke to the PTY in real-time as the user types in the Composer, so Claude's ink UI shows live autocomplete. Enter submits from the Composer. Preserves the interactive feel but adds complexity around syncing Composer text state with what Claude's ink UI displays.

Needs brainstorming to decide which approach.
