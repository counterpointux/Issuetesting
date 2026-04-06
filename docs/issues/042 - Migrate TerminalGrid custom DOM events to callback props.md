---
title: Migrate TerminalGrid custom DOM events to callback props
status: Resolved
priority: Medium
type: Improvement
area: Terminal
assigned: Unassigned
created: 2026-04-06
---

Replace the four custom DOM events that IssuesPanel dispatches to TerminalGrid with typed callback props threaded through App.tsx. Custom DOM events bypass React's data flow, are untyped, invisible to DevTools, and require grepping to trace.

### Events to migrate

1. `focus-session` — focuses an existing terminal pane by session ID
2. `resume-in-new-terminal` — creates a new pane with a Claude `--resume` command (used by "Work on This")
3. `import-issues` — creates a new pane that runs an issue import command
4. `batch-resume-sessions` — creates multiple panes for batch session resume

### Approach

For each event, add a callback prop on TerminalGrid (e.g., `onFocusSession`, `onResumeInNewTerminal`), expose it upward through DetailPanel to App.tsx, and pass it down to IssuesPanel. Remove the corresponding `window.addEventListener` / `window.dispatchEvent` calls.

This aligns with the pattern established in issue #40, which introduced the first callback-based cross-component terminal action (`onCreateIssueTerminal`).
