---
title: Merge Document Filtering and Selection
status: Needs Discussion
priority: Medium
type: Design
area: Merge Documents
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/28/26 (Original #89)*

CD does not filter restricted documents out of view. CD shows ALL documents in its tree at all times. Restrictions work at the action level — when you select 2+ documents, CD checks the entire selection against the conditions table and disables the Merge button if any selected document has a blocking condition.

CP's model is different — you're already in merge mode and now opening a modal to add documents. The approach for US7 is:
- Reuse Feature 14's Clear Docs browsing modal, filtered to the initial document's side
- All documents on that side are visible (CD panels as-is)
- Documents with merge-blocking conditions (Final+Inactive, Final+Duplicate, non-PDF, etc.) are shown but not selectable
- Documents already in the merge set are shown but not selectable
