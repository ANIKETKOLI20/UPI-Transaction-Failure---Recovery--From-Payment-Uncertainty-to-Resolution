# PhonePe Product Teardown — Final Recommendations Summary

**Teardown topic:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Product:** PhonePe consumer UPI app  
**Perspective:** Payer  
**Scope:** Domestic UPI P2P and P2M payment-status and recovery experiences  
**Document status:** Working recommendation draft; recommendations are not validated product findings

---

## 1. Executive summary

This teardown examines how PhonePe communicates and supports recovery when a payer's UPI transaction outcome is uncertain. The research reviewed PhonePe Help content supplied and inspected during the teardown, selected transaction-detail screens, and the relevant P2P/P2M workflows.

The evidence indicates that PhonePe Help content discusses pending-status updates, failure and refund guidance, transaction references, bank follow-up, and merchant payment-confirmation issues. However, the material reviewed does not establish whether users understand these distinctions, how often the problems occur, or whether the live P2P/P2M transaction screens provide sufficient guidance in every relevant state.

The recommendations below are therefore **evidence-informed opportunities for further validation**, not claims that PhonePe has a confirmed UX defect, regulatory breach, or measured duplicate-payment problem.

## 2. Evidence and limitations

### Evidence reviewed

- PhonePe Help content covering pending payments, failed payments, money debited but receiver not credited, UTR/reference lookup, refund follow-up, and merchant payment-confirmation issues.
- PhonePe Help guidance describing a pending status update window of up to 48 hours and, in relevant failed-payment guidance, a refund timeline of 3–5 days from the payment date.
- Selected successful P2P transaction-detail screens showing transaction information and support-related actions.
- Historical internet-found pending/failed transaction screenshots, treated as secondary evidence rather than proof of the current PhonePe interface.
- P2P and P2M workflow drafts and the documented unknowns register.

### Important limitations

1. The 48-hour status-update guidance and 3–5-day refund guidance describe different events. They must not be presented as one combined or guaranteed timeline for every transaction.
2. A PhonePe status of Successful, merchant payment confirmation, and order confirmation are separate concepts. A merchant's report of missing confirmation does not, by itself, prove that the beneficiary bank was not credited.
3. The reviewed successful P2P screens do not establish how the current app behaves for live P2P/P2M pending or failed transactions.
4. The current P2M transaction-detail path, availability and naming of transaction references, and exact complaint submission/tracking route still require direct verification.
5. No usability or comprehension study has been conducted. User confusion, duplicate-payment behaviour, and the impact of the proposed changes remain hypotheses.
6. Transaction references such as a PhonePe transaction ID and a UPI/bank reference such as a UTR should not be treated as interchangeable. Display whichever applicable reference is available for that transaction.

## 3. P2P recommendation — Clarify pending-status and refund timelines

### User scenario

A payer's account is debited, but the beneficiary has not received the funds or the transaction remains pending.

### Evidence-backed observation

The PhonePe Help content reviewed describes a pending-status update window of up to 48 hours. Separate relevant failed-payment guidance describes a refund timeline of 3–5 days from the original payment date and directs users to check their bank statement and use the transaction reference/UTR for bank follow-up where applicable.

### Problem framing

A payer may find it difficult to distinguish the time allowed for a pending transaction's final status update from the refund timeline that applies if the transaction is ultimately marked failed.

This is a plausible comprehension risk, not a proven user-research finding.

### Recommendation P2P-01

**Present the pending-status timeline and the applicable refund timeline as two separately labelled pieces of guidance in the relevant transaction experience.** Explain what event each timeline refers to, when its clock starts according to the applicable guidance, and what action the payer should take if the stated period passes without resolution.

The wording must reflect the specific transaction scenario and applicable policy. Do not imply that every pending transaction will be refunded within 3–5 days, or that the 3–5-day refund period begins only after the 48-hour status window.

### Expected user benefit

Payers may better understand what to expect while a transaction is pending, what happens if it is marked failed, and when to check their bank statement or seek further assistance.

### Proposed validation

