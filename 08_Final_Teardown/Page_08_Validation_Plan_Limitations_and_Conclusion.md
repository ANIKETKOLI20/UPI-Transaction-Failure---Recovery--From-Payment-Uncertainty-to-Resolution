# Page 08 — Validation Plan, Limitations & Conclusion

> **Document status:** Proposed validation plan. The tests and experiments below have been designed but have not been conducted. No participant results, product impact, or causal effect are claimed.

## 1. What should be validated?

The primary opportunity identified in this teardown is to make the distinction between **payment completion** and **merchant order/booking confirmation** clearer in the P2M transaction experience, while helping payers discover the existing issue-specific support paths.

A secondary validation stream can test whether payers understand the P2P pending-status and refund guidance. This is a comprehension question, not evidence that the current guidance is defective.

## 2. Proposed validation methods

| Recommendation / question | Method | Participant task | What it tests |
|---|---|---|---|
| P2M: payment vs order confirmation clarity | Comprehension and usability test | Show an anonymised successful P2M transaction screen and a scenario in which the merchant has not confirmed the order. Ask what the Successful status confirms and what the payer should do next. | Correct interpretation of payment completion versus order/booking confirmation. |
| P2M: discoverability of existing support routes | Task-based usability test | Ask participants to find the correct path for (a) merchant disputing receipt of payment and (b) order/booking not confirmed. | Whether users can locate and select the appropriate existing support route. |
| P2P: timeline comprehension | Comprehension test | Show the relevant PhonePe pending/refund guidance. Ask what the up-to-48-hour status-update window means, when the stated refund timeline begins, and what to do if the refund does not appear. | Understanding of separate status-update and refund guidance. |

Use neutral, non-leading prompts. Do not tell participants which answer is correct before they respond. Use anonymised screens and synthetic scenarios; do not expose personal transaction data or ask participants to initiate real payments.

## 3. Proposed metrics

### P2M — primary and supporting metrics

**Primary: Correct Next-Action Rate**

- **Numerator:** Eligible participants who choose the appropriate next action for the scenario shown.
- **Denominator:** All eligible participants who viewed the scenario and were given the task, including participants who respond “unable to determine.” Exclude only documented technical interruptions or participants who were not exposed to the scenario.
- **Unit:** Participant, one scored task per scenario.
- **Direction:** Higher is better.

The scoring rubric must distinguish the scenarios:

- Payment is successful, but the order/booking is not confirmed → contact the merchant for the order/booking issue, consistent with the inspected PhonePe Help guidance.
- PhonePe displays successful, but the merchant disputes receipt of payment → use the relevant PhonePe payment-issue/Report Issue route described in Help.
- Payer is debited and merchant transaction confirmation is not received → assess the exact facts against the applicable payment-failure guidance and regulatory category; do not automatically classify every merchant complaint as this failure type.

**Supporting: Payment-Status Comprehension Rate**

- **Numerator:** Eligible participants who correctly explain what the displayed Successful status means in the presented PhonePe scenario.
- **Denominator:** All eligible participants who viewed the relevant screen and were asked the comprehension question, including “unable to determine” responses.
- **Unit:** Participant.
- **Direction:** Higher is better.

**Supporting: Support-Path Selection Accuracy**

- **Numerator:** Eligible participants who select the correct existing support route for the specific issue presented.
- **Denominator:** All eligible participants who attempted the support-discovery task.
- **Unit:** Participant/task.
- **Direction:** Higher is better.

### P2P — supporting validation metrics

**Refund Timeline Comprehension Rate**

- **Numerator:** Eligible participants who correctly identify the stated starting point of the relevant PhonePe refund guidance as the original payment date, where that is what the displayed article says.
- **Denominator:** All eligible participants who viewed the applicable guidance and were asked the question, including “unable to determine” responses.
- **Unit:** Participant.
- **Direction:** Higher is better.

**48-hour Status-Update Comprehension Rate**

- **Numerator:** Eligible participants who correctly explain that the stated up-to-48-hour period concerns the pending transaction's final-status update, not the same event as a refund being credited.
- **Denominator:** All eligible participants who viewed the applicable guidance and were asked the question.
- **Unit:** Participant.
- **Direction:** Higher is better.

**Next-Action Accuracy**

- **Numerator:** Eligible participants who choose the appropriate next step for the presented P2P pending/debit/beneficiary-credit scenario.
- **Denominator:** All eligible participants who attempted the task.
- **Unit:** Participant/task.
- **Direction:** Higher is better.

### Guardrails

| Guardrail | Definition | Why it matters |
|---|---|---|
| Incorrect Repeat-Payment Intention Rate | Eligible participants who say they would initiate another payment before verifying the original transaction outcome, divided by all eligible participants asked the scenario question. | Detects potentially unsafe next-action interpretation. It measures stated intention, not actual duplicate payments. |
| Incorrect Order/Payment Classification Rate | Eligible participants who confuse payment completion/merchant receipt with order or booking confirmation, divided by all eligible participants asked to classify the scenario. | Detects confusion between payment and fulfilment outcomes. |
| Incorrect Reversal-Timeline Interpretation Rate (P2P) | Eligible participants who confuse the pending-status update window with the refund/reversal timeline or apply a general help-page estimate as a universal regulatory deadline, divided by all eligible participants asked. | Reduces the risk of users misunderstanding distinct events or time requirements. |

