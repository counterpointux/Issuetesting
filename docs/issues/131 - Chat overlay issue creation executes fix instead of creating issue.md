---
title: Chat overlay issue creation executes fix instead of creating issue
status: Resolved
priority: High
type: Bug
area: Chat Overlay
assigned: Unassigned
created: 2026-03-25
---

When using the chat overlay to add an issue, the AI attempts to fix the issue immediately instead of just creating an issue entry in docs/issues.md. The chat overlay should only create the issue record, not take action on it.