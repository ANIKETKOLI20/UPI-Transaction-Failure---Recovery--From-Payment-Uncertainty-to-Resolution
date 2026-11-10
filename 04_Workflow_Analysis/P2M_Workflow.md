# P2M Workflow — UPI Merchant Payment and Order-Issue Resolution

> **Document status:** Working draft v0.3 — evidence-ID reconciled and P2M scope clarified. Not a verified end-to-end production workflow.  
> **Workflow ID:** WF-P2M-01  
> **Product:** PhonePe consumer UPI app  
> **User perspective:** Payer/customer  
> **Evidence review date:** 10 November 2026  
> **PhonePe Help screenshot capture date:** 3 November 2026 (filename-derived; exact article URLs and app version were not visible).

## 1. Purpose

Map the payer's options when a merchant-payment or post-payment issue occurs. The supplied PhonePe Help screenshots document distinct scenarios that must not be collapsed:

1. A merchant disputes receipt of money after PhonePe displays a successful payment.
2. A payment is successful, but the merchant has not confirmed the order or booking.
3. The payer was debited but transaction confirmation was not received at the merchant location — the specific RBI-defined P2M failed-transaction category.
4. A duplicate payment or merchant-initiated order/booking refund is involved.

The workflow distinguishes PhonePe's displayed status, the payer's debit, merchant payment confirmation/receipt, order/booking confirmation, and merchant-initiated refunds.

## 2. Scope and boundaries

### Included

- Domestic UPI P2M payments from the payer's perspective.
- PhonePe Help's stated guidance for merchant receipt disputes and unconfirmed orders/bookings.
- The separate RBI-defined incident where the payer is debited but transaction confirmation is not received at the merchant location.
- Duplicate-payment and merchant-refund guidance where needed to distinguish adjacent issues.
- The role of transaction references and the current evidence gaps around the live transaction and complaint flows.

### Not established by the current evidence

- Whether a particular merchant's bank account was credited or settled.
- Whether the merchant's POS/ordering system received, displayed or reconciled a confirmation.
- The actual cause of a discrepancy between a payer's app and a merchant's report.
- The prevalence of merchant disputes, order failures or duplicate payments.
- Whether users find the current in-app support route easy to discover.

## 3. Evidence base — canonical Evidence Register IDs

Use the canonical IDs in `03_Evidence_Register/Evidence_Register.xlsx`. See `Evidence_ID_Crosswalk.md` for the mapping from IDs used in earlier drafts.

| Evidence ID | Source / item | What it supports | Limitation |
|---|---|---|---|
| E-003; E-004 | Historical internet-found pending/failed transaction screenshots | Historical UI context only | Secondary evidence; original source and publication date not established. Not verified as P2M screens. |
| E-006 | PhonePe Help — Payment Issues categories | Help information architecture and merchant-payment issue category | Shows categories; does not prove discoverability or effectiveness. |
| E-021 | What if the merchant denies having received the amount for a successful payment? | PhonePe Help says a payment is marked successful only after PhonePe receives confirmation that money has reached the merchant; says merchants do not inform PhonePe whether they confirmed the order/service; directs payer to Report Issue when merchant denies receipt | Attribute the status definition to PhonePe Help; it is not an independent audit of bank settlement or merchant records. |
| E-022 | What if I have paid twice for an order or booking? | Contact merchant to check records/refund excess; contact bank with UTR if merchant refuses; check final status before retrying | Supports the guidance, not actual repeat-payment frequency or behaviour. |
| E-023 | What if the order or booking is not confirmed for a successful payment? | Contact merchant for an order/booking update; distinguishes payment issue from order/booking issue | Does not prove why the order was not confirmed. |
| E-024 | When will I receive a refund for a cancelled or failed order/booking or payment? | Merchant-initiated refund guidance and merchant as refund-status contact | Do not conflate with automatic bank reversal for a failed UPI transaction. |
| E-015 | Where can I find the UTR number? | UTR lookup path: History → select payment → “Debited from” | Existing Help-documented route; accessibility and sharing usability not tested. |
| E-029 | RBI/2019-20/67 failed-transaction TAT circular | Specified P2M incident: payer debited, merchant location does not receive transaction confirmation; T+5 auto-reversal and applicable compensation | Apply only if the incident facts match the circular. Do not equate an unconfirmed order with missing transaction confirmation. |
| E-030 | NPCI UPI HELP Brand Guidelines | Dated ecosystem-level reference for UPI Help workflows | Not proof of PhonePe's current implementation. |
| E-031 | PhonePe Grievance Policy, Version 10 | PhonePe's published grievance stages and service targets | Revalidate exact clauses and product applicability; do not infer that every UPI issue has a PPI Ombudsman route. |

