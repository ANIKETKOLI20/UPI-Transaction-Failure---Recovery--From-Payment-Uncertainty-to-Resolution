# PhonePe UPI Transaction Recovery Teardown

**Working title:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Case-study status:** Draft v0.1 — content structure and executive-summary draft  
**Product:** PhonePe consumer UPI app  
**Perspective:** Payer  
**Geography:** Domestic UPI in India  
**Evidence window:** PhonePe Help screenshots collected 3 November 2026; live successful-transaction and support screens inspected 10–11 November 2026; official sources checked 11 November 2026.

> **Publication note:** This is a structured draft, not the final PDF. The exact app version, device/OS, Help article URLs and publication/update dates were not captured. Live pending/failed screens and the complete complaint-tracking journey have not been inspected. Do not remove these limitations unless the missing evidence is later collected.

---

## Draft executive summary

This teardown examines how PhonePe communicates UPI transaction outcomes and supports payer recovery across two domestic payment contexts: person-to-person (P2P) transfers and person-to-merchant (P2M) payments. The investigation focuses on what a payer can understand and do when a beneficiary says a transfer has not been credited, when a merchant disputes receipt of payment, or when a paid order or booking has not been confirmed.

The evidence includes PhonePe Help Centre screenshots collected on 3 November 2026, live successful P2P and P2M transaction screens and support interactions inspected on 10–11 November 2026, the RBI's 20 September 2019 failed-transaction turnaround-time circular, NPCI's UPI HELP Brand Guidelines (July 2023), and PhonePe's Grievance Policy (Version 10, dated 16 July 2026).

The inspection found that the successful transaction screens already expose key transaction information and utilities, including transaction references/UTR, payment details, receipt sharing and support access. The inspected P2P support journey includes an issue option for an amount not credited to a specific user and a bank-dispute route. PhonePe Help also provides guidance on pending-status updates, failed-payment refunds, UTR use and bank follow-up.

A material distinction emerged in the P2M journey. PhonePe Help states that it marks a payment successful after receiving confirmation that the money has reached the merchant, while separately explaining that PhonePe does not receive confirmation of whether the merchant confirmed the order or delivered the service. The inspected successful P2M transaction screen did not visibly present this payment-versus-order distinction. This is a potential communication and discoverability opportunity, not proof that PhonePe's payment status is inaccurate or that users are confused.

The teardown therefore does not recommend adding UTR visibility, receipt sharing or a new generic support route as if these capabilities were absent. The provisional opportunities are to make the distinction between payment completion and order/booking confirmation more visible at the relevant point in the P2M journey, and to make existing issue-specific recovery paths easier to discover. For P2P, the main opportunity to test is whether the pending-status and refund timelines are understood as separate events.

No user research, controlled experiment, production transaction analysis or backend investigation has been conducted. Expected benefits and validation metrics in this report are proposals, not measured outcomes. The report does not estimate PhonePe's UPI failure rate, claim that the app causes duplicate payments, diagnose technical root causes or conclude that PhonePe is non-compliant with RBI requirements.

---

## Eight-page report plan

### Page 1 — Executive summary

- Working title and product context.
- The payer-facing question being investigated.
- Three strongest evidence-backed takeaways.
- Two provisional product opportunities.
- A concise statement of research limitations.

### Page 2 — Research question, scope and method

**Primary research question**  
How does PhonePe communicate domestic UPI transaction outcomes and guide payer recovery in P2P beneficiary-credit and P2M merchant/order-confirmation scenarios, and what evidence-supported opportunities could improve clarity and access to the appropriate next step?

**In scope**
- Payer perspective; domestic UPI; P2P and P2M.
- Pending, failed and successful-status Help guidance.
- Transaction details, support entry points and visible support conversation.
- RBI failed-transaction TAT framework and PhonePe grievance information.

**Out of scope**
- Backend/network root-cause diagnosis.
- PhonePe-wide or UPI-wide failure rates.
- Actual user confusion, duplicate-payment frequency or causal effects without research/data.
- Merchant acquiring, settlement or reconciliation systems not directly evidenced.

**Method**
- Desk review of PhonePe Help Centre screenshots.
- Inspection of existing successful P2P/P2M transactions and support journeys; no deliberately failed payment or false complaint was created.
- Review of official RBI, NPCI and PhonePe documents.
- Evidence register and claim-to-evidence mapping.

