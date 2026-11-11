# Page 07 — Prioritised Product Recommendations

**Case study:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Product examined:** PhonePe consumer UPI app  
**Document status:** Portfolio recommendation draft — proposed improvements, not implemented or experimentally validated

## 1. Recommendation summary

The audit did not find that PhonePe lacks transaction references, receipt sharing, or issue-specific support guidance. These capabilities were visible in the successful P2P/P2M transaction journeys and/or documented in PhonePe Help. The strongest evidence-backed opportunity is narrower: make the distinction between **payment completion** and **order/booking confirmation** clearer at the point where a user views a successful merchant payment, and make the existing relevant support paths easier to reach from that context.

The recommendations below are designed to surface and connect existing guidance, not to claim that PhonePe needs to build an entirely new dispute or refund system.

## 2. Prioritisation method

Recommendations are prioritised using four practical criteria:

1. **Evidence strength:** Is the issue supported by direct screen inspection or official Help content?
2. **User consequence:** Could ambiguity plausibly lead to an incorrect next action or unnecessary support contact?
3. **Scope and feasibility:** Can the change be made in the payer-facing transaction/support experience without assuming a backend change?
4. **Validation need:** Can the proposed improvement be tested with a controlled usability/comprehension study before rollout?

This is a qualitative portfolio prioritisation, not a quantified RICE score. No engineering effort, reach, impact, or confidence scores are available from PhonePe internal data.

## 3. Priority 1 — Clarify payment completion versus order/booking confirmation

### Observed evidence

- In the inspected successful P2M transaction screen, the payer could see the successful status, transaction reference, payment details, receipt-sharing option and support access.
- No explicit payment-versus-order/booking distinction was visible on that inspected transaction screen.
- PhonePe Help separately explains that a successful payment reflects confirmation that the money reached the merchant, while PhonePe may not know whether the merchant confirmed the order or supplied the service.
- PhonePe Help directs a payer to contact the merchant for an unconfirmed order/booking, while a merchant dispute about receipt of payment follows a payment-issue support route.

### Problem framing

When a P2M payment is displayed as successful but the order or booking is not confirmed, the payer may not immediately know whether the unresolved issue concerns the payment itself or the merchant's order/service process. The inspected transaction screen did not visibly explain this distinction, although relevant guidance exists in PhonePe Help.

This is a **potential clarity and discoverability gap** based on one inspected successful P2M screen. It is not proof that users are confused or that every PhonePe transaction screen omits the explanation.

### Proposed change

Add a compact, contextual explanation to the successful P2M transaction details view:

> **Payment successful**  
> PhonePe has received confirmation that the payment reached the merchant. This does not confirm that your order or booking has been accepted.

Present two clearly differentiated next-step choices:

- **Order or booking not confirmed** — contact the merchant for the order, booking, goods or service update.
- **Merchant says payment was not received** — open the existing payment-issue / Report Issue route for this transaction.

Where appropriate, include a brief safety reminder:

> Before paying again, check the status and details of this original transaction.

The wording should be reviewed with PhonePe's legal, compliance and content-design teams. It must not imply that a successful payment is pending, failed, or automatically eligible for reversal.

### Expected benefit

- Help the payer distinguish payment outcome from order/service fulfilment.
- Make the next support owner clearer: merchant for the unconfirmed order/booking; PhonePe's existing payment-issue route for a merchant receipt dispute.
- Potentially reduce avoidable misclassification and premature repeat-payment intent. These outcomes require user testing and product data to verify.

### Priority rationale

**Highest priority.** The opportunity is grounded in a direct observation from the successful P2M transaction screen and an explicit distinction in PhonePe Help. It is also a focused payer-facing content/navigation change that can be evaluated before implementation.

## 4. Priority 2 — Surface existing issue-specific support paths from transaction context

### Observed evidence

- The inspected successful P2M transaction exposed support access.
- The P2M support/help content distinguished a merchant receipt dispute from an order/booking issue.
- The inspected P2P support journey displayed transaction context and issue suggestions, including an amount-not-credited option, as well as a bank-dispute guidance route.
- The inspected support context displayed transaction details such as amount, date/time, recipient and/or UTR/status. Whether all details are automatically attached to a formal complaint was not established.

### Problem framing

Relevant support paths exist, but the payer may need to move through support prompts or Help categories to identify the appropriate route. The audit did not establish end-to-end discoverability with multiple users, so this is a hypothesis to validate rather than a confirmed usability defect.

### Proposed change

From the transaction details screen, provide a concise **Get help with this payment** entry point that presents issue choices tied to the current payment context, for example:

- Money debited / beneficiary or merchant says it was not received.
- Order or booking not confirmed.
- Refund or reversal not received.
- Wrong recipient or another payment issue.

Route each choice to the relevant existing PhonePe guidance and support flow. Carry transaction context forward where technically and legally appropriate, but verify the actual data-passing behaviour before claiming it is already automatic or proposing a change to it.

### Expected benefit

- Reduce navigation between transaction history and general Help categories.
- Help users select the support route that matches their issue.
- Preserve the transaction details needed to discuss the original payment, subject to privacy and security controls.

### Priority rationale

**Second priority.** The existence of support options is observed; the ease of finding and completing the correct route has not been usability-tested. Validate discoverability before deciding the scale of the change.

## 5. What should not be recommended as new functionality

The inspected screens and Help material already showed the following. Do not present them as missing features or proposed net-new capabilities:

