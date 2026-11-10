# Validation, Metrics & Guardrails

**Project:** PhonePe Product Teardown — *UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution*  
**Document:** Validation_Metrics_Guardrails.md  
**Version:** 0.2 — Working draft; evidence IDs reconciled and P2M scenario clarified  
**Scope:** Payer-facing domestic UPI experience in PhonePe; P2P and P2M scenarios  
**Status:** Proposed research and experiment designs. No usability study, comprehension test, or product experiment has been conducted as part of this document.

---

## 1. Purpose

This document defines how the two problem statements and their hypotheses could be validated. It specifies:

- the research method appropriate to each hypothesis;
- the primary, supporting, and guardrail metrics;
- metric definitions, including numerator, denominator, unit, and exclusions;
- proposed controlled experiments for P2P and P2M;
- how results should influence a decision; and
- the limitations that prevent a small research exercise from being treated as proof of a live product impact.

The purpose is not to claim that PhonePe has a confirmed product defect. The purpose is to design a disciplined way to test whether users understand the available guidance and choose an appropriate next action in the scenarios being studied.

## 2. Research boundaries and evidence status

### 2.1 In-scope scenarios

**P2P:** The payer's bank account is debited, but the beneficiary has not received the money or the final transaction outcome is not yet clear.

**P2M:** Two Help-documented situations are considered separately: (1) PhonePe displays Successful but the merchant disputes receipt of the payment; and (2) the payment is successful but the order/booking is not confirmed. The RBI-defined incident where the payer is debited but merchant transaction confirmation is not received is a separate category and must be matched to its exact facts.

### 2.2 Important distinctions

The following are different events and must not be treated as interchangeable:

1. The payer's bank account is debited.
2. PhonePe displays a transaction status.
3. The beneficiary's bank account is credited.
4. The merchant receives or can verify payment confirmation.
5. The merchant's order or booking is confirmed.
6. A failed transaction is reversed and the payer's account is credited back.

A successful payment status does not, by itself, prove that a merchant order was confirmed. Likewise, an order problem does not automatically establish that the underlying UPI payment failed.

### 2.3 Evidence currently available

The working evidence set includes user-inspected PhonePe Help content and screenshots. It indicates that the Help guidance describes, among other things:

- a pending transaction status that may take up to 48 hours to update;
- a stated 3–5 day refund period for certain failed/debited-payment situations, described in the inspected guidance as running from the payment date;
- checking the bank statement and using the transaction reference/UTR when seeking bank assistance;
- separate Help categories for pending, failed, successful, merchant-payment, and refund issues; and
- a distinction between a payment issue and a merchant order/booking issue.

Relevant canonical evidence references include **E-006–E-008; E-010–E-017; E-021–E-026; E-029–E-031**, selected by scenario. The full mapping is in `03_Evidence_Register/Evidence_ID_Crosswalk.md`. The screenshots establish what PhonePe Help stated at capture time, not actual payment outcomes, bank processing or user behaviour. Exact article URLs, article publication/update dates, per-panel original filenames and app version remain missing or not visible.

These sources support statements about the Help content that was inspected. They do **not** establish how every live transaction screen behaves, how users interpret the guidance, how quickly banks actually process reversals, or whether users make duplicate payments. The historical transaction screenshots are secondary evidence and should not be treated as proof of the current PhonePe interface.

### 2.4 What this research cannot establish on its own

This proposed research cannot establish:

- the technical root cause of a pending or failed UPI transaction;
- the actual rate of payment-status mismatches across PhonePe;
- actual duplicate-payment incidence;
- actual reversal or resolution performance;
- merchant-bank settlement or confirmation failures;
- causal impact on production users; or
- regulatory non-compliance.

Those claims require suitable internal transaction, support, bank, merchant, or operational data and, where relevant, legal/regulatory analysis.

---

## 3. Validation approach

Use the method that can directly test the question. Do not use one method as a substitute for another.

