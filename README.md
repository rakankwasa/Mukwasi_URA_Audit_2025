# Mukwasi_URA_Audit_2025

## Background
Mukwasi General Contractors Ltd (“Mukwasi”) is a Ugandan company that specialises in property development, rental, and construction-related activities. Its primary source of income is rental income.  

The Uganda Revenue Authority (URA) is currently auditing Mukwasi’s:
- Income Tax
- Rental Tax
- VAT
- Withholding Tax (WHT)
- Pay-As-You-Earn (PAYE)

The audit covers two financial years:
- **2023:** 1 January 2023 – 31 December 2023  
- **2024:** 1 January 2024 – 31 December 2024:contentReference[oaicite:0]{index=0}  

The first priority is to reconcile **QuickBooks invoices** with **EFRIS VAT sales reports**, ensuring every QuickBooks invoice can be traced to an EFRIS invoice (identified by the unique FDN number). Later modules will extend to payroll, WHT, and subsequent years.

---

## Reconciliation Plan (QuickBooks ↔ EFRIS)
1. **Prepare & clean both datasets**
   - Keep only invoices in QuickBooks.
   - Clean headers and numeric fields in EFRIS, group by FDN.  

2. **Define matching keys**
   - Name of Purchaser ↔ Name (fuzzy match to handle typos).
   - Invoice Date ↔ Date (± few days tolerance).
   - Amount ↔ Rental Invoices Issued (allow ≤ 2% difference for FX/rounding).  

3. **Apply matching strategy**
   - Step A: Exact match (name, date, amount).
   - Step B: Fuzzy name match.
   - Step C: Date tolerance.
   - Step D: Amount tolerance.
   - Step E: Investigate unmatched items.  

4. **Outputs**
   - Matched invoices table (QB invoice ↔ EFRIS FDN).  
   - Unmatched QuickBooks list (potentially undeclared).  
   - Unmatched EFRIS list (potential over-declarations).  
   - Reconciliation summary (totals, variances, exception reasons):contentReference[oaicite:1]{index=1}.

---

## Work Units (Chronological, Audit-Trail Ready)
- **Stage 1: Data Preparation** → load QB & EFRIS files, clean, save datasets.  
- **Stage 2: Standardization** → normalize names, amounts, dates.  
- **Stage 3: Matching Process** → run exact, fuzzy, date, and amount matches.  
- **Stage 4: Exception Handling** → extract unmatched QB & EFRIS entries, categorize reasons.  
- **Stage 5: Reconciliation Summary** → consolidate results, generate audit-ready report:contentReference[oaicite:2]{index=2}.  

Each stage produces a file (e.g., `match_exact.csv`, `unmatched_qb.csv`) that becomes the input to the next stage.

---

## Project Setup
- **Folder:** `Mukwasi_URA_Audit_2025` (stored in Dropbox for backup).  
- **Tools:** VS Code + GitHub Desktop for version control, GitHub (private) for remote backup.  
- **Python Environment:**  
  ```bash
  python -m venv .venv
  .venv\Scripts\activate   # Windows
  pip install -r requirements.txt

