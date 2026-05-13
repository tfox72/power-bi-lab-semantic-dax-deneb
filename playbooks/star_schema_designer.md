# Star Schema Designer Playbook

## Purpose

Use this playbook to convert business requirements, flat files, exports, transactional tables, or messy source data into a clean Power BI star schema.

The goal is to design models that are:

- Simple to understand
- Easy to slice and filter
- Reliable for reporting
- Efficient for DAX
- Scalable for future reports
- Aligned to business processes

## Default Position

For Power BI semantic models, prefer star schema.

A star schema separates data into:

- Fact tables: numeric business events or snapshots
- Dimension tables: descriptive entities used to filter and group facts

## When to Use This Playbook

Use this playbook when the user asks to:

- Create a data model from raw data
- Convert Excel exports into a Power BI model
- Design fact and dimension tables
- Normalize or restructure source tables
- Build a reporting model from SQL tables
- Create a Power BI model from multiple systems
- Fix a flat table model
- Identify fact table grain
- Decide whether something is a fact or dimension
- Design a model for a dashboard

## Required Inputs

Ask for or infer:

1. Business process being analyzed
2. Business questions the report must answer
3. Source tables or files
4. Column names
5. Known keys
6. Dates involved
7. Measures needed
8. Slicers and grouping fields needed
9. Refresh frequency
10. Current reporting pain points

## Star Schema Design Process

Follow this sequence:

1. Define business questions.
2. Identify the business process.
3. Identify facts.
4. Define the grain of each fact table.
5. Identify dimensions.
6. Define keys.
7. Create relationship plan.
8. Identify required measures.
9. Identify required transformations.
10. Validate against business questions.

## Step 1: Business Questions

Start with the report purpose.

Examples:

```text
Which products are driving sales growth?
Which departments are over budget?
Which projects are at risk?
Which vendors are causing delays?
Which customers are most profitable?
How are actuals tracking against forecast?
```

The model should be designed to answer these questions cleanly.

## Step 2: Identify the Business Process

Examples:

- Sales transactions
- Budget planning
- Expense tracking
- Inventory snapshots
- Project delivery
- Support tickets
- Payroll
- Procurement
- Forecasting
- Customer activity

Each major business process often becomes one fact table.

## Step 3: Define Fact Tables

Fact tables should contain measurable events.

Examples:

```text
FactSales
FactExpenses
FactBudget
FactForecast
FactInventorySnapshot
FactProjectCosts
FactTickets
FactTimesheets
```

Fact table columns often include:

- Foreign keys to dimensions
- Amount
- Quantity
- Count
- Duration
- Balance
- Cost
- Revenue
- Transaction date key
- Snapshot date key

## Step 4: Define Grain

Every fact table must have a grain statement.

Examples:

```text
FactSales grain:
One row per sales transaction line.

FactBudget grain:
One row per department, account, scenario, and month.

FactInventorySnapshot grain:
One row per product, warehouse, and snapshot date.

FactProjectCost grain:
One row per project, vendor, cost category, and invoice line.
```

If two facts have different grains, do not blindly merge them into one table.

## Step 5: Identify Dimension Tables

Dimension tables provide descriptive context.

Common dimensions:

```text
DimDate
DimCustomer
DimProduct
DimEmployee
DimVendor
DimProject
DimAccount
DimDepartment
DimRegion
DimScenario
DimStatus
DimCategory
```

Dimension table columns often include:

- Key
- Name
- Category
- Type
- Segment
- Region
- Owner
- Status
- Hierarchy fields
- Sort fields

## Step 6: Define Keys

Use stable keys wherever possible.

Preferred keys:

- Surrogate keys from warehouse
- Business keys if stable and unique
- Composite keys only when necessary
- Generated keys in Power Query if needed

Rules:

- Dimension keys must be unique.
- Fact keys can repeat.
- Relationships should connect dimension keys to fact foreign keys.
- Avoid relationships on descriptive names when proper keys exist.

## Step 7: Relationship Plan

Default pattern:

```text
DimDate[DateKey] 1 ──── * FactSales[DateKey]
DimCustomer[CustomerKey] 1 ──── * FactSales[CustomerKey]
DimProduct[ProductKey] 1 ──── * FactSales[ProductKey]
```

Rules:

