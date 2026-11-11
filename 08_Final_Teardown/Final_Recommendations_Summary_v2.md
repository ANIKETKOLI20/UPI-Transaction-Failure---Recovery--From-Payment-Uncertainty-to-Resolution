# PhonePe Product Teardown — Revised Product Recommendations

**Working title:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Product:** PhonePe consumer UPI app  
**Perspective:** Payer  
**Scope:** Domestic P2P and P2M payment-status communication and recovery guidance  
**Document status:** Revised working draft based on the Help Centre evidence and the successful transaction/support screens inspected by the researcher.

---

## 1. Executive summary

This teardown examines how PhonePe communicates transaction status and helps payers find an appropriate recovery path when a P2P beneficiary-credit issue or a P2M merchant/order issue is reported.

The research found that PhonePe already provides substantial recovery information through its Help content and support journeys. In the inspected successful P2P and P2M transaction screens, transaction references, payment details, receipt-sharing functionality and support access were visible. The support journeys also exposed issue-specific routes, including **“Amount not credited to a specific user”** for P2P and merchant-related guidance for P2M.

Therefore, the teardown should **not** recommend adding basic UTR visibility, receipt sharing, or a new generic support route as though those capabilities do not exist.

The strongest product opportunity identified so far is narrower: the inspected successful P2M transaction-details screen did not visibly explain the distinction between **payment completion** and **order/booking confirmation**, while PhonePe Help separately explains that PhonePe receives a payment confirmation but does not receive confirmation that the merchant accepted the order or provided the service.

A second, lower-confidence opportunity is to test whether people can easily discover the existing issue-specific recovery routes from transaction details. The routes exist in the inspected support journey, but their discoverability and comprehension have not been tested with users.

These are opportunities for further validation, not proven defects or measured user problems.

## 2. Evidence-backed observations

### 2.1 Successful P2P transaction screen

The researcher reported that the inspected successful P2P transaction screen displayed:

- Transaction status: “Transaction Successful”.
- UTR/reference information.
- Recipient details.
- Payment details.
- Receipt-sharing option.
- Support access.

The researcher did not see beneficiary-not-credited guidance directly on that transaction-details screen.

### 2.2 P2P support journey

The inspected support journey displayed recipient and bank-related details and offered further-help options. The researcher reported seeing issue suggestions including:

- Amount not credited to a specific user.
- Money sent to a wrong account or UPI ID.
- Refund/cancellation-related query.
- Offer-related query.
- Report fraud for this payment.

PhonePe Help material separately contains guidance for pending status, failed-payment refunds, UTR lookup, contacting the bank, and reporting/escalating eligible issues. The existing issue-specific route should not be described as missing.

### 2.3 Successful P2M transaction screen

The researcher reported that the inspected successful P2M transaction screen displayed:

- Successful transaction status.
- Transaction reference/UTR.
- Payment details.
- Receipt-sharing option.
- Support access.

The researcher did not see an explicit explanation on that inspected screen distinguishing payment completion from order/booking confirmation.

### 2.4 P2M support journey and PhonePe Help distinction

The inspected support content advised users to contact the merchant for refunds, pending orders, or cancellations, stated that PhonePe cannot cancel or reverse payments, and provided a chargeback guidance link for cases where the merchant denies help. The researcher also reported seeing transaction amount, date/time, payee and debited-bank context in the support conversation, with UTR/status visible in the preceding context.

PhonePe Help article **“What if the merchant denies having received the amount for a successful payment?”** states that PhonePe marks a payment successful after receiving confirmation that the money has reached the merchant. The same article distinguishes this from whether the merchant has confirmed the order or provided the service. It directs a payment-receipt dispute to PhonePe's Report Issue route. A separate order/booking article directs the user to contact the merchant for an order or booking that has not been confirmed. (Use the canonical evidence IDs in the Evidence Register; the working mapping identified these as E-021 and E-023.)

### 2.5 Interpretation boundaries