### Page 3 — P2P and P2M scenario definitions

Keep these cases separate:

1. **P2P funds transfer:** payer's account is debited but the beneficiary's account is not credited.
2. **P2M payment-confirmation incident:** payer's account is debited but transaction confirmation is not received at the merchant location.
3. **P2M order/booking issue:** payment is successful, but the merchant has not confirmed the order or provided the service.

Do not treat case 2 and case 3 as interchangeable. PhonePe Help describes a successful payment as one for which PhonePe has received confirmation that money reached the merchant; it separately says PhonePe does not receive information about order/service confirmation.

Include the P2P/P2M workflow diagrams with explicit labels for observed guidance, scenario assumptions and uninspected branches.

### Page 4 — What the inspected PhonePe experience currently provides

**Successful P2P transaction screen (observed):**
- Status shown as "Transaction Successful".
- UTR/reference visible.
- Recipient details and payment details visible.
- Receipt sharing and support access available.
- Beneficiary-not-credited guidance was not visible directly on the inspected transaction-details screen.

**P2P support journey (observed/reported):**
- Recipient name and bank/account information shown in support context.
- Issue suggestions include an amount not credited to a specific user, wrong account/UPI ID, refund/cancellation and report-fraud options.
- A bank-dispute route is shown.
- Do not claim that a complaint was submitted or tracked; the flow was not taken through a real complaint submission.

**Successful P2M transaction screen (observed):**
- Successful status, UTR/reference, payment details, receipt sharing and support access available.
- No explicit payment-versus-order-confirmation explanation was visible on the inspected screen.

**P2M support conversation (observed/reported):**
- Context included transaction amount/date/time and transaction details.
- Guidance directed users to contact the merchant for refunds, pending orders or cancellations; it described a chargeback route if the merchant did not help.
- A "Successfully processed" message and further-help prompt appeared. This does not prove the underlying payment dispute was resolved.

### Page 5 — Findings and evidence-backed synthesis

Use no more than four findings:

1. **Recovery guidance exists across Help and support.** PhonePe provides separate routes for pending, failed, beneficiary-not-credited, merchant-payment and order/booking concerns. The unresolved question is how easily users find the correct route.
2. **Pending status and refund are different events.** Help describes up to 48 hours for final-status updates and 3–5 days for refunds in relevant failed-UPI scenarios. These are Help statements, not a universal guarantee or a substitute for RBI TAT rules.
3. **Transaction proof is already available in the inspected successful screens.** UTR/reference, payment details and receipt sharing were present; adding these as new features is not supported by the current inspection.
4. **P2M payment completion and order confirmation are distinct.** PhonePe Help explains this distinction, but it was not visible on the inspected successful P2M transaction screen. This supports a limited, testable opportunity to improve contextual clarity.

For every finding, cite the Evidence ID(s) from the canonical Evidence Register and identify whether the support is a direct live-screen observation, PhonePe Help statement or official external source.

### Page 6 — Regulatory and ecosystem context

**RBI Circular RBI/2019-20/67, 20 September 2019:**
- P2P: account debited but beneficiary account not credited — auto-reversal by beneficiary bank latest by T+1; ₹100 per day for delay beyond T+1.
- P2M: account debited but transaction confirmation not received at merchant location — auto-reversal within T+5; ₹100 per day for delay beyond T+5.
- T is the calendar date of the transaction.
- These are scenario-specific categories. Do not apply T+5 to every successful payment where an order is not confirmed.

**NPCI UPI HELP Brand Guidelines (July 2023):**
- Describe UPI HELP as an app/PSP/TPAP route for UPI transaction complaints, including P2P and P2M, and for pending/failed transaction status checks.
- Use as ecosystem-level context, not proof that PhonePe's exact interface must match every diagram in the guideline.

**PhonePe Grievance Policy, Version 10 (16 July 2026):**
- The policy states a first-response commitment of 24 hours and aims to resolve customer complaints within 15 days at Level 1; Level 2 aims for resolution within 7 business days, subject to policy notes and exceptions.
- The policy identifies Level 4 RBI Ombudsman access as applicable to PhonePe PPIs only. Do not describe it as a universal escalation route for all PhonePe UPI complaints.

