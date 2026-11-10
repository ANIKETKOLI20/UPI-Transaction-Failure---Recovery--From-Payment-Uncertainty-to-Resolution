# P2M Successful Transaction Audit

## 1. Audit purpose

This audit documents one existing successful merchant-payment experience inspected in the PhonePe app, together with the support guidance shown during the subsequent interaction.

The audit focuses on what was visible to the payer in the inspected experience. It does not establish how every PhonePe P2M transaction behaves, what happened in the merchant's backend, or whether the merchant's order system confirmed the order.

## 2. Inspection details

| Field | Record |
|---|---|
| Product | PhonePe consumer app |
| Flow | Domestic UPI, P2M (merchant payment) |
| Perspective | Payer |
| Transaction used | Existing successful merchant transaction |
| Inspection date | 10 November 2026 (based on the supplied support screenshot filename and conversation) |
| App version | Not recorded |
| Device / OS | Not recorded |
| Transaction amount | Visible in the support conversation context; exact amount intentionally not recorded here |
| Merchant name | Not recorded |
| Original transaction-screen screenshot | Not supplied with this audit; observations below are based on the user's inspection notes |
| Support-chat screenshot | Supplied by the user; filename: `WhatsApp Image 2026-11-10 at 17.21.50.jpeg` |

Do not add personal, bank, UPI ID, merchant, or transaction-reference details to the public repository. Keep original screenshots private or redact them before committing.

## 3. Transaction details screen — direct observations reported by the inspector

The user opened an existing successful P2M transaction from PhonePe History and reported the following:

| Element inspected | Observation | Evidence status |
|---|---|---|
| Transaction status | `Success` / `Successful` was displayed | Observed by the user; original transaction-screen capture was not supplied for this audit |
| Transaction reference | Reference information, including UTR, was available | Observed by the user; exact field labels and values are not reproduced |
| Payment details | Payment details were visible | Observed by the user |
| Receipt sharing | A receipt-sharing option was available | Observed by the user |
| Support access | A support/contact option was available | Observed by the user |
| Payment versus order distinction | No explicit distinction was visible on the inspected transaction screen | Screen-specific observation only; not evidence that no explanation exists elsewhere in the app |

### Screen-level observation

The inspected successful P2M transaction screen exposed the transaction status, applicable reference information, payment details, receipt-sharing functionality, and support access. The user did not see an explicit explanation on that screen separating payment completion from order or booking confirmation.

This finding is limited to the one screen inspected. It must not be generalised to all PhonePe transaction screens or the entire app.

## 4. Support journey — supplied screenshot and user-reported sequence

After opening support for the transaction, the user saw the following guidance in the support conversation. The supplied screenshot shows the end of the guidance card and the follow-up prompt.

### 4.1 Guidance visible in the supplied screenshot

The visible `Things to note` section states:

- Contact the merchant directly for refunds, pending orders, or cancellations.
- PhonePe cannot cancel or reverse payments.
- Raise a chargeback if the merchant denies help.
- A `How to raise a chargeback?` link is available.

The conversation then asks `Do you need any further help?` and presents two options:

- `Yes, I need help`
- `No, I got it`

### 4.2 User-reported follow-up

The user selected `Yes, I need help` and reported that the next interaction displayed `Successfully processed` and asked whether further help was needed.

The user also clarified that the transaction context above the cropped portion of the supplied screenshot showed the UTR and transaction status; the amount, date, and time were also visible.

| Support-journey element | Observation | Evidence status |
|---|---|---|
| Contextual transaction information | UTR and transaction status visible above the cropped support guidance; amount, date, and time also visible | User-reported from the inspected conversation; not all fields are visible in the supplied crop |
| Merchant guidance | Contact the merchant for refunds, pending orders, or cancellations | Visible in supplied screenshot |
| Payment cancellation / reversal guidance | PhonePe says it cannot cancel or reverse payments | Visible in supplied screenshot |
| Escalation guidance | Raise a chargeback if the merchant denies help | Visible in supplied screenshot |
| Chargeback help link | `How to raise a chargeback?` | Visible in supplied screenshot |
| Further-help prompt | `Do you need any further help?` | Visible in supplied screenshot |
| Further-help action | `Yes, I need help` and `No, I got it` | Visible in supplied screenshot |
| Result after selecting further help | `Successfully processed`, followed by a further-help prompt | Reported by the user; full resulting screen was not supplied |
| Separate complaint ID / ticket number | Not identified in the supplied screenshot or description | Not established; this does not prove that no reference is generated elsewhere |
| Formal complaint tracking | Not verified | Open question |

### 4.3 Important interpretation boundary

The phrase `Successfully processed` appeared after the user selected `Yes, I need help`. Based on the available material, it is not possible to determine whether this refers to the support interaction, a selected action, or the payment itself. Do not describe it as proof that the payment dispute was resolved or that a formal complaint was registered.

Likewise, the presence of UTR, status, amount, date, and time in the support conversation shows that transaction context was visible. It does not establish whether those details were automatically attached to a formal complaint or whether a support ticket was created.

## 5. Evidence versus interpretation

