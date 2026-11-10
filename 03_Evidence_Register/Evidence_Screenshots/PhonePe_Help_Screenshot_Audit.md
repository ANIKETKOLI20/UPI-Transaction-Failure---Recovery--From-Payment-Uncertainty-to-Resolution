# PhonePe Help Screenshot Audit

**Purpose:** Audit the PhonePe Help screenshots supplied for the final teardown and record what they actually support.

**Capture context:** The supplied filenames indicate screenshots captured on 3 November 2026. The screenshots show English-language PhonePe Help articles. They do not show article URLs, publication/update dates, or a verifiable PhonePe app version. Treat 3 November 2026 as the screenshot capture date, not the article publication date.

**Important:** H-01 to H-19 are provisional identifiers for this screenshot batch. Cross-reference them to the existing E-IDs in `03_Evidence_Register/Evidence_Register.xlsx`; do not leave two competing ID systems in the final report.

## 1. Screenshot inventory

| Provisional ID | Screenshot number | Article shown | What it supports |
|---|---:|---|---|
| H-01 | 1 | Can I cancel my pending payment? | PhonePe Help says an initiated UPI payment cannot be cancelled; asks users to wait 48 hours for final status. If it fails, the page says the amount will be refunded in 3–5 days. |
| H-02 | 2 | What if my payment is pending for more than 48 hours? | If the payment remains pending in History after 48 hours, the user can report the issue; the article says PhonePe will escalate it with banking authorities. |
| H-03 | 3 | Why did my UPI payment fail? | Lists possible reasons: UPI network, bank technical issue, wrong PIN, insufficient balance, bank/UPI limits, security reasons, and other account issues. Advises checking History before retrying. |
| H-04 | 4 | Why is my money deducted for my failed payment? | Describes a 3–5-day refund period from payment date, checking the bank statement after five days, contacting the bank with UTR if not refunded, possible immediate refund with delayed SMS, and a separate 7–9-day RuPay credit-card timeline. |
| H-05 | 5 | Why is my money not refunded yet? | Repeats the 3–5-day UPI refund guidance and says to contact the bank with UTR if no refund after five days; notes delayed SMS and a separate RuPay credit-card timeline. |
| H-06 | 6 | Where can I find the UTR number? | Gives the path History → select payment → 12-digit UTR in the “Debited from” section; also points to the bank statement. |
| H-07 | 7 | How does the receiver know into which account the money is deposited? | Says payments to a PhonePe-registered mobile number/UPI ID go to the receiver’s primary bank account set in PhonePe at payment time; for a non-PhonePe UPI ID, ask the receiver to check the account statement linked to that UPI ID. |
| H-08 | 8 | What if the money is not deposited into the receiver’s account instantly? | Advises the receiver to contact their bank and raise a chargeback using the UTR; says to check the bank statement because SMS may be delayed. |
| H-09 | 9 | How to raise a chargeback with a bank? | Lists bank portal/app, customer support, or branch as routes; says to do this within 60 days; lists amount, payment date, payment mode, and UTR as required information. |
| H-10 | 10 | Sample Template to Raise a Chargeback with Your Bank | Provides a sample email/template and fields including account holder, account number, date, amount, UTR, receiver, and reason. Treat the template as PhonePe Help content, not legal advice. |
| H-11 | 11 | What if the bank denies help? | Uses the label “RBI Banking Ombudsman” and says to complain if the bank denies or delays support. This terminology should not be copied into the final report as current escalation guidance without checking the current RBI framework. |
| H-12 | 12 | What if the merchant denies having received the amount for a successful payment? | PhonePe Help states that it marks a payment successful only after receiving confirmation that the money reached the merchant. It separately says merchants do not inform PhonePe whether they confirmed the order or provided the service. If the merchant denies receiving the money, the article directs the user to report the issue for that payment. |
| H-13 | 13 | What if I have paid twice for an order or booking? | Advises contacting the merchant to check payment records and refund the excess; if the merchant refuses, contact the bank with UTR. It explicitly advises checking final payment status before trying again. |
| H-14 | 14 | What if the order or booking is not confirmed for a successful payment? | Advises contacting the merchant for order/booking status. Distinguishes payment-related issues (PhonePe) from order/booking-related issues (merchant). Includes an IRCTC-specific example and payment-mode-specific timelines. |
| H-15 | 15 and 20 | When will I receive a refund for a cancelled or failed order/booking or payment? | Says the merchant automatically refunds for a cancelled/failed order, booking, or merchant payment; asks the user to contact the merchant for refund status; refund goes to the original payment account. Screenshots 15 and 20 are duplicate captures of the same article. |
| H-16 | 16 | When will I receive a refund for a failed UPI payment? | Says a failed UPI payment is automatically refunded within 3–5 days from payment date; advises checking the bank statement after five days; notes possible immediate refund with delayed SMS and separate 7–9-day RuPay credit-card timing. |
| H-17 | 17 | What if I don't receive the refund after 5 days for a failed UPI payment? | Advises contacting the bank with the 12-digit UTR if no refund arrives after five days; notes that banks process refunds. |
| H-18 | 18 | When will I receive the refund for a failed card payment? | Describes a 7–9-day refund period from payment date for debit/credit card payments. |
| H-19 | 19 | What if my money is not refunded after 9 days for a failed card payment? | Advises contacting the card-issuing bank with the refund reference number after nine days. |

## 2. Important correction to the P2M analysis

