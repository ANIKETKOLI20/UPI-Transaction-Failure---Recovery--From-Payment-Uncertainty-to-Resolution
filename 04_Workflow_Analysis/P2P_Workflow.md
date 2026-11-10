# P2P Workflow — UPI Fund Transfer Recovery

> **Document status:** Working draft v0.3 — evidence-ID reconciled, not a verified end-to-end production workflow.  
> **Workflow ID:** WF-P2P-01  
> **Product:** PhonePe consumer UPI app  
> **User perspective:** Payer (sender)  
> **Scenario under investigation:** Sender's account is debited, but the beneficiary is not credited.  
> **Evidence review date:** 4 November 2026  
> **PhonePe Help screens inspected:** 3 November 2026 (based on the supplied screenshots and conversation record).

---

## 1. Purpose

Map the payer's journey when a PhonePe UPI person-to-person (P2P) transfer has an uncertain or unsuccessful outcome. The workflow separates:

- the status displayed by PhonePe;
- whether the payer's bank account was debited;
- whether the beneficiary's bank account was credited; and
- the subsequent reversal, support and grievance process.

The workflow is a reconstruction from the PhonePe Help screens and transaction-screen observations supplied for this teardown. It is not proof that every branch or screen has been tested in the current live app.

## 2. Scope and boundary

### Included

- Domestic UPI P2P fund transfers initiated by a payer using PhonePe.
- Pending, failed and successful transaction statuses where relevant to the recovery journey.
- The specific failed-transaction incident in which the payer is debited but the beneficiary is not credited.
- PhonePe's published guidance about waiting, checking transaction status, refunds, UTR and support.
- The applicable RBI reversal framework for the matching P2P incident.

### Not automatically included

- Every transaction displaying `Pending`. A pending status alone does not prove that the payer was debited or the beneficiary was not credited.
- Wrong-credential, insufficient-balance, limit, security or other declines unless they produce the specific debit-without-beneficiary-credit incident being studied.
- P2M merchant payments, merchant order fulfilment, card payments or wallet payments.
- Actual bank/network root causes, actual reversal performance, or customer behaviour unless supported by appropriate telemetry, transaction records or user research.

## 3. Evidence base — canonical Evidence Register IDs

The canonical IDs below match `03_Evidence_Register/Evidence_Register.xlsx`. Earlier draft IDs have been reconciled in `03_Evidence_Register/Evidence_ID_Crosswalk.md`.

| Evidence ID | Source / item | What it supports | Evidence class / limitation |
|---|---|---|---|
| E-001 | Incoming successful P2P transaction details screen | Context on an observed successful incoming-payment screen | Researcher-reported observation; original filename and capture date not mapped. Not a failed/pending-flow screen. |
| E-002 | Outgoing successful P2P transaction details screen | Context on an observed successful outgoing-payment screen | Researcher-reported observation; original filename and capture date not mapped. Not a failed/pending-flow screen. |
| E-003 | Historical internet-found pending transaction screenshot | Historical visual example only | Secondary evidence; original source/publication date unknown. Do not present as current PhonePe UI. |
| E-004 | Historical internet-found failed transaction screenshot | Historical visual example only | Secondary evidence; original source/publication date unknown. Do not present as current PhonePe UI. |
| E-006 | PhonePe Help — Payment Issues categories | Help categorisation | Directly observed Help navigation screenshot; user discoverability not tested. |
| E-007 | What do I do if my UPI payment is pending? | Up-to-48-hour status guidance, outcome descriptions and History/notification instructions | PhonePe Help content; product guidance, not a measurement of actual bank processing. |
| E-008 | Why do I have to wait for 48 hours to know the final payment status? | PhonePe's explanation of the stated status-update window | Attribute explanation to PhonePe; not independent bank/network telemetry. |
| E-010 | Can I cancel my pending payment? | PhonePe Help says an initiated UPI payment cannot be cancelled and asks users to wait for status | Help content; no live cancellation action tested. |
| E-011 | What if my payment is pending for more than 48 hours? | Report-issue route after 48 hours and PhonePe's stated escalation action | Help content; exact submission, acknowledgement and tracking remain unverified. |
| E-012 | Why did my UPI payment fail? | Possible failure reasons and check-History-before-retry wording | Possible reasons only; not a transaction-level diagnosis. |
| E-013; E-014; E-025; E-026 | Failed-UPI debit/refund and refund escalation articles | 3–5-day guidance for relevant failed-UPI cases, bank-statement check and UTR follow-up | Attribute to PhonePe Help and keep scenario scope explicit. |
| E-015 | Where can I find the UTR number? | History → payment → “Debited from” UTR retrieval path | Shows an existing Help-documented retrieval path; ease of use not tested. |
| E-016; E-017 | Beneficiary account and delayed-credit guidance | How the receiver may check the relevant account and contact the bank using UTR | PhonePe Help guidance; do not infer actual credit from an SMS or merchant report alone. |
| E-018; E-019; E-020 | Bank chargeback, sample template and bank-denies-help articles | PhonePe Help's bank follow-up content | E-020 uses potentially stale “RBI Banking Ombudsman” wording; do not repeat as current regulatory advice without verification. |
| E-029 | RBI failed-transaction TAT circular | Defined P2P beneficiary-not-credited T+1 reversal category and compensation | Apply only when the exact P2P incident condition matches the circular. |

