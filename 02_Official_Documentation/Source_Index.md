# Official Documentation — Source Index

**Project:** PhonePe UPI Transaction Failure & Recovery Teardown  
**Access date:** 10 November 2026

This index records official sources used for the teardown. Keep the original downloaded documents in their respective subfolders. Do not treat source publication dates as evidence of current app behaviour.

## 1. Reserve Bank of India (RBI)

**File name:** `RBI_Circular_2019_Turnaround_Time.pdf`  
**Document:** RBI/2019-20/67 — DPSS.CO.PD No.629/02.01.014/2019-20  
**Date:** 20 September 2019  
**Official PDF:** https://rbi.org.in/commonman/Upload/English/Notification/PDFs/CIRCULAR677EC931A7A65E4D99AA957D8E85BC0A2A.PDF  
**Official notification page:** https://www.rbi.org.in/Scripts/NotificationUser.aspx?Id=11693

**Relevant use in this teardown:** The annex specifies turnaround-time and compensation rules for defined failed-transaction incidents, including (a) funds transfer where the originator is debited but the beneficiary is not credited, and (b) merchant payment where the payer is debited but confirmation is not received at the merchant location. It defines T as the calendar date of the transaction.

**Limitations:** This is the original 2019 circular. Before presenting it as the complete current regulatory position, check the RBI's current consolidated directions and any amendments. Do not apply its T+1 or T+5 timelines to every pending, failed, order, or refund scenario without matching the facts to the defined incident category.

## 2. National Payments Corporation of India (NPCI)

**File name:** `UPI_Help_Brand_Guidelines_2023.pdf`  
**Document:** UPI HELP Brand Guidelines  
**Date/version shown in file name:** July 2023  
**Official PDF:** https://www.npci.org.in/uploads/UPI_Help_Brand_Guidelines_86c8c28922.pdf

**Relevant use in this teardown:** Describes the UPI HELP concept and illustrative complaint/reporting and transaction-status flows for P2P and P2M transactions. It can support discussion of the intended UPI HELP framework and design guidance.

**Limitations:** These are NPCI guidelines, not proof that every PhonePe screen or current workflow exactly matches the examples. Do not present the illustrative screens as current PhonePe UI evidence.

## 3. PhonePe

**File name (recommended local copy):** `PhonePe_Grievance_Policy_v10_2026.pdf`  
**Document:** PhonePe Grievance Policy, Version 10  
**Date:** 16 July 2026  
**Official policy webpage:** https://www.phonepe.com/grievance-policy/

**How to create the local PDF:** Open the official policy webpage in a browser, press `Ctrl + P`, choose **Save as PDF** as the printer/destination, then save the file into `02_Official_Documentation/PhonePe/` using the filename above. Record that this is a PDF copy generated from the official webpage and retain the webpage URL as the source.

**Relevant use in this teardown:** Supports descriptions of PhonePe's published customer grievance levels, response/resolution service targets, escalation process, and policy scope. The current page identifies Version 10 dated 16 July 2026.

**Limitations:** Distinguish UPI complaints from PhonePe PPI complaints. The policy's RBI Ombudsman section is specifically scoped to PPIs; do not describe it as a universal RBI Ombudsman route for all PhonePe UPI issues. The policy also states that RBI, NPCI, or card-network prescribed timelines apply where relevant.

## Recommended folder structure

```text
02_Official_Documentation/
├── Source_Index.md
├── RBI/
│   └── RBI_Circular_2019_Turnaround_Time.pdf
├── NPCI/
│   └── UPI_Help_Brand_Guidelines_2023.pdf
└── PhonePe/
    └── PhonePe_Grievance_Policy_v10_2026.pdf
```

## Citation practice

- Cite the RBI circular for the specific TAT/compensation incident categories it defines.
- Cite the NPCI guidelines only for the UPI HELP framework and illustrative guidance they contain.
- Cite the PhonePe policy for PhonePe's published grievance process and service-level statements.
- Keep the PhonePe Help screenshots in `01_Product_Screenshots/Help_Centre_Screens/` and cite their Evidence IDs separately. These screenshots are not substitutes for the official policy or RBI/NPCI documents.
