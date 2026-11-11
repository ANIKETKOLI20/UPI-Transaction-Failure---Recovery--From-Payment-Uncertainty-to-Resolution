# Page 2 — Research Scope & Methodology

**Case study:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
**Product:** PhonePe consumer UPI app  
**Perspective:** Payer  
**Geography:** Domestic UPI in India  
**Research status:** Desk research and limited interface inspection; no user study or production-data analysis conducted.

---

## 1. Research question

**Primary research question**

How does PhonePe communicate domestic UPI transaction outcomes and guide payer recovery in P2P beneficiary-credit and P2M merchant/order-confirmation scenarios, and what evidence-supported opportunities could improve clarity and access to the appropriate next step?

The investigation focuses on the information available to a payer across three related but distinct situations:

1. **P2P beneficiary-credit issue:** the payer's account is debited but the beneficiary's account is not credited.
2. **P2M merchant payment-confirmation issue:** the payer's account is debited but transaction confirmation is not received at the merchant location.
3. **P2M order/booking issue:** PhonePe displays a successful payment, but the merchant has not confirmed the order or booking, or has not provided the service.

These situations are not interchangeable. In particular, a payment-confirmation issue at the merchant location must not be conflated with an order or service that has not been confirmed.

## 2. Research objectives

- Understand what transaction information and support entry points are visible on inspected successful P2P and P2M transaction screens.
- Review PhonePe Help guidance for pending status, failed payments, refunds, UTR use, bank follow-up, merchant payment disputes and order/booking issues.
- Compare the P2P and P2M recovery paths without assuming that similar labels represent the same underlying event.
- Place the observed guidance in the context of the cited RBI failed-transaction turnaround-time framework, NPCI UPI HELP guidance and PhonePe's grievance policy.
- Identify improvement opportunities that do not simply recreate functionality already visible in the inspected app.

## 3. Scope boundaries

| In scope | Out of scope |
|---|---|
| Payer-facing domestic UPI experience in PhonePe | Backend, bank-switch, NPCI or network root-cause diagnosis |
| P2P beneficiary-credit and P2M merchant/order scenarios | PhonePe-wide or UPI-wide failure-rate estimates |
| Help Centre guidance and inspected successful transaction/support screens | Actual user confusion or satisfaction without user research |
| Visible transaction details, UTR/reference, receipt and support entry points | Actual duplicate-payment frequency without transaction-event data |
| Scenario-specific RBI turnaround-time context and official grievance information | Merchant acquiring, settlement or reconciliation processes not directly evidenced |
| Proposed usability/comprehension validation | Causal claims without a controlled experiment or suitable data |

The investigation did not deliberately create a failed or pending payment, submit a false complaint, or initiate a bank dispute for research purposes.

## 4. Research approach and activities completed

This was a qualitative product teardown using document review, evidence logging and limited inspection of existing app screens.

| Activity | What was examined | What it can support | What it cannot support |
|---|---|---|---|
| PhonePe Help Centre review | Screenshots of Help articles and issue categories collected on 3 November 2026 | What the supplied Help content states about pending status, refunds, UTR, bank follow-up, merchant issues and order/booking concerns | Whether every article is current, how often users find it, or how PhonePe's backend processes an individual payment |
| Successful P2P interface inspection | Existing successful transaction details and the associated support journey, inspected 10–11 November 2026 | Visible status, recipient and bank context, UTR/reference, payment details, receipt/support access and displayed issue suggestions | Behaviour of live pending/failed screens or the outcome of a submitted complaint |
| Successful P2M interface inspection | Existing successful merchant transaction details and the associated support conversation, inspected 10–11 November 2026 | Visible status, transaction reference, payment details, receipt/support access and the displayed merchant/order support guidance | Actual merchant-side system state, order-system integration, or the resolution of a real disputed payment |
| Official-document review | RBI circular dated 20 September 2019; NPCI UPI HELP Brand Guidelines dated July 2023; PhonePe Grievance Policy Version 10 dated 16 July 2026 | The content and scope of those named official documents | A complete legal opinion or proof that every individual transaction is compliant |
| Evidence and claim mapping | Evidence register, screenshot index and claim map | Traceability between report statements and recorded material | Independent verification of source details that were not captured, such as missing article URLs or app metadata |

