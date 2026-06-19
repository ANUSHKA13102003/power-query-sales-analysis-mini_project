![Excel](https://img.shields.io/badge/Excel-Power_Query-217346?style=flat&logo=microsoftexcel&logoColor=white) ![Status](https://img.shields.io/badge/Status-Complete-success) ![Type](https://img.shields.io/badge/Type-Data_Cleaning-blue)

# Power Query — Sales Data Cleaning & Transformation

Cleaned a messy, manually-entered employee sales dataset into an analytics-ready table using Microsoft Excel Power Query. This is a repeatable, no-code ETL pipeline that turns inconsistent worksheets into tidy data you can load directly into pivot tables, dashboards, or BI tools.

Why recruiters should care: this project demonstrates real-world data-prep skills used in analytics and BI roles — handling dirty inputs, parsing mixed fields, reshaping wide data to tidy long formats, and building a reliable refreshable pipeline in Excel.

---

## Quick Highlights

- Problem: Employee names and codes combined, regional sales spread across columns, and random blank rows broke the table structure.
- Solution: A 5-step Power Query pipeline that splits, parses, cleans, and unpivots the data to produce a four-column tidy table: `NAME | EMPCODE | ATTRIBUTE | VALUE`.
- Outcome: A reusable transformation that eliminates manual cleanup and makes the data dashboard-ready with a single Refresh.

---

## Demo (Before → After)

![Raw data](1_raw_data.png)

![Power Query steps](2_power_query_steps.png)

![Final output](3_final_output.png)

---

## What I did (concise)

1. Removed blank and malformed rows to restore table structure.
2. Parsed `LastName(Code)` into separate `Last Name` and `EmployeeCode` fields using delimiter-based splitting and text extraction.
3. Merged `First Name` + `Last Name` into a single `NAME` column for a stable identifier.
4. Unpivoted regional columns (North/South/East/West) into `Attribute` and `Value` to convert wide → long format.
5. Standardized data types (text for names/codes, numeric for sales) and validated totals to ensure accuracy.

These steps are implemented entirely inside Power Query's Applied Steps — non-destructive and refreshable.

---

## Why this matters (impact)

- Saves time: Eliminates repeat manual rework when the source file is updated.
- Reduces errors: Removes fragile manual edits and parsing mistakes.
- Ready for analytics: Produces a tidy, aggregation-friendly table that loads into pivot tables, Power BI, or SQL with zero further cleanup.

Recruiters and hiring managers can quickly see this is the kind of practical, repeatable data engineering/analysis work that scales beyond a one-off spreadsheet fix.

---

## Files in this repo

- `raw_data.xlsx` — original messy dataset (example input)
- `cleaned_data.xlsx` — transformed output (example result)
- `1_raw_data.png`, `2_power_query_steps.png`, `3_final_output.png` — screenshots showing the workflow and result

---

## How to reproduce / use (open & refresh)

1. Open `raw_data.xlsx` in Microsoft Excel (Desktop) with Power Query (Get & Transform Data).
2. Go to Data → Get Data → From File → From Workbook and point to `raw_data.xlsx` (or open the workbook if queries are saved inside it).
3. In Power Query Editor, confirm the query's Applied Steps (you can inspect or modify any step).
4. Click Close & Load → Refresh to run the transformation on new data — no manual edits required.

Tip: Keep the original `raw_data.xlsx` structure consistent (same column headers) so the query steps apply correctly on refresh.

---

## Skills & Tools demonstrated

- Data cleaning & wrangling
- Excel Power Query: parsing, splitting, merging columns, unpivoting, and type enforcement
- Building repeatable, auditable ETL pipelines for BI consumption

**Tools:** Microsoft Excel (Power Query / Get & Transform)

---

## Notes for interviewers

- I can walk through the Applied Steps and explain each transformation, trade-offs, and how to adapt the query when new data quirks appear.
- If you'd like, I can convert this into a Power BI Desktop version or demonstrate the transformation live during an interview.

---

## More projects

Part of my Data Analyst portfolio — see my other project: [SQL 50 LeetCode Solutions](https://github.com/ANUSHKA13102003/sql-50-leetcode)

---

## License & Contact

MIT License — feel free to reuse these query patterns in your own work.

Contact: @ANUSHKA13102003 on GitHub
