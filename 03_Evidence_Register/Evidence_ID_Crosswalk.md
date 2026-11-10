# Evidence ID Crosswalk — PhonePe Product Teardown

**Status:** Reconciliation record, 10 November 2026  
**Canonical source of truth:** `03_Evidence_Register/Evidence_Register.xlsx`  
**Purpose:** Map evidence identifiers used in earlier working drafts to the canonical IDs now assigned in the Evidence Register.

## 1. Important rule

Use the canonical IDs in the right-hand column in all future documentation. Do not reuse old draft IDs for a different item. In particular:

- `E-005` and `E-009` in the workbook are **grouping/index records**, not individual Help articles. Cite article-level records instead.
- `E-015` in the canonical workbook is the **UTR lookup article**. It is not the merchant-payment dispute article.
- `E-021` is the canonical record for **“What if the merchant denies having received the amount for a successful payment?”**
- `E-029`, `E-030`, and `E-031` are the canonical RBI, NPCI, and PhonePe policy records, respectively.
- `RBI-002` appeared in an older unknowns draft but has no separate record in the current workbook. Do not cite it until the exact official source is added to the register.

## 2. Legacy-to-canonical mapping

| Earlier draft reference | Canonical Evidence ID(s) | Canonical item | Notes |
|---|---|---|---|
| E-001 | E-001 | Incoming successful P2P transaction details | Same ID; original filename still needs mapping. |
| E-002 | E-002 | Outgoing successful P2P transaction details | Same ID; original filename still needs mapping. |
| E-003 | E-003 | Historical internet-found pending screenshot | Same ID; secondary source, provenance incomplete. |
| E-004 | E-004 | Historical internet-found failed screenshot | Same ID; secondary source, provenance incomplete. |
| E-005 / E-005A (pending guidance) | E-007; E-008 | Pending guidance and 48-hour explanation | Use exact article-level record. |
| E-005B (failed debit/refund/UTR guidance) | E-013; E-014; E-025; E-026 | Failed-payment refund and escalation articles | Choose only the article matching the claim. |
| E-005C (failure reasons) | E-012 | Why did my UPI payment fail? | Lists possible reasons; not a diagnosis. |
| E-005D (merchant issues) | E-021; E-022; E-023; E-024 | Merchant receipt dispute, duplicate payment, order issue, merchant refund | Keep these scenarios distinct. |
| E-006 / E-006A–E | E-006 | Payment Issues Help categories | One canonical category-navigation record. |
| E-007 | E-007 | What do I do if my UPI payment is pending? | Same ID. |
| E-008 | E-008 | Why do I have to wait for 48 hours to know the final payment status? | Same ID. |
| E-009 (cancellation article in older drafts) | E-010 | Can I cancel my pending payment? | The canonical workbook's E-009 is a screenshot-batch grouping record. |
| E-010 (pending over 48 hours in older drafts) | E-011 | What if my payment is pending for more than 48 hours? | Shifted to canonical E-011. |
| E-011 (failure reasons in older drafts) | E-012 | Why did my UPI payment fail? | Shifted to canonical E-012. |
| E-012 (failed debit/refund bundle in older drafts) | E-013; E-014; E-025; E-026 | Failed-payment refund and bank-follow-up articles | Split into article-level records. |
| E-013 (UTR/beneficiary guidance in older drafts) | E-015; E-016; E-017 | UTR lookup and beneficiary-credit articles | Split into article-level records. |
| E-014 (bank chargeback/escalation bundle in older drafts) | E-018; E-019; E-020 | Chargeback instructions, sample template, bank-denies-help article | E-020 contains potentially stale “RBI Banking Ombudsman” wording. |
| E-015 (merchant issue in older P2M draft) | E-021 | Merchant denies receipt after successful payment | Canonical E-021. |
| E-016 (duplicate payment in older P2M draft) | E-022 | Paid twice for an order or booking | Canonical E-022. |
| E-017 (order/booking in older P2M draft) | E-023; E-024 | Order not confirmed; merchant refund for cancelled/failed order | Split into two articles. |
| E-018 (historical internet-found screens in older P2M draft) | E-003; E-004 | Historical pending/failed screenshots | Canonical secondary evidence IDs. |
| E-019 (PhonePe grievance policy in older P2M/unknowns drafts) | E-031 | PhonePe Grievance Policy, Version 10 | Revalidate exact policy clauses before publication. |
| RBI-001 | E-029 | RBI/2019-20/67 failed-transaction TAT circular | Canonical register ID. |
| NPCI-001 | E-030 | NPCI UPI HELP Brand Guidelines | Canonical register ID. |
| RBI-002 | Not currently registered | RBI Integrated Ombudsman Scheme 2026 source | Add a separate record only if this source is used; capture exact title, URL, access date and applicable scope. |