Define the acceptable guardrail thresholds before testing. Do not treat a guardrail as successful merely because the primary metric improves.

## 4. Proposed comparative test

For the P2M clarity recommendation, compare:

- **Control:** The current inspected transaction experience and its existing support entry points.
- **Treatment:** A clearly labelled explanation of (1) what PhonePe's Successful status means, (2) that order/booking confirmation is separate, and (3) the appropriate existing route for merchant-payment disputes versus order/booking issues.

Use participant-level random assignment and a between-subject design so each participant sees only one version. Keep the scenario, wording outside the treatment, device conditions, and task prompts consistent.

For the support-discoverability recommendation, test the current journey first. Only design a treatment after observing where participants fail, hesitate, or choose the wrong route. Do not assume discoverability is poor simply because the route is not on the first screen.

For P2P, test the existing Help guidance before proposing revised wording. A separate treatment should only be designed if comprehension testing identifies a specific misunderstanding.

## 5. Analysis and decision rules

Before recruitment, specify:

1. The smallest improvement that would be meaningful to users/product teams.
2. The sample-size calculation, using the baseline rate, chosen minimum detectable effect, significance level and desired statistical power.
3. The primary metric and pre-defined guardrail thresholds.
4. Exclusion rules, task wording, randomisation unit and stopping rule.
5. How partially correct, incorrect, unable-to-answer and missing responses will be scored.

Do not select a sample size merely because it is convenient. Small formative usability tests can identify usability issues, but they do not by themselves establish population-level effects.

**Decision framework:**

- Primary metric improves by a pre-defined meaningful amount and guardrails remain within pre-defined limits → consider a larger/production validation step.
- Primary metric improves but a guardrail worsens beyond its limit → do not roll out; investigate and revise.
- Primary metric does not improve → revisit the problem framing or treatment.
- Results are imprecise or inconclusive → collect additional evidence; do not claim success.

A later production A/B test would require PhonePe's internal event instrumentation and transaction/support data. It could measure actual support-path usage or repeat payment attempts; the proposed participant study cannot establish actual duplicate-payment incidence.

## 6. What this research establishes

- The researcher inspected one existing successful P2P transaction screen and one existing successful P2M transaction screen in PhonePe.
- The inspected screens exposed transaction status/details, reference information, receipt-sharing and support access.
- The inspected P2P support journey displayed recipient/bank context and issue suggestions including an amount-not-credited route and a bank-dispute option.
- The inspected P2M support guidance distinguished a merchant payment-receipt dispute from an order/booking issue and provided different next steps.
- PhonePe Help content reviewed by the researcher described pending-status, refund, UTR and bank-follow-up guidance for relevant cases.

These observations describe the specific screens and Help material inspected. They do not establish that every PhonePe user sees the same interface or that the experience is identical across app versions, banks, transaction types or dates.

## 7. Limitations and unresolved questions

- No live P2P or P2M pending/failed transaction was deliberately created or inspected in this audit.
- Only selected successful P2P and P2M transaction screens were inspected; they are not a full census of PhonePe's interface.
- No user interviews, usability sessions, comprehension tests or controlled experiments were conducted.
- No PhonePe internal transaction, support, merchant-confirmation or event data was available.
- The merchant-side bank/confirmation state and order-management state were not independently observed.
- A complaint was not submitted. A formal complaint ID, end-to-end complaint tracking and resolution outcome were not verified.
- App version, device/OS metadata and exact capture metadata were not consistently recorded for all inspected screens.
- PhonePe Help screenshots establish what the inspected Help content stated; they do not independently establish actual bank processing times or outcomes.
- RBI turnaround-time rules apply to defined failure conditions. They must not be applied to ordinary order cancellations, merchant refunds or all merchant complaints.
- Any proposed product impact, reduced confusion or reduced duplicate-payment behaviour remains unvalidated.

## 8. Conclusion

The teardown found that PhonePe already exposes substantial transaction information and recovery support in the selected successful-payment journeys. The clearest evidence-backed product opportunity is narrower: test whether the transaction experience should make the distinction between payment completion and order/booking confirmation more explicit, while helping users discover the appropriate existing support route for each issue.

The recommended next step is a controlled comprehension and usability study—not an immediate claim that the current interface causes confusion or duplicate payments. The proposed metrics and guardrails provide a way to test that opportunity before any broader rollout.

## 9. Publication note

All recommendations and experiments in this page are proposals. The audit did not measure user comprehension, actual repeat-payment behaviour, complaint-resolution performance or causal product impact. Keep these limitations visible in the final PDF and portfolio description.
