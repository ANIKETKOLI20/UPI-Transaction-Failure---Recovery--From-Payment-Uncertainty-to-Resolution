# Page 04 — PhonePe Experience Audit

> **Research status:** Observational audit of selected successful transactions and related support/Help journeys. This is not a full audit of every PhonePe screen or transaction outcome.

## 1. Audit approach

The audit examined one existing successful outgoing P2P transaction and one existing successful P2M transaction in the PhonePe consumer app. The researcher inspected the transaction details and opened the associated support journey. Separately, previously collected PhonePe Help screenshots were reviewed for the relevant recovery guidance.

No failed or pending payment was deliberately created. No false complaint, fraud report, chargeback or bank dispute was submitted.

## 2. What was visible in the inspected successful transaction screens

| Element | P2P — observed | P2M — observed | Interpretation |
|---|---|---|---|
| Transaction status | `Transaction Successful` | `Success` / `Successful` | Status was visible in both inspected examples. |
| UTR / transaction reference | Visible | Available | Do not recommend adding UTR as a new feature without identifying a specific usability gap. |
| Recipient / merchant details | Recipient details visible | Merchant / recipient details visible | Relevant counterparty information was available in the inspected examples. |
| Payment details | Visible | Visible | Amount and transaction details were available. |
| Receipt sharing | Available | Available | Receipt-sharing functionality was already present in both inspected examples. |
| Support access | Available | Available | A support entry point was available from both transaction journeys. |
| Issue-specific guidance on the transaction details screen | Beneficiary-not-credited guidance was not visible on the inspected screen | Payment-versus-order explanation was not visible on the inspected screen | These are screen-specific observations, not proof that the guidance is absent elsewhere. |

**P2P evidence note:** These transaction-screen observations were reported by the researcher. The earlier successful outgoing P2P transaction is recorded in the legacy evidence set as E-002; the exact original filename mapping should be retained from the canonical register.

**P2M evidence note:** These transaction-screen observations were reported by the researcher. The original transaction-details screenshot was not supplied with the audit notes; the screen-level observations should therefore be attributed to the inspection notes, not presented as a retained screenshot.

## 3. Support journeys observed

### P2P — beneficiary-not-credited route

After opening Payment Support for the existing successful P2P transaction, the researcher reported seeing recipient name, recipient bank name and bank-account information, together with a bank-dispute option and a prompt for further help. After selecting `Yes, I need help`, the conversation showed transaction amount, payment date/time, the debited bank, and issue suggestions including:

- `Amount not credited to a specific user`
- `Money sent to wrong account / UPI ID`
- Refund/cancellation query
- Offer-related query
- Report fraud for this payment

The researcher did not select an issue that did not apply, submit a complaint, report fraud, or raise a bank dispute. The exact next-step flow after choosing `Amount not credited to a specific user` remains uninspected.

### P2M — merchant-payment and order-related guidance

The supplied support screenshot shows guidance to contact the merchant for refunds, pending orders or cancellations; states that PhonePe cannot cancel or reverse payments; and points to chargeback guidance if the merchant denies help. It also shows a `How to raise a chargeback?` link and the options `Yes, I need help` / `No, I got it`.

The researcher reported that the support context above the cropped portion showed transaction status, UTR, amount, date and time. After selecting `Yes, I need help`, the conversation displayed `Successfully processed` and asked whether further help was needed. The available material does not establish that a formal complaint was registered or that the underlying issue was resolved.

## 4. What PhonePe Help adds to the live-screen observations

| Topic | Help evidence | What the inspected source supports |
|---|---|---|
| Pending status | E-007, E-008 | PhonePe Help describes up to 48 hours for a pending payment to receive a final status update. This is a status-update window, not a refund timeline. |
| Relevant failed-UPI refund guidance | E-013, E-014, E-025 | PhonePe Help describes a 3–5-day refund timeline from the payment date for relevant failed-UPI scenarios. It is not a universal timeline for all pending, successful or merchant-order issues. |
| UTR retrieval | E-015 | PhonePe Help explains where to find the UTR in transaction history/details. |
| Bank follow-up | E-017, E-026 | PhonePe Help describes bank follow-up using the UTR in relevant beneficiary-credit or failed-refund scenarios. The instructions differ by scenario. |
| Pending / failed escalation | E-011, E-018, E-019, E-026 | PhonePe Help describes reporting a payment that remains pending beyond 48 hours, bank chargeback channels and required information, and bank contact if a failed-payment refund has not arrived. |
| Merchant disputes receipt after Successful | E-021 | PhonePe Help states that it marks a payment Successful after receiving confirmation that the money has reached the merchant, and directs a payment-receipt dispute to `Report Issue`. |
| Successful payment; order/booking not confirmed | E-023 | PhonePe Help directs the payer to contact the merchant about the unconfirmed order/booking or service. |

