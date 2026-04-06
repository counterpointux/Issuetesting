---
title: Native notifications for session events
status: Open
priority: Medium
type: Feature
area: Sessions
assigned: Unassigned
created: 2026-03-27
---

Know when background sessions finish or need attention without watching every terminal.

**Already implemented:**
- System sound on terminal bell (`play_system_sound`)
- `request_attention()` when bell fires while app is unfocused
- Notification sound setting in SettingsDialog

**Still needed:**
- Native OS notifications via `@tauri-apps/plugin-notification`
- In-app notification badge on sidebar showing unread events
- Notification types: session complete, needs input (Y/n prompt), error (PTY closed unexpectedly)
- Click notification to jump to relevant terminal pane
- Notification preferences: toggle per type, mute per project, do-not-disturb mode
- Smart batching to prevent spam (e.g., "3 sessions completed")
- Depends on SessionStateDetector (#22) for state classification