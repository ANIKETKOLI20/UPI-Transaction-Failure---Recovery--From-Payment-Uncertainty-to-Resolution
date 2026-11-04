# Workflow Unknowns — PhonePe UPI Transaction Failure & Recovery

> **Document status:** Working register v0.2  
> **Product:** PhonePe consumer UPI app  
> **Related workflows:** `P2P_Workflow.md` and `P2M_Workflow.md`  
> **Review date:** 4 November 2026

---

## 1. Purpose

This document records what is not yet verified in the P2P and P2M payment-recovery workflows. Unknowns must remain explicitly labelled until supported by direct product evidence, official documentation, transaction records or appropriately designed user research.

**Do not present an unverified step as actual PhonePe behaviour.** A Help article can establish what PhonePe tells customers; it does not by itself establish backend processing, actual transaction outcomes or actual user behaviour.

## 2. What is established so far

The following are supported by the research material collected to date:

- PhonePe's Help section separates issues with pending payments, failed payments, successful payments, merchant payments and refunds (screens supplied by the researcher on 3 November 2026).
- PhonePe Help says banks may take from 2 minutes to 48 hours to confirm the final status of a pending payment.
- PhonePe Help says initiated UPI payments cannot be cancelled and advises waiting up to 48 hours for final status.
- PhonePe Help says a pending transaction that remains pending after 48 hours can be reported to PhonePe for escalation.
- PhonePe Help lists possible failure reasons and advises users to check the reason in History before trying again.
- PhonePe Help gives generic 3–5-day refund guidance for failed UPI payments, advises checking the bank statement and directs the user to contact the bank with the UTR if the refund is not received after five days.
- PhonePe Help has separate merchant guidance for payment confirmation, order/booking issues, duplicate payments and merchant refunds.
- PhonePe's Grievance Policy, Version 10, dated 16 July 2026, describes customer support and grievance-desk/nodal-officer stages. Its RBI Integrated Ombudsman Scheme section specifies PPI applicability; do not assume that this is automatically the direct Ombudsman route for a PhonePe UPI complaint.
- RBI's 2019 framework sets T+1 for the specified UPI P2P debit-without-beneficiary-credit incident and T+5 for the specified UPI P2M debit-without-merchant-confirmation incident, with applicable ₹100-per-day compensation beyond the relevant deadline.
- NPCI's July 2023 UPI HELP guidelines describe complaint functionality for P2P and P2M UPI transactions, but do not prove every feature is currently implemented in PhonePe.

These statements describe the inspected help content and official published frameworks. They do not establish actual transaction-resolution performance or user behaviour.

## 3. Unknowns and why they matter

