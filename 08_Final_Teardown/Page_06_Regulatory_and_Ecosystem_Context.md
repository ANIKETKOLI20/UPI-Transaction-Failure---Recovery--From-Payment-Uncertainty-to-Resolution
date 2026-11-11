# Page 06 — Regulatory & UPI Ecosystem Context

> **Case study:** UPI Transaction Failure & Recovery: From Payment Uncertainty to Resolution  
> **Research product:** PhonePe consumer UPI app  
> **Source review date:** 11 November 2026  
> **Document status:** Working draft for the final case study

## 1. Why the ecosystem matters

A UPI payment is not operated by the app alone. The payer interacts with a TPAP/UPI app, while participating banks and the UPI network perform regulated payment-system functions. The precise responsibility depends on the incident and the participant involved. A customer-facing app can provide the support entry point and explain next steps, but it should not be described as the bank or as the sole decision-maker for every inter-bank payment outcome.

PhonePe's current Grievance Policy identifies PhonePe as a **Third-Party Application Provider (TPAP)** for UPI services, operating in partnership with banks and NPCI. The same policy separately states that PhonePe is authorised by RBI to issue and operate PPIs and has other authorisations. Those roles must not be conflated: PhonePe's PPI authorisation does not make PhonePe the payer's or beneficiary's bank for an ordinary bank-account UPI transfer.

## 2. Key ecosystem participants

| Participant | Role relevant to this teardown | What not to assume |
|---|---|---|
| **RBI** | Regulator; issues applicable payment-system directions, failed-transaction turnaround-time (TAT) and compensation rules; operates the RBI grievance framework for covered regulated entities. | RBI does not investigate every in-app support conversation or automatically decide every merchant/order dispute. |
| **NPCI** | Operates UPI as the network/scheme institution and publishes UPI operating, dispute and UPI HELP guidance for member participants. | An NPCI guideline or pilot is not proof that a particular PhonePe screen is live or that NPCI itself makes every case-level credit decision. |
| **Issuer / remitter bank** | Bank linked to the payer's account; relevant to the debit and the payer-side account record. | Do not assume the app alone can confirm every bank-ledger state. |
| **Beneficiary bank** | Bank receiving the P2P credit; the RBI circular assigns the P2P T+1 auto-reversal action to the beneficiary bank when it cannot credit the beneficiary. | Do not use the P2P beneficiary-bank rule for every P2M or order issue. |
| **Acquirer / merchant-side participant** | Relevant to the merchant payment flow. The RBI circular assigns initiation of the P2M credit adjustment to the acquirer for the specified merchant-confirmation failure. | Do not equate a merchant's unconfirmed order with the RBI-defined missing payment-confirmation-at-merchant-location incident. |
| **PhonePe (TPAP / app)** | User-facing UPI app and support interface; PhonePe's policy provides customer grievance channels and escalation levels for complaints about its app services, including UPI. | PhonePe is not itself the payer's or beneficiary's bank in an ordinary linked-bank UPI transaction. |
| **Merchant** | Owns order acceptance, booking, fulfilment, cancellation and merchant-side service questions where payment itself is confirmed. | A successful payment does not prove that an order, booking or service was confirmed. |

## 3. RBI failed-transaction framework: the two UPI cases

RBI Circular **RBI/2019-20/67**, dated 20 September 2019, sets out specific TAT and compensation requirements for failed transactions. Its Annex defines **T as the transaction calendar date** and states that the framework covers domestic transactions where both originator and beneficiary are in India. The circular describes the prescribed TAT as the outer limit and says banks and other system participants should endeavour to resolve failures sooner.

| RBI-defined UPI incident | Required action in the circular | Compensation for delay beyond TAT |
|---|---|---|
| **P2P funds transfer:** payer's account debited but beneficiary account not credited | If the beneficiary cannot be credited, the **beneficiary bank** must auto-reverse by **T+1 day**. | **₹100 per day** beyond T+1. |
| **P2M merchant payment:** payer's account debited but transaction confirmation not received at the merchant location | The **acquirer** must initiate a **Credit Adjustment** within **T+5 days**. | **₹100 per day** beyond T+5. |

