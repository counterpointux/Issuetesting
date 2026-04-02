---
title: Document Status Enum Role Mapping
status: Open
priority: Medium
type: Requirements
area: Review Documents Wizard
assigned: Tim
created: 2026-04-01
---

*Added by Josephine on 2/21/26 (Original #61)*

Document Status enum: "Not Reviewed", "Reviewed", "Approved", "Inactive"

**Processor III:**
- Pending = "Not Reviewed"
- Accepted = "Reviewed" (or "Approved"?)
- Rejected = "Inactive"

**Underwriter:**
- Pending = "Reviewed"
- Accepted = "Approved"
- Rejected = "Inactive"

Gap: What about a document with status "Approved" seen by a Processor, or "Not Reviewed" seen by an Underwriter? Those aren't "pending" for that role — do they land in the Accepted section, or do they fall through?

**Resolution:** JY decided: Pending — already in Requirements.MD. UW only see Final Docs. When Proc does "Ready for UW", all Accepted Docs go to Final. Add an OQ for Stakeholders for Ready for UW Conditions and there is a linked Document in Draft.
