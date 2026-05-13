# Power BI Semantic Model Review Template

## Executive Summary

Summarize whether the model is strong, acceptable, or weak.

Include:

- Overall model quality
- Main risk
- Main recommendation
- Whether the model is ready for production use

## Business Objective

Describe the business questions this model is intended to answer.

Examples:

- Sales performance by customer, product, region, and time
- Budget vs actuals by department, account, and month
- Project cost tracking by vendor, project, and cost category
- Ticket resolution performance by team, priority, and date

## Current Model Interpretation

Explain what the current model appears to represent.

Include:

- Source systems or files
- Primary business process
- Current table structure
- Any assumptions being made

## Fact Tables

| Fact Table | Grain | Key Measures | Notes |
|---|---|---|---|
| FactExample | One row per ___ | Total ___ |  |

## Dimension Tables

| Dimension Table | Key | Important Attributes | Notes |
|---|---|---|---|
| DimExample | ExampleKey | Name, Category, Status |  |

## Grain Review

For each fact table, state:

```text
The grain of [Fact Table] is one row per [business event or snapshot].
```

Check:

- Is the grain clearly defined?
- Is the grain consistent within the table?
- Are multiple grains mixed together?
- Are facts being merged at incompatible grains?

## Relationship Review

| From Table | To Table | Cardinality | Filter Direction | Status | Notes |
|---|---|---|---|---|---|
| DimExample | FactExample | 1:* | Single | Active |  |

Review:

- One-to-many relationships
- Single-direction filters
- Active vs inactive relationships
- Many-to-many risks
- Bidirectional filter risks
- Fact-to-fact relationship risks

## Date Table Review

Check:

- Dedicated Date table exists
- Date table has continuous dates
- Date table is connected to facts
- Date table is used in visuals instead of fact date fields
- Multiple date roles are handled correctly
- Fiscal calendar requirements are addressed

## Star Schema Quality Score

Score from 1 to 10.

| Area | Score | Notes |
|---|---:|---|
| Fact/dimension separation |  |  |
| Grain clarity |  |  |
| Relationship design |  |  |
| Date table design |  |  |
| DAX readiness |  |  |
| Performance readiness |  |  |

## DAX Implications

Explain how the model affects:

- Measure complexity
- Filter context
- Total behavior
- Time intelligence
- Slicer behavior
- Percent of total calculations
- Budget vs actual comparisons

## Performance Risks

Review:

- High-cardinality columns
- Large text columns
- Unused columns
- Excessive calculated columns
- Many-to-many relationships
- Bidirectional filters
- Large table visuals
- Complex measures
- Query folding risks
- Refresh risks

## Recommended Model Design

Describe the improved model.

### Recommended Fact Tables

```text
FactTableName
- Grain:
- Keys:
- Numeric columns:
- Recommended measures:
```

### Recommended Dimension Tables

```text
DimTableName
- Key:
- Attributes:
- Used for:
```

## Suggested Relationship Diagram

Use this format:

```text
DimDate[DateKey] 1 ──── * FactSales[OrderDateKey]
DimCustomer[CustomerKey] 1 ──── * FactSales[CustomerKey]
DimProduct[ProductKey] 1 ──── * FactSales[ProductKey]
```

## Required Measures

| Measure | DAX Pattern | Notes |
|---|---|---|
| Total Sales | SUM | Base measure |
| Gross Margin % | DIVIDE | Ratio measure |
| Budget Variance | Difference | Actual minus budget |

## Power Query / SQL Transformation Plan

List recommended transformations:

1. Remove unused columns.
2. Create dimension tables.
3. Create fact tables.
4. Create stable keys.
5. Unpivot wide files if needed.
6. Validate row counts.
7. Disable load for staging queries.
8. Preserve query folding where important.

## Validation Checklist

- [ ] Fact table row counts reconcile to source.
- [ ] Dimension keys are unique.
- [ ] Relationships are correct.
- [ ] Filters flow from dimensions to facts.
- [ ] Date table works with time intelligence.
- [ ] Measures match source system totals.
- [ ] Slicers behave as expected.
- [ ] Totals behave correctly.
- [ ] Performance is acceptable.
- [ ] Model answers the intended business questions.

## Top 3 Priority Fixes

1. 
2. 
3. 

## Final Recommendation

Give a clear final recommendation.
