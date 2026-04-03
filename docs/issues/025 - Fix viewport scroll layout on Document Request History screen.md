---
title: Fix viewport scroll layout on Document Request History screen
status: Open
priority: Medium
type: Bug
area: Email History
assigned: Unassigned
created: 2026-04-03
---

The Document Request History screen currently scrolls the entire page vertically to view the email list. The email list and the email preview pane should each scroll independently within the viewport, so the full layout fits the screen without a page-level scrollbar. This means the email list panel and the email preview panel should each have their own overflow scroll, constrained to the available viewport height.