- **Primary metric:** Refund Timeline Comprehension Rate — share of eligible participants who correctly identify the starting point and meaning of the refund timeline stated in the guidance.
- **Supporting metric:** 48-hour Status-Update Comprehension Rate — share of eligible participants who correctly explain what the stated status-update window means.
- **Supporting metric:** Next-Action Accuracy — share of participants who select the appropriate next step for the scenario presented.
- **Guardrail:** Incorrect Repeat-Payment Intention Rate — share of participants who indicate that they would attempt another payment before verifying the original transaction.

These are proposed research metrics. They are not current PhonePe performance measurements.

## 4. P2M recommendation — Distinguish payment status, merchant confirmation, and order confirmation

### User scenario

A customer pays a merchant using PhonePe. The payer sees Successful in PhonePe, but the merchant reports that payment confirmation has not arrived.

### Evidence-backed observation

The PhonePe Help content reviewed includes guidance for cases where a payment appears successful but the merchant reports that payment has not been received or recognised. The Help content also distinguishes merchant payment issues from order, booking, and refund issues.

The reviewed evidence does not establish whether the live transaction screen already explains these distinctions clearly.

### Problem framing

The payer may not understand the discrepancy between PhonePe's displayed transaction status and the merchant's reported lack of payment confirmation, or know which action to take next.

This is a plausible user problem requiring usability validation.

### Recommendation P2M-01 — Status clarity

**Explain what the Successful status indicates and distinguish it from merchant payment confirmation and order confirmation.** Make this distinction visible in the relevant transaction details experience, rather than relying only on a user finding a separate Help article.

Do not state that a successful transaction is incomplete merely because a merchant reports that confirmation has not arrived. Do not claim merchant-bank credit or merchant-system receipt unless the product has reliable evidence of that event.

### Recommendation P2M-02 — Contextual merchant issue guidance

Provide a contextual route such as **“Merchant hasn't received payment?”** from the relevant transaction details screen. The flow should guide the payer to verify the original transaction, identify the appropriate proof to share, and reach the relevant PhonePe or merchant support route.

Initially, this should be treated as a user-reported issue unless PhonePe has an appropriate merchant-side confirmation signal. The interface should not imply that PhonePe has independently verified the merchant's status when it has not.

### Recommendation P2M-03 — Make transaction references easy to access

Ensure the applicable transaction reference, such as the UPI transaction ID or UTR/bank reference where available, is easy to locate and copy or share. First audit the current P2M transaction details experience to establish which references and sharing actions already exist. Recommend a change only where a genuine access gap is observed.

Do not label every reference as “UTR” or imply that different reference identifiers are interchangeable.

### Expected user benefit

Payers may better understand what PhonePe's transaction status does and does not confirm, follow an appropriate resolution path, and be less likely to make another payment before verifying the original transaction.

This is an expected benefit, not a measured outcome. Stated repeat-payment intention must not be reported as actual duplicate-payment incidence.

### Proposed validation

- **Primary metric:** Correct Next-Action Rate — share of eligible participants who choose the appropriate next action for the merchant-confirmation scenario.
- **Supporting metric:** Payment-Status Comprehension Rate — share of participants who correctly explain what the displayed payment status establishes and what it does not establish.
- **Supporting metric:** Support-Path Selection Accuracy — share of participants who select the appropriate merchant/PhonePe support route for the scenario.
- **Guardrail:** Incorrect Repeat-Payment Intention Rate — share of participants who say they would pay again before verifying the original transaction.
- **Guardrail:** Incorrect Order/Payment Classification Rate — share of participants who confuse payment confirmation with order confirmation.
- **For Recommendation P2M-03:** Transaction Reference Retrieval Success Rate — share of eligible participants who can locate and identify the applicable transaction reference in the existing or proposed interface.

These are proposed usability/comprehension measures, not current PhonePe performance measurements.

## 5. Proposed implementation sequence

The sequence below is a **provisional product-development sequence**, not a validated engineering plan. It should be revisited after the current P2P/P2M screens and technical dependencies are verified.

