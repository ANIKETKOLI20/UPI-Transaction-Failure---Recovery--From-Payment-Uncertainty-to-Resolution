# P2M Workflow — UPI Merchant Payment Recovery

> **Document status:** Working draft v0.2 — evidence-informed, not a verified end-to-end production workflow.  
> **Workflow ID:** WF-P2M-01  
> **Product:** PhonePe consumer UPI app  
> **User perspective:** Payer/customer  
> **Core scenario:** Payer is debited, but transaction confirmation is not received at the merchant location.  
> **Evidence review date:** 4 November 2026  
> **PhonePe Help screens inspected:** 3 November 2026 (based on the supplied screenshots and conversation record).

---

## 1. Purpose

Map the payer's experience when a PhonePe UPI merchant payment has an uncertain or unsuccessful outcome. The workflow separates four events that must not be treated as equivalent:

1. the payer's bank account is debited;
2. the merchant receives transaction confirmation;
3. the merchant receives/records the payment in its own systems or settlement records; and
4. the merchant confirms the order, booking, goods or service.

The workflow also separates a UPI failed-transaction reversal from a merchant-initiated refund and an order/booking fulfilment dispute.

## 2. Scope and boundary

### Core scenario included

The specific UPI P2M failed-transaction incident in which the payer's account is debited but transaction confirmation is not received at the merchant location.

### Separate adjacent branches

- PhonePe shows a successful payment, but the merchant says it cannot identify or confirm receipt.
- The payment is successful, but the order or booking is not confirmed.
- A duplicate payment has been made for one order or booking.
- A merchant cancels or fails an order/booking and a merchant refund is expected.

These are separate situations. They can have different responsible parties and different processes or timelines.

### Excluded

- Merchant settlement/reconciliation diagnostics without merchant-side records.
- Delivery, product-quality or other fulfilment disputes except where needed to distinguish them from a payment-confirmation problem.
- P2P beneficiary-credit failures, card refunds and wallet refunds as core workflow scenarios.
- Claims about actual merchant receipt or non-receipt based only on the payer's app screenshot.

## 3. Evidence base used in this draft

Evidence references are provisional and must be reconciled with the final `Evidence_Register.xlsx` before publication.

| Evidence ID | Source / item | What it supports | Evidence class |
|---|---|---|---|
| E-003/E-004 | Internet-found pending and failed transaction screenshots | Historical visual examples of transaction screens; not proof of the current P2M flow | Secondary visual evidence; original publication/source not established |
| E-005D | PhonePe Help content about money debited but merchant did not receive payment | Merchant-related payment guidance reported by researcher | PhonePe Help evidence; preserve screenshot |
| E-006A–E | PhonePe Payment Issues categories and merchant-help list | Help information architecture, including merchant-payment issue category | Direct app screenshots supplied by researcher |
| E-015 | PhonePe Help: successful merchant payment disputed by merchant | PhonePe's statement about successful status and the Report Issue action | Direct Help screenshot supplied by researcher |
| E-016 | PhonePe Help: duplicate payment for order/booking | Contact merchant; merchant checks payment records; bank complaint if merchant refuses refund; check final status before retrying | Direct Help screenshot supplied by researcher |
| E-017 | PhonePe Help: order/booking not confirmed and merchant refund guidance | Distinguishes payment-related issues from order/booking issues; refund instructions | Direct Help screenshots supplied by researcher |
| E-018 | Internet-found pending/failed transaction screens | Historical visual context only; the supplied images appear to show P2P transfers, not a verified P2M journey | Secondary visual evidence |
| E-019 | PhonePe grievance policy and relevant support guidance | Published customer complaint and escalation channels | Official PhonePe policy; see source list |

**Capture-date note:** The Help screenshots' filenames and conversation record indicate 3 November 2026. Confirm the date and record the app version in the evidence register if available. The version was not visible in the supplied screenshots.

## 4. Reconstructed P2M workflow

```text
1. Customer initiates a UPI payment to a merchant
                  |
                  v
2. Check the payer's payment status and account outcome
   - Was the payer debited?
   - What status does PhonePe display?
   - Did the merchant receive transaction confirmation?
   - Was an order / booking created?
                  |
                  v
3. Distinguish the incident
   |                         |                         |
   v                         v                         v
A. Payer debited;       B. Payment shown as       C. Payment successful;
   merchant did not        successful; merchant     order / booking not
   receive transaction     disputes receipt or       confirmed / service
   confirmation            cannot identify it        not provided
   |                         |                         |
   v                         v                         v
4A. Assess the specific  4B. Use PhonePe's          4C. Contact merchant for
    RBI P2M failed-          Report Issue route          order / booking update;
    transaction scenario    for the relevant payment   separate payment from
    and follow verified     and verify evidence         fulfilment problem
    app/bank guidance       with appropriate parties
   |                         |                         |
   v                         v                         v
5A. If eligible,          5B. Follow payment-       5C. Follow merchant's
    auto-reversal under       dispute investigation      order / cancellation /
    applicable T+5 rule      and support route          refund process
   |                         |                         |
   +-------------------------+-------------------------+
                             |
                             v
6. If unresolved, use the relevant payment-app, bank,
   merchant or formal grievance route for that issue
```

