---
title: Artifact extraction from Claude sessions
status: Open
priority: Medium
type: Feature
area: Sessions
assigned: Unassigned
created: 2026-03-27
---

Automatically detect and surface files Claude created or modified during a session.

**Already implemented:**
- `TOOL_RE` regex in TerminalView detects tool names and arguments (Read, Edit, Write, Bash, Grep, Glob, etc.)
- Currently used only for dynamic terminal title updates

**Still needed:**
- New `SessionArtifact` type: `sessionId`, `filePath`, `operation` (created | modified | deleted | read), `detectedAt`
- Extend tool detection to capture file paths and classify operation types
- Artifact list panel alongside the terminal or in issue detail view
- Each entry shows: file path, operation type, link to open file or view diff
- Pin important artifacts to the issue for quick reference
- Normalize relative file paths against project working directory
- Consider de-emphasizing "Read" artifacts (lower signal than writes)