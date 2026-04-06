---
title: Session queue system
status: Open
priority: Medium
type: Feature
area: Sessions
assigned: Unassigned
created: 2026-03-27
---

Line up issues for implementation and let Claude work through them sequentially or in parallel.

- Queue panel where you drag issues from the backlog into an execution queue
- Configurable concurrency limit (1 = sequential, N = parallel)
- When a queue slot opens, auto-start next issue: create Claude session, inject context, send implementation prompt
- Queue item statuses: pending, running, completed, failed/needs-input
- Pause/resume the queue, reorder items, pull items out for manual work
- Completion detection: detect `>` prompt pattern, session cost summary, or timeout after last output
- Failed/needs-input items pause that slot and notify the user
- Initial prompt per item from issue plan field, user-written prompt, or a template
- New `QueueItem` type: `featureId`, `projectId`, `position`, `status`, `sessionId`, `prompt`
- Depends on SessionStateDetector (#22) for reliable completion detection