- A successful payment status must not be described as merely a payer-side acknowledgement; PhonePe Help states that its successful status follows confirmation that money reached the merchant.
- Payment completion is not the same as order/booking confirmation.
- The existence of a Help article or support route does not prove that users can discover or understand it easily.
- One inspected transaction screen does not establish how every PhonePe transaction screen behaves.
- No user-comprehension study, usability study, or production transaction-event analysis has yet been conducted.

## 3. Revised opportunity prioritisation

| Priority | Opportunity | Evidence basis | Confidence | Decision |
|---|---|---|---|---|
| 1 | Make the distinction between payment completion and order/booking confirmation clearer in the successful P2M transaction experience. | The inspected P2M details screen did not visibly show this distinction; PhonePe Help explicitly distinguishes payment confirmation from order/service confirmation. | Moderate for the screen observation; low-to-moderate for user impact until tested. | Retain as the primary product opportunity to validate. |
| 2 | Improve discoverability of existing issue-specific recovery paths from transaction details for P2P and P2M. | Support access and issue-specific options were observed; the researcher did not see beneficiary-not-credited guidance directly on the P2P details screen. | Low-to-moderate; no task-based discoverability testing yet. | Retain as a secondary research opportunity, not a confirmed defect. |
| 3 | Improve access to UTR, transaction details and receipt sharing. | These were already visible/available in both inspected successful transaction screens. | High confidence that these capabilities were present in the inspected examples. | Do not recommend adding them. Revisit only if testing identifies a specific usability problem. |
| 4 | Add a new generic support or merchant-issue route. | Issue-specific support paths already appeared in the inspected journeys and Help content. | High confidence that relevant routes exist in the inspected journeys. | Remove as a new-feature recommendation. Consider improving route labelling/discoverability only if validated. |

## 4. Revised product recommendations

### Recommendation 1 — Clarify payment completion versus order/booking confirmation

**Priority:** Primary opportunity for validation  
**Problem to investigate:** A payer may see a successful P2M payment and still have an unconfirmed order or booking. The inspected transaction-details screen did not visibly explain this distinction, although PhonePe Help provides a separate explanation.

**Proposed change:** Add a concise, contextual explanation in the successful P2M transaction details experience that separates:

1. **Payment status:** PhonePe's status for the UPI payment. PhonePe Help says Successful is displayed after PhonePe receives confirmation that money has reached the merchant.
2. **Order/booking status:** Whether the merchant has accepted or confirmed the order/booking or will provide the service. PhonePe Help says it does not receive this confirmation from the merchant.

Provide an appropriate link or next step for an unconfirmed order/booking that directs the payer to the merchant, consistent with PhonePe's existing Help guidance. Keep payment-receipt disputes distinct and route those to the existing PhonePe Report Issue path.

**Rationale:** It connects the explanation already available in Help to the transaction context where the payer is likely to need it, without implying that a successful payment is unconfirmed at the bank level.

**Expected benefit (hypothesis):** Better payer comprehension of payment completion versus order/booking confirmation, and more accurate selection of the next action.

**Primary validation metric:** P2M Correct Next-Action Rate in a task-based comprehension/usability test.

**Supporting metric:** Payment-versus-order distinction comprehension rate.

**Guardrails:** Incorrect payment/order classification rate and incorrect repeat-payment intention rate.

**Validation required:** Compare the existing transaction details experience with a clearly labelled treatment concept. Do not claim actual improvement until testing is conducted.

### Recommendation 2 — Improve discoverability of existing issue-specific recovery paths

**Priority:** Secondary opportunity for validation  
**Problem to investigate:** The support route exists, but beneficiary-not-credited guidance was not visible directly on the inspected successful P2P transaction details screen. The user had to enter the support journey to see issue-specific suggestions.

**Proposed change:** Test whether a more visible contextual entry point—such as a clearly labelled “Payment issue?” or “Recipient has not received the money?” link—would help payers find the existing issue-specific support route faster. For P2M, maintain separate paths for a merchant disputing payment receipt and an order/booking not confirmed.

**Rationale:** This builds on existing support capabilities rather than duplicating them.

**Expected benefit (hypothesis):** Faster discovery of the relevant recovery route and fewer users selecting an unrelated support category.