### Page 7 — Opportunities and recommendations

**Opportunity 1 (provisional priority): Make payment completion versus order/booking confirmation clearer in the P2M transaction experience.**
- Rationale: PhonePe Help distinguishes payment receipt from order/service confirmation; the inspected successful P2M screen did not visibly explain the distinction.
- Proposed treatment: add a concise contextual explanation or entry point to the existing order/booking help path on relevant successful merchant transactions. Do not imply that PhonePe can independently verify order confirmation unless it has a reliable signal.
- Expected benefit: better understanding of what a successful payment confirms and what to do if an order is not confirmed.

**Opportunity 2: Improve discoverability of existing issue-specific recovery paths.**
- Rationale: support options and Help guidance exist, but the inspection has not tested how easily users locate the correct path from the transaction screen.
- Proposed treatment: make existing categories such as beneficiary-not-credited and merchant-payment/order issues easier to reach from relevant transaction details.
- Expected benefit: higher task completion and more accurate next-step selection.

**P2P supporting opportunity:** Test whether the app clearly distinguishes the up-to-48-hour pending-status update from the refund timeline that applies if the payment ultimately fails. Do not state that users misunderstand this until tested.

Explicitly remove recommendations to add UTR, receipt sharing or a generic support route, because those were present in the inspected successful transaction screens/support journeys.

### Page 8 — Validation plan, limitations, conclusion and references

**Proposed validation (not conducted):**
- Moderated usability and comprehension tasks using realistic, clearly labelled scenarios.
- Primary metric for P2M: Correct Next-Action Rate.
- Supporting metric: Payment/Order Status Comprehension Rate.
- Guardrails: Incorrect Repeat-Payment Intention Rate and Incorrect Order/Payment Classification Rate.
- P2P comprehension metric: correct understanding of status-update versus refund timelines.
- Define sample size, thresholds, exclusions and decision rules before any experiment. Do not present illustrative percentages from training exercises as project results.

**Limitations:**
- Only successful P2P/P2M transaction-detail screens were inspected live.
- Live pending/failed screens were not inspected.
- The full complaint submission/reference/tracking journey was not completed.
- No users were recruited or interviewed; no usability/comprehension study was conducted.
- No production transaction logs, merchant confirmation events or backend records were available.
- Exact PhonePe app version, device/OS, Help article URLs and article publication/update dates were not captured.

**Conclusion:** The available evidence supports a focused opportunity around contextual payment-versus-order clarity and discoverability of existing recovery guidance. It does not support broad claims about system reliability, frequent duplicate payments, root causes or regulatory non-compliance.

---

## Working references for final PDF

1. Reserve Bank of India. (20 September 2019). *Harmonisation of Turn Around Time (TAT) and customer compensation for failed transactions using authorised Payment Systems*, RBI/2019-20/67. https://www.rbi.org.in/Scripts/BS_CircularIndexDisplay.aspx?Id=11693
2. National Payments Corporation of India. (July 2023). *UPI HELP Brand Guidelines*. https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf
3. PhonePe. (16 July 2026). *Grievance Policy*, Version 10. https://www.phonepe.com/grievance-policy/
4. PhonePe Help Centre screenshots supplied by the researcher; captured 3 November 2026. Article URLs and publication/update dates not captured; cite the canonical Evidence IDs in the Evidence Register.
5. PhonePe app transaction and support screens inspected by the researcher, 10–11 November 2026. App version and device/OS metadata not captured; cite the corresponding live-screen Evidence IDs once mapped in the register.

---

## Editorial rules for the final report

- Label every claim as direct observation, source-supported statement, interpretation/hypothesis or recommendation.
- Do not call a payment "payer-side successful only" when describing PhonePe's own Help definition; attribute the Help definition accurately.
- Keep merchant payment confirmation separate from order/booking confirmation.
- Keep PhonePe's 48-hour/3–5-day Help language separate from RBI's scenario-specific T+1/T+5 turnaround times.
- Do not claim that UTR, receipt sharing or support access is missing where observed screens show those functions.
- Do not present hypothetical test scores as results.
- Use exact Evidence IDs from the reconciled workbook and verify all IDs before publication.
