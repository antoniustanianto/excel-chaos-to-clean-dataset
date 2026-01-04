# Project 4 — Excel Chaos to Clean Dataset (Operational Data)

## Overview
In many operational environments, especially field operations, data is often recorded in Excel files designed for **human readability**, not for analytics or databases.

This project demonstrates how messy, human-oriented Excel reports can be transformed into a **clean, normalized dataset** that is ready for database ingestion and downstream analysis.

The focus of this project is **data engineering**, not data analysis or visualization.

---

## Problem Description
The original Excel data has several common real-world issues:

- Merged cells used for reporting periods (e.g., monthly headers)
- Dates represented as column headers (1–30)
- Measurement types stored as rows instead of columns
- Multiple units of measurement in a single table
- Placeholder symbols such as `-` or visually empty cells
- Manual data entry artifacts (spaces and hidden characters)

Such structures are readable for humans but problematic for automation, aggregation, and databases.

---

## Raw Excel Structure (Conceptual Example)

| No | Name     | Type       | 1 | 2 | 3 | ... |
|----|----------|------------|---|---|---|-----|
| 01 | Worker A | Janjang    | 3 | 5 | 7 |     |
|    |          | Brondolan  |90 |100|95 |     |

**Notes:**
- The reporting month is displayed as a merged cell above the table
- Dates (1–30) are column headers
- `Janjang` is measured in pieces (pcs)
- `Brondolan` is measured in kilograms (kg)
- Placeholder symbols may represent missing values

---

## Target Data Structure (Normalized)

| no | name     | date       | type      | value | unit |
|----|----------|------------|-----------|-------|------|
| 01 | Worker A | 2024-01-01 | Janjang   | 3     | pcs  |
| 01 | Worker A | 2024-01-01 | Brondolan | 90    | kg   |
| 01 | Worker A | 2024-01-02 | Janjang   | 5     | pcs  |
| 01 | Worker A | 2024-01-02 | Brondolan | 100   | kg   |

This structure ensures:
- One row represents one event
- One column represents one meaning
- Measurement units are explicit
- Data is safe for database ingestion

---

## Transformation Approach
The transformation follows a repeatable data engineering pattern:

1. Separate metadata from row-level data
2. Normalize visually empty values and placeholder symbols
3. Flatten multi-level headers
4. Convert dates from columns into row values (unpivot)
5. Treat measurement types as categorical values
6. Explicitly assign units of measurement
7. Validate consistency and completeness

---

## Engineering Focus
This project emphasizes:
- Data quality over visualization
- Structural correctness over insight generation
- Repeatability over one-off cleaning
- Safe handling of sensitive operational data

All examples are simplified and anonymized to reflect the original structure without exposing real production data.

---

## Outcome
The final dataset:
- Can be directly loaded into relational databases
- Supports reliable aggregation and filtering
- Reduces ambiguity for downstream analytics
- Provides a trustworthy foundation for further analysis

---

## Key Takeaway
> **Data engineering ensures that data does not lie.  
> Insights come later, built on reliable foundations.**
