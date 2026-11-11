# Page 5 — Research Findings & Problem Analysis

> **Document status:** Working draft for the final PhonePe product teardown.  
> **Research basis:** PhonePe Help screenshots inspected on 3 November 2026; live successful P2P/P2M transaction and support journeys inspected on 10 November 2026; official source documents recorded in `02_Official_Documentation/Source_Index.md`.  
> **Important boundary:** These are findings from a limited, researcher-led interface and content audit. No user interviews, usability sessions, controlled experiments, production event data, or merchant-side transaction records were collected.

## Central research question

How does PhonePe communicate UPI transaction outcomes and support payer recovery across P2P beneficiary-credit and P2M merchant/order-confirmation scenarios?

## Finding 1 — Successful transaction screens expose useful payment information and support access

**Evidence**

- The inspected successful P2P transaction screen displayed the status as **Transaction Successful**, recipient details, payment details, UTR, receipt sharing, and support access.
- The inspected successful P2M transaction screen displayed the successful status, transaction reference, payment details, receipt sharing, and support access.
- In the inspected P2P support journey, recipient and bank details were shown, alongside issue suggestions including **Amount not credited to a specific user** and a bank-dispute route.
- In the inspected P2M support conversation, transaction context (amount, date/time, UTR and status) was visible with payment-related guidance and an option to request further help.

**Interpretation**

The inspected successful transaction journeys already provide core payment details, transaction references, receipt sharing and access to support. The teardown should not recommend adding these capabilities as if they were absent.

**Product implication**

Do not propose a new UTR field, receipt-sharing feature, or generic support entry point on the basis of the current evidence. Further work should test whether users can find and correctly use the existing options.

**Evidence references**

- `01_Product_Screenshots/Transaction_Screens/P2P_Successful_Transaction_Audit.md`
- `01_Product_Screenshots/Transaction_Screens/P2M_Successful_Transaction_Audit.md`
- Relevant original screenshots in `01_Product_Screenshots/Transaction_Screens/` (personal and transaction identifiers must remain redacted in public materials).

**Confidence:** High for the specific inspected screens; not evidence that every PhonePe transaction type or app version has identical behaviour.

## Finding 2 — PhonePe Help describes distinct pending-status, failed-payment and bank-follow-up steps

**Evidence**

The inspected PhonePe Help articles state that:

- a pending UPI payment may take up to 48 hours from the payment time to receive a final status;
- a pending payment that remains pending after 48 hours can be reported from History;
- for relevant failed UPI payments, the Help guidance describes a refund within 3–5 days from the payment date;
- the payer should check the relevant bank statement and contact the bank with the UTR if the refund is not received within the stated period; and
- a UTR-location article explains where the 12-digit reference appears in transaction details.

**Interpretation**

The 48-hour period is a stated final-status update window. The 3–5-day guidance is a separate refund expectation for relevant failed-payment scenarios. They should not be described as one continuous or interchangeable timeline.

**Product implication**

A possible improvement is to surface the relevant next step and its applicable timeline in the transaction context, rather than requiring the payer to infer which Help article applies. Whether users currently struggle to distinguish the timelines has not been tested.

**Evidence references**

- E-007 and E-008 — pending status and explanation of the 48-hour window.
- E-013, E-014 and E-025 — relevant failed-payment/refund guidance (use the exact article-specific mapping in `Evidence_Register.xlsx`).
- E-015 — UTR location guidance.
- E-017 and E-026 — bank follow-up / beneficiary-credit guidance, as mapped in the canonical register.

**Confidence:** High for what the inspected Help articles state; no evidence of actual user comprehension or actual refund duration.

## Finding 3 — PhonePe Help separates merchant payment-receipt disputes from order/booking problems

**Evidence**

- The merchant-dispute article says PhonePe marks a payment successful after receiving confirmation that the money has reached the merchant. It then directs the payer to report the issue to PhonePe when the merchant denies receipt. (E-021)
- The order/booking article says the merchant is better placed to resolve an unconfirmed order or booking and directs the payer to contact the merchant. (E-023)
- The RBI-defined P2M failure category—payer debited but transaction confirmation not received at the merchant location—is a separate, specific incident condition. It must not be applied to every successful-payment/order dispute. (E-029; see the RBI circular in `02_Official_Documentation/RBI/`.)

**Interpretation**

Three situations must remain separate:

1. payer debited but merchant transaction confirmation not received;
2. PhonePe shows successful and the merchant disputes receipt of payment; and
3. payment is successful but the merchant has not confirmed the order, booking, or service.

The support owner and applicable resolution process differ by scenario.

**Product implication**