| Method | What it can test | Example evidence or output | What it cannot prove by itself |
|---|---|---|---|
| Comprehension testing | Whether a participant correctly understands guidance and timelines | Correct interpretation of 48 hours, refund timing, or next step | Actual behaviour during a real failed payment |
| Usability testing | Whether a participant can find a feature or complete a task in the interface | Task completion, time to find the relevant Help route, navigation errors | Whether the bank or payment network resolved a transaction |
| Product analytics | What users actually did in the product, when suitable event data exists | Repeat payment attempts, time to status update, support entry points | Why a user acted that way without further research |
| Operational investigation | What happened across transaction, bank, PSP, and merchant systems | Correlated logs, transaction references, acknowledgements, timestamps | Broad user comprehension or satisfaction |

**Chosen primary method for this teardown:** comprehension testing with realistic, controlled scenarios and the exact Help content being evaluated. A separate usability task can test whether users can locate that content. Neither requires creating a real failed UPI transaction.

Do not intentionally disconnect a network, interrupt a live payment, or create a failed payment to generate evidence. A transaction may still settle or debit the account even when the app loses connectivity.

---

## 4. P2P validation plan

### 4.1 Problem statement

When a P2P UPI payment remains pending in PhonePe, the payer needs clear and accessible information about the current transaction status and appropriate next steps, because uncertainty about the payment outcome may make it difficult to determine whether to wait, verify the bank-account status, or seek support.

This is a working problem statement, not a confirmed finding that PhonePe's guidance is defective.

### 4.2 Hypotheses

| ID | Hypothesis | Validation route | Evidence required |
|---|---|---|---|
| DH-01 — Discoverability | Payers may struggle to find relevant recovery instructions because transaction status information and detailed Help guidance may be located in different parts of the app. | Usability task: ask participants to find the relevant Help guidance from a supplied transaction scenario or prototype. | Whether participants reach the correct information, time taken, navigation path, and points of failure. |
| DH-02 — Comprehension | Payers may misunderstand the relationship between the up-to-48-hour final-status update and the stated 3–5-day refund guidance. | Comprehension test using the inspected Help content, followed by neutral questions. | Participants' explanation of what each timeline refers to, when the refund period starts, and what to do next. |
| DH-03 — Operational dependency | Prolonged uncertainty may primarily result from delayed bank status confirmation rather than inadequate PhonePe guidance. | Operational investigation; outside the scope of participant-only comprehension testing. | Transaction-level timestamps and bank/PSP status acknowledgements correlated by transaction reference. |

DH-02 is the primary user-facing hypothesis for this teardown because it can be tested directly using the Help guidance already inspected. DH-01 is a separate discoverability question. DH-03 requires operational data and must not be inferred from user interviews or screenshots.

### 4.3 Proposed comprehension task

Present participants with the exact pending-payment Help content and a short scenario. Do not explain the answer before asking the questions.

**Scenario:** A payer's account has been debited for a P2P UPI payment. PhonePe shows the transaction as pending, and the beneficiary says the money has not arrived.

Ask each participant:

1. What does the up-to-48-hour period refer to?
2. What does the stated 3–5-day period refer to?
3. According to the wording shown, when does the refund period begin?
4. What should the payer do if the transaction is still pending after the stated status-update period?
5. What should the payer do if the amount has not been refunded within the stated period?
6. What transaction information would be useful when contacting the bank?

Use neutral wording. Do not ask, “Is the guidance confusing?” or tell the participant that the two timelines are easy to mix up. The test is whether they can explain the guidance without being led to the intended answer.

### 4.4 P2P metrics

#### Primary metric — Refund Timeline Comprehension Rate

**Definition:** The percentage of eligible participants who correctly identify the refund timeline and its stated starting point from the guidance they viewed.

- **Numerator:** Number of eligible participants who correctly explain that the inspected guidance states a 3–5-day refund period for the relevant failed/debited-payment case and identifies the payment date as the stated starting point.
- **Denominator:** All eligible participants who were exposed to the relevant guidance and had a valid opportunity to answer the question. Include an “unable to answer” response in the denominator and not in the numerator. Exclude only participants who were not exposed to the content or whose test was invalidated by a documented technical interruption.
- **Unit:** Participant; one scored response per participant.
- **Observation window:** One moderated or unmoderated research session, after exposure to the guidance.
- **Direction:** Higher is better.

