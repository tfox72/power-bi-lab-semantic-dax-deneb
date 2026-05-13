# Power Query Optimizer Playbook

## Purpose

Use this playbook when helping the user clean, transform, troubleshoot, or optimize data using Power Query / M in Power BI.

The goal is to create Power Query logic that is:

- Refresh-safe
- Readable
- Efficient
- Foldable where possible
- Easy to maintain
- Aligned with the semantic model
- Free of unnecessary columns and rows

## When to Use This Playbook

Use this playbook when the user asks to:

- Clean data in Power Query
- Fix Power Query errors
- Improve refresh performance
- Understand query folding
- Merge or append tables
- Remove duplicate rows
- Create keys
- Transform flat files
- Prepare data for star schema
- Decide whether logic belongs in Power Query, DAX, SQL, or source system
- Troubleshoot refresh failures related to transformations

## Default Position

Use Power Query for repeatable data preparation and structural shaping.

Use DAX for calculations that must respond to filters and report context.

Use SQL/source system when the transformation is heavy, reusable, or more efficiently handled upstream.

## Decision Framework

Use this rule:

```text
Source / SQL:
Heavy joins, filtering, aggregation, source-controlled business logic, large transformations.

Power Query:
Repeatable ETL, cleanup, reshaping, column selection, type changes, merging small/medium lookup tables, unpivoting, key creation.

Semantic Model:
Relationships, metadata, hierarchies, model organization.

DAX:
Dynamic analytical calculations that must respond to slicers, filters, and visual context.

Visual Layer:
Presentation only, not business logic.
```

## Required Inputs

Ask for or infer:

1. Data source type
2. Current Power Query steps
3. Error message if any
4. Desired output table
5. Row counts
6. Column names
7. Whether query folding matters
8. Refresh performance symptoms
9. Import vs DirectQuery
10. Gateway or service refresh context if relevant

## Power Query Review Checklist

Always evaluate:

1. Are only needed columns loaded?
2. Are unnecessary rows filtered early?
3. Are data types set correctly?
4. Are expensive transformations pushed upstream if possible?
5. Is query folding preserved where important?
6. Are merges causing duplicate rows?
7. Are append operations aligning columns correctly?
8. Are column names business-friendly?
9. Are keys stable and unique?
10. Are transformations documented enough?
11. Are errors handled deliberately?
12. Are fact and dimension outputs aligned to the model?

## Preferred Step Order

General recommended order:

1. Connect to source.
2. Filter rows early if safe.
3. Remove unused columns early.
4. Rename columns clearly.
5. Set data types.
6. Clean text values.
7. Create keys if needed.
8. Merge or append carefully.
9. Unpivot/pivot if needed.
10. Add calculated structural columns.
11. Remove intermediate columns.
12. Validate row counts.
13. Load only final tables.

## Query Folding Guidance

Query folding is when Power Query pushes transformations back to the source system.

Important for:

- SQL sources
- Large datasets
- DirectQuery
- Incremental refresh
- Faster refresh
- Reduced local processing

Common folding-friendly steps:

- Filtering rows
- Selecting columns
- Renaming columns
- Changing simple data types
- Simple joins against foldable sources
- Simple aggregations

Common folding breakers:

- Custom functions
- Complex row-by-row logic
- Some index columns
- Non-foldable sources like many files or web sources
- Certain type conversions
- Buffering
- Complex text parsing
- Merging foldable and non-foldable sources

When query folding matters, recommend checking:

```text
Right-click applied step > View Native Query
```

If View Native Query is disabled, folding may have stopped before that step.

## Merge Guidance

Before merging, check:

1. Are join keys clean?
2. Are data types the same?
3. Are keys unique on the lookup side?
4. Is the join type correct?
5. Will the merge duplicate fact rows?
6. Is this better as a relationship in the model instead of a merge?

Common recommendation:

```text
Do not merge dimension attributes into a fact table just for reporting if a proper relationship can handle it in the model.
```

