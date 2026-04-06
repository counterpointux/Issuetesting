---
title: Clickable file paths in terminal output
status: Open
priority: Medium
type: Feature
area: Terminal
assigned: Unassigned
created: 2026-04-02
---

Make file paths in terminal output clickable so users can open them in their editor directly from Orchestrator.

Use xterm.js's link provider API to register a pattern matcher that detects file paths (e.g., `src/components/Foo.tsx`, `src/components/Foo.tsx:42`, `src/components/Foo.tsx:42:10`). On click, open the file in the user's default editor using `open` on macOS or a configurable editor command.

Should handle:
- Relative paths from the project working directory
- Paths with line numbers (`file.tsx:42`) and column numbers (`file.tsx:42:10`)
- Common output formats from Claude Code, TypeScript compiler errors, test runners, and linters
- Only match paths that actually exist on disk (avoid false positives)
