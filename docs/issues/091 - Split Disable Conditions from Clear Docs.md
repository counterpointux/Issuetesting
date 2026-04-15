---
title: Split Disable Conditions from Clear Docs
status: Open
priority: Medium
type: Design
area: Split Documents
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/23/26 (Original #81). SME Owner: Hema.*

Clear Docs disables Split under certain conditions:

| Condition | Flag |
|-----------|------|
| No documents selected | noneSelected |
| Multiple documents selected | multipleSelected |
| Non-PDF document | anyNonPdfs |
| Document pending AI classification | anyPendingClassification |
| Draft + Inactive document | anyDraftInactive |
| Final + Inactive | anyInactive |
| Final + Duplicate | anyDuplicate |
| Final + Illegible | anyIllegible |
| Final + Incomplete | anyIncomplete |
| Final + Unacceptable | anyUnacceptable |
| Final + MissingPages | anyMissingPages |

**Resolution (2/26):** Reviewed with Tim the 26 item checklist between CP and CD and made decisions.