**Important:** This is a reconstructed analytical workflow. It does not prove that every stage or screen has been tested in the current PhonePe app.

## 5. Four distinct merchant scenarios

### Scenario A — Payer debited; merchant transaction confirmation not received

This is the core RBI-defined P2M failed-transaction scenario.

- Confirm that the payer was debited.
- Establish that transaction confirmation was not received at the merchant location.
- Do not replace this fact pattern with a general statement that the merchant has not confirmed an order.
- Apply the relevant RBI reversal framework only when the facts match this scenario.
- Capture the payer's transaction status, transaction reference and available support route.

### Scenario B — PhonePe shows successful, but merchant says it did not receive payment

PhonePe Help states that a payment is marked successful only after PhonePe receives confirmation that the money has reached the merchant. The same Help article says that if the merchant denies receiving the money, the payer should use the `Report Issue` action for the relevant payment (E-015).

This creates an investigation, not an automatic finding:

- What exact status does the payer see?
- What evidence does the payer have?
- What does the merchant's own payment/confirmation record show?
- What does PhonePe's Report Issue flow ask the payer to provide?

A payer-facing screenshot alone cannot establish what the merchant received or recorded.

### Scenario C — Payment successful, but order or booking is not confirmed

PhonePe Help says to contact the merchant directly for an order/booking update. It distinguishes payment-related issues, for which PhonePe says it takes responsibility, from order/booking-related issues that the merchant is better placed to resolve (E-017).

Do not treat an unconfirmed order as proof of a failed UPI payment. The payment may have completed while the merchant's order system or fulfilment process has a separate issue.

### Scenario D — Duplicate payment or merchant-initiated cancellation/refund

PhonePe Help says users who paid twice should contact the merchant and inform it about the duplicate payment; the merchant should check its payment records and refund the excess amount. If the merchant refuses, PhonePe advises contacting the bank with the UTR and raising a complaint. The Help article also advises checking the final payment status before attempting payment again (E-016).

For a cancelled/failed order or booking, PhonePe Help directs the customer to contact the merchant about the refund. Its IRCTC example contains payment-method-specific estimates (UPI 3–5 days, debit/credit cards 7–9 days, wallets 24 hours). These are contextual merchant/booking refund instructions; do not generalise them as the RBI P2M failed-transaction reversal deadline.

## 6. Step-by-step workflow analysis

| Stage | What is currently documented | Payer's information / need | Evidence and limitation |
|---|---|---|---|
| 1. Initiation | Customer initiates a UPI payment to a merchant | Confirm merchant and amount | No current failed P2M transaction screen directly inspected |
| 2. Payment status | PhonePe Help separates merchant issues from pending, failed and successful payment issues | Understand whether payment is pending, failed or successful | E-006 and E-015–E-017; payer-facing status and merchant-side status must be distinguished |
| 3. Debit and merchant confirmation | Core incident requires both payer debit and missing merchant confirmation | Know whether funds left the payer's account and whether merchant confirmation was received | Requires payer transaction/account record and merchant-side confirmation evidence |
| 4A. Missing merchant confirmation | RBI framework defines a specific P2M failure condition | Understand reversal process and expected timeline | Apply RBI T+5 only if the incident facts match the circular |
| 4B. Merchant denies receipt after successful status | PhonePe Help says use `Report Issue` for the relevant payment | Report a payment-related dispute | Help article is visible; exact submitted complaint flow is not verified |
| 4C. Order/booking not confirmed | PhonePe Help advises contacting the merchant | Obtain order/booking update | This is an order/fulfilment issue unless separate payment evidence shows otherwise |
| 5. Duplicate payment | PhonePe Help says contact merchant; bank complaint if merchant refuses refund | Recover excess payment and avoid another duplicate | Confirm each transaction independently; do not infer two successful debits from an order complaint |
| 6. Merchant cancellation/refund | PhonePe Help says contact merchant; its IRCTC example provides method-specific estimates | Know which party initiates the refund | Merchant refund is not the same as automatic reversal for a failed UPI payment |
| 7. Further escalation | PhonePe policy describes customer support, grievance desk and nodal-officer stages | Know the applicable payment or order-dispute route | Exact route depends on the issue and relevant entity; see Section 8 |

## 7. Regulatory overlay — verify before publication

### 7.1 RBI turnaround time for the specific P2M incident

For the specific UPI merchant-payment incident where the payer's account is debited but transaction confirmation is not received at the merchant location, RBI's 20 September 2019 framework specifies auto-reversal within T+5. Compensation of ₹100 per day is payable for applicable delay beyond T+5.

