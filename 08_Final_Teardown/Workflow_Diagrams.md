# PhonePe Product Teardown — Workflow Diagrams

**Purpose:** Report-ready conceptual diagrams for the two scoped UPI payment scenarios. These diagrams describe payer-facing investigation and recovery paths; they do not represent PhonePe's internal backend architecture.

## Legend and interpretation

- **Scenario / event:** A step stated in the scoped scenario.
- **Observed guidance:** A statement or route found in PhonePe Help content inspected for this teardown.
- **Proposed action:** A recommended payer action or product improvement, not a claim that the live app currently provides it in this exact form.
- A merchant's lack of confirmation does **not** establish that the merchant's bank account was not credited.
- Payment status, beneficiary/merchant credit, merchant payment confirmation, and order confirmation are separate concepts.

---

## 1. P2P workflow — payer debited, beneficiary not credited

**Scoped scenario:** The sender's bank account has been debited, but the beneficiary says the funds have not been credited or cannot yet confirm receipt.

```mermaid
flowchart TD
    A[Sender initiates a UPI transfer] --> B[Payer's bank account is debited]
    B --> C[PhonePe displays the transaction status]
    C --> D{What status is displayed?}

    D -->|Pending| E[Final transaction outcome is not yet clear]
    E --> F[Follow the relevant pending-status guidance]
    F --> G[Check PhonePe transaction history for an updated status]
    G --> H{Has a final status appeared?}
    H -->|No| F
    H -->|Yes| I{Final status}

    D -->|Successful| J[Verify whether the beneficiary's account was credited]
    I -->|Successful| J
    J --> K{Beneficiary confirms credit?}
    K -->|Yes| L[Payment issue resolved]
    K -->|No| M[Keep transaction details and applicable UTR/reference]

    D -->|Failed| N[Check the payer's bank account for reversal]
    I -->|Failed| N
    N --> O{Has the reversal appeared?}
    O -->|Yes| L
    O -->|No| M

    M --> P[Use the relevant PhonePe Help / bank follow-up route]
    P --> Q[Share the applicable transaction reference and supporting details]
```

### P2P notes for the report

1. The diagram separates **PhonePe transaction status** from **beneficiary account credit**.
2. The inspected PhonePe Help content describes a pending-status update period of up to 48 hours and refund guidance of 3–5 days for relevant failed-payment scenarios. These refer to different stages and should not be presented as one universal timeline.
3. The applicable RBI turnaround requirement depends on the exact transaction scenario and regulatory classification. Do not place a blanket T+1 claim on every pending or failed P2P transaction. Cite the applicable RBI rule separately and explain its precise scope.
4. The diagram's follow-up route is a conceptual payer journey. Confirm the exact current in-app complaint path and tracking experience before describing them as live PhonePe functionality.

---

## 2. P2M workflow — PhonePe shows successful, merchant reports no confirmation

**Scoped scenario:** The payer's account is debited and PhonePe displays **Successful**, but the merchant says payment confirmation has not arrived.

```mermaid
flowchart TD
    A[Customer initiates a merchant UPI payment] --> B[Payer's bank account is debited]
    B --> C[PhonePe displays Successful]
    C --> D[Merchant reports that payment confirmation has not arrived]

    D --> E[Do not assume the merchant bank was or was not credited]
    E --> F[Payer verifies the original transaction details]
    F --> G[Check amount, date/time, status and applicable transaction reference / UTR]
    G --> H[Check the relevant payer bank-account record where appropriate]
    H --> I[Share transaction proof/reference with the merchant]
    I --> J{Has the merchant reconciled / recognised the payment?}
    J -->|Yes| K[Confirm the order or service separately]
    J -->|No / still uncertain| L[Use the appropriate PhonePe Help / support route]
    L --> M[Provide transaction details and follow the resolution guidance]

    C -. separate question .-> N[Order confirmation: has the merchant confirmed the order?]
    N -. not equivalent to payment status .-> O[Check with the merchant's ordering system]
```

### P2M notes for the report

1. **Successful** is the status displayed by PhonePe in the scoped scenario. It does not, by itself, prove that the merchant's ordering system has confirmed the order.
2. A merchant's report of missing confirmation does not prove that the merchant's bank account was not credited. Avoid asserting the underlying bank or network cause without operational evidence.
3. The payer should verify the original transaction before deciding whether another payment is necessary. The proposed experience should discourage an unverified repeat payment; do not claim that duplicate payments are common without transaction data.
4. The inspected PhonePe Help material recognises merchant-payment issues, including successful payments where the merchant reports not receiving confirmation. It also indicates that the merchant may be better placed to resolve certain order or booking issues. Preserve the distinction between payment resolution and order fulfilment.
5. The transaction-reference step is a proposed emphasis in the visual. Inspect the current P2M transaction screen before claiming that the transaction ID or UTR is missing or difficult to access.

---

## 3. Proposed product experience overlay

The following is a **recommendation**, not a verified current PhonePe screen:

1. **Explain status:** State what the displayed UPI status means and what it does not confirm.
2. **Separate confirmation types:** Distinguish payment status, merchant payment confirmation, and order confirmation.
3. **Provide the right next step:** Offer a contextual merchant-issue route when the payer reports missing confirmation.
4. **Expose transaction proof:** Make the applicable transaction reference easy to locate and copy/share, where available.
5. **Prevent premature retry:** Encourage verification of the original transaction before another payment is attempted.

## 4. Evidence and publication checklist

Before publishing these diagrams:

- Attach the relevant evidence IDs to each PhonePe Help statement in the report (for example, the pending, refund, UTR, and merchant-issue evidence already catalogued in the evidence register).
- Add the exact inspection date and source URL or article title for each Help page, where captured.
- Label conceptual paths and proposed actions so they cannot be mistaken for verified live app screens.
- Verify current P2P and P2M transaction-detail screens, including transaction-reference visibility and the actual complaint submission/tracking route.
- Keep RBI turnaround and compensation statements in a separate, precisely scoped regulatory note with an official citation.
- Do not infer technical root cause, merchant-bank credit, actual repeat-payment behaviour, or duplicate-payment incidence from these workflows alone.
