# Excel Chaos to Clean Dataset

## Overview
This project demonstrates how unstructured and messy Excel reports commonly found in operational environments can be transformed into clean, analysis-ready datasets.

The focus of this project is not on Excel formulas, but on data engineering thinking: identifying structure, normalizing data, and preparing it for downstream analysis.

---

## Common Problems Found in Raw Excel Reports
- Merged cells
- Multi-level headers
- Inconsistent column structures
- Manual data entry errors
- Multiple reporting periods in a single sheet

---

## Approach
1. Identify actual data vs metadata
2. Normalize the data into a single, tabular structure
3. Standardize column names and data types
4. Validate data consistency
5. Prepare dataset for analysis or pipeline integration

---

## Example Case (Simplified)

### Raw Excel Structure (Before)
A typical operational Excel report may look like this:

- Title and report metadata at the top
- Merged cells for dates and categories
- Multi-level headers
- Multiple reporting periods in one sheet

Example (conceptual):

|        | Jan 2024 |        | Feb 2024 |        |
|--------|----------|--------|----------|--------|
| Name   | Present  | Absent | Present  | Absent |
| John   | 20       | 2      | 18       | 1      |
| Maria | 22       | 0      | 21       | 1      |

This structure is readable for humans, but not suitable for analysis.

---

### Normalized Dataset (After)
After transformation, the data is normalized into a single tabular structure:

| name  | month    | present_days | absent_days |
|-------|----------|--------------|-------------|
| John  | 2024-01  | 20           | 2           |
| John  | 2024-02  | 18           | 1           |
| Maria | 2024-01  | 22           | 0           |
| Maria | 2024-02  | 21           | 1           |

This format allows:
- Easy aggregation
- Filtering by time period
- Loading into databases
- Integration with data pipelines

---

## Tools Used
- Microsoft Excel
- Power Query
- Python (Pandas)

---

## What This Project Demonstrates
- Real-world data wrangling skills
- Ability to handle human-generated data
- Data normalization and standardization
- Engineering mindset applied to business reports

---

## Possible Extensions
- Automating the transformation using Python
- Loading cleaned data into a database
- Integrating with a data pipeline

