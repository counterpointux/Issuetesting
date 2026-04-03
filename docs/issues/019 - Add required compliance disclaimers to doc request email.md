---
title: Add required compliance disclaimers to doc request email
status: Resolved
priority: High
type: Requirements
area: Send Doc Request Modal
assigned: Tiffany
created: 2026-03-25
---

# Requirement: Borrower Email Compliance Language

---

## Summary

The Loan Conditions Portal must include standardized compliance language in all borrower-facing emails. This language is currently implemented in the CLEAR/EPS BNL email templates and must be carried forward into the Conditions Portal to maintain regulatory compliance.

---

## Requirement

All borrower-facing emails sent from the Loan Conditions Portal must include the following four compliance sections in the email footer.

### Section 1: Document Collection Disclaimer

> Please note: You are not required to provide any of the documents listed or requested unless one of the following applies:
>
> You are actively seeking a TBD Preapproval (a preapproval not yet tied to a specific property), or
>
> You have received a Loan Estimate from us and have formally provided your Intent to Proceed with the application.
>
> If neither of these conditions apply, you are under no obligation to submit any documentation at this time.

### Section 2: Password Protected Document Notice

> Documents upload to the portal are secure and encrypted. Please do not upload Password Protected Documents.

### Section 3: Secure Document Upload Link

> Please use this URL to upload requested document(s): {Dynamic Secure Docs Portal URL}

- The URL must be dynamically generated and include the loan number.
- The link must resolve to the borrower's secure document upload portal.

### Section 4: Solicitor Calls Opt-Out Notice

> *Avoid Solicitor Calls:* To reduce unsolicited credit offers, you may choose to opt out of prescreened offers for five years at [www.optoutprescreen.com](http://www.optoutprescreen.com). This is a free, third-party service provided by the major consumer reporting agencies. Use of this site is optional and not required to apply for or obtain a loan from us.

---

## Design Constraints

1. **Consistent placement:** The compliance sections must appear below the document request list and above the closing salutation, in the order listed above (Sections 1-4).
2. **Formatting:** The compliance text must render correctly in all major email clients (Outlook, Gmail, Apple Mail). Italic formatting on "Avoid Solicitor Calls:" must be preserved.
3. **Dynamic URL:** The Secure Docs portal link (Section 3) must be dynamically populated per loan and must be a clickable hyperlink.

---

## Source of Information

The compliance language was sourced from the existing CLEAR/EPS production codebase, where it is currently in use for BNL borrower emails:

| Source | File Path | Details |
|--------|-----------|---------|
| BNL Email HTML Layout (DB Migration) | `C:\Github\clear-codebase\CMG.EPS.Loan\CMG.EPS.Loan\CMG.EPS.Loan.Database\Migrations\20251218_89898_Generated-BNL-Email-HTML-Enhancements.sql` | Lines 24-32. Contains the HTML email layout seeded into the database, including all four compliance sections in the footer. Dated 12/18/2025. |
| Docs Email Template (Razor View) | `C:\Github\clear-codebase\CMG.Docs\CMG.Docs\CMG.Docs.Templates\Views\DocumentUploadRequestBorrower.cshtml` | Lines 82-96. The CMG Docs Razor template for borrower document upload request emails. Contains identical compliance language rendered via Cshtml. |
