![Excel](https://img.shields.io/badge/Excel-Power_Query-217346?style=flat&logo=microsoftexcel&logoColor=white) ![Status](https://img.shields.io/badge/Status-Complete-success) ![Type](https://img.shields.io/badge/Type-Data_ETL-blue)

# Power Query — Sales Data Cleaning & Transformation

Cleaned a messy, manually-entered employee sales dataset into an analytics-ready table using Microsoft Excel Power Query. This is a repeatable, no-code ETL pipeline that turns inconsistent worksheets into production-grade data.

**Why recruiters should care:** this project demonstrates real-world data-prep skills used in analytics and BI roles — handling dirty inputs, parsing mixed fields, reshaping wide data to tidy long format, and building auditable transformations.

---

## Quick Highlights

- **Problem:** Employee names and codes combined, regional sales spread across columns, and random blank rows broke the table structure.
- **Solution:** A 5-step Power Query pipeline that splits, parses, cleans, and unpivots the data to produce a four-column tidy table: `NAME | EMPCODE | ATTRIBUTE | VALUE`.
- **Outcome:** A reusable transformation that eliminates manual cleanup and makes the data dashboard-ready with a single Refresh.

---

## Demo (Before → After)

![Raw data](screenshots/1_raw_data.png)

![Power Query steps](screenshots/2_power_query_steps.png)

![Refresh demo](assets/refresh_demo.svg)

![Final output](screenshots/3_final_output.png)

---

## What I did (concise)

1. Removed blank and malformed rows to restore table structure.
2. Parsed `LastName(Code)` into separate `Last Name` and `EmployeeCode` fields using delimiter-based splitting and text extraction.
3. Merged `First Name` + `Last Name` into a single `NAME` column for a stable identifier.
4. Unpivoted regional columns (North/South/East/West) into `Attribute` and `Value` to convert wide → long format.
5. Standardized data types (text for names/codes, numeric for sales) and validated totals to ensure accuracy.

These steps are implemented entirely inside Power Query's Applied Steps — non-destructive and refreshable. See `docs/APPLIED_STEPS.md` for the full Applied Steps and the Power Query M code.

---

## Project Structure

```
📦 power-query-sales-analysis-mini_project
├── 📄 README.md
├── 📄 LICENSE
├── 📄 CODE_OF_CONDUCT.md
├── 📄 .gitignore
│
├── 📁 docs/                          # Documentation
│   ├── 📄 APPLIED_STEPS.md          # Full M code and step breakdown
│   ├── 📄 PROJECT_ONE_PAGER.md      # One-page project summary
│   └── 📄 TALKING_POINTS.md         # 60-second interview pitch
│
├── 📁 data/                          # Data files
│   ├── 📁 raw/                      # Input data
│   │   ├── 📊 raw_data.xlsx
│   │   └── 📊 sample_raw_data.csv
│   └── 📁 cleaned/                  # Output data
│       └── 📊 cleaned_data.xlsx
│
├── 📁 screenshots/                   # Visual demos
│   ├── 🖼️ 1_raw_data.png
│   ├── 🖼️ 2_power_query_steps.png
│   └── 🖼️ 3_final_output.png
│
└── 📁 assets/                        # Animations & SVGs
    └── 🎬 refresh_demo.svg
```

---

## How to reproduce / use (open & refresh)

1. Open `data/raw/sample_raw_data.csv` or `data/raw/raw_data.xlsx` in Microsoft Excel (Desktop) with Power Query (Get & Transform Data).
2. Go to **Data → Get Data → From File → From Workbook / From Text/CSV** and point to the sample file.
3. In Power Query Editor, inspect the query's Applied Steps (open `docs/APPLIED_STEPS.md` to see the exact M code used).
4. Click **Close & Load → Refresh** to run the transformation on new data — no manual edits required.

**Tip:** Keep the original `raw_data.xlsx` structure consistent (same column headers) so the query steps apply correctly on refresh.

---

## Skills & Tools Demonstrated

- **Data cleaning & wrangling**
- **Excel Power Query:** parsing, splitting, merging columns, unpivoting, and type enforcement
- **Building repeatable, auditable ETL pipelines** for BI consumption

**Tools:** Microsoft Excel (Power Query / Get & Transform)

---

## Notes for Interviewers

- I can walk through the Applied Steps and explain each transformation, trade-offs, and how to adapt the query when new data quirks appear.
- I can demonstrate live during an interview or share a short recorded walkthrough.
- The M script is fully adaptable to different data sources (CSVs, databases, Power BI).

---

## See Also

Explore more of my projects:

- **[SQL Projects](https://github.com/ANUSHKA13102003?tab=repositories&q=sql)** — Database queries, optimization, and complex transformations
- **[LeetCode Solutions](https://github.com/ANUSHKA13102003?tab=repositories&q=leetcode)** — Algorithm practice and problem-solving
- **[My GitHub](https://github.com/ANUSHKA13102003)** — View all repositories and pinned projects

---

## Quick Links

- 📖 **Full Documentation:** `docs/APPLIED_STEPS.md`
- 📋 **One-Pager:** `docs/PROJECT_ONE_PAGER.md`
- 🎤 **Interview Pitch:** `docs/TALKING_POINTS.md`
- 📊 **Sample Data:** `data/raw/sample_raw_data.csv`

---

## License & Contact

MIT License — see `LICENSE` file.

**Contact:** [@ANUSHKA13102003](https://github.com/ANUSHKA13102003) on GitHub