| Sequence | Improvement | Reason for sequence | Key dependency/check |
|---|---|---|---|
| 1 | Clarify transaction status and the applicable timelines | Establishes a correct understanding before the payer chooses a recovery action | Validate wording against the exact transaction scenario and applicable policy; inspect existing UI first |
| 2 | Add contextual issue guidance | Makes the appropriate recovery path easier to find after the payer understands the status | Verify the current issue-reporting route and avoid implying unverified merchant status |
| 3 | Improve transaction-reference access where a gap exists | Supports follow-up with the merchant, bank, or support team | Audit current P2M references and sharing capability; confirm which identifier applies |

The order does not mean later improvements are unimportant. Some may be inexpensive or already implemented, and the actual release order should depend on evidence, technical dependencies, risk, and effort.

## 6. Prioritization rationale

The provisional first priority is **status clarity (P2P-01 and P2M-01)** because it helps the payer understand the transaction before choosing a next action. Contextual guidance is the next proposed layer. Transaction-reference accessibility should be improved only if a current-flow audit confirms that users cannot readily find or share the necessary reference.

Current confidence is limited:

- **User impact:** Plausibly meaningful because payment uncertainty can affect what the payer does next; not quantified.
- **Evidence confidence:** PhonePe Help content establishes that these scenarios are documented, but does not establish their frequency or prove that users misunderstand the live UI.
- **Implementation feasibility:** Clearer explanatory content may be relatively straightforward, but exact effort is unknown. Any merchant-status integration could require additional systems and should not be assumed feasible without technical review.

A prioritization score should not be fabricated without agreed scoring definitions, stakeholder input, and engineering estimates.

## 7. Experiment decision principles

Before any controlled test or rollout:

1. Define the control and treatment experiences precisely.
2. Set the primary metric, supporting metrics, and guardrails before examining results.
3. Establish the minimum meaningful improvement, sample-size/power approach, significance threshold, guardrail tolerance, test duration, and stopping rules in advance.
4. Compare treatment against control. A treatment-only percentage is not enough to determine whether the change improved or worsened a guardrail.
5. Do not proceed to a broad launch solely because the primary metric improves if a guardrail materially deteriorates.
6. Treat comprehension and stated intention as research measures. They do not substitute for production measures such as actual repeat payment attempts or duplicate successful payments.

If primary comprehension improves but repeat-payment intention worsens versus control, investigate the cause and revise/retest before broad rollout. If the guardrail is unchanged or improved, interpret it alongside uncertainty, sample size, and pre-defined thresholds rather than using an arbitrary percentage in isolation.

## 8. What remains to be verified

Before publishing the final teardown as a firm critique or making stronger recommendations, investigate:

- Current live P2P pending/failed transaction screens and exact wording.
- Current live P2M pending/failed/successful transaction details and merchant-issue entry points.
- Whether the payer can already locate and share the relevant transaction ID/UTR in P2M.
- Exact complaint submission, acknowledgement/reference number, status tracking, and escalation path.
- Which exact refund/reversal timeline applies to each scenario and whether the source uses calendar days, business days, or another defined convention.
- Whether the product can obtain a reliable merchant payment-confirmation signal.
- User comprehension and next-action behaviour through unprimed usability/comprehension research.

Do not create a real failed UPI transaction or deliberately interrupt a live payment to obtain evidence. Use safe, available product screens, official Help content, and appropriately designed research materials.

## 9. Conclusion

The central product opportunity is to reduce avoidable uncertainty by making transaction status, merchant payment confirmation, order confirmation, and recovery actions easier to distinguish.

The most defensible starting point is clearer status and timeline communication, followed by contextual merchant-issue guidance and easier access to applicable transaction references where a verified gap exists. These recommendations should be tested with users and reviewed against technical and policy constraints before being presented as confirmed product improvements.

---

**Document integrity note:** This summary reflects the evidence and exercises documented in the teardown to date. It must be updated if direct inspection of current failure-state screens, official source verification, or user research produces new evidence.
