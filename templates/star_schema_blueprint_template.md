# Star Schema Blueprint Template

## Business Purpose

Describe what the model needs to support.

```text
This model supports analysis of:
- 
- 
- 
```

## Business Questions

List the questions the model must answer.

1. 
2. 
3. 
4. 
5. 

## Source Data

| Source | Table/File | Description | Refresh Frequency | Notes |
|---|---|---|---|---|
|  |  |  |  |  |

## Source Columns

| Source Table | Column | Description | Keep? | Target Table | Notes |
|---|---|---|---|---|---|
|  |  |  | Yes/No |  |  |

## Recommended Model Overview

```text
Dimensions:
- DimDate
- DimCustomer
- DimProduct

Facts:
- FactSales
```

## Fact Tables

### Fact Table: `FactName`

Business process:

```text

```

Grain:

```text
One row per 
```

Columns:

| Column | Type | Purpose | Notes |
|---|---|---|---|
|  | Key | Foreign key |  |
|  | Numeric | Measure input |  |

Recommended measures:

| Measure | Definition |
|---|---|
|  |  |

## Dimension Tables

### Dimension Table: `DimName`

Purpose:

```text

```

Key:

```text
DimName[DimNameKey]
```

Attributes:

| Column | Purpose | Used In |
|---|---|---|
|  |  | Slicer / Axis / Tooltip |

## Date Table

Required date logic:

| Date Role | Fact Table Column | Active? | Notes |
|---|---|---|---|
| Order Date | FactSales[OrderDateKey] | Yes |  |
| Ship Date | FactSales[ShipDateKey] | No | Use USERELATIONSHIP |

Date table columns required:

- Date
- DateKey
- Year
- Quarter
- Month Number
- Month Name
- Year-Month
- Week
- Day
- Fiscal Year if needed
- Fiscal Period if needed

## Relationship Diagram

Use this format:

```text
DimDate[DateKey] 1 ──── * FactName[DateKey]
DimCustomer[CustomerKey] 1 ──── * FactName[CustomerKey]
DimProduct[ProductKey] 1 ──── * FactName[ProductKey]
```

## Relationship Table

| From Table | From Column | To Table | To Column | Cardinality | Filter Direction | Active |
|---|---|---|---|---|---|---|
| DimDate | DateKey | FactName | DateKey | 1:* | Single | Yes |

## Required Base Measures

```DAX
Total Amount =
SUM ( FactName[Amount] )
```

```DAX
Total Quantity =
SUM ( FactName[Quantity] )
```

## Required Analytical Measures

```DAX
Average Amount =
AVERAGE ( FactName[Amount] )
```

```DAX
Amount % of Total =
DIVIDE (
    [Total Amount],
    CALCULATE (
        [Total Amount],
        REMOVEFILTERS ( DimName )
    )
)
```

## Power Query / SQL Build Plan

1. Create staging queries.
2. Clean source data.
3. Remove unused columns.
4. Create dimension tables.
5. Remove duplicate dimension keys.
6. Create fact tables.
7. Create/assign keys.
8. Validate row counts.
9. Disable load for staging queries.
10. Load only final fact and dimension tables.

## Data Quality Checks

- [ ] Null keys handled.
- [ ] Duplicate dimension keys removed or resolved.
- [ ] Fact rows retain original row count.
- [ ] Numeric columns have correct data types.
- [ ] Date fields parse correctly.
- [ ] Totals reconcile to source.
- [ ] Unknown or missing dimension members handled.

## Risks and Assumptions

| Risk / Assumption | Impact | Mitigation |
|---|---|---|
|  |  |  |

## Implementation Steps

1. 
2. 
3. 
4. 
5. 

## Validation Checklist

- [ ] Model uses star schema.
- [ ] Fact table grain is documented.
- [ ] Dimension keys are unique.
- [ ] Relationships are one-to-many.
- [ ] Filter direction is single.
- [ ] Date table works.
- [ ] Measures return expected totals.
- [ ] Slicers filter visuals correctly.
- [ ] Report pages answer business questions.