**Formula:**

`Refund Timeline Comprehension Rate = Correct participants / Eligible exposed participants × 100`

The result measures comprehension of the wording shown in the test. It does not measure actual refund performance or prove that the stated timeline applies to every type of UPI dispute.

#### Supporting metric 1 — 48-hour Status-Update Comprehension Rate

- **Numerator:** Eligible participants who correctly explain that the up-to-48-hour statement refers to the time for the pending transaction's final status to update, according to the guidance shown.
- **Denominator:** All eligible participants exposed to the relevant guidance who had a valid opportunity to answer, including “unable to answer” responses.
- **Unit:** Participant; one response per participant.
- **Observation window:** One research session.
- **Direction:** Higher is better.

#### Supporting metric 2 — Next-Action Accuracy

- **Numerator:** Eligible participants who select or describe the appropriate next step for the exact point in the scenario, based on the guidance shown. Score the response against a prewritten answer key.
- **Denominator:** All eligible participants who saw the scenario and had a valid opportunity to respond, including “unable to answer” responses.
- **Unit:** Participant; one response per participant.
- **Observation window:** One research session.
- **Direction:** Higher is better.

The answer key must distinguish between a transaction that is still pending, a transaction that has been marked failed, and a transaction for which the refund is overdue. Do not use one generic “contact support” answer for all three states.

#### Guardrail — Incorrect Repeat-Payment Intention Rate

- **Definition:** The percentage of eligible participants who say they would initiate another payment before checking or resolving the original transaction's status in the presented scenario.
- **Numerator:** Eligible participants who indicate an intention to repeat the payment before verifying the original transaction outcome.
- **Denominator:** All eligible participants who answered the repeat-payment intention question.
- **Unit:** Participant; one response per participant.
- **Observation window:** One research session, immediately after the scenario.
- **Direction:** Lower is better.

This is a self-reported intention measure. It is **not** an actual duplicate-payment rate. A higher result is a warning signal that requires follow-up, not proof that duplicate payments occurred.

### 4.5 P2P proposed experiment

**Objective:** Test whether a clearer presentation of the pending-status and refund timelines improves comprehension without increasing unsafe repeat-payment intentions.

| Element | Proposed design |
|---|---|
| Control | The existing PhonePe Help guidance as captured in the evidence set. Preserve its wording and presentation accurately. |
| Treatment | A proposed revised version that clearly separates (a) the pending final-status update period and (b) the refund timeline for a failed/debited-payment case, including the stated starting point and next action. The treatment copy must be drafted and reviewed before the test; it is not represented as existing PhonePe content. |
| Participants | People who use or understand UPI payments and can reasonably interpret the payer scenario. Record relevant eligibility criteria before recruitment. |
| Assignment | Randomly assign participants at the participant level to control or treatment. Each participant sees only one version for the primary comparison. |
| Primary metric | Refund Timeline Comprehension Rate. |
| Supporting metrics | 48-hour Status-Update Comprehension Rate; Next-Action Accuracy. |
| Guardrail | Incorrect Repeat-Payment Intention Rate. |
| Method | Controlled comprehension test using the same scenario, questions, order, and scoring rubric in both groups. |

**Why participant-level randomization:** If a participant sees both versions before answering, the first version may teach them what to look for in the second. That creates a learning or carryover effect and weakens the comparison.

**Decision logic:** Do not recommend the treatment merely because the primary metric improves. The result must also be checked against the guardrail. For example, if comprehension improves but incorrect repeat-payment intention also rises materially, do not recommend rollout without understanding the cause and revising the treatment.

---

## 5. P2M validation plan

### 5.1 Problem statement

When a payer sees a successful merchant payment but the merchant disputes receipt of the payment or the order/booking remains unconfirmed, the payer needs to distinguish a payment-receipt dispute from an order/booking issue and follow the appropriate resolution route.