| Type | Statement | Appropriate treatment |
|---|---|---|
| Direct observation (screen) | The inspected transaction screen showed Successful, reference information, payment details, receipt sharing, and support access | Include as a one-screen observation, attributed to the inspection |
| Direct observation (screen) | No explicit payment-versus-order distinction was visible on that inspected transaction screen | Include with the one-screen limitation |
| Direct observation (support screenshot) | Support guidance directs users to contact the merchant for refunds, pending orders, or cancellations | Include as observed support guidance |
| Direct observation (support screenshot) | Support guidance says PhonePe cannot cancel or reverse payments and provides chargeback guidance if the merchant denies help | Attribute the wording to the displayed PhonePe support guidance |
| User-reported observation | UTR, status, amount, date, and time were visible in the transaction context above the cropped screenshot | Mark as user-reported; retain a full redacted capture if available |
| Interpretation | The support conversation provides a contextual path for merchant-related questions and further help | Reasonable interpretation, not a measured outcome |
| Hypothesis | Making the distinction between payment completion and order/booking confirmation clearer on the transaction screen may help users choose the correct next action | Requires usability/comprehension testing |
| Unsupported conclusion | PhonePe's successful P2M transaction is not credited to the merchant | Do not claim this; PhonePe Help describes Successful as displayed after PhonePe receives confirmation that money reached the merchant (see canonical Help evidence E-021) |
| Unsupported conclusion | The support journey creates no ticket or complaint reference | Do not claim this; a separate identifier or tracking mechanism was not established from the supplied view |

## 6. Related PhonePe Help evidence and interpretation

The canonical evidence register should be used for the exact evidence IDs. In the reconciled register discussed in this project:

- **E-021** records PhonePe Help guidance for a merchant disputing receipt of payment after PhonePe shows Successful. The Help article says PhonePe marks a payment Successful after receiving confirmation that money has reached the merchant, and directs the payer to report the payment-related issue to PhonePe. It also distinguishes merchant receipt from whether the merchant confirmed an order or service.
- **E-023** records guidance for a successful payment where the order or booking is not confirmed. The Help article directs the payer to contact the merchant for the order/booking issue.
- **E-029** records the RBI-defined P2M incident category where the payer is debited but transaction confirmation is not received at the merchant location. The regulatory T+5 auto-reversal rule applies only when the circular's conditions for that incident are met.

Keep these cases separate:

1. **Merchant disputes receipt of payment:** PhonePe Help directs the payer to report the payment-related issue to PhonePe.
2. **Order or booking is not confirmed:** PhonePe Help directs the payer to contact the merchant.
3. **Payer debited, transaction confirmation not received at merchant location:** This is the specific RBI P2M incident category; do not automatically treat every order/booking problem or merchant support complaint as this category.

## 7. What this audit supports

The evidence supports these limited statements:

1. On the inspected successful P2M transaction screen, the payer could access transaction status, reference information, payment details, receipt sharing, and support.
2. No explicit payment-versus-order confirmation explanation was visible on that inspected transaction screen.
3. The inspected support conversation displayed guidance about contacting the merchant for refunds, pending orders, and cancellations, and chargeback guidance if the merchant denied help.
4. Transaction context (UTR/status and amount/date/time) was visible in the support conversation according to the user's inspection.
5. The support interaction offered a further-help choice and subsequently displayed `Successfully processed`, but the precise meaning of that message and any formal complaint status remain unverified.

## 8. What this audit does not establish

This audit does not establish:

- That PhonePe's entire app lacks payment-versus-order clarity.
- That the displayed Successful status was incorrect.
- That a merchant's bank account was not credited.
- That a merchant's POS, QR, or order-management system received or failed to receive a particular confirmation signal.
- That users are confused or make duplicate payments.
- That the support interaction created a formal complaint or ticket.
- That a complaint ID, service-level timeline, or tracking mechanism does not exist elsewhere in the flow.
- That PhonePe breached an RBI requirement.

## 9. Open questions for further inspection

| Open question | Next safe verification step |
|---|---|
| Is a separate complaint ID or ticket number displayed? | Review the complete support conversation and any case-details/history screen without submitting a false complaint |
| Is the support response tied to the original transaction automatically? | Observe whether the transaction is preselected and whether transaction details are shown in the conversation; do not infer automatic attachment from visibility alone |
| Is there a track-status or complaint-history route? | Inspect the app's existing Support / Help / History area |
| Are payment-receipt disputes and order/booking issues routed differently in the live app? | Inspect available issue categories without submitting a complaint |
| Does the transaction screen itself explain payment completion versus order confirmation? | Retain a full redacted screenshot of the relevant transaction screen and compare it with the Help article |
| What does `Successfully processed` mean in the support conversation? | Capture the complete preceding and following messages; do not assume it means payment dispute resolution |

## 10. Evidence handling and privacy

- Keep the original support screenshot in the project's private evidence archive.
- Before publishing or pushing a screenshot to a public GitHub repository, redact UTR, transaction ID, UPI ID, account details, phone numbers, personal names, merchant-specific identifiers, and any other sensitive information.
- The support screenshot supplied for this audit is named `WhatsApp Image 2026-11-10 at 17.21.50.jpeg`. Preserve the original filename in the private archive and reference it in the evidence register if it is assigned a canonical evidence ID.
- The original successful transaction details screenshot was not supplied with this audit. Add its filename and evidence ID only after a redacted capture is saved and mapped in the register.
- Record the PhonePe app version and device/OS if available during a future inspection. Do not backfill these details from memory.

## 11. Current audit conclusion

The inspected PhonePe successful P2M transaction screen provides access to transaction status, reference information, payment details, receipt sharing, and support. The inspected screen did not visibly explain the distinction between payment completion and order/booking confirmation.

The support conversation provides merchant-contact guidance, chargeback guidance, transaction context, and a way to request further assistance. However, the available evidence does not establish whether a formal complaint ID or complaint-tracking mechanism is generated.

The most defensible product opportunity is therefore to investigate whether the transaction details experience can make the distinction between **payment completion** and **order/booking confirmation** clearer, while preserving the existing support routes and transaction-reference access. This is a proposed opportunity that still requires further usability validation; it is not a confirmed product defect.