| Capability | Evidence from this audit | Recommendation decision |
|---|---|---|
| Transaction reference / UTR visibility | Visible in inspected transaction/support context; Help explains where to find it | Do not recommend simply adding UTR visibility |
| Payment details | Amount, date/time and transaction details were visible in inspected flows | Do not recommend adding basic transaction details without a specific verified gap |
| Receipt sharing | Available on inspected successful transaction screens | Do not recommend adding receipt sharing |
| Support access | Available from inspected successful transaction screens | Do not recommend creating support access from scratch |
| Issue-specific recovery guidance | PhonePe Help and support suggestions contain relevant payment/order issue paths | Improve contextual surfacing and clarity, not duplicate the guidance |
| Bank dispute / escalation guidance | Bank-dispute or chargeback guidance was visible in the inspected support/help journey | Do not describe this route as absent; exact completion/tracking behaviour remains unverified |

## 6. Proposed validation plan

The recommendations have not been implemented or tested. Validate them before rollout using a controlled prototype or moderated/unmoderated comprehension study.

### Study design

- **Population:** People who use UPI to pay merchants; define eligibility before recruitment.
- **Task scenario:** Participant sees a successful PhonePe P2M transaction, but the merchant has not confirmed the order/booking. Ask the participant to explain what the displayed payment status means and choose the next action.
- **Control:** Existing transaction details and current Help/support route as captured during the audit.
- **Treatment:** Revised contextual explanation and clearly separated order/booking versus payment-receipt support choices.
- **Randomisation unit:** Participant level; each participant sees only one version to reduce learning/contamination.
- **Method:** Comprehension and next-action testing. Do not ask leading questions such as “Were you confused?”

### Metrics

**Primary metric — Correct Next-Action Rate**

- **Numerator:** Eligible participants who select the appropriate next action for the scenario presented, before attempting another payment.
- **Denominator:** All eligible participants who view the assigned scenario and have a valid opportunity to answer.
- **Unit:** Participant, one scored task per participant.
- **Scoring:** Correct / partially correct / incorrect / unable to answer, with scoring rules defined before sessions begin. Predefine how partial responses are handled in the primary result.

**Supporting metrics**

- **Payment-Status Comprehension Rate:** Share of eligible participants who correctly explain what PhonePe's Successful status indicates in the scenario.
- **Support-Path Selection Accuracy:** Share of eligible participants who choose the route matching the stated issue (merchant order/booking issue versus payment-receipt dispute).

**Guardrails**

- **Incorrect Repeat-Payment Intention Rate:** Share of eligible participants who say they would make another payment before checking or resolving the original transaction.
- **Incorrect Order/Payment Classification Rate:** Share who mistake an order/booking issue for a payment failure, or the reverse.

These are research measures of comprehension and stated intention. They are not live duplicate-payment incidence or observed customer behaviour.

### Decision rule

Consider a broader rollout only if:

1. The primary Correct Next-Action Rate improves by a pre-defined meaningful amount;
2. Payment-status comprehension and support-path accuracy do not deteriorate; and
3. Neither guardrail worsens beyond a pre-defined acceptable threshold.

If the primary metric improves but a guardrail deteriorates, do not automatically roll out. Investigate the failure mode, revise the treatment, and retest. Calculate sample size and define thresholds before running the study; do not treat a small convenience sample as statistically conclusive.

## 7. Dependencies and implementation considerations

- Confirm the exact copy with Product, UX Writing, Legal and Compliance.
- Confirm the correct routing owner for each issue type with PhonePe support operations.
- Ensure the payment-success message does not conflict with the authoritative transaction status or applicable UPI dispute rules.
- Preserve transaction references and relevant details securely; do not expose full bank account numbers or sensitive information unnecessarily.
- Provide accessible, plain-language wording and clear local-language equivalents.
- Instrument impressions, issue-choice selection and support-route completion only if privacy, consent, retention and data-governance requirements are satisfied.

## 8. Risks and mitigations

| Risk | Mitigation |
|---|---|
| Wording implies Successful does not mean funds reached the merchant | State accurately that PhonePe received confirmation that the money reached the merchant; separate this from order confirmation |
| Users choose the wrong route because choices overlap | Use short, mutually distinguishable labels and test with representative users |
| Reminder creates unnecessary anxiety or discourages legitimate payments | Keep the reminder neutral and show it only in the relevant context |
| Existing help content and new contextual copy conflict | Maintain one approved source of truth and review all linked Help content |
| Experiment improves comprehension but increases repeat-payment intent | Use guardrail thresholds and stop/revise rather than relying on the primary metric alone |

## 9. Evidence limitations

- The live audit covered selected successful P2P and P2M transactions, not every app version, transaction type, bank or device.
- Live pending/failed P2P and P2M transaction screens were not fully inspected.
- The exact complaint submission, formal ticket generation and complaint-tracking journey was not completed. No false complaint or bank dispute was submitted.
- No merchant-side system record was available to independently verify a merchant confirmation event.
- No user interviews or usability study were conducted; confusion, repeat-payment behaviour and business impact remain hypotheses.
- No PhonePe internal event data, support-contact data or transaction telemetry was available.

## 10. Recommendation conclusion

Prioritise a contextual explanation on the successful P2M transaction screen that separates payment completion from order/booking confirmation and directs the payer to the existing issue-specific path. Second, test whether the existing support paths can be surfaced more directly from transaction context. Do not propose new UTR visibility, receipt sharing or generic support access as missing capabilities: they were already visible in the inspected experience.

**Decision status:** Proposed for validation; not implemented, not experimentally validated, and not a claim of a confirmed PhonePe defect.
