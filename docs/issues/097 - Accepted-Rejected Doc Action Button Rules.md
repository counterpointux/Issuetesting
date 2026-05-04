---
title: Rework Update Loan Status modal for approval and conditions for review flows
status: Ready for Review
priority: Medium
type: Improvement
area: Update Loan Status Modal
assigned: Tiffany
created: 2026-03-31
---

Two changes to the Update Loan Status modal:

1. **Remove specialized approval questions (Underwriter flow):** The underwriter-specific flow that prompts whether they plan to update the status to approval is not needed per user testing. Remove those specialized approval confirmation questions entirely.

2. **Add "Conditions for Review" state (Processor flow):** When a processor sets the loan status to "Conditions for Review," they should be prompted to define why they're setting that status. Add a new state/step to the modal that captures the processor's reasoning before confirming the status change.
