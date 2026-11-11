# PhonePe P2P vs P2M Experience Comparison

**Project:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Product:** PhonePe consumer UPI app  
**Perspective:** Payer  
**Status:** Working comparison based on inspected successful-transaction screens, support interactions, and PhonePe Help screenshots. This is not a full audit of pending/failed live transactions.

---

## 1. Purpose

This comparison identifies what is common and different in the payer's P2P and P2M experiences, and separates directly observed interface elements from Help guidance, interpretation, and unresolved questions.

The comparison must not assume that P2P and P2M have identical recovery paths.

## 2. P2P and P2M are different recovery contexts

### P2P: payer debited, beneficiary not credited

The central recovery question is whether the beneficiary's bank account was credited. The payer may need to check the transaction details and UTR, confirm the beneficiary's bank statement, and follow the relevant PhonePe/bank support guidance.

### P2M: payment status versus merchant order/service confirmation

P2M can involve two distinct questions:

1. **Payment receipt:** Did the payment reach the merchant?
2. **Order or service fulfilment:** Did the merchant confirm the order, booking, or service?

PhonePe Help states that it marks a payment Successful only after receiving confirmation that the money has reached the merchant. The same Help article explains that PhonePe does not receive information about whether the merchant confirmed the order or provided the service. Therefore, a successful payment does not, by itself, prove that the order or service was confirmed.

Do not describe this as merely a payer-side status or say that a successful PhonePe status means the merchant has not received the money. Those statements conflict with the inspected PhonePe Help wording.

## 3. Side-by-side experience comparison

| Area | P2P — inspected experience | P2M — inspected experience | What can be concluded |
|---|---|---|---|
| Successful status | Transaction screen displayed “Transaction Successful”. | Transaction screen displayed a successful status. | Successful status was visible in the inspected examples. |
| Transaction reference | UTR visible. | Applicable transaction reference/UTR visible. | The inspected successful transaction screens already expose reference information. Do not recommend adding UTR access without evidence of a specific accessibility gap. |
| Transaction details | Recipient and payment details visible. | Merchant/payment details, amount and date/time visible. | Core transaction context was available in the inspected examples. |
| Receipt sharing | Available. | Available. | Receipt-sharing functionality was observed in both inspected examples. |
| Support access | Contact PhonePe Support available. | Contact PhonePe Support available. | A support entry point exists on both inspected successful transaction screens. |
| Issue-specific support | Support suggestions included “Amount not credited to a specific user”, wrong account/UPI ID, refund/cancellation, offer-related query and fraud reporting. A bank-dispute route was also shown. | Support guidance distinguished a merchant disputing payment receipt from an order/booking not being confirmed. | The support content is issue-specific; the P2P and P2M recovery questions should remain separate. |
| Transaction context in support | Amount, payment date/time, recipient and debited-bank information were visible in the support conversation. | Amount/date/time, UTR and status were visible in the support conversation described by the user. | Transaction context appeared in both inspected support interactions. Whether every field is automatically attached or populated for all cases has not been verified. |
| Recovery guidance | PhonePe Help screenshots describe pending-status guidance, relevant failed-payment refund guidance, UTR use and bank follow-up. | PhonePe Help covers payment-receipt disputes, order/booking issues, merchant contact and relevant refund guidance. | Guidance exists in Help for both categories. Do not claim recovery guidance is wholly missing. |
| Resolution tracking | A separate complaint ID or formal tracking mechanism was not established in the inspected successful-transaction support path. | A separate complaint ID or formal tracking mechanism was not established in the inspected support interaction. | Tracking remains unverified. Do not state that tracking is absent throughout PhonePe. |
| Pending/failed live screens | Not inspected. | Not inspected. | Current live pending/failed screen behaviour remains an open research gap. |

## 4. Important P2M distinction from PhonePe Help

The inspected PhonePe Help content describes two different cases:

### A. Merchant disputes receipt of payment

PhonePe Help says that a payment is marked Successful only after PhonePe receives confirmation that the money has reached the merchant. If the merchant nevertheless denies receipt, the Help article directs the payer to report the issue against the relevant payment to PhonePe.

### B. Order or booking not confirmed

PhonePe Help says merchants do not inform PhonePe whether an order or service has been confirmed/provided. For an unconfirmed order or booking, the guidance directs the payer to contact the merchant for an update.

These are not interchangeable:

- A dispute about payment reaching the merchant is a **payment-related issue**.
- A dispute about an order, booking, or service is an **order/service issue**.

The RBI's defined P2M failed-transaction category (payer debited but transaction confirmation not received at the merchant location) is a separate regulatory scenario. Apply its T+5 auto-reversal rule only when the incident meets the circular's specified conditions. Do not apply it automatically to every successful-payment/order-confirmation complaint.

## 5. Main comparative insights

### Insight 1 — Both inspected successful transaction screens expose useful payment evidence

The user observed transaction status, payment details, a transaction reference/UTR, receipt sharing, and support access in both P2P and P2M examples. This weakens the case for recommending that PhonePe simply add these existing features.