**Capture-date note:** The supplied Help screenshot filenames indicate 3 November 2026. The individual article URLs, publication/update dates and app version are not visible in the supplied images. Do not invent these metadata fields.

## 4. Reconstructed P2P workflow

```text
1. Payer initiates a UPI P2P transfer
                  |
                  v
2. PhonePe displays a transaction status
   (Pending / Successful / Failed)
                  |
                  v
3. Establish the account-level outcome
   - Was the payer debited?
   - Was the beneficiary credited?
                  |
          +-------+--------+
          |                |
          v                v
   A. Outcome known   B. Outcome uncertain / pending
          |                |
          |                v
          |          PhonePe Help says to wait up to
          |          48 hours for the bank's final status
          |                |
          |                v
          |          Check History / await notification
          |                |
          |          If still pending after 48 hours:
          |          PhonePe Help says report the issue
          |          so PhonePe can escalate it
          |                |
          +-------+--------+
                  |
                  v
4. Final outcome / account credit is checked
   - Successful and beneficiary credited; or
   - Failed / sender debited but beneficiary not credited; or
   - Still unresolved (requires investigation)
                  |
        +---------+----------+
        |                    |
        v                    v
5A. Credit confirmed    5B. Failed with debit
        |                    |
        v                    v
   Close payment          Check bank statement and
   recovery branch        follow the applicable reversal
                          requirement and PhonePe guidance
                               |
                               v
                          If refund is not received:
                          use the UTR and contact the
                          relevant bank / support channel
                               |
                               v
                          Further grievance escalation
                          through the applicable route
```

**Important:** This diagram is an analytical reconstruction. The exact current in-app pending/failed screens and complete complaint-submission journey remain unverified.

## 5. Step-by-step workflow analysis

| Stage | What is currently documented | Payer's information / need | Evidence and limitation |
|---|---|---|---|
| 1. Initiation | Payer initiates a P2P transfer in PhonePe | Confirm recipient and amount before authorising | E-001/E-002 are successful-transaction observations, not failure-flow evidence |
| 2. Status display | PhonePe Help discusses `Pending`, `Successful` and `Failed`; an internet-found screen shows a pending example | Understand the transaction state | E-003 is secondary; a current failed/pending transaction screen has not been directly inspected |
| 3. Pending guidance | PhonePe Help says banks may take 2 minutes to 48 hours to confirm final status; it advises waiting up to 48 hours | Know whether to wait and how to check status | E-007/E-008; PhonePe's statement is product guidance, not a measurement of actual bank processing time |
| 4. Cancellation | PhonePe Help says an initiated UPI payment cannot be cancelled and advises waiting 48 hours | Understand whether the payment can be stopped | E-010; no live cancellation action was tested |
| 5. Status still pending after 48 hours | PhonePe Help says to report the issue from the app; PhonePe says it will escalate with banking authorities | Know how to request assistance | E-011; exact complaint submission, acknowledgement and tracking steps remain unverified |
| 6. Failure reason | PhonePe lists UPI network, bank technical, wrong PIN, insufficient balance, bank/UPI limits, security and other bank-account reasons; it advises checking History before trying again | Understand the stated reason before any retry | E-012; these are possible reasons, not diagnoses of a particular transaction |
| 7. Failed payment with debit | PhonePe Help says refund within 3–5 days from the payment date and recommends checking the bank statement after five days | Confirm whether funds were returned | E-013; E-014; E-025; the wording says “days” and does not specify calendar or business days in the screenshot |
| 8. Refund not received | PhonePe Help says to contact the bank with the UTR if the refund is not received after five days | Find the reference and approach the right party | E-013; E-014; E-015; E-026; actual bank outcome is unknown |
| 9. Further escalation | PhonePe has published a grievance policy with customer-support, grievance-desk and nodal-officer stages | Know the appropriate escalation route | See Section 7; do not assume that RBI Ombudsman eligibility for PhonePe PPIs applies to UPI services |