## 5. Evidence handling and analytical rules

Each report statement is classified according to the type of support available:

- **Direct observation:** something visible on the inspected PhonePe screen or in a supplied screenshot.
- **Source-supported statement:** something explicitly stated in PhonePe Help or an identified official document. Attribute the statement to its source.
- **Interpretation or hypothesis:** a possible explanation or user difficulty that has not yet been validated.
- **Recommendation:** a proposed product change, not a statement about existing functionality.

The report uses Evidence IDs from the canonical `Evidence_Register.xlsx`. Help Centre screenshots are evidence of the Help content shown in those captures; they are not proof of backend processing. Live successful-transaction screens are evidence of the particular screens inspected; they do not establish that every PhonePe user sees an identical flow.

Where metadata was not captured, it remains disclosed rather than inferred. This includes the exact PhonePe app version, device/OS, Help article URLs and article publication/update dates.

## 6. Source base

The case study draws on four source groups:

1. **PhonePe Help Centre screenshots** supplied by the researcher and collected on 3 November 2026. The report cites the corresponding canonical Evidence IDs; article URLs and publication/update dates were not captured.
2. **PhonePe app screens** inspected by the researcher on 10–11 November 2026, limited to existing successful P2P and P2M transactions and their visible support journeys. App version and device/OS details were not captured.
3. **Reserve Bank of India:** *Harmonisation of Turn Around Time (TAT) and customer compensation for failed transactions using authorised Payment Systems*, RBI/2019-20/67, 20 September 2019. The circular defines specific P2P and P2M failed-transaction scenarios; its timelines must not be generalized to every payment or order issue.  
   https://www.rbi.org.in/Scripts/BS_CircularIndexDisplay.aspx?Id=11693
4. **NPCI and PhonePe official documents:** *UPI HELP Brand Guidelines* (July 2023) and PhonePe *Grievance Policy*, Version 10 (16 July 2026). These provide ecosystem and grievance-policy context; their precise scope should be retained when cited.  
   NPCI: https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf  
   PhonePe: https://www.phonepe.com/grievance-policy/

## 7. Research limitations

- Only successful P2P and P2M transaction screens were inspected live. Live pending and failed transaction screens were not inspected.
- The full complaint submission, ticket/reference creation and complaint-tracking journey was not completed. No false complaint or bank dispute was submitted.
- No participant interviews, usability tests, comprehension tests or controlled experiments were conducted.
- No internal PhonePe transaction events, bank records, merchant confirmation signals or backend logs were available.
- The number of screenshots and support articles reviewed does not establish the frequency or severity of a user problem.
- Exact app version, device/OS, Help article URLs and article publication/update dates were not captured.
- Any proposed user benefit remains an expected outcome to validate, not a measured result.

## 8. Interpretation guardrails

- PhonePe Help describes a pending-status update window of up to 48 hours and a 3–5-day refund timeline for relevant failed-payment scenarios. These are different events and must not be presented as a single universal timeline.
- RBI's P2P T+1 and P2M T+5 turnaround-time categories apply to the specific incidents defined in the RBI circular. They must not be applied indiscriminately to every pending payment or an unconfirmed order.
- PhonePe Help states that a payment is marked successful after PhonePe receives confirmation that the money reached the merchant; it separately distinguishes merchant order/service confirmation. Attribute this explanation to PhonePe Help.
- The presence of a support category does not establish that users can easily discover it or that a complaint has been resolved.
- A visible "Successfully processed" message in a support conversation does not, by itself, prove that the underlying payment dispute was resolved.
- Do not claim high transaction failure rates, frequent duplicate payments, technical root causes or regulatory non-compliance from the evidence collected in this teardown.

---

**Page takeaway:** This teardown combines Help-content review, limited inspection of existing successful P2P/P2M journeys and official-document review. It identifies evidence-supported opportunities while explicitly separating observed interface behaviour from untested hypotheses and proposed improvements.
