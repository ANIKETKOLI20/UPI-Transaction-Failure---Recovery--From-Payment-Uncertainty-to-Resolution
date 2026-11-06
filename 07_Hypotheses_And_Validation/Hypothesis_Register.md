# Hypothesis Register — PhonePe UPI Transaction Failure & Recovery

> **Document status:** Working draft — hypotheses are unvalidated unless explicitly stated otherwise.  
> **Version:** 0.1  
> **Created:** 2026-11-06  
> **Project:** PhonePe UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
> **Scope:** Consumer/payer experience for selected domestic UPI P2P and P2M scenarios.

## 1. Purpose

This register records possible explanations for the potential user problems identified during the teardown. It distinguishes diagnostic hypotheses (possible reasons a problem occurs) from intervention hypotheses (possible product changes and their expected effects).

A hypothesis is not a finding. Do not describe any hypothesis as true until appropriate evidence has been collected and assessed. Multiple hypotheses may be true at the same time; they are not necessarily mutually exclusive.

## 2. Problem statements under investigation

### PS-01 — P2P pending-payment clarity

When a P2P UPI payment remains pending in PhonePe, the payer needs clear and accessible information about the current transaction status and appropriate next steps, because uncertainty about the payment outcome may make it difficult to determine whether to wait, verify the bank-account status or seek support.

**Status:** Working problem statement; user impact and prevalence have not been established.

### PS-02 — P2M payment-confirmation uncertainty

When PhonePe displays a merchant payment as successful but the merchant reports that payment confirmation has not been received, the payer needs clear guidance to verify the payment outcome and determine the appropriate next action, such as presenting transaction proof or seeking support. Without sufficiently clear guidance, the payer may remain uncertain and could attempt another payment before the original discrepancy is resolved, creating a potential duplicate-payment risk.

**Status:** Working problem statement; current PhonePe screen behaviour, merchant-side confirmation and user impact have not been fully verified.

## 3. P2P diagnostic hypotheses

### DH-01 — Recovery-instruction discoverability

**Hypothesis**  
Payers may struggle to find relevant recovery instructions because transaction-status information and detailed Help guidance may be presented in different parts of the application.

**Why it is plausible**  
The evidence collected includes transaction-detail screens and a separate Payment Issues / Help structure. The existence of information in Help does not by itself establish how easily a payer can find it from a pending transaction.

**Evidence that would support it**
- Participants cannot find the relevant Help topic from the pending transaction screen within a defined task and time limit.
- Participants select an incorrect support category or abandon the task.
- Direct inspection shows that the route from the transaction screen to the relevant guidance is difficult to discover.

**Evidence that would weaken it**
- Representative participants consistently find the correct guidance quickly and without assistance.
- The current transaction screen provides an obvious, direct route to the relevant instructions.

**Validation method**  
Moderated or unmoderated usability testing with a clearly defined task; record task success, time-to-find, incorrect routes and abandonment. Inspect the current PhonePe app directly and record app version and observation date.

**Limitations**  
Finding the Help article does not prove that the user understands it. Discoverability and comprehension must be measured separately.

**Current status:** Unvalidated. It was weakened in a hypothetical classroom exercise only; no actual participant study has been conducted.

### DH-02 — Status and refund-timeline comprehension

**Hypothesis**  
Payers may find the pending-payment guidance but misunderstand the relationship between the up-to-48-hour final-status update period and the stated 3–5-day refund period, potentially interpreting them as sequential waiting periods rather than separate timelines measured from the original payment date.

**Why it is plausible**  
The PhonePe Help screenshot inspected on 2026-11-03 states that banks may take 2 minutes to 48 hours to update the final status. A separate Help answer says that, if a payment is marked failed, the amount will be refunded within 3–5 days from the date the payment was made. The two statements describe different events.

**Evidence that would support it**
- Participants who can find the guidance give an incorrect explanation of what the 48-hour period measures.
- Participants incorrectly start the 3–5-day period from the date the status changes to Failed, rather than from the original payment date stated in the Help answer.
- Participants believe the two periods must be added together despite the wording referring to the original payment date.

