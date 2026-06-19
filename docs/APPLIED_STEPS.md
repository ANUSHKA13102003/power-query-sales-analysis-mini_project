# Applied Steps & Power Query M

This file contains the Applied Steps description and a ready-to-use Power Query M script that implements the 5-step pipeline used in this project.

Notes before using
- The M script below expects the source to be a table or a sheet with headers that include at least: `First Name`, `Last Name`, `North`, `South`, `East`, `West` (case-sensitive).
- If your sheet has different column names, either rename the columns in Excel or update the M script's column names accordingly.

---

## High-level applied steps

1. Promote first row to headers (if needed) and remove fully blank rows.
2. Split `Last Name` where it contains `LastName(Code)` into Last Name and an EmpCode field (strip parentheses).
3. Trim text fields and merge `First Name` + `Last Name` into `NAME`.
4. Unpivot region columns (`North`, `South`, `East`, `West`) into `Attribute` and `Value`.
5. Convert types: `NAME` and `EMPCODE` as text; `Value` as number.

---

## Power Query M script (paste this into Power Query Advanced Editor)

```m
let
    // Replace the Source step if your data is in a different workbook/sheet or a named table
    Source = Excel.Workbook(File.Contents("raw_data.xlsx"), null, true),
    // Change Item/Kind to match the worksheet/table name in your workbook
    Sheet = Source{[Item="Sheet1",Kind="Sheet"]}[Data],
    PromotedHeaders = Table.PromoteHeaders(Sheet, [PromoteAllScalars=true]),

    // 1) Remove rows where all columns are null/empty
    RemoveBlankRows = Table.SelectRows(PromotedHeaders, each List.NonNullCount(Record.FieldValues(_)) > 0),

    // 2) Split Last Name containing code like "Green(121)" into Last Name and code
    // If the column header is "LastName(Code)" or similar change the column name below
    SplitLastNameCode = Table.SplitColumn(RemoveBlankRows, "Last Name", Splitter.SplitTextByEachDelimiter({"("}, QuoteStyle.Csv, false), {"Last Name", "EmpCodeTemp"}),
    // Remove trailing ")" from code and trim
    TrimEmpCode = Table.TransformColumns(SplitLastNameCode, {{"EmpCodeTemp", each if _ = null then null else Text.BeforeDelimiter(_, ")"), type text}}),

    // 3) Trim names and create full name
    RenameAndTrim = Table.TransformColumns(TrimEmpCode, {{"First Name", Text.Trim, type text}, {"Last Name", Text.Trim, type text}, {"EmpCodeTemp", Text.Trim, type text}}),
    AddFullName = Table.AddColumn(RenameAndTrim, "NAME", each Text.Trim(Text.Combine({Record.Field(_, "First Name"), Record.Field(_, "Last Name")}, " ")), type text),
    RemoveOldNameCols = Table.RemoveColumns(AddFullName, {"First Name", "Last Name"}),

    // 4) Unpivot the regional columns into Attribute + Value
    UnpivotRegions = Table.UnpivotOtherColumns(RemoveOldNameCols, {"NAME", "EmpCodeTemp"}, "Attribute", "Value"),

    // 5) Set data types and rename EmpCode
    ChangeTypes = Table.TransformColumnTypes(UnpivotRegions, {{"NAME", type text}, {"EmpCodeTemp", type text}, {"Attribute", type text}, {"Value", type number}}),
    RenameEmpCode = Table.RenameColumns(ChangeTypes, {{"EmpCodeTemp", "EMPCODE"}})
in
    RenameEmpCode
```

---

If your source is a named table (e.g., `Table1`) replace the first steps with:

```m
Source = Excel.CurrentWorkbook(){[Name="Table1"]}[Content],
PromotedHeaders = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
```

Questions or need this adapted to Power BI Desktop? I can update the M code to reference a folder, CSV files, or a database as the source.
