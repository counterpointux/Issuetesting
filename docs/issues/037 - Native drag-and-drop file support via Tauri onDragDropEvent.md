---
title: Native drag-and-drop file support via Tauri onDragDropEvent
status: Resolved
priority: Medium
type: Feature
area: Platform
assigned: Unassigned
created: 2026-04-01
---

Tauri's native WebKit layer intercepts all file drag-and-drop events from Finder before they reach JavaScript. This means standard HTML `onDrop` handlers never fire for files dragged from Finder — only clipboard paste works. This affects the entire app: the import drop zone, image attachments in the issue creation textarea, and any future drag-and-drop features.

**Fix:** Use Tauri v2's `onDragDropEvent` listener from `@tauri-apps/api/webview` to receive native drag-drop events. These events provide file paths (not File objects), so a Rust command is needed to read the dropped files. The main challenge is that `onDragDropEvent` is window-level, not element-level — coordinate hit-testing against element bounds is required to determine which component the file was dropped on.

**Scope:**
- Listen for `onDragDropEvent` at the app level
- Route drops to the correct component based on mouse coordinates and element bounds
- Read dropped files via Rust command and pass content to the target component
- Fixes: import drop zone file drops, image attachment drops in issue creation, and any future drop targets