## 6. Recovery branches and key distinctions

### Branch A — Beneficiary credit is confirmed

- Treat the transfer as successful only when the relevant payment/credit outcome is confirmed.
- Do not classify a transfer as failed solely because an earlier screen displayed `Pending`.
- PhonePe Help says a recipient using a PhonePe-registered mobile number or UPI ID can check transaction details in History; a recipient using a non-PhonePe UPI ID should check the bank account linked to that UPI ID (E-016).
- A delayed bank SMS is not, by itself, proof that the credit did not occur; PhonePe advises checking the bank statement (E-014/E-016).

### Branch B — Payer is debited, beneficiary is not credited

- Confirm that the facts match the specific P2P failed-transaction scenario.
- Keep the app status separate from the account-level debit/credit outcome.
- Check the transaction reference and account statement.
- Follow the applicable reversal requirement and the verified support guidance.
- If the expected reversal does not occur, contact the relevant bank/payment support channel with the transaction reference (UTR, where applicable).

### Branch C — Status remains pending / outcome is unknown

- Do not assume that the beneficiary has not been credited merely because the app says `Pending`.
- PhonePe Help says initiated UPI payments cannot be cancelled and advises waiting up to 48 hours for final status (E-007; E-008; E-010).
- Do not recommend a repeat payment while the first payment's outcome is unknown. PhonePe's separate duplicate-payment guidance advises checking the final payment status before attempting payment again (E-022).
- If the status remains pending after 48 hours, PhonePe Help says to report the issue for escalation (E-011).

### Branch D — Failed without debit / decline

- This is not automatically the RBI P2P debit-without-beneficiary-credit reversal scenario.
- Check the reason shown in History and follow the relevant guidance.
- PhonePe lists several possible decline reasons (E-012); do not infer a technical root cause without diagnostic evidence.

## 7. Regulatory and grievance overlay — verify before publication

### 7.1 RBI turnaround time for the specific P2P incident

For the specific incident where the payer's account is debited but the beneficiary account is not credited in a UPI funds transfer, RBI's 20 September 2019 framework specifies auto-reversal by the beneficiary bank no later than T+1 if it is unable to credit the beneficiary. Compensation of ₹100 per day is payable for applicable delay beyond T+1.

- **T** is the transaction date for applying the framework.
- The rule applies to the defined debit-without-beneficiary-credit incident, not to every transaction labelled `Pending` or every UPI decline.
- Do not use PhonePe's generic 3–5-day Help estimate as a replacement for the applicable regulatory TAT.
- Do not conclude that PhonePe has violated RBI requirements from a generic Help article alone. First confirm the transaction scenario, the clock's start point, the relevant participant's responsibility and the exact current guidance.

**Official source:** RBI, *Harmonisation of Turn Around Time (TAT) and customer compensation for failed transactions using authorised Payment Systems*, RBI/2019-20/67, 20 September 2019:  
https://rbi.org.in/commonman/Upload/English/Notification/PDFs/CIRCULAR677EC931A7A65E4D99AA957D8E85BC0A2A.PDF

### 7.2 PhonePe guidance observed

The PhonePe Help screenshots supplied for this teardown state:

- banks may take 2 minutes to 48 hours to update a pending payment's final status;
- if a pending payment is marked failed, the amount is stated to be refunded within 3–5 days from the original payment date;
- the user is advised to check the bank statement after five days and contact the bank with the UTR if the refund is not received.

These are PhonePe's customer-facing statements observed in the Help screens. They do not establish actual transaction-resolution performance. The screenshots do not clearly state whether the generic 3–5-day guidance applies to every P2P failure scenario or whether “days” means calendar or business days.