## 3. Canonical article-level Help index

| Canonical ID | Help article / item | Main use |
|---|---|---|
| E-006 | Payment Issues categories | Help information architecture |
| E-007 | What do I do if my UPI payment is pending? | Pending status and outcomes |
| E-008 | Why do I have to wait for 48 hours to know the final payment status? | PhonePe's explanation of the 48-hour window |
| E-010 | Can I cancel my pending payment? | Cancellation guidance |
| E-011 | What if my payment is pending for more than 48 hours? | Report-issue route after 48 hours |
| E-012 | Why did my UPI payment fail? | Possible failure reasons and retry wording |
| E-013 | Why is my money deducted for my failed payment? | 3–5-day failed-payment refund and UTR escalation wording |
| E-014 | Why is my money not refunded yet? | Failed-UPI refund follow-up |
| E-015 | Where can I find the UTR number? | UTR retrieval path in History / Debited from |
| E-016 | How does the receiver know into which account the money is deposited? | Beneficiary account verification |
| E-017 | What if the money is not deposited into the receiver's account instantly? | Beneficiary-credit dispute and bank contact |
| E-018 | How to raise a chargeback with a bank? | Bank chargeback instructions |
| E-019 | Sample Template to Raise a Chargeback with Your Bank | Sample bank communication template |
| E-020 | What if the bank denies help? | Escalation article; terminology requires current verification |
| E-021 | What if the merchant denies having received the amount for a successful payment? | P2M payment-receipt dispute and Report Issue route |
| E-022 | What if I have paid twice for an order or booking? | Duplicate-payment guidance and check final status before retrying |
| E-023 | What if the order or booking is not confirmed for a successful payment? | Order/booking issue; contact merchant |
| E-024 | When will I receive a refund for a cancelled or failed order/booking or payment? | Merchant-initiated order/booking refund guidance |
| E-025 | When will I receive a refund for a failed UPI payment? | Failed-UPI refund timing |
| E-026 | What if I don't receive the refund after 5 days for a failed UPI payment? | Failed-UPI refund bank escalation with UTR |
| E-027 | When will I receive the refund for a failed card payment? | Card refund; outside primary UPI scope |
| E-028 | What if my money is not refunded after 9 days for a failed card payment? | Card refund escalation; outside primary UPI scope |

## 4. Material P2M interpretation correction

The canonical evidence record `E-021` states that PhonePe marks a payment successful only after it receives confirmation that the money has reached the merchant. The same Help article separately states that merchants do not inform PhonePe whether they have confirmed an order or provided the service. It directs a payer to report the relevant payment if the merchant denies receiving the amount.

The separate article `E-023` says that if a successful payment's order or booking is not confirmed, the customer should contact the merchant for an update.

Therefore, the final teardown must distinguish:

1. **Merchant disputes receipt of payment:** PhonePe Help's stated successful-status criterion and its Report Issue route (`E-021`).
2. **Order/booking not confirmed:** The payment may be successful while order confirmation/fulfilment remains unresolved; PhonePe Help directs the customer to the merchant (`E-023`).
3. **RBI-defined P2M failed transaction:** Payer debited but transaction confirmation is not received at the merchant location. Apply the RBI T+5 rule only when the incident facts match the circular (`E-029`). Do not automatically equate this with an order not being confirmed or with every merchant dispute.

## 5. Remaining provenance gaps

The workbook deliberately records missing metadata rather than inventing it. The exact original image filename for each Help panel, Help article URL, article publication/update date, and PhonePe app version are not visible in the supplied screenshot batch. Capture date is inferred from filenames and the research record as 3 November 2026. These gaps remain open until verified.
