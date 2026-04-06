---
title: Diff summary per issue
status: Open
priority: Medium
type: Feature
area: Issues
assigned: Unassigned
created: 2026-03-27
---

See exactly what files changed during an issue's implementation, all in one place.

- Add `baselineCommit` field to Issue model, captured when status transitions to "in progress"
- "Changes" tab on the issue detail panel showing consolidated diff of all files
- Inline diff viewer (side-by-side or unified) rendered in the app
- Diff computed via `git diff <baseline>..HEAD` through Tauri shell commands
- Support multiple sessions per issue — diffs accumulate across all attached sessions
- Large diffs need pagination or file-level collapsing
- Note: overlapping diffs possible if multiple issues share a branch — branch-per-issue would solve this cleanly