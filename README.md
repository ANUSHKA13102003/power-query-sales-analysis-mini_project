# 📊 Power Query: Cleaning & Reshaping Messy Sales Data

![Excel](https://img.shields.io/badge/Excel-Power_Query-217346?style=flat&logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success)
![Type](https://img.shields.io/badge/Type-Data_Cleaning-blue)

A mini ETL project using **Microsoft Excel Power Query** to transform a messy, manually-entered employee sales dataset into a clean, analysis-ready table — using a no-code transformation pipeline that's fully repeatable on any future data refresh.

## 🎯 The Problem

The raw dataset (`raw_data.xlsx`) had issues common to almost every real-world dataset analysts receive:
- First and last names split across columns, with employee codes glued onto the last name (e.g. `Green(121)`)
- Regional sales figures (North, South, East, West) spread across separate columns instead of rows
- Random blank rows breaking the table structure
- Inconsistent layout that couldn't be loaded directly into a pivot table or BI tool

![Raw data](1_raw_data.png)

## ✅ The Solution

Built a repeatable Power Query transformation pipeline — five steps, applied once, reusable on every future refresh of this data:

| Step | Transformation Applied | Why It Matters |
|------|------------------------|-----------------|
| 1 | Removed blank/null rows | Eliminates breaks in the data structure |
| 2 | Split combined `LastName(Code)` into `Last Name` + `EmployeeCode` | Separates two different data types that were incorrectly merged |
| 3 | Merged `First Name` + `Last Name` into a single `NAME` column | Creates one clean, queryable identity field |
| 4 | **Unpivoted** North/South/East/West columns into `Attribute` (region) + `Value` (sales figure) | Converts wide format into tidy long format — the standard shape required by BI tools, SQL, and pandas |
| 5 | Standardized data types (text vs. numeric) | Ensures values aggregate and chart correctly downstream |

![Power Query steps](2_power_query_steps.png)

## 📊 Before vs After

**Before:** Wide, inconsistent sheet — names split and merged with codes, blank rows breaking structure, regional sales scattered across separate columns.

**After:** A clean 4-column table — `NAME | EMPCODE | Attribute | Value` — ready to be loaded straight into a pivot table, dashboard, or BI tool with zero further manual cleanup.

![Final output](3_final_output.png)

## 🛠️ Skills Demonstrated
- Data cleaning & wrangling
- Unpivoting (wide-to-long transformation) — a core data prep skill for BI/analytics work
- Column splitting, merging, and parsing using delimiters
- Data type standardization
- Building a repeatable, auditable transformation pipeline (not one-off manual edits)

**Tools:** Microsoft Excel — Power Query Editor

## 💡 Why This Matters

Unpivoting wide data into tidy long-format data is one of the most common real-world data prep tasks in analytics — it's the difference between a spreadsheet a human can read and a dataset a tool (Power BI, SQL, Python/pandas) can actually consume. Every step here is also non-destructive and repeatable: refresh the source file, hit "Refresh" in Power Query, and the same clean output regenerates automatically — no manual rework needed.

## 📁 Repository Contents
- `raw_data.xlsx` — original messy dataset
- `cleaned_data.xlsx` — final transformed output
- `1_raw_data.png` — view of the raw data before cleaning
- `2_power_query_steps.png` — the Applied Steps pipeline in Power Query
- `3_final_output.png` — the clean, tidy final table

---
*Part of my Data Analyst portfolio — check out my other project: [SQL 50 LeetCode Solutions](https://github.com/ANUSHKA13102003/sql-50-leetcode)*