**Evidence that would weaken it**
- Participants consistently explain the status-update period and refund-period starting point correctly in their own words.
- Participants correctly identify the action to take if the transaction remains pending or the refund is not reflected.

**Validation method**  
Comprehension testing using the actual, dated PhonePe Help wording. Ask open-ended questions; classify responses as correct, partially correct, incorrect or unable to answer. Do not rely only on asking participants whether the wording is clear.

**Limitations**
- The Help wording inspected does not explicitly state whether the 3–5 days are calendar days or business days.
- The article's exact applicability to every P2P failure scenario has not been established.
- Comprehension-test results from a small or convenience sample cannot be generalized to all PhonePe users.

**Current status:** Priority for validation; unvalidated. The earlier 8-of-10 / 3-of-8 example was a hypothetical teaching scenario, not actual user research.

### DH-03 — Underlying bank/payment-processing delay

**Hypothesis**  
Prolonged uncertainty may primarily result from delayed transaction-status confirmation by a bank or another payment-system participant, rather than from inadequate PhonePe communication.

**Why it is plausible**  
PhonePe's inspected Help answer attributes variation in final-status confirmation time to banks and states that confirmation may take between 2 minutes and 48 hours. This is PhonePe's explanation; it does not independently establish the technical cause of an individual transaction delay.

**Evidence that would support it**
- Reliable transaction records show that status-confirmation latency is elevated for defined banks, time windows or transaction segments.
- The sequence of timestamps indicates that the app communicated the available status promptly, while final confirmation arrived later from the relevant payment participants.

**Evidence that would weaken it**
- Transaction records show prompt final-status availability but a delay in displaying or communicating that status in the app.
- The delay is primarily associated with app-side status refresh, notification or presentation behaviour rather than upstream confirmation.

**Validation method**  
Analyze transaction-level timestamps and operational logs, including initiation, bank response, network response, status update and notification timestamps where available. Segment carefully and examine alternative explanations.

**Limitations**  
The supplied portfolio transaction dataset does not contain the diagnostic telemetry, attempt-level event history or complete latency records needed to establish the technical root cause. Do not use bank-level outcome differences alone as proof of bank causation.

**Current status:** Not tested; requires internal or otherwise reliable diagnostic data.

## 4. P2M diagnostic hypotheses

### PH-01 — Understanding payment status versus merchant confirmation

**Hypothesis**  
Payers may not understand the appropriate next action when PhonePe displays a successful status but the merchant reports that payment confirmation has not been received.

**Why it is plausible**  
The scenario contains two different signals: the payer-facing app status and the merchant's reported confirmation state. The payer may need to determine whether to show transaction proof, wait, seek support or take another action. This is a research question, not proof of user confusion.

**Evidence that would support it**
- In a scenario-based usability or comprehension test, participants cannot explain what the successful status establishes and what it does not establish.
- Participants cannot identify a safe, appropriate next action when the merchant disputes receipt.
- Participants interpret successful payment status as proof that the merchant's order or service has necessarily been confirmed.

**Evidence that would weaken it**
- Participants consistently distinguish payer debit, payment confirmation, merchant credit and order confirmation.
- Participants select an appropriate next action and can explain why another payment should not be initiated until the original discrepancy is checked.

**Validation method**  
Scenario-based usability and comprehension testing. Use a neutral prompt; do not lead participants toward a preferred answer. Record their explanation and intended action.

**Limitations**  
A stated intention to pay again is not proof of actual repeat-payment behaviour. Actual behaviour requires suitable event data. The merchant's assertion alone does not prove that its bank account was not credited or that payment confirmation was not received by another system.

**Current status:** Priority for validation; unvalidated. The earlier 3-of-5 repeat-payment example was a hypothetical classroom exercise, not actual user research.

### PH-02 — Merchant-payment support-path discoverability

**Hypothesis**  
Payers may struggle to identify the correct support category when a merchant disputes a payment, because PhonePe separates merchant-payment confirmation issues, duplicate payments and order/booking problems into different Help topics.