This is a working problem statement. PhonePe Help already documents separate routes: it says a payment is marked Successful after PhonePe receives confirmation that money has reached the merchant and directs a merchant receipt dispute to `Report Issue` (E-021); for a successful payment with an unconfirmed order/booking, it directs the customer to contact the merchant (E-023). Whether users understand and can find these routes in the live experience remains unvalidated.

**Keep separate:** The RBI-defined P2M failed-transaction condition is payer debit with transaction confirmation not received at the merchant location (E-029). Do not assume that an unconfirmed order/booking or every merchant report after PhonePe Successful matches that regulatory incident.

### 5.2 Hypotheses

| ID | Hypothesis | Validation route | Evidence required |
|---|---|---|---|
| PH-01 — Correct scenario classification | Payers may not consistently distinguish a merchant disputing receipt of payment from a successful payment with an unconfirmed order/booking. | Two separate scenario-based comprehension tasks. | Whether participants identify the problem type and explain the difference between PhonePe's stated Successful criterion and order confirmation. |
| PH-02 — Support-path discoverability | Payers may struggle to find the right route even though Help documents Report Issue for a payment-receipt dispute and merchant contact for an unconfirmed order. | Task-based usability test using the current app/Help flow. | Correct route selection, completion, time-to-find, misroutes and abandonment. |
| PH-03 — Receipt/confirmation discrepancy | In some merchant disputes, payer-facing status and merchant/acquirer records may not appear to align. | Operational investigation using reconciled transaction, merchant/acquirer and payment-system records. | Correlated transaction references, payer debit, PhonePe status, merchant confirmation events and timestamps. |

PH-01 is payer-facing and can be tested with controlled scenarios. PH-02 tests route discovery. PH-03 cannot be established from public Help screenshots or a payer's verbal report; it needs operational and merchant-side evidence.

### 5.3 Proposed comprehension tasks

Use two distinct scenarios; do not combine them into one ambiguous prompt.

**Scenario A — Merchant disputes receipt after PhonePe Successful**

A customer pays a restaurant using PhonePe. PhonePe displays Successful. The restaurant says it has not received the amount. PhonePe Help states that it marks a payment successful after receiving confirmation that money has reached the merchant and advises the payer to report the relevant payment if the merchant denies receipt (E-021).

Ask participants:
1. What does PhonePe's Help content say its Successful status means?
2. What remains to be checked or reconciled between PhonePe and the merchant?
3. What is the appropriate PhonePe route described by the guidance?
4. What transaction details/reference would you retain or share?
5. Would you make another payment immediately? Why or why not?

**Scenario B — Payment successful, order/booking not confirmed**

A customer pays for an order/booking using PhonePe. The payment is successful, but the merchant has not confirmed the order or booking. PhonePe Help says merchants do not inform PhonePe whether an order has been confirmed or service delivered and directs the customer to contact the merchant for an update (E-021; E-023).

Ask participants:
1. Does successful payment status prove the order/booking has been confirmed?
2. Which party should the payer contact for the order/booking update, according to the guidance?
3. What would you check before considering another payment?
4. How is this scenario different from a merchant disputing receipt of the payment?

The moderator must not tell participants the expected route before they answer. Score against a predefined answer key. Record explanations, not only selections.

### 5.4 P2M metrics

#### Primary metric — Correct P2M Issue Classification and Next-Action Rate

**Definition:** Percentage of eligible participants who correctly identify the scenario type and select the matching next action.

- **Numerator:** Participants who correctly distinguish (A) merchant receipt dispute after PhonePe Successful — use the relevant `Report Issue` route; from (B) order/booking not confirmed after successful payment — contact the merchant for an update.
- **Denominator:** All eligible participants exposed to the applicable scenario and given a valid opportunity to answer, including “unable to answer” responses. If both scenarios are shown, report scenario-level rates separately as well as any aggregate.
- **Unit:** Participant-scenario response; do not treat two answers from one participant as two independent people.
- **Observation window:** One research session.
- **Direction:** Higher is better.

#### Supporting metric 1 — Successful-Status Meaning Comprehension

