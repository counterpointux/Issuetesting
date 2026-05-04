---
title: Confirm auto-reminder email content carries over as-is
status: Resolved
priority: Low
type: Design
area: Auto-Reminders
assigned: Tiffany
created: 2026-03-19
---

# Memo: BNL Email vs. Auto Reminder Email — Differences for Design

---

**To:** Design Team
**From:** Product
**Date:** March 26, 2026
**Re:** How the initial Borrower Needs List email differs from the Auto Reminder email

---

## Background

The Borrower Needs List (BNL) feature sends document request emails to borrowers. There are two scenarios in which an email is sent:

1. **Initial Email** — The loan officer manually clicks "Send Email" from the Step 2 of 2 email preview slide-out.
2. **Auto Reminder Email** — The system automatically re-sends the email on a schedule when the borrower has not yet uploaded all requested documents.

As we build this into the Conditions Portal, Design needs to account for both email types. This memo documents how they differ today in CLEAR production.

---

## Key Finding: The Emails Are Nearly Identical

The initial email and the auto reminder email use the **same email template and body content**. The only difference is a **"Reminder: " prefix added to the subject line** on auto reminder emails.

---

## Side-by-Side Comparison

| Element | Initial Email | Auto Reminder Email |
|---------|--------------|---------------------|
| **Subject Line** | Documentation Needed for Your Loan - Loan #[LoanNumber] | **Reminder:** Documentation Needed for Your Loan - Loan #[LoanNumber] |
| **Salutation** | Same | Same |
| **Intro Paragraph** | Same (CMG AI Intro or user's Intro Template) | Same |
| **Document Request List** | Same | Same |
| **Compliance Footer** | Same (all 4 sections) | Same (all 4 sections) |
| **Closing** | Same | Same |
| **From** | Logged-in user | Logged-in user (original sender) |
| **To** | Borrower email(s) | Borrower email(s) |
| **CC** | Logged-in user | Logged-in user (original sender) |

---

## How Auto Reminders Are Triggered

Auto reminders are not a separate email compose flow. They are system-generated re-sends governed by user-configured settings:

- **Frequency:** How often to re-send (24hrs, 48hrs, or 72hrs)
- **Number of Reminders:** Maximum re-sends (1-10)
- **Stop Condition:** Reminders stop automatically when the borrower uploads all requested documents via SmartApp

These settings are configured per-user in the Auto Reminder Settings modal (accessible from the Step 2 of 2 email slide-out). The user can also set their preferences as the default for new loans.

In CLEAR, a background Hangfire job (`SendRemindersJob`) runs on a schedule and queries for any emails eligible for a reminder based on elapsed time and remaining reminder count.

---

## Implementation Detail (for reference)

The conditional subject line logic in CLEAR is handled by a single boolean flag (`IsReminder`) in the email template model:

```
Subject = (IsReminder ? "Reminder: " : "") + "Documentation Needed for Your Loan - Loan #" + LoanNumber
```

No other content in the email changes between the initial send and subsequent reminders.

---

## Design Implications for the Conditions Portal

1. **Single email template:** Design only needs one email template. The reminder variant is the same layout with a subject line prefix.
2. **Subject line prefix:** The "Reminder: " prefix should be automatically prepended by the system — not shown or editable in the email compose UI.
3. **No visual distinction in the email body:** The borrower sees the same email content whether it is the initial send or a reminder. There is no "This is a reminder" banner or callout in the body.
4. **Auto Reminder settings UI:** The settings modal (On/Off toggle, frequency, number of reminders, default preference) should be carried forward as-is. See the existing BNL Phase 2 test plan for the full specification of the Auto Reminder Settings modal.

---

## Source of Information

| Source | Location |
|--------|----------|
| Borrower email template model | `CMG.Docs.Templates/Models/DocumentUploadRequestBorrower.cs` (line 22 — conditional subject line) |
| Reminder sending logic | `CMG.Docs.Logic/Managers/DocumentUploadRequestManager.cs` (lines 593-630, 799-836) |
| Auto reminder scheduling | `CMG.Docs/Hangfire/SendRemindersJob.cs` |
| Reminder eligibility query | `CMG.Docs.Database/dbo/Stored Procedures/usp_FindAutoReminders.sql` |
| Auto reminder config model | `CMG.EPS.Loan.Common/Models/AutoReminderConfig.cs` |
| BNL email HTML layout | `CMG.EPS.Loan.Database/Migrations/20251218_89898_Generated-BNL-Email-HTML-Enhancements.sql` |

All source files are in the CLEAR production codebase at `C:\Github\clear-codebase`.