**Critical scope boundary:** T+1 and T+5 apply only when the transaction facts match the corresponding RBI-defined failure incident. They are not universal refund promises for all failed payments, merchant cancellations, refunds, delivery disputes or unconfirmed orders. In particular, a PhonePe payment shown as Successful with an order or booking not confirmed is a separate merchant/order issue unless the evidence also establishes the RBI-defined condition that transaction confirmation was not received at the merchant location.

The RBI circular also says that where financial compensation is involved, it is to be credited **suo motu** (without waiting for a customer complaint or claim). Do not tell readers that they must file a support ticket to become eligible for compensation under the applicable framework.

## 4. Distinguish the three customer scenarios

| Scenario | What is uncertain? | Primary pathway to investigate |
|---|---|---|
| **P2P: beneficiary not credited** | Whether the recipient's bank account received the funds after the payer was debited. | Check transaction status and account records; use PhonePe/bank support and the applicable P2P failure process. |
| **P2M: payment confirmation not received at merchant location** | Whether the merchant-side payment confirmation was received after the payer was debited. | Check transaction state and the applicable P2M payment-failure process; identify the correct bank/acquirer/support route. |
| **P2M: payment Successful, order/booking not confirmed** | Payment is shown as successful, but order acceptance, booking or service fulfilment remains unresolved. | PhonePe Help directs the payer to contact the merchant for order/booking issues; this is not automatically a T+5 failed-payment case. |

## 5. PhonePe's published grievance process

PhonePe Grievance Policy **Version 10, dated 16 July 2026**, includes UPI among the products/services covered by its customer grievance process. The published process for customer complaints is:

| Level | Published route / service level |
|---|---|
| **Level 1** | 24x7 customer support through the PhonePe app (select the transaction in History and choose Contact PhonePe Support), or the published customer support phone numbers. PhonePe commits to a first response within 24 hours and aims to resolve complaints within 15 days, subject to policy notes and external dependencies. |
| **Level 2** | Escalation to the grievance desk if the Level 1 timeline has passed or the customer is dissatisfied. PhonePe commits to a first response within 24 hours and aims to resolve Level 2 complaints within 7 business days, subject to policy notes and exceptions. |
| **Level 3** | Nodal / Principal Nodal Officer escalation. PhonePe commits to a first response within 24 working hours and aims to resolve within 7 business days, subject to policy notes and external dependencies. |
| **Level 4 in PhonePe's policy** | The policy expressly labels the RBI Ombudsman route as applicable to **PhonePe PPIs only** (PhonePe Wallet, Gift Cards and PhonePe RuPay On-The-Go Card / NCMC). Do not copy this Level 4 label as a universal PhonePe UPI escalation route. |

PhonePe's policy also notes that timelines prescribed by RBI, NPCI or card networks apply where those guidelines prescribe a resolution timeline, and that external dependencies may affect actual resolution. Its general note that a refund may take 3–10 days to reflect, depending on payment instrument, must not be substituted for the scenario-specific RBI TAT or the UPI-specific Help text captured in this project.

## 6. RBI Integrated Ombudsman Scheme, 2026: careful escalation wording

The RBI's **Reserve Bank – Integrated Ombudsman Scheme, 2026 (RB-IOS 2026)** came into force on **1 July 2026**, replacing the 2021 Scheme for complaints received from that date. The RBI FAQ says the Scheme covers specified regulated entities, including banks and non-bank PPI issuers; it does not cover every entity or every service automatically.

For a potentially eligible complaint, the customer must first approach the concerned regulated entity and retain proof of that complaint. Under the RBI FAQ, an Ombudsman complaint may be filed if the entity does not reply within **30 days or the timeline specified by RBI/NPCI/card network, whichever is higher**, or if the customer is dissatisfied with the response/resolution. The FAQ also sets a 90-day filing window in the circumstances described there. Eligibility depends on the entity and subject matter; confirm maintainability rather than assuming that every PhonePe UPI issue can be escalated against PhonePe under the Ombudsman Scheme.

The RBI FAQ confirms that a successfully registered RB-IOS 2026 complaint receives a complaint number and can be tracked through the RBI CMS portal. This is distinct from the transaction UTR and from a PhonePe support conversation status.

## 7. NPCI UPI HELP: framework versus live implementation

