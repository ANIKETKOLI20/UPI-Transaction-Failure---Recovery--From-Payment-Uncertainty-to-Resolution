# PhonePe Product Teardown — Problem Statements

> **Document status:** Working draft — not validated findings.  
> **Version:** 0.2 — evidence-ID reconciled and P2M scope clarified  
> **Created:** 10 November 2026  
> **Scope:** PhonePe consumer UPI payment recovery; payer perspective; domestic P2P and P2M scenarios.

## Purpose

This document records the potential user problems guiding the teardown. The statements do not establish a confirmed PhonePe product defect, the prevalence of a problem, or actual customer behaviour.

## PS-01 — P2P pending-payment clarity

**Scenario:** A payer initiates a P2P UPI transfer and PhonePe displays a pending status.

**Problem statement:**

> When a P2P UPI payment remains pending in PhonePe, the payer needs clear and accessible information about the current transaction status and appropriate next steps, because uncertainty about the payment outcome may make it difficult to determine whether to wait, verify the bank-account status or seek support.

**Evidence currently relevant:**

- E-007: PhonePe Help guidance says to wait up to 48 hours for final status and describes the possible successful/failed outcomes.
- E-008: PhonePe Help explains its stated 48-hour final-status update window.
- E-010: PhonePe Help says an initiated UPI payment cannot be cancelled and advises waiting for the final status.
- E-011: PhonePe Help describes reporting a payment that remains pending after 48 hours.
- E-013; E-014; E-025; E-026: PhonePe Help's relevant failed-UPI refund and bank-follow-up instructions.

**Evidence status:** These are statements in PhonePe Help screenshots inspected by the researcher. They establish the guidance visible in the supplied material, not actual bank processing or individual payment outcomes.

**What remains unvalidated:**

- Whether the guidance is sufficiently visible from the live pending transaction screen.
- Whether users understand the difference between a pending status, final failure and account-level reversal.
- Whether users know when to check the bank statement or contact the bank.
- Whether users attempt repeat payments or contact support because of uncertainty.

**Do not claim:** That PhonePe provides no pending-payment guidance, that users are demonstrably confused, or that duplicate payments are caused by the current interface.

## PS-02 — P2M payment-receipt versus order/booking issue clarity

**Scenario:** A payer sees a successful merchant payment in PhonePe, but the merchant either disputes receipt of the money or has not confirmed the order/booking.

**Problem statement:**

> When a payer sees a successful merchant payment but the merchant disputes receipt of the payment or the order/booking remains unconfirmed, the payer needs to distinguish a payment-receipt dispute from an order/booking issue and follow the appropriate resolution route. The payer may need to understand PhonePe's stated meaning of Successful, use Report Issue for a payment-receipt dispute, or contact the merchant for an order/booking update.

This is a potential comprehension and support-path problem, not a confirmed interface defect. PhonePe Help already documents distinct routes: it says Successful is shown after PhonePe receives confirmation that money has reached the merchant and directs a merchant receipt dispute to Report Issue (E-021); it separately directs an unconfirmed order/booking to the merchant (E-023).

**Evidence currently relevant:**

- E-006: Payment Issues Help categories.
- E-021: Merchant denies receipt after PhonePe Successful; Help states PhonePe's successful-status criterion and the Report Issue route.
- E-022: Duplicate-payment guidance, including checking final status before retrying.
- E-023: Successful payment but order/booking not confirmed; Help directs the customer to contact the merchant.
- E-024: Merchant-initiated refund guidance for cancelled/failed order/booking.

**Important separate regulatory scenario:** RBI's P2M failed-transaction category concerns payer debit where transaction confirmation is not received at the merchant location (E-029). Do not assume that an unconfirmed order/booking or every merchant report after PhonePe Successful automatically meets that condition.

**What remains unvalidated:**

- Whether users understand PhonePe's stated meaning of Successful.
- Whether users distinguish a merchant payment-receipt dispute from an order/booking issue.
- Whether users can locate the Report Issue path from the live transaction screen.
- Whether users can identify when to contact the merchant instead of PhonePe.
- Whether users attempt another payment before checking the original transaction.
- What merchant/acquirer records show in an actual receipt dispute.

**Do not claim:** That PhonePe's Successful status is incorrect; that an unconfirmed order proves the underlying UPI payment failed; that the merchant's bank was not credited based only on a merchant statement; or that duplicate payments commonly result from this scenario.

## Important distinctions to preserve

1. **PhonePe status vs account-level money movement:** Attribute PhonePe's stated Successful definition to PhonePe Help; do not treat a screenshot as an independent bank settlement record.
2. **Merchant payment receipt vs order confirmation:** PhonePe Help separates a merchant dispute about receiving the amount from an unconfirmed order/booking.
3. **Automatic UPI reversal vs merchant-initiated refund:** These have different triggers and responsible parties.
4. **Regulatory turnaround time vs product guidance:** Apply an RBI TAT only when the facts match the specific regulatory incident category.
5. **Potential behaviour vs measured behaviour:** Confusion, repeat-payment intention, actual repeat attempts and duplicate successful payments require different forms of evidence.

## Next validation work

- Inspect the current PhonePe P2P pending/failed transaction screens using safe, existing examples.
- Inspect the current P2M transaction details and the Report Issue route without submitting a real complaint.
- Test whether participants distinguish the merchant receipt-dispute route from the order/booking route.
- Verify whether UTR/reference details are easy to find in the current live P2M transaction flow.
- Confirm the exact complaint acknowledgement/reference and tracking path if accessible without submitting a false complaint.
- Revalidate regulatory and PhonePe policy claims against current official sources before PDF export.

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-05 | Initial P2P and P2M working problem statements. |
| 0.2 | 2026-11-10 | Reconciled evidence IDs and revised P2M framing to distinguish merchant receipt dispute from order/booking not confirmed, following E-021 and E-023. |