- **Numerator:** Participants who accurately explain PhonePe Help's stated criterion for displaying Successful and distinguish it from order/booking confirmation.
- **Denominator:** All eligible participants exposed to the relevant Help wording and given a valid opportunity to answer, including “unable to answer”.
- **Unit:** Participant.
- **Observation window:** One research session.
- **Direction:** Higher is better.

This measures comprehension of PhonePe's stated guidance. It does not independently validate the underlying payment-system event or merchant settlement.

#### Supporting metric 2 — Support-Path Selection Accuracy

- **Numerator:** Participants who select `Report Issue` for a merchant receipt dispute and contact the merchant for an order/booking update, according to the scenario and prewritten answer key.
- **Denominator:** All eligible participants asked to choose a route and given a valid opportunity to answer, including “unable to answer”.
- **Unit:** Participant-scenario response.
- **Observation window:** One research session.
- **Direction:** Higher is better.

#### Guardrail 1 — Incorrect Repeat-Payment Intention Rate

- **Definition:** Percentage of participants who say they would make another payment before checking the original transaction or following the relevant route.
- **Numerator:** Eligible participants indicating intention to pay again before verifying the original transaction.
- **Denominator:** All eligible participants who answered the question.
- **Unit:** Participant.
- **Observation window:** One research session.
- **Direction:** Lower is better.

This is stated intention, not an actual repeat-payment attempt or duplicate successful-payment rate.

#### Guardrail 2 — Incorrect Payment/Order Classification Rate

- **Definition:** Percentage of participants who incorrectly treat an unconfirmed order/booking as proof that the underlying UPI payment failed, or treat successful payment status as proof that the order is confirmed.
- **Numerator:** Participants exhibiting either predefined classification error.
- **Denominator:** All eligible participants who answered the classification question; define treatment of unable-to-answer responses before testing.
- **Unit:** Participant.
- **Observation window:** One research session.
- **Direction:** Lower is better.

### 5.5 P2M proposed experiment

**Objective:** Test whether a clearer explanation and scenario-specific routing help payers distinguish merchant receipt disputes from order/booking issues and choose the correct next action.

| Element | Proposed design |
|---|---|
| Control | Existing PhonePe Help guidance captured for E-021 and E-023. Preserve the wording and scenario context accurately. |
| Treatment | A proposed presentation that explicitly separates “Merchant says payment not received” (review transaction and use Report Issue) from “Order/booking not confirmed” (contact merchant for an update), while explaining PhonePe's stated Successful criterion. This is a proposed treatment, not existing PhonePe content. |
| Participants | People who use or understand UPI payments and can reasonably interpret the two scenarios. Define eligibility in advance. |
| Assignment | Random assignment at participant level. Each participant sees one version for the primary comparison to avoid carryover. |
| Primary metric | Correct P2M Issue Classification and Next-Action Rate, reported separately by scenario. |
| Supporting metrics | Successful-Status Meaning Comprehension; Support-Path Selection Accuracy. |
| Guardrails | Incorrect Repeat-Payment Intention Rate; Incorrect Payment/Order Classification Rate. |
| Method | Controlled scenario-based comprehension test using consistent facts, wording exposure, question order and prewritten scoring in both groups. |

**Decision logic:** Do not recommend rollout solely because the primary metric improves. If repeat-payment intention or payment/order misclassification worsens versus control, investigate the cause and revise/retest. Actual duplicate-payment impact requires production event/transaction data.

## 6. Metric definitions and scoring rules

### 6.1 Denominator discipline

A denominator must include everyone who had a valid opportunity to produce the outcome being measured. Do not remove participants simply because they answered incorrectly or could not answer; doing so inflates the result.

For comprehension metrics:

- Include correct, partially correct, incorrect, and “unable to answer” responses in the denominator when the participant saw the content and had a valid opportunity to respond.
- Count only responses that meet the predefined correctness standard in the numerator.
- Exclude a participant from that metric only when they were not exposed to the relevant content or the session was invalidated by a documented technical issue.
- Report exclusions and missing responses separately.