## 4. Reconstructed P2M decision workflow

```text
1. Customer initiates a merchant UPI payment
                  |
                  v
2. Check payer-side transaction status and debit record
                  |
                  v
3. Identify what the merchant is actually reporting
   |                         |                         |
   v                         v                         v
A. Merchant says          B. Order/booking          C. Payer debited, but
   money was not             not confirmed after       transaction confirmation
   received, while           a successful payment      was not received at the
   PhonePe shows                                        merchant location
   Successful
   |                         |                         |
   v                         v                         v
PhonePe Help says          PhonePe Help says          Check whether facts match
Successful is shown        contact the merchant        RBI's specific P2M failed-
after PhonePe receives     for an order/booking        transaction category
confirmation that money    update                       (do not assume it does)
reached the merchant       |                         |
   |                         v                         v
   v                      Follow merchant's           If eligible, applicable
Use Report Issue for       order/booking process       T+5 auto-reversal framework
that payment               and refund route            applies
   |                                                   |
   v                                                   v
Follow PhonePe's           D. Duplicate payment / merchant-initiated refund
payment-dispute route      Follow the relevant merchant/bank instructions
```

**Interpretation rule:** Branch A, B and C are related but not interchangeable. In particular, PhonePe Help's definition of its Successful status must be reported accurately and attributed to PhonePe; an order not being confirmed does not by itself prove that the UPI transaction failed.

## 5. Four documented scenario types

### Scenario A — PhonePe shows Successful, but merchant says the money was not received

PhonePe Help states that it marks a payment successful only after receiving confirmation that the money has reached the merchant. The same article says that if the merchant denies receiving the amount, the payer should select the relevant payment and use `Report Issue` (E-021).

This is a discrepancy between the PhonePe status/confirmation described by PhonePe and the merchant's report. The supplied evidence does not establish which side's records are correct or why the discrepancy exists.

**Payer-oriented investigation questions:**
- What is the exact status shown in PhonePe?
- Was the payer's bank account debited?
- What transaction details/reference are available?
- What does the merchant's own payment record show?
- What information does the Report Issue flow request?

Do not independently conclude that merchant-bank credit or settlement did or did not occur from a payer screenshot or verbal merchant statement.

### Scenario B — Successful payment, but order or booking is not confirmed

PhonePe Help says merchants do not inform PhonePe whether an order has been confirmed or a service delivered. For an unconfirmed order/booking, PhonePe advises the customer to contact the merchant for an update (E-021; E-023).

This is an order/booking or fulfilment issue unless separate payment evidence establishes a payment problem. Do not classify an unconfirmed order as a failed UPI payment by default.

### Scenario C — Payer debited, but transaction confirmation was not received at the merchant location

This is the specific P2M failure condition defined in the RBI circular (E-029). The applicable T+5 auto-reversal framework and compensation for delay beyond the TAT should be discussed only when the facts match this incident category.

Do not apply T+5 to every merchant complaint, unconfirmed booking, service-delivery dispute, duplicate payment or merchant-initiated refund.

### Scenario D — Duplicate payment or merchant-initiated order/booking refund

PhonePe Help advises customers who paid twice for an order or booking to contact the merchant so it can check its payment records and refund the excess amount; if the merchant refuses, the article advises contacting the bank with the UTR. It also tells users to check final payment status before retrying (E-022).

For a cancelled/failed order or booking, the Help article says the merchant will refund the money and asks the customer to contact the merchant for refund status (E-024). This is not the same as automatic reversal of a failed UPI transaction.

## 6. Step-by-step analysis