**Why it is plausible**  
The inspected Payment Issues screens show separate categories and issue types. This demonstrates categorization, but not whether users can select the correct route easily.

**Evidence that would support it**
- Participants choose an order/booking category when the issue concerns payment confirmation, or choose a payment category for an order-fulfilment issue.
- Participants take repeated incorrect routes or cannot find the appropriate support option.

**Evidence that would weaken it**
- Participants consistently choose the correct category for distinct merchant-payment scenarios.
- The transaction screen offers a direct and contextually appropriate support route.

**Validation method**  
Task-based usability testing with separate scenarios for missing merchant confirmation, successful payment with an unconfirmed order, duplicate payment and merchant cancellation/refund.

**Limitations**  
The existence of separate Help categories does not itself establish that the information architecture is confusing or ineffective.

**Current status:** Unvalidated.

### PH-03 — Merchant-side payment-confirmation delay or failure

**Hypothesis**  
A discrepancy between the payer-facing successful status and the merchant's reported confirmation may arise from delayed or unsuccessful merchant-side confirmation or another payment-system process, rather than from a PhonePe communication problem alone.

**Why it is plausible**  
The payer-facing status and merchant-reported confirmation are separate signals. The available screenshots and Help articles do not reveal the merchant's acquiring-side records or the underlying transaction messages.

**Evidence that would support it**
- Transaction and merchant/acquirer records show that the relevant confirmation was delayed, not delivered or not reflected in the merchant's system.
- A reconciled transaction trace identifies a specific point of delay or failure.

**Evidence that would weaken it**
- Merchant/acquirer records show that confirmation was received on time, while the remaining issue concerns merchant staff, order processing or communication.
- The payment was confirmed and the problem is solely an order/booking fulfilment issue.

**Validation method**  
Reconciled transaction traces, merchant/acquirer confirmation records, relevant bank/payment-system logs and timestamps. This investigation requires access beyond public app screenshots.

**Limitations**  
Do not infer that the merchant's bank was not credited solely because the restaurant says it did not receive confirmation. Do not infer a technical root cause from payer-facing screenshots.

**Current status:** Not tested; requires merchant-side and technical evidence.

## 5. Hypothesis comparison and investigation priority

The following priorities are proposed for the teardown's next research activities. They are not measured impact rankings and do not imply that any hypothesis is true.

| Priority | Hypothesis | Reason for priority | Current status |
|---|---|---|---|
| 1 | DH-02 — Status/refund-timeline comprehension | Directly testable with the PhonePe wording already collected; important to recovery expectations. | Priority for validation |
| 2 | PH-01 — Payment status versus merchant confirmation | Central to the P2M problem statement and can be tested with scenario-based research. | Priority for validation |
| 3 | DH-01 — Recovery-instruction discoverability | Can be tested through the current app's navigation and task success. | Unvalidated; weakened only in a hypothetical exercise |
| 4 | PH-02 — Merchant support-path discoverability | Tests whether users can distinguish payment issues from order issues. | Unvalidated |
| 5 | DH-03 — Bank/payment-processing delay | Important alternative explanation, but requires operational data unavailable in the current portfolio dataset. | Not tested |
| 6 | PH-03 — Merchant-side confirmation delay/failure | Important technical alternative explanation; requires merchant/acquirer evidence. | Not tested |

## 6. Intervention hypotheses — not yet finalized

Diagnostic hypotheses investigate why a potential problem occurs. Intervention hypotheses propose a product change and an expected outcome. Do not jump to an intervention until the diagnostic work and evidence justify it.

### Candidate P2P intervention hypothesis (exploratory)

If PhonePe makes the appropriate next steps more prominent on the pending-transaction screen, payers may be better able to identify whether to wait, check the final status or seek support.

**Potential validation:** Compare task success and correct next-step selection in a usability test using the current experience and a proposed alternative. If internal event data is available, separately assess eligible repeat-payment attempts after pending transactions.

**Status:** Exploratory; not selected or validated.

### Candidate P2M intervention hypothesis