For discoverability/usability metrics, a participant who cannot find the article is a task failure and should remain in the task-completion denominator. They may not enter a subsequent content-comprehension denominator if they never saw the content. Report both stages so the end-to-end drop-off is visible.

### 6.2 Example denominator calculation

Assume a hypothetical study recruits 20 participants:

- 2 participants cannot find the Help article;
- 18 participants view the article;
- among those 18, 15 correctly understand the refund timeline, 2 answer incorrectly, and 1 says they cannot answer.

Then:

- **Discoverability rate:** 18 / 20 = **90%**.
- **Comprehension rate among exposed participants:** 15 / 18 = **83.3%**.
- **End-to-end successful completion:** 15 / 20 = **75%**.

These are illustrative numbers only, not actual PhonePe research results. The three metrics answer different questions and must not be substituted for one another.

### 6.3 Scoring rubric

Use a predefined rubric for each open-text response:

| Score | Meaning | Treatment in binary accuracy metric |
|---|---|---|
| Correct | The participant accurately identifies the relevant status/timeline/action and does not introduce a material misconception. | Numerator = 1 |
| Partially correct | The participant identifies part of the answer but misses or misstates a material detail. | Numerator = 0 unless the metric specification explicitly defines a partial-credit score before testing. |
| Incorrect | The participant gives a materially wrong answer or chooses an unsuitable action. | Numerator = 0 |
| Unable to answer | The participant cannot explain or select an answer despite valid exposure. | Numerator = 0; remains in denominator |
| Not exposed / invalid session | The participant did not receive the test content or a documented technical interruption invalidated the response. | Exclude from that metric and report the exclusion |

If partial credit is used, define the scoring weights before testing and report both the weighted score and the strict correct-response rate. Do not retrospectively change the rubric to make results look better.

### 6.4 Percentage versus percentage-point change

When comparing two groups or periods, report both the raw rates and the difference in **percentage points**.

Example: a metric moving from 55% to 70% is an increase of **15 percentage points**, not 15%. The relative increase is approximately 27.3% because `(70 - 55) / 55 × 100 ≈ 27.3%`.

For guardrails, state clearly whether a change is an absolute percentage-point increase or a relative percentage increase. These are not interchangeable.

---

## 7. Experiment quality and statistical plan

The experiments in this document are proposed designs. No sample size, statistical power, significance level, minimum detectable effect, or guardrail tolerance has yet been established.

Before running a controlled comparison:

1. **Define the decision.** State what decision the study is intended to inform: retain current guidance, revise the wording, run another test, or investigate a new problem.
2. **Set the minimum practically important effect.** Decide what improvement would be large enough to justify the change. Do not choose this after seeing the data.
3. **Estimate sample size.** Use the expected control rate, the chosen minimum detectable effect, selected statistical power, and significance level. For a two-group comparison of proportions, use a suitable two-proportion sample-size calculation. Document the assumptions and calculation.
4. **Predefine guardrail tolerances.** Decide what increase, if any, in an undesirable outcome would make the treatment unacceptable. Do not invent a tolerance after the results are known.
5. **Randomize appropriately.** Assign participants to one version and keep scenario wording, device conditions, moderator instructions, and question order consistent.
6. **Predefine the analysis.** Specify the primary metric, supporting metrics, guardrails, exclusions, missing-data handling, and comparison method before collecting responses.
7. **Report uncertainty.** Show group counts, rates, absolute percentage-point differences, and suitable confidence intervals. Do not present a small-sample percentage as a precise population estimate.
8. **Avoid repeated peeking.** Do not stop the study early simply because a result temporarily looks favourable. Use a predefined sample size or a documented sequential-testing method.
9. **Record deviations.** Note recruitment issues, invalid sessions, scoring disagreements, or changes to the protocol.

### 7.1 Small-sample limitation

A small formative study can reveal wording problems, confusing concepts, and potential design directions. It cannot reliably establish the prevalence of a problem across PhonePe's user base or prove a production-level effect.

For example, 3 out of 5 participants selecting an unsafe repeat-payment action is 60% **of that five-person sample**. It is a useful signal for further investigation, not evidence that 60% of PhonePe users would behave that way.

