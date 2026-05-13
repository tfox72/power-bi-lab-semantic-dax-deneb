# DAX Debugger Playbook

## Purpose

Use this playbook when helping the user write, debug, explain, or optimize DAX measures in Power BI.

The goal is to produce DAX that is:

- Correct
- Readable
- Maintainable
- Filter-aware
- Performant
- Easy to validate
- Consistent with a well-designed semantic model

## Default Position

Before fixing DAX, understand the model.

Many DAX problems are actually model problems.

Always consider:

- Table relationships
- Filter direction
- Cardinality
- Fact table grain
- Dimension table keys
- Date table design
- Whether the calculation should be a measure or calculated column

## When to Use This Playbook

Use this playbook when the user asks to:

- Fix a DAX measure
- Explain a DAX formula
- Build a new measure
- Diagnose wrong totals
- Create time intelligence
- Create percent of total
- Create running totals
- Create rankings
- Debug slicer behavior
- Decide between measure and calculated column
- Improve DAX performance

## Required Inputs

Ask for or infer:

1. Current DAX formula
2. Expected result
3. Actual result
4. Relevant tables
5. Relevant relationships
6. Visual layout
7. Slicers/filters involved
8. Date table details if time intelligence is involved
9. Example rows or expected totals if available

If inputs are incomplete, provide a likely diagnosis and list what is needed to confirm.

## DAX Response Standard

When debugging DAX, use this structure:

```markdown
## What the Measure Is Doing

## Why the Result May Be Wrong

## Corrected DAX

## Explanation of the Fix

## Filter Context Walkthrough

## Row Context / Context Transition Notes

## Test Cases

## Performance Notes

## Common Mistakes to Avoid
```

## Core DAX Principles

## 1. Explain Filter Context

Filter context is the set of filters active when a measure is evaluated.

Filters can come from:

- Visual rows and columns
- Slicers
- Page filters
- Report filters
- Drill-through context
- Relationships
- Cross-filtering
- DAX filter modifiers inside CALCULATE

Always explain which filters exist before and after the key part of the measure.

## 2. Explain Row Context When Relevant

Row context exists when DAX is evaluating row by row.

Common sources:

- Calculated columns
- SUMX
- AVERAGEX
- FILTER
- ADDCOLUMNS
- RANKX
- GENERATE

Example:

```DAX
Revenue =
SUMX (
    FactSales,
    FactSales[Quantity] * FactSales[Unit Price]
)
```

Explain that SUMX iterates over rows in FactSales.

## 3. Explain Context Transition

Context transition happens when row context is transformed into filter context, commonly through CALCULATE.

Mention it when:

- CALCULATE appears inside an iterator
- A measure is used inside row context
- A calculated column references a measure
- Results change unexpectedly row by row

## 4. Treat CALCULATE Carefully

CALCULATE changes filter context.

When explaining CALCULATE, identify:

1. Base expression
2. Original filter context
3. Filters added
4. Filters removed
5. Filters preserved
6. Final evaluation context

Example:

```DAX
Sales All Products =
CALCULATE (
    [Total Sales],
    REMOVEFILTERS ( DimProduct )
)
```

Explain:

```text
This evaluates [Total Sales] while removing filters from DimProduct. Other filters, such as Date or Region, remain active.
```

## 5. Use Variables

Prefer variables in complex measures.

Example:

```DAX
Sales Variance % =
VAR CurrentSales =
    [Total Sales]
VAR PriorSales =
    [Sales Prior Year]
VAR Result =
    DIVIDE ( CurrentSales - PriorSales, PriorSales )
RETURN
    Result
```

Benefits:

- Easier to read
- Easier to debug
- Avoids repeating logic
- Makes intent clearer
- Can improve performance

## 6. Use DIVIDE

Prefer:

```DAX
Margin % =
DIVIDE ( [Gross Margin], [Total Sales] )
```

Instead of:

```DAX
Margin % =
[Gross Margin] / [Total Sales]
```

DIVIDE safely handles zero or blank denominator cases.

## Common DAX Patterns

## Base Measures

Use explicit base measures first.

```DAX
Total Sales =
SUM ( FactSales[Sales Amount] )

Total Cost =
SUM ( FactSales[Cost Amount] )

Gross Margin =
[Total Sales] - [Total Cost]

Gross Margin % =
DIVIDE ( [Gross Margin], [Total Sales] )
```

## Percent of Total