Use merges for:

- Creating clean dimensions
- Adding required keys
- Data preparation
- Source cleanup
- Small lookup enrichment when justified

Avoid merges that create:

- Duplicated fact rows
- Bloated fact tables
- Flat-table models that should be star schemas

## Append Guidance

Before appending, check:

1. Do columns align correctly?
2. Are names consistent?
3. Are data types consistent?
4. Is there a source/system column to identify origin?
5. Are duplicate records possible?
6. Is the resulting grain consistent?

## Unpivot Guidance

Use unpivot when source columns represent values that should be rows.

Example source:

```text
Product | Jan | Feb | Mar
```

Better analytical shape:

```text
Product | Month | Value
```

Unpivot is common for:

- Monthly budget files
- Survey responses
- Forecast files
- Excel exports
- Wide operational reports

## Error Troubleshooting

Common Power Query errors:

- Token Literal Expected
- Expression.Error
- DataFormat.Error
- Formula.Firewall
- Column not found
- Cannot convert value
- We cannot apply operator
- The key did not match any rows
- Cyclic reference

For any error, respond with:

```markdown
## Most Likely Cause

## Where It Is Happening

## Fix

## Safer Version of the M Code

## How to Validate
```

## M Code Standards

When writing M:

- Use readable step names.
- Avoid spaces in step names when practical.
- Comment outside code when possible.
- Keep transformations modular.
- Avoid hard-coding file paths unless required.
- Avoid fragile column position references.
- Use column names deliberately.
- Validate types.

Example style:

```powerquery
let
    Source = Excel.Workbook(File.Contents(FilePath), null, true),
    RawTable = Source{[Item="Sales", Kind="Table"]}[Data],
    ChangedTypes = Table.TransformColumnTypes(
        RawTable,
        {
            {"Order Date", type date},
            {"Sales Amount", Currency.Type},
            {"Quantity", Int64.Type}
        }
    ),
    RemovedUnusedColumns = Table.SelectColumns(
        ChangedTypes,
        {
            "Order Date",
            "Customer ID",
            "Product ID",
            "Sales Amount",
            "Quantity"
        }
    )
in
    RemovedUnusedColumns
```

## Performance Recommendations

Recommend:

- Remove unused columns.
- Filter unnecessary rows early.
- Avoid unnecessary merges.
- Avoid expanding large nested tables carelessly.
- Avoid repeated expensive steps.
- Disable load for staging queries.
- Use reference queries intentionally.
- Keep fact tables narrow.
- Avoid high-cardinality text columns when not needed.
- Push heavy transformations to SQL when possible.
- Preserve folding for large SQL sources.

## Staging Query Pattern

Use staging queries for clean architecture.

Example:

```text
stg_Sales_Raw
stg_Customers_Raw
dim_Customer
dim_Product
fact_Sales
```

Recommended pattern:

- Staging queries connect to source and do light cleanup.
- Dimension queries reference staging and create unique dimension tables.
- Fact queries reference staging and keep measurable event rows.
- Disable load for staging queries.
- Load only final fact and dimension tables.

## Output Format

When optimizing Power Query, use:

```markdown
## Current Issue

## Likely Cause

## Recommended Transformation Strategy

## Revised Power Query / M Code

## Query Folding Notes

## Model Impact

## Validation Checklist

## Performance Risks
```

## Validation Checklist

1. Row counts match expectations.
2. Column data types are correct.
3. Joins do not duplicate rows unexpectedly.
4. Keys are unique where required.
5. Nulls are handled.
6. Totals match source.
7. Query refreshes successfully.
8. Folding is preserved where needed.
9. Final output supports the star schema.
10. Staging queries have load disabled if appropriate.

## Final Recommendation Style

Be practical and direct.

Example:

```text
This transformation can work in Power Query, but for a large SQL source I would push the join and filtering upstream to SQL to preserve performance and refresh reliability. Power Query should then handle final cleanup and model shaping.
```
