# PhonePe Product Teardown — Final Publication Audit

**Purpose:** Final pre-publication quality checklist for the PhonePe UPI Transaction Failure & Recovery teardown.

**Audit status:** Preliminary document audit. The final PDF, complete evidence register, and complete repository have not yet been supplied for end-to-end inspection. Do not mark this checklist fully complete until those items are reviewed.

## 1. Current audit scope

Files inspected in this review:

- `Final_Recommendations_Summary.md`
- `Workflow_Diagrams.md`

Other project documents and screenshots have been discussed, but their current local versions and the complete evidence register have not been audited in this pass.

## 2. Preliminary document assessment

| Area | Status | Required action |
|---|---|---|
| Research scope and payer perspective | PASS | Keep the domestic UPI P2P/P2M scope consistent. |
| Separation of P2P and P2M | PASS | Preserve separate incident definitions and recovery paths. |
| Distinction among transaction status, beneficiary/merchant credit, merchant confirmation, and order confirmation | PASS | Keep these concepts separate in every diagram and report section. |
| Recommendations labelled as proposals | PASS | Continue stating that expected benefits are unvalidated. |
| Workflow diagrams labelled conceptual | PASS | Do not describe them as PhonePe backend architecture or fully verified live app flows. |
| PhonePe Help article source metadata | VERIFY | Add exact article title, URL where available, capture date, and evidence ID for each Help screenshot. Do not invent missing URLs. |
| Official source citations in the final recommendations summary | FIX | Add inline references and a references section. Evidence IDs alone are not full public citations. |
| Current grievance route and policy scope | FIX | Use the current PhonePe Grievance Policy details below. Do not describe RBI Ombudsman access as universal for PhonePe UPI complaints. |
| Full evidence register and screenshot quality | NOT AUDITED | Inspect the actual workbook and selected original images before publication. |
| Final PDF layout and export | NOT AUDITED | Review the exported PDF page by page; no final PDF was available for this audit. |

## 3. Regulatory and policy details to cite accurately

### 3.1 RBI failed-transaction TAT — UPI

RBI circular `RBI/2019-20/67`, dated 20 September 2019, sets out two distinct UPI incident rows:

- **P2P funds transfer:** payer/originator account debited but beneficiary account not credited. If the beneficiary account cannot be credited, the beneficiary bank must auto-reverse by latest T+1. Compensation is ₹100 per day for delay beyond T+1.
- **P2M merchant payment:** payer account debited but transaction confirmation is not received at the merchant location. Auto-reversal is within T+5. Compensation is ₹100 per day for delay beyond T+5.

The circular defines T as the transaction day and explicitly says it refers to the calendar date. These requirements apply to the specified incident categories; they must not be generalised to every pending, failed, order, or refund scenario.

Official source: https://rbi.org.in/commonman/English/scripts/Notification.aspx?Id=3074

### 3.2 PhonePe Grievance Policy — current version reviewed

The official PhonePe Grievance Policy page shows **Version 10, dated 16 July 2026**. It states that PhonePe operates as a UPI TPAP in partnership with banks and NPCI.

For customer complaints on the PhonePe app, the policy says:

- Level 1 support is available 24 hours a day, seven days a week.
- A customer can select the relevant transaction in History and choose “Contact PhonePe Support”, or use the in-app help route.
- PhonePe commits to a first response within 24 hours and aims to resolve customer complaints within 15 days, subject to stated exceptions and dependencies.
- If unresolved after the Level 1 timeline or the customer is dissatisfied, Level 2 grievance registration is available. The policy commits to a first response within 24 hours and aims to resolve Level 2 complaints within 7 business days, subject to stated exceptions.
- The policy's Level 4 RBI Ombudsman route is explicitly identified as applicable to **PhonePe PPIs only** (Wallet, Gift Cards, and PhonePe RuPay On-The-Go Card/NCMC). Do not present this as a universal Level 4 route for PhonePe UPI complaints.