| ID | Unknown | Why it matters | Evidence needed | Status |
|---|---|---|---|---|
| U-001 | Exact current P2P pending/failed transaction-detail screen behaviour | Internet-found transaction screenshots do not establish the current live app experience; successful P2P screens do not establish failure behaviour. | Directly inspect a genuine existing P2P pending/failed transaction if available; record exact status, wording, actions, app version and date. Do not create a risky payment to manufacture a failure. | Not verified |
| U-002 | Exact current P2M pending/failed transaction-detail screen behaviour | The P2M Help material is available, but the actual P2M transaction screen has not been directly inspected. | Directly inspect an existing P2M payment issue or a safe official demonstration; record app version and date. | Not verified |
| U-003 | Exact complaint-submission journey from a transaction | A Help article or `Report Issue` button does not prove the screens, fields and successful submission process. | Inspect the in-app flow using a safe path and stop before submitting a real complaint; record each screen and required field. | Not verified |
| U-004 | Complaint acknowledgement/reference generation and tracking | The reference, status page, update cadence and closure behaviour have not been fully established. | Capture a legitimate existing complaint's redacted acknowledgement/tracking view if available, or verify through current official PhonePe policy. Do not submit a false complaint. | Not verified |
| U-005 | Actual time taken for a P2P reversal | RBI's deadline and PhonePe's estimate are not evidence of the time an individual transaction actually takes. | Suitable transaction-level records or clearly attributed, credible user research. Do not infer actual performance from policy timelines. | Not verified |
| U-006 | Actual time taken for a P2M reversal or merchant refund | A failed-transaction auto-reversal, merchant-initiated refund and order cancellation are different events. | Separate transaction reversal records, merchant refund records and order records with timestamps; otherwise retain as unknown. | Not verified |
| U-007 | Actual customer behaviour after a pending status, including repeat-payment attempts | The interface and Help content cannot establish whether users retry, wait, contact support or abandon the payment. | Product event data, customer-support data or appropriately designed user research. | Not verified |
| U-008 | Exact current grievance route for a PhonePe UPI complaint after app-level support | A Help article refers to the RBI Banking Ombudsman, while the current PhonePe policy describes RB-IOS applicability for PhonePe PPI services. The route for a particular UPI complaint must not be assumed. | Verify the complaint's responsible regulated entity, PSP/issuer bank role, PhonePe escalation stages and current NPCI/RBI rules for that specific complaint. | Not verified |
| U-009 | Whether the generic 3–5-day PhonePe UPI refund guidance applies to the RBI-defined P2P and P2M failure scenarios | The Help wording is generic and does not clearly specify every applicable scenario or whether “days” means calendar or business days. | Locate scenario-specific PhonePe wording or obtain clarification from official PhonePe documentation; compare only like-for-like incident definitions and clock start points. | Not verified |
| U-010 | Whether the current PhonePe app implements the relevant NPCI UPI HELP functionality exactly as described in the July 2023 guidelines | NPCI guidance describes an ecosystem framework; actual implementation can vary by app/version and may change. | Directly inspect current PhonePe UPI complaint eligibility, categories, status updates and tracking; record app version and date. | Not verified |
| U-011 | Merchant-side transaction confirmation and receipt in a P2M case | A payer-facing screen cannot prove what the merchant's system received or recorded. | Merchant-side confirmation/POS or acquiring-bank evidence in a legitimate controlled research context, or clearly attributed merchant research. | Not verified |
| U-012 | Original provenance and publication date of internet-found pending/failed transaction screenshots | The screen content may be historical, edited, reposted or from a different app version; visible transaction dates are not publication dates. | Locate original source URLs, publication dates and context. Until then, retain as secondary visual examples only. | Not verified |
| U-013 | Current PhonePe app version and exact date for every direct Help screenshot | Help wording and navigation can change; the supplied images do not show the app version. | Record app version from app settings/about or store listing and capture date in the evidence register. | Partially verified — capture date inferred from supplied filenames/conversation; version unknown |

## 4. Evidence rules

- **Direct observation:** Use only for behaviour personally observed in PhonePe and supported by a screenshot or contemporaneous notes. Record capture date and app version where available.
- **PhonePe Help evidence:** Attribute statements to the exact Help heading and screenshot. It establishes customer-facing information visible at capture time, not backend processing or real-world results.
- **Official policy:** Record the document title, version/date, URL and relevant section. Do not confuse complaint service levels with transaction-reversal deadlines.
- **Regulatory evidence:** Apply an RBI/NPCI rule only when the transaction type and incident conditions match. Keep P2P and P2M scenarios separate.
- **Secondary evidence:** Label internet-found screenshots, articles and posts as secondary sources. Do not treat them as proof of current PhonePe behaviour.
- **Behavioural claims:** Do not claim that users retry payments, feel confused, contact support or abandon transactions without user research or behavioural data.
- **Financial outcomes:** Distinguish payment status, payer debit, beneficiary/merchant credit, automatic reversal, merchant refund and order fulfilment.
- **Timelines:** Distinguish status-update estimates, RBI reversal deadlines, complaint-resolution service levels and the time for a refund to reflect in an account.
- **Personal data:** Redact names, phone numbers, UPI IDs, UTRs, account numbers and other transaction identifiers before adding screenshots to a public repository.