### 7.2 Interpreting an example guardrail result

Suppose a hypothetical P2P experiment produces:

- Primary comprehension: 55% in control and 85% in treatment.
- Incorrect repeat-payment intention: 10% in control and 25% in treatment.

The primary metric improves by 30 percentage points, but the guardrail worsens by 15 percentage points. The treatment should **not** be recommended for rollout on the primary metric alone. Investigate why the revised wording may have increased repeat-payment intention, review the exact responses, revise the treatment, and test again.

The 15-point guardrail movement is a research signal. It is not proof that actual duplicate payments increased.

---

## 8. Decision framework

Apply the following logic separately to P2P and P2M. The actual decision also depends on sample size, uncertainty, study quality, and the predefined thresholds.

| Outcome | Decision | Reason |
|---|---|---|
| Primary metric improves by a practically meaningful amount and all guardrails remain within predefined tolerances. | Consider the treatment promising; proceed to the next validation step or a carefully monitored product test if appropriate. | The intended outcome improved without an unacceptable observed guardrail deterioration. |
| Primary metric improves but a guardrail worsens beyond its predefined tolerance. | Do not recommend rollout yet. Investigate and revise the treatment. | A better primary result may be offset by a harmful unintended outcome. |
| Primary metric does not improve meaningfully and guardrails are unchanged. | Do not recommend the treatment in its current form; reconsider the problem or intervention. | The proposed change has not demonstrated the intended benefit. |
| Results are inconclusive or too imprecise. | Gather more evidence or run a better-designed test. | The data do not support a confident decision. |
| Results differ substantially across important participant groups. | Investigate the differences before making a broad recommendation. | An overall average may hide a group for whom the guidance works poorly. |
| The research suggests an operational or technical issue. | Escalate the question for operational investigation; do not claim a technical root cause from the comprehension study. | User research cannot replace transaction and system evidence. |

“Consider” does not mean automatic production rollout. A participant research study evaluates comprehension and intended actions; a production change requires product, operational, compliance, and engineering review, plus appropriate live monitoring.

---

## 9. Product analytics metrics that would require internal data

The following metrics may help evaluate real-world behaviour after an appropriately designed product change. They are **not measurable from the current public Help screenshots or the synthetic lifecycle dataset** unless the required event-level fields are separately available and validated.

| Metric | Example definition | Required data | Key limitation |
|---|---|---|---|
| Repeat payment attempt rate after an unresolved episode | Eligible pending or confirmation-mismatch episodes followed by a second payment attempt within a predefined window / all eligible episodes. | Stable transaction/episode ID, payer ID, event timestamps, payment-attempt relationship, and valid status history. | A second attempt may be legitimate; deduplication and episode rules are essential. |
| Duplicate successful-payment incidence | Eligible payment episodes with more than one successful payment for the same intended purchase / all eligible episodes. | Linked payment attempts, order/purchase identifiers, transaction outcomes, and merchant/order data. | Two successful payments alone do not prove a duplicate without a reliable purchase/intent linkage. |
| Time to final transaction status | Time from payment initiation to the first authoritative final status, by transaction episode. | Initiation timestamp, status-event history, source/system of each status, and finality rules. | App display time and bank/network event time may differ. |
| Refund completion time | Time from the relevant original payment event or failure event—defined consistently—to the payer's account being credited back. | Original transaction reference, failure/reversal event, bank credit timestamp, and reconciliation. | The start event must be explicit; do not mix different refund/reversal scenarios. |
| Merchant confirmation mismatch rate | Eligible P2M payment episodes where payer-side successful status exists but merchant confirmation is absent or delayed beyond a predefined threshold / eligible P2M episodes. | Payer-side transaction status, merchant confirmation events, correlated transaction/order references, and timestamps. | Requires dependable merchant confirmation telemetry; customer/merchant reports alone may be incomplete. |
| Support contact rate after a payment issue | Eligible payment issue episodes followed by a support contact within a defined window / eligible episodes. | Support events linked to transaction episodes, reason/category, and timestamps. | A lower contact rate is not automatically better; it could mean users cannot find support. |

