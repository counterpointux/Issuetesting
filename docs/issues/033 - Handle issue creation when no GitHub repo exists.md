---
title: Handle issue creation when no GitHub repo exists
status: Open
priority: Medium
type: Improvement
area: Issues Panel
assigned: Unassigned
created: 2026-04-01
---

Both issue creation flows (in-app issues panel and GitHub issues) should gracefully handle the case where the project has no GitHub remote configured. Currently this may fail silently or error out. The app should detect the absence of a repo and either skip the GitHub sync or clearly inform the user, while still allowing local issue creation to work normally.
