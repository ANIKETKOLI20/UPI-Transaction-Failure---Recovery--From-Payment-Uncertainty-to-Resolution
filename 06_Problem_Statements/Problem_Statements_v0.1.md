# PhonePe Product Teardown — Problem Statements

> **Document status:** Working draft — not validated findings.
>
> **Version:** 0.1  
> **Created:** 2026-11-05  
> **Scope:** PhonePe consumer UPI payment recovery; payer perspective; P2P and P2M scenarios.

## Purpose

This document records the potential user problems identified during Stage 7 (Problem Framing). These statements guide further investigation. They do not establish that PhonePe has a confirmed product defect, that users commonly experience the described difficulty, or that a particular outcome occurs in practice.

## PS-01 — P2P pending-payment clarity

**Scenario:** A payer initiates a P2P UPI transfer and PhonePe displays a pending status.

**Problem statement:**

> When a P2P UPI payment remains pending in PhonePe, the payer needs clear and accessible information about the current transaction status and appropriate next steps, because uncertainty about the payment outcome may make it difficult to determine whether to wait, verify the bank-account status or seek support.

**Evidence currently relevant:**

- E-007: PhonePe Help guidance says to wait up to 48 hours for the bank to update the final status; it describes successful and failed outcomes, notification and checking History.
- E-008: PhonePe Help guidance says banks may take between 2 minutes and 48 hours to confirm the final status.
- E-009 / cancellation-related Help screenshot: PhonePe guidance says an initiated UPI payment cannot be cancelled.
- E-005B: PhonePe Help guidance about failed payments with a debit, refund expectations, bank-statement checks and UTR-based bank contact.

**Evidence status:** PhonePe Help content was directly inspected in screenshots supplied by the researcher. The screenshots establish the customer-facing guidance visible at the time of capture; they do not establish backend processing behaviour or actual customer outcomes.

**What remains unvalidated:**

- Whether the relevant guidance is sufficiently visible at the point where the user sees a pending status.
- Whether users understand the difference between a pending status, final failure and account-level reversal.
- Whether users know what to do if the status remains unresolved.
- Whether users attempt repeat payments or contact support because of uncertainty.

**Do not claim:** That PhonePe provides no pending-payment guidance, that users are demonstrably confused, or that duplicate payments are caused by the current interface.

## PS-02 — P2M payment-confirmation clarity

**Scenario:** A customer pays a merchant using PhonePe. The payer's bank account is debited, PhonePe displays successful, but the merchant says payment confirmation has not arrived.

**Problem statement:**

> When PhonePe displays a merchant payment as successful but the merchant reports that payment confirmation has not been received, the payer needs clear guidance to verify the payment outcome and determine the appropriate next action, such as presenting transaction proof or seeking support. Without sufficiently clear guidance, the payer may remain uncertain and could attempt another payment before the original discrepancy is resolved, creating a potential duplicate-payment risk.

**Evidence currently relevant:**

- E-006E: PhonePe Help categories distinguish merchant payment problems, including a merchant denying receipt of a successful payment, duplicate payment and an order or booking not confirmed.
- E-005D: PhonePe Help guidance on money debited but merchant not receiving payment, including the distinction between PhonePe payment support and merchant-side order/booking resolution.
- P2M scenario exercise: The scenario above was used for analytical practice; it is not a verified transaction observed in PhonePe.

**Evidence status:** The Help categories and guidance were directly inspected in screenshots supplied by the researcher. The specific mismatch between a successful payer-facing status and missing merchant confirmation has not been independently reproduced or verified in a current PhonePe transaction.

**What remains unvalidated:**

- Whether PhonePe's current payer-facing transaction screen can show successful while the merchant has not received confirmation in the specific scenario.
- What confirmation the merchant actually receives and when.
- Whether the payer can easily identify the correct support category.
- Whether users attempt another payment before the first discrepancy is resolved.
- Whether the applicable P2M failed-transaction reversal condition is met.

**Do not claim:** That PhonePe's successful status is incorrect, that the merchant did not receive funds solely because an order was not confirmed, or that duplicate payments commonly result from this scenario.

## Important distinctions to preserve

1. **Transaction status is not the same as account-level money movement.** Check whether the payer was debited and whether the beneficiary or merchant was credited.
2. **Merchant payment confirmation is not the same as order confirmation.** A successful payment does not by itself prove that an order was created or fulfilled.
3. **Payment reversal is not the same as a merchant-initiated refund.** Keep the responsible party and applicable process separate.
4. **A regulatory turnaround time is not an observed processing time.** Apply an RBI rule only when the exact transaction type and failure condition match the circular.
5. **Potential impact is not measured impact.** Confusion, repeat-payment behaviour, duplicate-payment incidence and support burden require user research or suitable internal data.

## Next validation work

- Inspect the current PhonePe P2P pending/failed transaction screens, if an existing safe example is available.
- Inspect the current PhonePe P2M transaction and support journey; do not create an artificial failure or submit a real complaint.
- Verify the complaint initiation, acknowledgement/reference and tracking path without submitting a complaint.
- Confirm exact PhonePe Help wording, URL, publication/update date, app version and capture date in the evidence register.
- Compare each specific P2P/P2M failure scenario with the applicable official RBI/NPCI requirements.
- Use appropriately designed user research or internal event/support data to validate behavioural claims.

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-05 | Created initial P2P and P2M working problem statements from the Stage 7 exercises; recorded evidence links, limitations and validation needs. |