**Implication:** Any improvement proposal about transaction references should focus on a demonstrated usability or discoverability gap, not on adding a capability that was already visible.

### Insight 2 — The recovery question differs by transaction type

For P2P, the key question is whether the beneficiary's account was credited. For P2M, the payer may need to distinguish payment receipt from order/booking/service confirmation.

**Implication:** Use separate issue-specific explanations and recovery paths rather than one generic “payment failed” flow.

### Insight 3 — Help guidance exists, but its connection to the transaction screen needs evaluation

PhonePe Help contains relevant guidance for P2P beneficiary-not-credited cases and P2M merchant/order issues. The inspected successful P2M transaction screen did not visibly explain the payment-versus-order distinction.

**Implication:** A reasonable product opportunity to test is whether the transaction details experience should surface a concise explanation and an appropriate issue-specific route at the point where the payer needs it.

This is a potential integration/discoverability opportunity, not proof that users are confused or that the existing support route is unusable.

### Insight 4 — Formal complaint tracking remains unverified

The inspected support conversations displayed transaction context and further-help options, but the evidence gathered so far does not establish whether a formal complaint reference or tracking mechanism is generated for a submitted issue.

**Implication:** Keep complaint tracking as an open research question. Do not claim that PhonePe lacks tracking without completing a valid complaint journey or obtaining authoritative documentation.

## 6. Priority research opportunities

| Priority | Opportunity to investigate | Evidence basis | What is still needed |
|---|---|---|---|
| 1 | Make the distinction between payment receipt and order/booking confirmation clear in the P2M transaction context. | The inspected P2M transaction screen did not show this distinction; PhonePe Help explains it separately. | Further inspection of screen entry points and usability/comprehension testing. |
| 2 | Evaluate how easily payers find the correct P2P beneficiary-not-credited or P2M merchant-payment support path. | Relevant issue options and Help articles exist. | Task-based discoverability testing; do not assume poor discoverability. |
| 3 | Establish what complaint reference/status visibility exists after a genuine issue is submitted. | No separate complaint ID/tracking mechanism was established in the inspected support interaction. | Official documentation or a legitimate complaint journey; do not submit a false complaint. |
| 4 | Evaluate transaction-reference retrieval and sharing usability. | UTR/reference and receipt access were already visible in the inspected successful transaction examples. | Test actual retrieval/sharing difficulty before recommending changes. |

## 7. Recommended wording for the teardown

> The inspected PhonePe successful-transaction screens exposed transaction details, applicable reference information, receipt sharing, and support access in both P2P and P2M examples. PhonePe Help also provides issue-specific recovery guidance. The key difference is the recovery question: P2P guidance focuses on beneficiary credit, while P2M guidance must distinguish payment receipt from order or service confirmation. A potential improvement is to make this distinction and the relevant support route more explicit within the P2M transaction experience. This opportunity requires usability validation; the current evidence does not establish user confusion, duplicate-payment behaviour, or a general failure of PhonePe's recovery process.

## 8. Evidence references and provenance

Use the canonical Evidence Register as the source of truth for evidence IDs and screenshot filenames. The following references are based on the current project mapping and must be checked against the latest workbook before publication:

- **P2P pending and refund guidance:** E-007, E-008, E-013, E-014, E-025.
- **P2P UTR and bank follow-up:** E-015, E-017, E-026.
- **P2M merchant payment-receipt dispute:** E-021.
- **P2M order/booking not confirmed:** E-023.
- **RBI-defined P2M transaction-confirmation incident:** E-029.

Live successful transaction screen observations and support-conversation observations should also be linked to their actual screenshot files and evidence IDs once their filenames and IDs are registered. Do not invent IDs for these newly inspected live screens.

## 9. Limitations

- Only existing successful P2P and P2M transactions were inspected.
- Live pending and failed transaction screens were not inspected.
- No genuine beneficiary-not-credited or merchant-confirmation dispute was submitted.
- The support journey was not taken through a false complaint or bank dispute.
- Whether support context is automatically attached, whether a formal complaint ID is generated, and how complaint tracking works remain unverified.
- No participant usability/comprehension testing was conducted.
- No PhonePe internal transaction, support, merchant-confirmation, or repeat-payment data was available.
- The findings describe the inspected examples and supplied Help content; they should not be generalised to all PhonePe users, transactions, devices, app versions, or dates.

## 10. Publication checklist

- [ ] Confirm all cited E-IDs against the latest `Evidence_Register.xlsx`.
- [ ] Register the P2P and P2M live transaction screenshots with exact filenames and inspection dates.
- [ ] Register the support-conversation screenshot(s) with redacted originals.
- [ ] Record PhonePe app version and device/OS if available; otherwise mark unavailable.
- [ ] Keep payment receipt, beneficiary/merchant credit, merchant confirmation, and order/service confirmation distinct.
- [ ] Label the P2M transaction-screen opportunity as provisional and requiring validation.
- [ ] Do not report duplicate-payment incidence or user confusion as findings without data.
- [ ] Preserve the unresolved complaint-tracking question.

---

**Document status:** Working comparison; update after evidence-register reconciliation and any further verified interface inspection.