| Stage | What the evidence supports | Payer's information need | Evidence / limitation |
|---|---|---|---|
| 1. Initiation | Customer initiates a UPI payment to a merchant | Confirm merchant and amount | No current P2M failure transaction was deliberately created or tested. |
| 2. PhonePe status | PhonePe Help distinguishes pending, failed, successful and merchant-payment issue topics | Understand the displayed status | E-006; current live transaction screens still need inspection. |
| 3A. Merchant disputes receipt after Successful | PhonePe Help gives its stated Successful criterion and a Report Issue route | Understand the status explanation and report the payment discrepancy | E-021; merchant/acquirer records not available. |
| 3B. Order/booking not confirmed | PhonePe Help advises contacting merchant for order update | Identify this as an order/booking issue, not automatically a payment failure | E-023; order system not inspected. |
| 3C. Debit with no merchant transaction confirmation | RBI defines a specific P2M failed-transaction incident | Establish whether the exact incident condition is met | E-029; requires transaction and merchant-side evidence. |
| 4. Transaction reference | PhonePe Help shows where to find a 12-digit UTR | Locate the applicable reference for bank/support follow-up | E-015; does not prove the reference is hard to find. |
| 5. Duplicate payment | PhonePe Help says contact merchant and check final status before retrying | Resolve excess payment and avoid an unverified repeat | E-022; no actual duplicate-payment rate is known. |
| 6. Merchant refund | PhonePe Help says to contact the merchant for cancelled/failed order/booking refund status | Know who initiates and updates the refund | E-024; distinct from automatic UPI reversal. |
| 7. Grievance route | PhonePe policy describes support/grievance levels | Identify the correct entity and applicable complaint route | E-031; exact route depends on issue/product; revalidate. |

## 7. Regulatory and policy overlay

### 7.1 RBI P2M turnaround time

RBI/2019-20/67 specifies auto-reversal within T+5 for the defined P2M case in which the payer's account is debited but transaction confirmation is not received at the merchant location. Compensation of ₹100 per day applies for delay beyond the applicable TAT. T refers to the transaction date/calendar date in the circular (E-029).

**Scope caution:** An unconfirmed order/booking (Scenario B) is not by itself proof of the RBI-defined missing merchant-transaction-confirmation condition (Scenario C). Nor should every merchant report of non-receipt after a PhonePe Successful status be automatically classified as that RBI incident without checking the facts.

Official source recorded in the register: https://m.rbi.org.in/commonman/English/Scripts/Notification.aspx?Id=3074

### 7.2 PhonePe Help guidance

- Merchant denies receiving amount after Successful: select the payment and use Report Issue (E-021).
- Order/booking not confirmed: contact the merchant for an update (E-023).
- Duplicate payment: contact merchant to verify its records; if excess amount is not refunded, PhonePe Help describes a bank follow-up with UTR (E-022).
- Cancelled/failed order or booking refund: contact the merchant for refund status (E-024).
- UTR location: History → select payment → “Debited from” (E-015).

These are statements in the inspected Help material, not independent evidence of actual payment settlement, refund processing or complaint outcomes.

### 7.3 PhonePe Grievance Policy and NPCI reference

The PhonePe Grievance Policy (Version 10) is recorded as E-031. Re-open the current policy and verify the exact clause, dates, response target, resolution target and product applicability before quoting it. Do not treat a PPI-specific RBI Ombudsman route as a universal UPI complaint route.

NPCI's UPI HELP Brand Guidelines are recorded as E-030. Use them as dated ecosystem context, not proof that PhonePe's current screens or flows implement every guideline.

## 8. Product-analysis questions

1. Can a payer tell which situation they are in: merchant disputes receipt, order/booking is unconfirmed, or the RBI-defined transaction-confirmation failure condition may apply?
2. Does the live PhonePe transaction experience make its stated Successful criterion understandable?
3. Is the Report Issue route for a merchant payment dispute easy to find from the relevant transaction?
4. Does the experience clearly direct an order/booking issue to the merchant, without implying that the UPI payment failed?
5. Can the payer find the applicable transaction reference without unnecessary navigation?
6. Does PhonePe show acknowledgement, complaint reference and status tracking after a report is submitted?
7. Does the experience distinguish automatic reversal from merchant-initiated refund?

These are research questions. The available screenshots do not answer all of them.

## 9. Open questions and limitations

- The current P2M transaction-detail screen and in-app Report Issue journey have not been fully inspected end to end.
- Merchant/acquirer records were not available to establish what the merchant received or recorded.
- Exact complaint submission, acknowledgement/reference generation and tracking remain unverified.
- User comprehension of the distinction between payment receipt and order confirmation has not been tested.
- Actual repeat-payment attempts and duplicate successful payments have not been measured.
- RBI T+5 applies only where the specified debit and missing merchant-transaction-confirmation facts are established.
- The article URLs, publication/update dates and app version are not visible in the supplied screenshots.

## 10. Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-04 | Initial P2M workflow draft. |
| 0.2 | 2026-11-07 | Expanded workflow and regulatory overlay. |
| 0.3 | 2026-11-10 | Reconciled evidence IDs to Evidence_Register.xlsx; separated merchant receipt dispute, order/booking issue and RBI-defined P2M failure scenario; corrected the interpretation of PhonePe's stated Successful status. |