The same policy's general note says that, in some cases, refund initiation may be instant but the amount may take **3–10 days** to reflect, depending on the payment instrument. This is general policy wording and must not be silently merged with the separate 3–5-day UPI Help guidance captured in the user's screenshots. Keep each statement attached to its source and scenario.

Official source: https://www.phonepe.com/grievance-policy/

### 3.3 RBI Integrated Ombudsman Scheme, 2026

RBI's official information says the Reserve Bank–Integrated Ombudsman Scheme, 2026 came into force on **1 July 2026** and replaced the 2021 scheme for new complaints from that date, subject to transition provisions. If the final report mentions the current scheme, cite the 2026 RBI source and carefully identify the regulated entity/product involved.

Official source: https://www.rbi.org.in/CommonPerson/english/Scripts/PressReleases.aspx?Id=3407

Do not copy the 2019 circular's historical reference to the 2021 Ombudsman Scheme as though it were the current scheme.

## 4. PhonePe Help evidence — required source metadata

For each Help screenshot used in the PDF, record:

1. Canonical Evidence ID (for example, E-021 or E-029); use `Evidence_ID_Crosswalk.md` for older draft references.
2. Exact article/page title as displayed.
3. Exact URL, if captured or retrievable. Do not fabricate a URL.
4. Date inspected/captured.
5. The exact statement being cited, paraphrased accurately.
6. Whether the item is PhonePe Help content, an in-app screen, or a secondary historical screenshot.

The reviewed Help material includes guidance describing up to 48 hours for a pending-status update and a 3–5-day refund timeline for relevant failed-UPI scenarios. It also distinguishes a merchant receipt dispute after PhonePe Successful (E-021) from an unconfirmed order/booking (E-023). Keep these as separate events and do not extend the 3–5-day failed-UPI refund guidance to every P2M dispute. Attribute PhonePe's Successful definition to its Help article. If the exact article URL or day-count convention was not captured, disclose that limitation or recover the source before publication.

Historical internet-found pending/failed screenshots must be labelled secondary/historical. They are not proof of the current PhonePe interface.

## 5. Claim and language checks

Before publication, search the report for these terms and verify each use:

- **“Successful”** — attribute it to the status displayed by PhonePe; do not imply it proves order confirmation.
- **“Merchant not credited”** — do not infer bank-account credit status from a merchant's statement that confirmation is missing.
- **“UTR”** — do not use as a synonym for every PhonePe transaction ID or reference. Say “applicable transaction reference/UTR” where the exact identifier depends on the transaction.
- **“3–5 days”** — attach it only to the relevant Help guidance and failed-payment scenario. Do not apply it to all pending or P2M confirmation cases.
- **“48 hours”** — describe it as the Help content's pending-status update guidance, not as the RBI reversal deadline.
- **“T+1/T+5”** — use only for the RBI-defined UPI incident categories above; T is a calendar date.
- **“Duplicate payment”** — distinguish intention, repeat attempt, and two successful payments for the same intended purchase. Do not claim frequency without actual data.
- **“Users are confused”** — label as a hypothesis unless user research confirms it.
- **“PhonePe lacks”** — make this claim only after inspecting the current live flow and recording the app version, date, and steps.
- **“RBI Ombudsman”** — do not state that PhonePe's Level 4 route applies to UPI; the current PhonePe policy identifies Level 4 for PPIs only.

## 6. Eight-page PDF publication checklist

Recommended report length: 8 pages.

| Page | Section | Publication checks |
|---:|---|---|
| 1 | Executive summary | Clear central message, scope, strongest evidence-backed insight, and proposed recommendations. No unverified claims. |
| 2 | Scope and methodology | Research question, payer perspective, P2P/P2M definitions, sources, inspection dates, and limitations. |
| 3 | Payment workflows | P2P/P2M diagrams, scenario labels, separate payment status and credit/confirmation events. |
| 4 | PhonePe experience audit | Selected Help/app screenshots with E-IDs, article titles, dates, and concise captions. |
| 5 | Findings and problem framing | Evidence-backed observations separated from interpretations and hypotheses. |
| 6 | Hypotheses and validation | Research method, proposed metrics, denominator definitions, guardrails, and limitations. |
| 7 | Product recommendations | Priorities, rationale, expected benefits, dependencies, and measurement plan. |
| 8 | Conclusion and references | Limitations, unresolved questions, official sources, Help source list, and evidence register reference. |

