---
title: Replace hidden service session with visible terminal for issue creation
status: Resolved
priority: High
type: Improvement
area: Issues Panel
assigned: Unassigned
created: 2026-04-02
---

Replace the hidden service session (useServiceSession hook) with a visible terminal session for issue creation via the `+` button. The current approach has several problems:

- **Silent failures** — if Claude asks a clarifying question, nobody sees it and the request times out after 30 seconds
- **Auth errors are invisible** — authentication failures produce a generic timeout with no explanation (#34)
- **React StrictMode/HMR instability** — the hidden PTY lifecycle conflicts with React's dev-mode double-mount, requiring workarounds (#35)
- **No conversational flow** — issue creation sometimes needs back-and-forth ("is this one issue or two?") which a fire-and-forget model can't support

### Proposed approach

When the user clicks `+` and submits text:
1. Open a terminal session — either in the existing terminal grid or embedded in the issues panel itself
2. Send `/issues <text>` to Claude in that visible terminal
3. The user can see Claude working, answer questions, and correct mistakes
4. The issues panel detects new files via the existing file watcher and updates the list

This matches how the GitHub CLI extension works in VS Code — commands run in a visible terminal, not a hidden background process.

### Open design question

Should the terminal open in the main terminal grid (splitting a pane), or should the issues panel have its own embedded mini-terminal for issue operations? The latter would keep the terminal grid undisturbed but adds UI complexity. Needs brainstorming.

### Scope

- Remove `useServiceSession` hook and the hidden service session spawning
- Update `+` button handler to open/reuse a terminal and send the `/issues` command
- Keep the file watcher detection for updating the issues list
- Remove the 30-second timeout and "Creating issues..." status (no longer needed — the user watches it happen)