Do not calculate these metrics using synthetic fields or transaction data that lacks the required event relationships. The existing analytics project may provide contextual descriptive analysis, but it cannot validate PhonePe-specific user behaviour, merchant confirmations, or causal impact.

---

## 10. Research execution checklist

### Before recruitment

- [ ] Confirm the exact PhonePe Help article/screen used in each test.
- [ ] Record source URL, access date, app version/device context where available, and screenshot filename in the Evidence Register.
- [ ] Confirm that the control condition faithfully reproduces the inspected current guidance.
- [ ] Draft the proposed treatment copy and label it as a concept, not existing PhonePe functionality.
- [ ] Write the participant eligibility criteria and recruitment method.
- [ ] Finalize the scenarios, neutral questions, answer keys, and scoring rubric.
- [ ] Define primary metrics, supporting metrics, guardrails, exclusions, and denominator rules.
- [ ] For any quantitative comparison, define the minimum practically important effect, sample-size method, power, significance level, and guardrail tolerances.

### During the study

- [ ] Show each participant only their assigned version for the primary comparison.
- [ ] Give identical scenario facts and instructions to control and treatment groups.
- [ ] Avoid leading questions or teaching participants the answer.
- [ ] Record answers verbatim where possible, then score them using the predefined rubric.
- [ ] Record task failures, time, navigation path, and moderator assistance separately.
- [ ] Do not ask participants to make a real payment or deliberately create a failed/pending transaction.

### After the study

- [ ] Report participant counts and exclusions.
- [ ] Report raw numerators and denominators alongside percentages.
- [ ] Report primary metric, supporting metrics, and each guardrail separately.
- [ ] Show percentage-point differences and uncertainty where appropriate.
- [ ] Review incorrect and partially correct responses to understand the source of misunderstanding.
- [ ] Separate observed participant responses from interpretation and recommendation.
- [ ] State the limitations of sample size, recruitment, and test conditions.
- [ ] Do not claim production impact, regulatory non-compliance, or technical root cause without the relevant additional evidence.

---

## 11. Current status and open work

| Item | Status |
|---|---|
| P2P validation method selected | Defined — proposed comprehension test, with a separate discoverability task. |
| P2M validation method selected | Defined — proposed scenario-based comprehension test, with a separate support-route usability task. |
| P2P primary/supporting/guardrail metrics | Defined at working-draft level. |
| P2M primary/supporting/guardrail metrics | Defined at working-draft level. |
| Metric numerator, denominator, unit, window, exclusions, direction | Specified; final answer keys still need to be completed and reviewed. |
| P2P and P2M experiment designs | Proposed; treatment copy has not yet been authored or tested. |
| Statistical sample-size plan | Not calculated. Requires expected baseline, minimum practically important effect, power, and significance level. |
| Guardrail tolerances | Not set. Must be agreed before running a quantitative experiment. |
| User research | Not conducted. All test outcomes in examples are hypothetical. |
| Current live P2P/P2M failed or pending transaction screens | Not yet verified through a safely completed live transaction journey. Do not simulate a failure by interrupting a real payment. |
| Complaint submission and tracking journey | Requires further direct evidence and should remain an open question until verified. |
| Internal operational/product analytics | Not available in the current evidence set. |

## 12. Conclusion

The proposed validation plan focuses on two testable payer-facing questions:

- **P2P:** Can users correctly distinguish the pending final-status update period from the stated refund timeline and identify the right next step?
- **P2M:** Can users distinguish a successful payment status from merchant/order confirmation and choose an appropriate next action without immediately repeating the payment?

The primary metrics measure comprehension and next-action accuracy. Supporting metrics provide context. Guardrails check whether an intervention introduces a harmful misunderstanding, particularly an intention to pay again before verifying the original transaction.

No product defect, actual duplicate-payment increase, technical root cause, or regulatory breach has been established by this document. Those conclusions require additional evidence. Treat this file as a research and experiment specification, not a report of completed testing or proven product impact.