Not yet formulated. First validate whether the main difficulty concerns understanding the difference between payment status and merchant confirmation, discovering the correct support path, or an underlying merchant-side confirmation issue.

## 7. Evidence and measurement requirements

Before testing any hypothesis, define:

- The target user and eligible scenario.
- The event or task being measured.
- The numerator and denominator for any rate.
- The observation window.
- Exclusions and edge cases.
- The data source and its provenance.
- What result would support, weaken or leave the hypothesis inconclusive.

Potential measures include:

| Research question | Potential measure | Data/method required |
|---|---|---|
| Can users find the guidance? | Task success rate; time-to-find; incorrect navigation rate | Usability testing |
| Do users understand the timelines? | Correct comprehension rate by question; misunderstanding types | Comprehension testing |
| Do users understand P2M confirmation? | Correct next-action rate; distinction between payment and order confirmation | Scenario-based testing |
| Do users repeat a payment after pending status? | Eligible repeat-payment attempt rate; duplicate successful-payment incidence | Product event and transaction data |
| Are status updates delayed? | Time from initiation to final status; latency percentiles by eligible segment | Transaction/operational telemetry |
| Is merchant confirmation delayed? | Time from payer debit/authorization to merchant confirmation; missing-confirmation rate | Merchant/acquirer and payment-system records |

Do not claim a causal effect from observational comparisons. A proposed experiment must be labelled as a proposal until it has actually been run and appropriately analyzed.

## 8. Research integrity and evidence rules

1. **Do not treat teaching examples as research findings.** The hypothetical 8-of-10 / 3-of-8 comprehension exercise and 3-of-5 repeat-payment exercise were fictional examples. They are not PhonePe user-study results and must not appear as empirical findings in the final teardown.
2. **Do not claim actual customer confusion, repeat-payment behaviour or trust impact** without suitable user research or product data.
3. **Do not claim a bank or merchant caused a technical failure** without diagnostic or reconciled transaction evidence.
4. **Separate direct observations from Help guidance.** A Help screenshot establishes what the inspected article displayed at the time of capture, not what happened in a real transaction.
5. **Separate payment status, payer debit, beneficiary/merchant credit, merchant confirmation and order fulfilment.** These are different facts and may require different evidence.
6. **Separate PhonePe customer guidance from RBI turnaround-time requirements.** Confirm that the transaction facts match the exact regulatory scenario before comparing deadlines or compensation.
7. **Keep every hypothesis open to rejection.** Record contradictory evidence and alternative explanations.

## 9. Evidence references to reconcile

The following existing research materials may be relevant. Match them to the final evidence IDs in `02_Evidence_Register/Evidence_Register.xlsx`; the IDs below are topic references, not a replacement for the evidence register.

- PhonePe Help screenshots: pending-payment categories, 48-hour status-update guidance, cancellation guidance, failure reasons, refund/UTR instructions, bank escalation, merchant-payment and order/booking guidance.
- PhonePe transaction screenshots: incoming/outgoing successful P2P screens inspected directly.
- Internet-found transaction screenshots: pending and failed examples; retain as secondary evidence, not proof of current PhonePe app behaviour.
- RBI: September 20, 2019 circular on harmonisation of turnaround time and customer compensation for failed transactions.
- NPCI: UPI HELP Brand Guidelines, July 2023; use as a dated ecosystem reference and verify current implementation separately.
- PhonePe: current Grievance Policy and applicable Help/UPI terms; record the exact URL, version/date and relevant section in the evidence register.

## 10. Completion criteria

This register is ready to support the next validation stage when:

- Each hypothesis has a clearly defined scope and target user.
- Supporting and weakening evidence are specified.
- The validation method can realistically distinguish the hypothesis from alternatives.
- Required data sources and their limitations are documented.
- Hypotheses remain labelled unvalidated until evidence is collected.
- Fictional classroom examples are excluded from empirical findings.
- Relevant evidence IDs are reconciled with the evidence register.

## 11. Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-06 | Initial consolidated P2P and P2M diagnostic hypothesis register; added validation methods, supporting/rejecting evidence, limitations and exploratory intervention hypothesis. |
