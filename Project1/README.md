# E-Commerce Data Cleaning & Quality Verification Pipeline (DecodeLabs Project 1)

## Executive Summary
This project delivers a verified, gold-standard e-commerce transactional dataset for downstream business analytics and reporting. The primary objective was to inspect, clean, mathematically verify, and transform **1,200 raw transaction records** spanning from January 2023 to June 2025.

Through rigorous cross-field mathematical validation, missing-value imputation, and standardized formatting, the pipeline achieved a **0.00% error rate** across all core verification gates without dropping a single customer transaction row.

---

## Workspace & Environment Evolution
* **Phase 1 (Exploratory Analysis)**: Google Colab / Jupyter Notebook (`Project1decode.ipynb`).
* **Phase 2 (Production & Delivery)**: Local VS Code environment integrated with Git version control for GitHub repository submission.

---

## Key Business Metrics

| Metric Name | Value |
| :--- | :--- |
| **Total Transaction Volume** | 1,200 orders |
| **Total Revenue** | $1,264,761.96 |
| **Average Order Value (AOV)** | $1,053.97 |
| **Unique Customer Count** | 1,189 customers |
| **Top Performing Product** | Chair ($195,620.11 total sales) |
| **Dataset Date Range** | 2023-01-01 to 2025-06-30 |
| **Remaining Missing Values** | 0 |

---

## Data Cleaning Workflow

1. **Missing Value Imputation (`CouponCode`)**:
   * **Issue**: Audit revealed exactly 309 missing entries (`NaN`) in `CouponCode`.
   * **Solution**: Applied `.fillna('None')` to explicitly capture non-promotional transactions while preserving 100% of order rows.

2. **ISO Date Standardization (`Date`)**:
   * **Issue**: Raw timestamps contained mixed date formats.
   * **Solution**: Standardized all entries to clean ISO 8601 strings (`YYYY-MM-DD`).

3. **Cross-Field Mathematical Verification (`CalculatedTotalPrice`)**:
   * **Issue**: Verified line-item calculation ($\text{Quantity} \times \text{UnitPrice}$) against recorded totals.
   * **Result**: Verified $0.00$ calculation discrepancies across all 1,200 orders.

4. **Price Number Formatting**:
   * **Solution**: Formatted `UnitPrice`, `TotalPrice`, and `CalculatedTotalPrice` to fixed 2-decimal point floating precision without raw dollar signs for database compatibility.

---

## Quality Control Audit Matrix

| Verification Parameter | Target Requirement | Observed Result | Status |
| :--- | :--- | :--- | :--- |
| **Primary Key Uniqueness (`OrderID`)** | 0 Duplicates | 0 Duplicates | **PASSED** |
| **Tracking Identifier (`TrackingNumber`)** | 0 Duplicates | 0 Duplicates | **PASSED** |
| **Date Parsing Validity (`Date`)** | 0 Invalid Dates | 0 Invalid Dates | **PASSED** |
| **Missing / Null Cells** | 0 Null Cells | 0 Null Cells | **PASSED** |

---