NPCI's July 2023 UPI HELP Brand Guidelines describe a model in which users can raise UPI transaction complaints through an app / PSP / TPAP, for both P2P and P2M, and check pending or failed transaction status. The guidelines show a reason-selection flow and a complaint-success screen with a complaint reference number and a Check Status action. These are NPCI guidelines/mock-ups; they do not, by themselves, prove that every listed element appears in the current PhonePe journey inspected for this teardown.

NPCI also issued an **8 October 2025 circular** introducing a separate AI-powered UPI HELP Assistant pilot. The circular describes transaction-status checking, logging and tracking complaints, issuer-bank decision support, and access initially through participating member-bank channels / DigiSaathi, with UPI-app integration described as a future step. Treat this as a dated pilot, not evidence that the assistant is currently integrated into PhonePe.

## 8. Implications for this teardown

1. **Do not frame PhonePe as the bank.** PhonePe is the TPAP/app layer for UPI and provides a customer support process; the relevant account-holding and network participants also matter.
2. **Do not collapse T+1 and T+5.** They cover different UPI failure conditions and assign actions to different participants.
3. **Do not apply T+5 to order fulfilment.** Successful payment with an unconfirmed order is a separate merchant/order path in PhonePe's Help guidance.
4. **Do not claim that UTR or support access is missing.** Both were visible in the successful transaction journeys inspected by the researcher.
5. **Do not overstate RBI Ombudsman access.** PhonePe's own policy limits its stated Level 4 route to PPIs; RB-IOS 2026 coverage and maintainability depend on the specific regulated entity and complaint.
6. **Treat complaint tracking as unresolved for the inspected PhonePe journey.** The researcher saw transaction details and a “Successfully processed” support message, but did not verify a distinct PhonePe complaint reference number or tracking page. NPCI's UPI HELP mock-up and RBI CMS tracking do not prove that this particular PhonePe flow displayed those features.

## 9. What this page supports — and what it does not

**Supported:** The exact RBI-defined P2P and P2M failure categories and TATs; the distinction between those categories and a separate order/booking issue; PhonePe's published TPAP description and grievance levels; the current RB-IOS 2026 framework; and NPCI's published UPI HELP guideline/pilot descriptions.

**Not supported by this research:** Actual bank processing time for any individual payment; PhonePe's backend routing or technical root cause; the merchant's internal reconciliation state; the completeness of every current PhonePe support flow; customer confusion or repeat-payment frequency; or a finding that PhonePe is non-compliant.

## 10. Sources

1. **RBI**, Circular RBI/2019-20/67, *Harmonisation of Turn Around Time (TAT) and customer compensation for failed transactions using authorised Payment Systems*, 20 September 2019. [Official circular (PDF)](https://rbi.org.in/commonman/Upload/English/Notification/PDFs/CIRCULAR677EC931A7A65E4D99AA957D8E85BC0A2A.PDF). See Annex, general instructions and UPI table.
2. **RBI**, *Reserve Bank – Integrated Ombudsman Scheme, 2026 — FAQs*, updated 1 July 2026. [Official RBI FAQ](https://www.rbi.org.in/commonperson/english/scripts/FAQs.aspx?Id=3407).
3. **PhonePe**, *Grievance Policy*, Version 10, 16 July 2026. [Official policy](https://www.phonepe.com/grievance-policy/).
4. **NPCI**, *UPI HELP Brand Guidelines*, July 2023. [Official guidelines (PDF)](https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf).
5. **NPCI**, Circular NPCI/UPI/OC-227/2025-26, *Introduction of “UPI HELP” – a pilot with AI powered support for UPI payments*, 8 October 2025. [Official circular (PDF)](https://www.npci.org.in/uploads/UPI_OC_No_227_FY_2025_26_Introduction_of_UPI_HELP_Assistant_an_AI_powered_support_for_UPI_payments_cd501de8f3.pdf).
6. **RBI**, *Master Directions on Prepaid Payment Instruments*, updated 30 September 2026. [Official RBI Master Directions](https://rbi.org.in/scripts/BS_ViewMasDirections.aspx?id=12156). This is additional current regulatory context; it is not a replacement for the scenario-specific TAT circular above.

---

**Editorial note for final PDF:** Keep this page concise. Show the T+1/T+5 table, the three-scenario distinction, the PhonePe grievance ladder and one clear callout: *a merchant order not confirmed after a successful payment is not automatically the RBI P2M T+5 failed-confirmation case.* Use footnotes or endnotes for the full source list.