## 5. Critical P2M distinction

PhonePe Help separates two situations that must not be combined:

1. **Merchant disputes receipt of payment after PhonePe displays Successful:** PhonePe's Help article says Successful is displayed after PhonePe receives confirmation that the money reached the merchant; it directs the payer to report the payment-related issue to PhonePe (`E-021`).
2. **Payment is successful but the order, booking or service is not confirmed:** PhonePe's Help article directs the payer to contact the merchant (`E-023`).

The RBI-defined P2M failure category—payer debited but transaction confirmation not received at the merchant location—is a separate, specific incident category (`E-029`). Do not apply its T+5 reversal rule to every merchant complaint, order cancellation, service issue or merchant refund.

## 6. Evidence-backed findings

1. In the successful P2P and P2M transaction examples inspected, transaction status, transaction-reference information, payment details, receipt sharing and support access were available.
2. The inspected successful P2P transaction details screen did not visibly show beneficiary-not-credited guidance; an issue-specific `Amount not credited to a specific user` option was reported later in the support journey.
3. The inspected successful P2M transaction details screen did not visibly show an explicit payment-versus-order explanation; the support conversation included merchant-contact and chargeback guidance.
4. PhonePe Help already provides distinct guidance for P2P beneficiary-credit issues, P2M payment-receipt disputes, and P2M order/booking issues.
5. UTR visibility, receipt sharing and issue-specific support routes were present in the inspected examples. They should not be proposed as entirely new features without further evidence of a usability gap.

## 7. Interpretation and product implications

The evidence does **not** support the claim that PhonePe lacks payment-recovery guidance or transaction-reference functionality. Instead, it suggests two opportunities to validate:

- **Primary opportunity:** Test whether adding a concise explanation of payment completion versus order/booking confirmation to the successful P2M transaction experience improves users' understanding and next-action choice.
- **Secondary opportunity:** Test whether users can discover the existing P2P beneficiary-not-credited and P2M merchant-payment support routes efficiently from transaction details.

These are hypotheses about clarity and discoverability, not confirmed UX defects. No user-comprehension or task-based usability study has yet been conducted.

## 8. Limitations and unverified points

- Only successful P2P and P2M transactions were inspected live; live pending and failed transaction screens were not inspected.
- The P2P support issue option was observed, but the deeper flow after selecting `Amount not credited to a specific user` was not explored because the selected transaction had actually succeeded.
- The full P2M issue-selection flow was not explored because the selected transaction did not represent a genuine unresolved merchant dispute.
- A separate complaint ID, support ticket reference, and formal complaint-tracking mechanism were not established from the inspected material. Their absence has not been proven.
- The meaning of `Successfully processed` in the P2M support conversation was not established; do not treat it as proof of payment-dispute resolution.
- Some live-screen observations were recorded as researcher notes rather than retained redacted screenshots. App version, device/OS, and exact inspection timestamps were not consistently captured.
- No customer interviews, usability tests, production transaction data, or internal PhonePe operational records were available.

## Suggested visual evidence for the PDF

Use a compact comparison table plus two redacted screenshots: (1) successful transaction details and support-entry context, and (2) the P2M support guidance card. Add captions identifying which observations are researcher-reported where a full screenshot is not retained. Never publish UTRs, bank account numbers, UPI IDs, recipient names, phone numbers, or transaction IDs.

---

**Page takeaway:** PhonePe's inspected successful transaction and support journeys already expose transaction references, receipt sharing and issue-specific help. The most defensible opportunities are to test contextual clarity between P2M payment completion and order/booking confirmation, and discoverability of existing recovery routes—not to claim that these capabilities are missing.