The H-12 article materially changes how the P2M problem should be framed.

PhonePe Help explicitly states:

- PhonePe marks a payment successful only after it receives confirmation that the money has reached the merchant.
- Merchants do not inform PhonePe whether they have confirmed the order or delivered the service.
- If the merchant denies receiving the money, the user should report the issue for the relevant payment.

H-14 describes a different case: payment is successful but the order or booking is not confirmed. For that situation, PhonePe tells the payer to contact the merchant directly for an order/booking update.

Therefore, separate these two P2M situations in the report:

### P2M-A — Merchant disputes receipt of payment

PhonePe displays Successful, but the merchant says the amount was not received. PhonePe Help says to report the issue for that specific payment. Do not assume this is simply an unconfirmed order.

### P2M-B — Payment succeeded, but the order/service is not confirmed

PhonePe displays Successful, and the merchant has not confirmed the order, booking, or service. PhonePe Help directs the payer to contact the merchant for the order/service issue.

Do not merge P2M-A and P2M-B into one generic “merchant confirmation” problem. Payment receipt and order fulfilment are distinct.

## 3. What the screenshots support — and what they do not

### Supported by this evidence batch

1. PhonePe Help provides guidance for pending, failed, successful, merchant-payment, refund, and order/booking scenarios.
2. PhonePe Help describes a 48-hour pending-status update window and a report-issue route if the payment remains pending in History after 48 hours.
3. Relevant failed-UPI-payment articles describe a 3–5-day refund timeline from the payment date, and direct the user to check the bank statement and contact the bank with UTR if no refund appears after five days.
4. PhonePe Help explains where to find the 12-digit UTR in transaction details.
5. PhonePe Help distinguishes a merchant denying receipt of money from an order/booking not being confirmed.
6. PhonePe Help tells users who paid twice to contact the merchant and verify final payment status before retrying.

### Not established by this evidence batch

1. Whether the live P2P/P2M transaction screens surface these explanations at the right moment.
2. Whether users can discover the relevant Help articles or correctly understand them.
3. Whether users actually make duplicate payment attempts, or how frequently.
4. Whether any particular transaction was credited, reversed, or delayed.
5. Whether PhonePe’s published guidance matches the precise regulatory treatment of every incident.
6. Whether transaction-reference retrieval is difficult in the live app. The Help article itself describes an existing UTR retrieval path.

## 4. Required changes to earlier drafts

Review `P2M_Workflow.md`, `Workflow_Unknowns.md`, `Problem_Statements_v0.1.md`, `Hypothesis_Register.md`, `Validation_Metrics_Guardrails.md`, `Final_Recommendations_Summary.md`, and `Workflow_Diagrams.md`.

Make these corrections:

- Split “merchant did not receive payment” from “order/booking not confirmed.”
- Do not state that PhonePe’s Successful status is inherently ambiguous about merchant payment receipt; H-12 says PhonePe defines it as confirmation that money reached the merchant.
- Reframe the potential improvement around how the live transaction experience communicates this definition and routes the two different problem types. Verify the live screen before claiming a gap.
- Do not recommend adding UTR as a new field without checking the existing History → transaction → “Debited from” path described in H-06.
- Treat a more discoverable UTR copy/share control as a conditional opportunity only if usability testing finds friction.
- Keep the 3–5-day refund guidance specific to the failed-UPI scenarios in the relevant Help articles. Do not apply it to every successful-but-disputed merchant payment or every order/booking problem.
- Attribute chargeback instructions and time limits to PhonePe Help; do not present them as universal legal rules.
- Do not copy the “RBI Banking Ombudsman” label from H-11 as current guidance without checking the latest official RBI process.
- Treat the IRCTC example in H-14 as an example for that specific service, not a general rule for all merchant orders.

## 5. Recommended screenshot selection for an 8-page report

Do not insert all 20 screenshots into the PDF. Use a small, representative set and keep the full evidence set in the repository.

| Report page | Suggested screenshot | Reason |
|---|---|---|
| PhonePe Help experience | H-02 | Shows pending issue escalation after 48 hours. |
| Pending/refund guidance | H-01 or H-16 | Shows the distinction between status update and failed-payment refund guidance. |
| Transaction reference | H-06 | Shows the existing UTR retrieval path. |
| P2M payment issue | H-12 | Shows PhonePe’s definition of Successful and the payment-dispute route. |
| P2M order issue | H-14 | Shows the separate merchant-owned order/booking path. |
| Duplicate-payment prevention | H-13 | Shows guidance to verify final payment status before retrying. |

Include evidence ID, article title, source, and capture date below each selected image. Redact identifiers from any embedded transaction illustration if they could identify a real customer or transaction.

## 6. Evidence-register actions still required

- Map H-01 to H-19 to the existing E-IDs in `Evidence_Register.xlsx`.
- Mark screenshot 20 as a duplicate of screenshot 15; retain one canonical image.
- Record the article title, capture date (3 November 2026), source as PhonePe Help, and source URL if you can retrieve it.
- Record that the app version and article publication/update date are not visible in the supplied screenshots.
- Keep screenshots 3–5, 16–17 as separate articles even though some guidance overlaps; their wording and context differ.

## 7. Publication decision

**This screenshot batch is useful evidence of PhonePe Help content, but it does not complete the final evidence audit.** The remaining essential source is `Evidence_Register.xlsx`, plus inspection of the live transaction and complaint flows if you intend to make claims about those interfaces.