**Primary validation metric:** Issue-specific support-path task success / Support-Path Selection Accuracy.

**Supporting metric:** Time to reach the appropriate support guidance.

**Guardrails:** Incorrect issue-category selection and incorrect repeat-payment intention.

**Validation required:** Conduct task-based usability tests. The current evidence does not establish that discoverability is poor for users generally.

## 5. Recommendations explicitly removed

The following should not appear as new-feature recommendations in the final case study unless new evidence reveals a specific usability gap:

- **Add UTR to transaction details:** UTR/reference information was visible in the inspected successful P2P and P2M transaction screens and described in PhonePe Help.
- **Add receipt-sharing functionality:** Receipt sharing was available in both inspected successful transaction screens.
- **Create a new generic support route:** Support access and issue-specific options already appeared in the inspected journeys.
- **Claim that PhonePe's successful P2M status does not confirm merchant payment receipt:** This contradicts the wording of the inspected PhonePe Help article. The relevant distinction is payment confirmation versus order/booking confirmation.
- **Claim that users make duplicate payments frequently:** No behavioural or production data supports this claim.

## 6. P2P and P2M recovery distinctions to preserve

| Dimension | P2P | P2M |
|---|---|---|
| Core outcome to verify | Whether the beneficiary's bank account was credited. | Whether the merchant received payment confirmation; separately, whether the order/booking was confirmed. |
| Existing support route observed | “Amount not credited to a specific user” issue option. | Merchant payment issue / Report Issue guidance; separate merchant contact guidance for order/booking issues. |
| Transaction references | UTR/reference was visible in the inspected successful transaction context. | UTR/reference was visible in the inspected successful transaction context. |
| Key distinction | Payer debit does not by itself prove beneficiary credit. | Payment confirmation and order/booking confirmation are different outcomes. |
| Remaining live-flow gap | Pending/failed P2P screens and complete complaint tracking not inspected. | Pending/failed P2M screens and complete complaint tracking not inspected. |

## 7. Regulatory and timeline cautions

Keep the following concepts separate in the final report:

- PhonePe Help's stated up-to-48-hour pending-status guidance.
- PhonePe Help's 3–5-day refund guidance for relevant failed-payment scenarios.
- RBI's specified T+1 P2P and T+5 P2M auto-reversal categories under the cited 2019 circular.

Do not present the PhonePe Help 3–5-day guidance as a universal replacement for the RBI-defined timelines. Apply the RBI TAT only when the incident facts match the circular's specified category. Check for subsequent regulatory amendments before publication.

## 8. Research limitations

1. The live P2P and P2M screens inspected were successful transactions only.
2. Live pending and failed transaction screens have not been inspected.
3. The complete complaint submission, reference-number and tracking journey has not been verified.
4. Issue-specific support options were observed, but no false complaint or bank dispute was submitted.
5. The researcher did not conduct participant usability or comprehension testing.
6. No internal PhonePe event data or production metrics were available.
7. Screenshot inspection reflects the researcher's app experience at the time of inspection and should not be generalized to every app version or user.

## 9. Final recommendation statement

> PhonePe already provides transaction references, receipt sharing and issue-specific recovery guidance in the successful transaction and support experiences inspected. The strongest opportunity identified is to make the distinction between payment completion and order/booking confirmation more explicit within the P2M transaction experience. A secondary opportunity is to test whether users can discover the existing P2P and P2M recovery routes efficiently. Both opportunities require user validation before being treated as confirmed UX problems.

## 10. Publication checklist

- [ ] Confirm canonical Evidence IDs against `03_Evidence_Register/Evidence_Register.xlsx`.
- [ ] Attach redacted screenshots for each live transaction/support observation.
- [ ] Record inspection date, device and app version if available; do not invent missing metadata.
- [ ] Cite the PhonePe Help article for its definition of Successful and its order/booking distinction.
- [ ] Cite the RBI circular only for its specified P2P/P2M incident categories.
- [ ] Keep hypotheses and expected benefits labelled as unvalidated.
- [ ] Do not include hypothetical exercise percentages as research findings.
- [ ] Verify the complete final report and PDF after export.
