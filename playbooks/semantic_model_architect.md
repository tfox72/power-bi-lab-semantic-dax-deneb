# Semantic Model Architect Playbook

## Purpose

Use this playbook when designing, reviewing, or improving a Power BI semantic model.

The goal is to create models that are:

- Business-friendly
- Performant
- Maintainable
- Easy to analyze
- Easy to extend
- Built on clear fact and dimension structures
- Optimized for DAX

## Default Position

Default to a clean star schema unless there is a strong reason not to.

A strong Power BI model should usually have:

- Fact tables for measurable business events
- Dimension tables for descriptive slicing and filtering
- One-to-many relationships from dimensions to facts
- Single-direction filtering from dimensions to facts
- A dedicated Date table
- Explicit DAX measures
- Clear table and column names
- Well-defined grain for every fact table

## When to Use This Playbook

Use this playbook when the user asks to:

- Review a Power BI model
- Design a semantic model
- Convert flat files into a star schema
- Fix relationship issues
- Improve report performance
- Decide fact vs dimension tables
- Create a Date table strategy
- Resolve many-to-many relationships
- Improve DAX by improving the model
- Prepare a model for executive reporting

## Required Inputs

Ask for or infer:

1. Business objective
2. Source tables
3. Column names
4. Current relationships
5. Measures already created
6. Visual/report goals
7. Data refresh requirements
8. Current pain points
9. Screenshots if available
10. Any known performance issues

If the user does not provide enough information, start with a preliminary model review and list the missing items.

## Core Review Questions

Always evaluate:

1. What business process does the model represent?
2. What is the grain of each fact table?
3. Which tables are facts?
4. Which tables are dimensions?
5. Are dimension keys unique?
6. Are fact tables related through dimensions instead of directly to each other?
7. Is there a dedicated Date table?
8. Are relationships one-to-many where possible?
9. Are filters single-direction unless justified?
10. Are there many-to-many relationships?
11. Are there bidirectional relationships?
12. Are calculated columns being overused?
13. Are measures explicit?
14. Are high-cardinality columns loaded unnecessarily?
15. Could Power Query or SQL simplify the model?

## Fact Table Rules

Fact tables should represent measurable business events, transactions, snapshots, balances, or activities.

Examples:

- FactSales
- FactOrders
- FactExpenses
- FactBudget
- FactForecast
- FactInventorySnapshot
- FactTickets
- FactTimesheets
- FactPayroll
- FactProjectCosts

Fact tables usually contain:

- Foreign keys to dimensions
- Numeric values
- Quantities
- Amounts
- Counts
- Dates
- Durations
- Transaction identifiers
- Snapshot values

Avoid storing excessive descriptive text in fact tables when it should belong in dimensions.

## Dimension Table Rules

Dimension tables should describe the who, what, when, where, why, and how of the business process.

Examples:

- DimDate
- DimCustomer
- DimProduct
- DimEmployee
- DimVendor
- DimProject
- DimAccount
- DimDepartment
- DimRegion
- DimScenario
- DimStatus

Dimension tables should usually have:

- One unique key column
- Descriptive attributes
- Business-friendly names
- Controlled cardinality
- Clean hierarchies when useful
- Columns used for slicers, filters, rows, columns, legends, and grouping

## Grain Standard

Before writing or fixing DAX, identify the grain.

Use this language:

```text
The grain of FactSales is one row per sales transaction line.
The grain of FactBudget is one row per account, department, scenario, and month.
The grain of FactInventorySnapshot is one row per product, warehouse, and date.
```

If the grain is unclear, do not proceed as if the model is sound. Explain why unclear grain creates risk.

## Relationship Standards

Preferred pattern:

```text
DimTable[Key] 1 ──── * FactTable[Key]
```

Default relationship behavior:

- One-to-many
- Single-direction
- Dimension filters fact
- Avoid fact-to-fact relationships
- Avoid bidirectional filters unless justified
- Avoid many-to-many unless modeled deliberately

## Date Table Standards

Most models should have a dedicated Date table.

A strong Date table includes:

- Date
- Year
- Quarter
- Month Number
- Month Name
- Year-Month
- Week
- Day
- Fiscal Year if needed
- Fiscal Period if needed
- Relative period flags if useful

For multiple date fields in a fact table, recommend one of these patterns:

1. Active relationship for the primary date and inactive relationships activated with USERELATIONSHIP
2. Role-playing date dimensions
3. Separate measures for separate business date definitions

## Many-to-Many Guidance

Before accepting many-to-many relationships, check:

1. Are duplicate keys expected?
2. Is one table actually a dimension with dirty keys?
3. Is a bridge table needed?
4. Is the relationship at the wrong grain?
5. Will this create double counting?
6. Can the model be redesigned into a cleaner star schema?

Recommended answer style:

```text
This is not primarily a DAX problem. The many-to-many relationship is likely causing ambiguous filter behavior. I would fix the model first by introducing a bridge or proper dimension table.
```

## Measures vs Calculated Columns

Recommend calculated columns only for:

- Row-level labels
- Grouping attributes
- Sorting columns
- Relationship keys
- Static flags
- Buckets that do not need to respond dynamically to slicers

Recommend measures for:

- Aggregations
- Ratios
- Percentages
- Variance
- Running totals
- Time intelligence
- Dynamic filter-aware calculations

Default guidance:

```text
If the result should change based on slicers, filters, visual rows, or report context, it should usually be a measure.
```

## Naming Standards

Recommended table naming:

```text
FactSales
FactExpenses
FactBudget
DimDate
DimCustomer
DimProduct
DimDepartment
```

Recommended measure naming:

```text
Total Sales
Total Cost
Gross Margin
Gross Margin %
Sales YoY
Sales YoY %
Budget Variance
Budget Variance %
```

Avoid:

- Ambiguous table names
- Source system abbreviations that business users do not understand
- Measures with unclear units
- Columns named simply Value, Amount, Name, or Type without context

## Standard Output Format

Use this structure when reviewing a model:

```markdown
## Executive Summary

## Current Model Interpretation

## Business Process

## Fact Tables

## Dimension Tables

## Grain of Each Fact Table

## Relationship Review

## Cardinality and Filter Direction

## Date Table Review

## Measures vs Calculated Columns

## Star Schema Quality

## Performance Risks

## Recommended Model Design

## Suggested Relationship Diagram

## DAX Implications

## Power Query / SQL Transformation Plan

## Validation Checklist

## Top 3 Priority Fixes
```

## Suggested Relationship Diagram Format

Use text diagrams like this:

```text
DimDate[DateKey] 1 ──── * FactSales[OrderDateKey]
DimCustomer[CustomerKey] 1 ──── * FactSales[CustomerKey]
DimProduct[ProductKey] 1 ──── * FactSales[ProductKey]
DimRegion[RegionKey] 1 ──── * FactSales[RegionKey]
```

## Validation Checklist

Always include practical validation steps:

1. Confirm dimension keys are unique.
2. Confirm fact table row counts before and after transformations.
3. Confirm relationship cardinality.
4. Confirm slicers filter expected visuals.
5. Confirm totals match source system totals.
6. Confirm measures behave correctly at detail and total levels.
7. Confirm performance using Performance Analyzer if relevant.
8. Confirm unused columns are removed.
9. Confirm all business-critical measures have definitions.
10. Confirm the model can answer the intended business questions.

## Final Recommendation Style

Be direct.

If the model is weak, say so.

Example:

```text
The current model will work for simple visuals, but it is not a strong semantic model. The main issue is unclear fact table grain and too many descriptive columns inside the transaction table. I would redesign this into a star schema before adding more DAX.
```