### 7.3 PhonePe grievance policy and RBI Ombudsman caution

PhonePe's Grievance Policy, Version 10, dated 16 July 2026, describes customer support through History → relevant transaction → Contact PhonePe Support, and through the Help (?) section. For customer complaints, the policy publishes these service levels:

- Level 1: customer support is available 24 hours a day, 7 days a week; PhonePe commits to a first response within 24 hours and aims to resolve complaints within 15 days.
- Level 2: grievance-desk escalation; PhonePe commits to a first response within 24 hours and aims to resolve complaints within 7 business days.
- Level 3: nodal-officer escalation; PhonePe commits to a first response within 24 working hours and aims to resolve complaints within 7 business days.

These are PhonePe complaint-service targets, not substitutes for a shorter transaction-specific RBI reversal deadline. The policy's Reserve Bank–Integrated Ombudsman Scheme, 2026 section states that the scheme applies to PhonePe for its specified prepaid payment instrument services (such as PhonePe Wallet, Gift Cards and PhonePe RuPay On-The-Go Card). **Do not assume that the PPI Ombudsman route described in the policy is automatically the direct Ombudsman route for a PhonePe UPI complaint.** For a UPI case, identify the responsible regulated entity/bank and the applicable bank/NPCI grievance path before describing formal escalation.

**Official source:** PhonePe Grievance Policy, Version 10, 16 July 2026:  
https://www.phonepe.com/grievance-policy/

**Current RBI scheme reference:** RBI FAQ for the Reserve Bank–Integrated Ombudsman Scheme, 2026, effective 1 July 2026:  
https://old.rbi.org.in/commonman/english/scripts/faqs.aspx?id=3407

### 7.4 NPCI UPI HELP guidance

NPCI's July 2023 UPI HELP guidelines describe a framework for UPI transaction-related complaints through the UPI payment app, covering P2P and P2M transactions and enabling users to check pending/failed transaction status. This document is an ecosystem guideline; it does not prove that every described feature is currently implemented in the PhonePe version inspected for this teardown.

**Official source:** NPCI, *UPI HELP Guidelines*, July 2023:  
https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf

## 8. Product-analysis questions

1. Does the current PhonePe transaction screen explain what `Pending` means and what the payer should do next?
2. Is the 48-hour status-update guidance clearly distinguished from the applicable reversal deadline?
3. Does the app communicate that an initiated pending payment cannot be cancelled?
4. Is the instruction to verify final status before retrying sufficiently visible at the point where a user might repeat a payment?
5. Does PhonePe distinguish a pending status from a confirmed failed transaction and from a failed transaction with an actual debit?
6. Can the payer find the UTR/reference and the correct support route without difficulty?
7. Does the complaint process provide a clear acknowledgement, reference and status-tracking route?
8. Does customer-facing guidance explain the applicable P2P reversal deadline and compensation accurately for the specific incident?

## 9. Open questions and limitations

- The current PhonePe P2P pending/failed transaction-detail screens have not been directly inspected. Internet-found transaction screenshots are secondary evidence.
- The app version used for the Help screenshots is not recorded.
- The exact in-app complaint submission, reference-generation and tracking flow has not been completed or verified.
- Actual payer debit, beneficiary credit and bank reversal outcomes are not available from the Help screenshots.
- Actual transaction-resolution time and real-world bank performance are unknown.
- Actual user repeat-payment behaviour is unknown; it requires product event data, support records or appropriately designed user research.
- The generic PhonePe 3–5-day guidance must not be assumed to apply identically to the specific RBI P2P debit-without-credit incident without confirmation.
- Do not claim customer confusion, duplicate-payment incidence, technical root cause, regulatory non-compliance or causal impact without suitable evidence.

## 10. Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-04 | Initial reconstructed P2P workflow draft. |
| 0.2 | 2026-11-04 | Incorporated PhonePe Help screenshot evidence; clarified the pending, failed, debit and credit branches; added the RBI P2P TAT and PhonePe grievance-policy distinction; corrected evidence limitations and escalation caveats. |
| 0.3 | 2026-11-10 | Reconciled evidence IDs to the canonical Evidence Register and replaced bundled references with article-level IDs. |

---

**Document rule:** Keep this as a working analysis document. Update the workflow only when new evidence is recorded in the evidence register. Do not silently convert unknowns or interpretations into verified product behaviour.
