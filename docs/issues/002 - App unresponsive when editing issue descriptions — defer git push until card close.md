---
title: App unresponsive when editing issue descriptions — defer git push until card close
status: Resolved
priority: High
type: Bug
area: Issue Tracker
assigned: Unassigned
created: 2026-03-20
---

The app becomes unresponsive when editing an issue description, likely due to git push happening on every write. Fix: only perform local writes while editing, and defer the git push until the issue card is closed. This reduces I/O during editing and keeps the UI responsive. I