```DAX
Sales % of Total =
DIVIDE (
    [Total Sales],
    CALCULATE (
        [Total Sales],
        REMOVEFILTERS ( DimProduct )
    )
)
```

Explain which filters should remain and which should be removed.

## Year-over-Year

```DAX
Sales Prior Year =
CALCULATE (
    [Total Sales],
    SAMEPERIODLASTYEAR ( DimDate[Date] )
)

Sales YoY =
[Total Sales] - [Sales Prior Year]

Sales YoY % =
DIVIDE ( [Sales YoY], [Sales Prior Year] )
```

Confirm that DimDate is a proper Date table.

## Running Total

```DAX
Sales Running Total =
VAR MaxVisibleDate =
    MAX ( DimDate[Date] )
RETURN
    CALCULATE (
        [Total Sales],
        FILTER (
            ALLSELECTED ( DimDate[Date] ),
            DimDate[Date] <= MaxVisibleDate
        )
    )
```

Explain the difference between ALL and ALLSELECTED.

## Ranking

```DAX
Product Sales Rank =
RANKX (
    ALLSELECTED ( DimProduct[Product Name] ),
    [Total Sales],
    ,
    DESC,
    Dense
)
```

Clarify whether the rank should respect slicers.

## Wrong Total Fix Pattern

Use only when business logic requires summing results at a specific grain.

```DAX
Corrected Total =
SUMX (
    VALUES ( DimCustomer[CustomerKey] ),
    [Customer-Level Measure]
)
```

Explain that totals are recalculated in total filter context, not simply added from visible rows.

## Common Problems and Diagnosis

## Wrong Totals

Likely causes:

- Measure is correct at row level but not total level
- Missing iterator
- Wrong grain
- Model issue
- Many-to-many relationship
- Calculated column used instead of measure

Diagnosis steps:

1. Identify visual grain.
2. Identify business calculation grain.
3. Compare detail rows to total.
4. Test with VALUES at the correct grain.
5. Check relationships.

## Measure Ignores Slicer

Likely causes:

- Slicer table is disconnected
- Relationship is inactive
- Filter direction is wrong
- Measure removes filters using ALL or REMOVEFILTERS
- Slicer uses the wrong table

Diagnosis steps:

1. Check relationship path.
2. Check active/inactive relationship.
3. Check filter direction.
4. Look for ALL, REMOVEFILTERS, ALLEXCEPT.
5. Test with a simple COUNTROWS measure.

## Duplicate or Inflated Results

Likely causes:

- Duplicate keys in dimension
- Many-to-many relationship
- Fact-to-fact relationship
- Power Query merge duplicated rows
- Relationship at wrong grain

Diagnosis steps:

1. Count distinct keys in dimensions.
2. Compare fact row counts before/after merges.
3. Check relationship cardinality.
4. Test totals at lowest grain.
5. Consider bridge table or model redesign.

## Time Intelligence Does Not Work

Likely causes:

- No proper Date table
- Date table not marked as Date table
- Gaps in dates
- Relationship inactive
- Wrong date column used
- Date field from fact table used instead of DimDate

Diagnosis steps:

1. Confirm DimDate has continuous dates.
2. Confirm relationship to fact table.
3. Confirm visual uses DimDate fields.
4. Confirm measure uses DimDate[Date].
5. Check active relationship.

## Performance Notes

Watch for:

- Large FILTER over fact tables
- Excessive use of iterators over high-cardinality tables
- Complex nested CALCULATE logic
- Many calculated columns
- High-cardinality columns in visuals
- Bi-directional filters
- Many-to-many relationships
- Measures that repeat expensive subexpressions

Recommend:

- Use variables
- Filter dimensions rather than facts where possible
- Simplify the model
- Remove unused columns
- Use Performance Analyzer
- Consider DAX Studio for deeper investigation

## Standard Validation Steps

Always provide test cases.

Example validation table:

```text
Create a table visual with:
- DimDate[Year]
- DimProduct[Category]
- [Total Sales]
- [Corrected Measure]
```

Then verify:

1. Detail rows match expected values.
2. Totals match business logic.
3. Slicers change the measure correctly.
4. Blank or zero cases behave properly.
5. Prior-year or running-total logic works across date boundaries.

## Final Recommendation Style

If the DAX is complex because the model is weak, say so clearly.

Example:

```text
I can write DAX around this, but the better fix is to correct the model. The current relationship structure is forcing unnecessary DAX complexity and creates a real risk of wrong totals.
```