- Use one-to-many relationships.
- Use single-direction filtering.
- Avoid direct fact-to-fact relationships.
- Avoid many-to-many unless deliberate.
- Avoid bidirectional filtering as a shortcut.

## Step 8: Required Measures

After the schema is defined, identify measures.

Examples:

```DAX
Total Sales =
SUM ( FactSales[Sales Amount] )

Total Cost =
SUM ( FactSales[Cost Amount] )

Gross Margin =
[Total Sales] - [Total Cost]

Gross Margin % =
DIVIDE ( [Gross Margin], [Total Sales] )

Budget Variance =
[Actual Amount] - [Budget Amount]

Budget Variance % =
DIVIDE ( [Budget Variance], [Budget Amount] )
```

## Common Design Patterns

## Sales Model

```text
DimDate
DimCustomer
DimProduct
DimRegion
DimSalesperson
DimChannel

FactSales
```

Relationships:

```text
DimDate[DateKey] 1 ──── * FactSales[OrderDateKey]
DimCustomer[CustomerKey] 1 ──── * FactSales[CustomerKey]
DimProduct[ProductKey] 1 ──── * FactSales[ProductKey]
DimRegion[RegionKey] 1 ──── * FactSales[RegionKey]
DimSalesperson[SalespersonKey] 1 ──── * FactSales[SalespersonKey]
DimChannel[ChannelKey] 1 ──── * FactSales[ChannelKey]
```

## Budget vs Actual Model

```text
DimDate
DimAccount
DimDepartment
DimScenario
DimCostCenter

FactActuals
FactBudget
```

Important:

- FactActuals and FactBudget usually have different grain.
- Do not merge them unless the grain is aligned.
- Use shared dimensions to compare them.

## Project Cost Model

```text
DimDate
DimProject
DimVendor
DimCostCategory
DimDepartment
DimStatus

FactProjectCosts
FactBudget
FactForecast
```

## Inventory Snapshot Model

```text
DimDate
DimProduct
DimWarehouse
DimSupplier

FactInventorySnapshot
```

Important:

Snapshot facts are not the same as transaction facts.

## Flat File Conversion Rules

When converting one large flat file into a star schema:

1. Identify repeated descriptive attributes.
2. Move them to dimension tables.
3. Keep numeric transaction values in the fact table.
4. Create keys.
5. Remove duplicate dimension rows.
6. Validate fact row count remains stable.
7. Validate totals match original file.

Example flat file columns:

```text
OrderID
OrderDate
CustomerName
CustomerSegment
ProductName
ProductCategory
Region
SalesAmount
Quantity
CostAmount
```

Recommended model:

```text
FactSales:
OrderID
OrderDateKey
CustomerKey
ProductKey
RegionKey
SalesAmount
Quantity
CostAmount

DimCustomer:
CustomerKey
CustomerName
CustomerSegment

DimProduct:
ProductKey
ProductName
ProductCategory

DimRegion:
RegionKey
Region

DimDate:
DateKey
Date
Year
Month
Quarter
```

## Anti-Patterns

Avoid:

- One giant table for complex reporting
- Direct fact-to-fact relationships
- Many-to-many without bridge logic
- Bidirectional filters used casually
- Dimensions with duplicate keys
- Fact tables with too many descriptive columns
- Measures hidden inside calculated columns
- Multiple unrelated date columns without role strategy
- Merging facts at different grains
- Using names instead of keys for relationships

## Output Format

When designing a star schema, use:

```markdown
## Business Questions

## Source Data Summary

## Recommended Model

## Fact Tables

## Dimension Tables

## Grain Statements

## Relationship Diagram

## Required Measures

## Power Query / SQL Transformation Plan

## Risks and Assumptions

## Validation Checklist

## Implementation Steps
```

## Validation Checklist

1. Fact table row counts match source after transformation.
2. Dimension keys are unique.
3. Relationships are one-to-many.
4. Filters flow from dimensions to facts.
5. Totals match source system.
6. Slicers behave correctly.
7. Measures return expected results at detail and total level.
8. Date logic uses DimDate.
9. Model answers the original business questions.
10. Unused columns are removed.

## Final Recommendation Style

Be decisive.

Example:

```text
This should be modeled as two fact tables, not one merged table, because actuals and budget are at different grains. Use shared dimensions for Date, Department, Account, and Scenario so the measures can compare them cleanly.
```