Keep separate, clearly labelled routes for a payment-receipt dispute and an order/booking issue. Do not route both to the same generic refund instruction or describe every merchant complaint as an RBI T+5 failed transaction.

**Evidence references**

- E-021 — merchant disputes receipt after a successful payment.
- E-023 — order/booking not confirmed after successful payment.
- E-029 — RBI-defined P2M merchant-confirmation failure scenario.

**Confidence:** High for the wording of the inspected Help articles and the cited RBI scenario; merchant-side receipt and order records were not independently inspected.

## Finding 4 — The inspected successful P2M transaction screen did not visibly explain the order-confirmation distinction

**Evidence**

The inspected successful P2M transaction details screen exposed transaction status, reference information, payment details, receipt sharing and support access. In the review, no explicit explanation distinguishing payment completion from order/booking confirmation was visible on that particular screen. PhonePe's Help article does explain that distinction (E-021 and E-023).

**Interpretation**

There may be a contextual gap between the transaction details view and the more detailed Help explanation. This is a screen-specific observation—not proof that the distinction is absent elsewhere in the app, or that users misunderstand it.

**Product implication**

Test a concise contextual explanation or issue choice on the successful P2M transaction screen, for example separating **payment received by merchant** from **order/booking confirmed** and linking to the appropriate existing support path. Treat this as a concept to validate, not a confirmed defect.

**Evidence references**

- `01_Product_Screenshots/Transaction_Screens/P2M_Successful_Transaction_Audit.md`
- E-021 and E-023 — PhonePe Help explanations of payment receipt versus order/booking confirmation.

**Confidence:** Moderate. The observation is direct but limited to one inspected successful P2M transaction screen; the broader app journey has not been fully inspected.

## Consolidated problem analysis

The evidence does **not** establish that PhonePe lacks payment-recovery functionality. The inspected screens and Help content show transaction references, receipt sharing, support access, issue-specific guidance, bank follow-up instructions, and separate handling for payment-receipt versus order issues.

The most defensible product opportunity is narrower:

> **On the inspected successful P2M transaction screen, the distinction between payment completion and order/booking confirmation was not explicit. PhonePe's Help content explains the distinction, creating an opportunity to test whether a concise, contextual explanation and direct access to the relevant existing support route would improve users' understanding and next-action selection.**

A secondary opportunity is to test the discoverability of existing P2P/P2M recovery options. Discoverability has not yet been measured, so it should remain a validation question rather than a confirmed usability problem.

## Hypotheses to validate — not findings

| Hypothesis | Why it is plausible | Required validation |
|---|---|---|
| Some payers may not distinguish payment completion from order/booking confirmation when viewing a successful P2M transaction. | The inspected transaction details screen did not show the distinction, while Help content explains it separately. | Comprehension/usability testing using the actual screen and a neutral scenario. |
| Some payers may have difficulty identifying the correct existing support route for payment-receipt versus order issues. | PhonePe exposes different guidance for the two issues. | Task-based discoverability testing; measure correct route selection and task completion. |
| Some payers may misunderstand the relationship between the 48-hour final-status window and the 3–5-day failed-payment refund guidance. | The Help articles describe two different stages and time references. | Comprehension testing with the exact Help content; do not infer confusion from the wording alone. |

## What this research cannot conclude

- It cannot estimate PhonePe's UPI failure rate or claim a reliability problem.
- It cannot establish actual user confusion, repeat-payment intention, or duplicate-payment frequency.
- It cannot establish actual bank reversal durations from published turnaround-time guidance.
- It cannot establish the full current behaviour of P2P/P2M pending and failed screens; those live states were not directly inspected.
- It cannot confirm the full complaint-submission, complaint-reference generation, or tracking journey. The inspected support interaction showed transaction context and further-help options, but no separate complaint ID or complete tracking flow was established.
- It cannot verify merchant-side account credit, merchant system receipt, or order creation without merchant-side records.

## Reporting rules

- Use **observed** for the exact screens and articles inspected.
- Attribute Help content to **PhonePe Help says...** rather than presenting it as independently measured transaction performance.
- Use **may**, **could**, and **hypothesis** for untested user-behaviour explanations.
- Keep the P2P T+1 and P2M T+5 regulatory scenarios separate and apply them only when the incident facts match the RBI-defined conditions.
- Do not reuse a generic 3–5-day refund statement as a universal UPI rule or as a substitute for the applicable RBI turnaround time.

## Suggested visual for the PDF

Use a four-row findings panel with columns **Evidence**, **What was observed**, **Interpretation**, and **Product implication**. Highlight Finding 4 as the main product opportunity, but label it **screen-specific / requires validation**. Keep the full evidence IDs in small, readable footnotes and place the complete register in the GitHub repository.
