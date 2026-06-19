Power Query — Sales Data Cleaning & Transformation (One Pager)

Project: Convert messy employee sales sheets into an analytics-ready table

Goal
- Produce a repeatable, refreshable pipeline in Excel Power Query that turns inconsistent wide spreadsheets into tidy long-format tables ready for pivot tables or BI tools.

Problem
- Employee names and employee codes combined into one cell (e.g., "Green(121)").
- Regional sales split across columns (North, South, East, West) rather than rows.
- Random blank rows and inconsistent layouts prevented loading into pivot tables.

Solution
- Implemented a 5-step Power Query pipeline (remove blanks, split names+codes, merge names, unpivot regions, enforce data types). The query is fully refreshable and non-destructive.

Impact
- Eliminates manual cleanup on each update.
- Ensures aggregation and dashboards are accurate.
- Saves analyst time and reduces human errors.

Files
- `raw_data.xlsx` (original)
- `cleaned_data.xlsx` (output)
- `APPLIED_STEPS.md` (full M code)

Contact
- GitHub: @ANUSHKA13102003