- Do not apply T+5 to every merchant dispute, order cancellation, delivery problem, duplicate payment or merchant-initiated refund.
- Do not assume that “merchant did not confirm the order” means “transaction confirmation was not received at merchant location.”
- Confirm that the payer debit and missing merchant transaction confirmation are both established before applying the framework.

**Official source:** RBI, *Harmonisation of Turn Around Time (TAT) and customer compensation for failed transactions using authorised Payment Systems*, RBI/2019-20/67, 20 September 2019:  
https://rbi.org.in/commonman/Upload/English/Notification/PDFs/CIRCULAR677EC931A7A65E4D99AA957D8E85BC0A2A.PDF

### 7.2 PhonePe merchant guidance

The PhonePe Help screenshots supplied for this teardown state:

- if a merchant denies receiving a successful payment, the payer can report the issue for that payment;
- if a successful payment has an unconfirmed order/booking, PhonePe directs the payer to contact the merchant for an order update;
- for a duplicate payment, PhonePe directs the payer to contact the merchant and, if the merchant refuses the excess refund, contact the bank with the UTR;
- for a cancelled/failed merchant order, PhonePe says the merchant will refund the money and the payer should contact the merchant for refund status.

These statements describe PhonePe's Help guidance. They do not establish merchant-side receipt, actual settlement, actual refund performance or the outcome of an individual complaint.

### 7.3 PhonePe grievance policy and escalation

PhonePe's Grievance Policy, Version 10, dated 16 July 2026, describes support and escalation for PhonePe customers. It states that UPI is a service PhonePe operates as a Third-Party Application Provider (TPAP) in partnership with banks and NPCI. For customer complaints, the policy publishes these service levels:

- Level 1: customer support is available 24 hours a day, 7 days a week; PhonePe commits to a first response within 24 hours and aims to resolve complaints within 15 days.
- Level 2: grievance-desk escalation; PhonePe commits to a first response within 24 hours and aims to resolve complaints within 7 business days.
- Level 3: nodal-officer escalation; PhonePe commits to a first response within 24 working hours and aims to resolve complaints within 7 business days.

These are PhonePe complaint-service targets, not substitutes for a transaction-specific RBI reversal deadline. The policy's RBI–Integrated Ombudsman Scheme section specifies applicability to PhonePe's defined PPI services. Do not copy a generic “RBI Ombudsman” statement from an older Help article into the UPI workflow without confirming the relevant regulated entity and eligible grievance route for the specific UPI issue.

**Official source:** PhonePe Grievance Policy, Version 10, 16 July 2026:  
https://www.phonepe.com/grievance-policy/

### 7.4 NPCI UPI HELP guidance

NPCI's July 2023 UPI HELP guidelines describe complaint functionality for P2P and P2M transactions through the UPI payment app and status checking for pending/failed transactions. The guidelines provide ecosystem-level context; they do not prove that every feature or timing is currently implemented in PhonePe.

**Official source:** NPCI, *UPI HELP Guidelines*, July 2023:  
https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf

## 8. Product-analysis questions

1. Does the payer's PhonePe app clearly distinguish pending, failed and successful merchant-payment states?
2. Does the product distinguish missing merchant transaction confirmation from an order/booking that is not confirmed?
3. Does the app tell the payer what to do next when the payer is debited but merchant confirmation is missing?
4. Is the `Report Issue` route easy to find and does it capture the relevant payment context?
5. Does PhonePe explain which problems should be raised with PhonePe, the payer's bank or the merchant?
6. Does it communicate the applicable P2M reversal deadline for the specific RBI-defined incident?
7. Does the experience help the payer distinguish payment confirmation from order fulfilment and merchant refund?
8. Can a payer track the complaint and understand which party owns the next action?

## 9. Open questions and limitations

- The current PhonePe P2M pending/failed transaction screen has not been directly inspected.
- Merchant-side transaction confirmation and settlement records have not been inspected; the payer's app cannot independently establish what the merchant received.
- The exact complaint-submission, reference-generation and tracking flow has not been completed or verified.
- The RBI T+5 rule must only be applied where payer debit and missing merchant transaction confirmation at the merchant location are established.
- PhonePe's order/booking and merchant-refund guidance must not be treated as the same process as an automatic reversal for a failed UPI payment.
- Actual refund time, merchant reimbursement and order fulfilment outcomes are unknown.
- Do not claim merchant fault, payment-system fault, regulatory non-compliance, customer confusion or causal impact without suitable evidence.

## 10. Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-04 | Initial reconstructed P2M workflow draft. |
| 0.2 | 2026-11-04 | Incorporated PhonePe merchant Help screenshots; separated missing transaction confirmation, successful payment disputes, order/booking issues, duplicate payments and merchant refunds; added RBI P2M scope and escalation caveats. |

---

**Document rule:** Keep this as a working analysis document. Update it only when new evidence is recorded in the evidence register. Do not combine payment reversal, merchant refund and order resolution into one generic “refund” outcome.