### Layout and readability

- Use one consistent page size (A4 portrait is suitable for a report) and consistent margins.
- Use one heading hierarchy and no more than two font families.
- Keep body text readable at normal zoom; avoid shrinking text to force content onto a page.
- Use consistent spacing, alignment, table styles, and caption formatting.
- Add page numbers and a short footer with the project title and version/date.
- Prefer diagrams and annotated screenshots over dense paragraphs, but avoid decorative visuals that do not add evidence.
- Keep every figure legible at 100% PDF zoom. Avoid blurry screenshots and excessive browser/desktop chrome.
- Use a consistent legend for evidence-backed, hypothesis, and proposed elements.
- Ensure no table, diagram, footnote, or screenshot is clipped across page boundaries.

### Screenshot rules

- Use original-quality captures, not compressed re-screenshots where avoidable.
- Crop irrelevant browser/desktop areas, but retain enough context to identify the source and screen.
- Redact names, phone numbers, UPI IDs, account information, transaction IDs, balances, and any other personal/financial identifiers.
- Add a caption with source, date, and evidence ID.
- Do not use historical UI screenshots as proof of the present-day app.
- Do not create or trigger a real failed payment to obtain screenshots.

## 7. PDF export and final visual QA

After exporting the report:

- Open the PDF and inspect every page at 100% zoom.
- Check that Mermaid diagrams are rendered as diagrams, not displayed as raw code fences.
- Check hyperlinks and references are clickable and resolve to the intended sources.
- Check page numbering, headings, footers, line breaks, table widths, image resolution, and font rendering.
- Confirm no accidental blank page, clipped content, orphan heading, or unreadable footnote exists.
- Confirm that the PDF text is selectable/searchable where possible.
- Reopen the final saved PDF after export; do not rely only on the editor preview.

## 8. GitHub publication QA

Before making the repository public or publishing the PDF:

- Include the final PDF and the editable Markdown/source files.
- Include a README that explains the problem, scope, methodology, deliverables, and limitations.
- Keep the evidence register and evidence IDs consistent with the report.
- Check that screenshot files contain no personal or financial information.
- Remove temporary exports, duplicate drafts, unused screenshots, and local-only files from the public repository.
- Add source links and a concise references section.
- Use meaningful commit messages and verify `git status` before pushing.
- Confirm the GitHub repository contains the same final PDF version that you reviewed locally.

## 9. Final release gate

Do not mark the teardown publication-ready until all are true:

- [ ] Complete Evidence_Register.xlsx audited and all used canonical E-IDs resolve; older draft mappings documented in Evidence_ID_Crosswalk.md.
- [ ] Exact PhonePe Help titles/URLs/date metadata captured or limitations disclosed.
- [ ] RBI T+1/T+5 claims cite the 2019 circular and preserve the scenario definitions.
- [ ] PhonePe Grievance Policy Version 10 details are accurately represented.
- [ ] PhonePe policy's generic 3–10-day refund-reflection note is not conflated with the Help 3–5-day guidance.
- [ ] No blanket RBI Ombudsman claim is made for PhonePe UPI complaints.
- [ ] Current app screens are distinguished from historical screenshots and conceptual recommendations.
- [ ] No hypothetical research results are represented as real findings.
- [ ] Final PDF reviewed page by page.
- [ ] Public GitHub repository checked for privacy, consistency, and correct final files.

**Current status:** Preliminary audit only. The final PDF, full evidence register, and public GitHub repository still require review before release.
