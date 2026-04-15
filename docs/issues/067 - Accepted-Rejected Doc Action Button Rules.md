---
title: Accepted/Rejected Doc Action Button Rules
status: In Progress
priority: Medium
type: Design
area: Review Documents Wizard
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/22/26 (Original #68). SME Owner: Hema.*

If User clicks on an "Accepted/Rejected Document" in Doc Explorer, should we not show the Action Buttons?

**Resolution (2/23):**
- Review Doc Wiz to exclude Condition Status = Cleared
- Review Doc Wiz Associated Condition dropdown exclude Condition Status = Cleared

**Additional context (2/24):**
- CP will have many-to-many condition-to-document associations
- Clear Docs will have to support many-to-many and Draft Document Association to Condition
- Clear Docs will have to figure out how to NOT break Byte
