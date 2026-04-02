---
title: Exception Request Read-Only Display
status: Open
priority: Medium
type: Design
area: Exceptions
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/11/26 (Original #20)*

Stripped out exception request display. For this feature, the section renders as a read-only placeholder:
- If no exception request exists (both exceptionRequestedDateTime and exceptionStatus are null): display text "There currently is not an exception request"
- If an exception request exists: display the requested date, requested by, and status as read-only text

**Resolution:** Need a way to showcase this in the prototype. May need to update the seed data.