## 5. Current evidence index (provisional)

These references are provisional and must be reconciled with `Evidence_Register.xlsx`.

| Evidence ID | Evidence item | Class |
|---|---|---|
| E-001–E-002 | Researcher-reported successful incoming/outgoing P2P transaction observations | First-hand observations reported in notes |
| E-003–E-004 | Internet-found pending/failed transaction screenshots | Secondary visual evidence |
| E-005A–E-005D | PhonePe Help guidance initially transcribed/reviewed | Product guidance |
| E-006A–E-006E | PhonePe Help categories and issue-navigation screens | Direct app screenshots |
| E-007 | “What do I do if my UPI payment is pending?” | Direct Help screenshot |
| E-008 | “Why do I have to wait for 48 hours to know the final payment status?” | Direct Help screenshot |
| E-009 | “Can I cancel my pending payment?” | Direct Help screenshot |
| E-010 | “What if my payment is pending for more than 48 hours?” | Direct Help screenshot |
| E-011 | “Why did my UPI payment fail?” | Direct Help screenshot |
| E-012 | Failed UPI payment debit/refund and refund-not-received guidance | Direct Help screenshots |
| E-013 | UTR location and beneficiary account/credit guidance | Direct Help screenshots |
| E-014 | Bank chargeback, sample template and bank-denies-help guidance | Direct Help screenshots |
| E-015 | Merchant denies receiving a successful payment | Direct Help screenshot |
| E-016 | Duplicate payment for an order/booking | Direct Help screenshot |
| E-017 | Order/booking not confirmed; cancelled/failed order refund guidance | Direct Help screenshots |
| E-018 | Failed card refund guidance | Direct Help screenshots; outside core UPI scope |
| E-019 | PhonePe Grievance Policy, Version 10, 16 July 2026 | Official PhonePe policy |
| RBI-001 | RBI/2019-20/67, failed-transaction TAT and compensation, 20 September 2019 | Official RBI circular |
| NPCI-001 | NPCI UPI HELP Guidelines, July 2023 | Official NPCI guidance |
| RBI-002 | RBI FAQ: Reserve Bank–Integrated Ombudsman Scheme, 2026 | Official RBI guidance |

## 6. Research questions to resolve

1. What exactly does the current PhonePe app display after a P2P payment becomes pending or failed?
2. What exactly does the current PhonePe app display after a P2M payment becomes pending or failed?
3. What next-step guidance appears on each transaction screen, not just in the Help article?
4. How does a payer reach the exact complaint flow from a transaction?
5. Is a complaint reference generated, and can the payer track its status?
6. Which entity is responsible for the next step in each P2P and P2M scenario?
7. Which RBI reversal rule applies to the exact incident, and does the PhonePe guidance explain it accurately?
8. What real user behaviour follows a pending status, and what evidence would be needed to measure it?

## 7. Update log

| Version | Date | Update | Evidence IDs added / updated | Notes |
|---|---|---|---|---|
| 0.1 | 2026-11-04 | Initial unknowns recorded from the workflow review. | None | Six initial unknowns documented. |
| 0.2 | 2026-11-04 | Expanded unknowns after reviewing PhonePe Help screenshots and current official policy references. | E-005A–E-019; RBI-001–RBI-002; NPCI-001 | Added grievance-route, scenario applicability, merchant-side confirmation, current app-version and source-provenance gaps. |

## 8. Completion rule

Change an item's status from **Not verified** only when the required evidence has been collected and recorded in `02_Evidence_Register/Evidence_Register.xlsx` (or the final agreed evidence-register location).

When an unknown is resolved:

1. Record the evidence ID.
2. State exactly what the evidence establishes.
3. Record any remaining limitation.
4. Update the related P2P or P2M workflow.
5. Add the change to this document's update log.

If evidence is unavailable, retain the item as unknown and disclose the limitation in the final teardown.

---

**Document rule:** Unknowns are not defects. They are questions requiring evidence. Do not convert them into product findings or recommendations until the investigation supports that change.
