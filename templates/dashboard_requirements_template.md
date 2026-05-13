# Power BI Dashboard Requirements Template

## Dashboard Name

```text

```

## Business Owner

```text

```

## Audience

Select all that apply:

- Executives
- Finance
- Operations
- Sales
- PMO
- Analysts
- Managers
- External stakeholders
- Other

## Dashboard Objective

Describe the purpose:

```text
The dashboard is intended to help users:
```

## Decisions Supported

List decisions the dashboard should support:

1. 
2. 
3. 

## Key Business Questions

1. 
2. 
3. 
4. 
5. 

## Success Criteria

The dashboard is successful if:

- [ ] 
- [ ] 
- [ ] 

## KPIs

| KPI | Definition | Target / Benchmark | Source | Notes |
|---|---|---|---|---|
|  |  |  |  |  |

## Dimensions / Slicers

| Dimension | Example Values | Required? | Notes |
|---|---|---|---|
| Date | Year, Quarter, Month | Yes |  |
| Region |  |  |  |
| Department |  |  |  |
| Product |  |  |  |

## Source Data

| Source | Type | Owner | Refresh Frequency | Notes |
|---|---|---|---|---|
|  | Excel / SQL / SharePoint / API / Other |  |  |  |

## Security Requirements

- [ ] No row-level security required.
- [ ] Row-level security required.
- [ ] Users should only see their department.
- [ ] Users should only see their region.
- [ ] Sensitive data exists.
- [ ] External sharing required.

Details:

```text

```

## Refresh Requirements

| Requirement | Details |
|---|---|
| Refresh frequency |  |
| Gateway required |  |
| Incremental refresh needed |  |
| Data latency tolerance |  |
| Refresh owner |  |

## Report Pages

| Page | Purpose | Audience | Notes |
|---|---|---|---|
| Executive Summary | High-level status | Executives |  |
| Detail Analysis | Deeper exploration | Analysts/Managers |  |

## Recommended Visuals

| Page | Visual | Purpose |
|---|---|---|
| Executive Summary | KPI cards | Headline metrics |
| Executive Summary | Trend chart | Performance over time |
| Executive Summary | Ranking bar chart | Top drivers |
| Detail | Matrix | Detailed review |

## Semantic Model Notes

Recommended model type:

```text
Star schema with shared dimensions and one or more fact tables.
```

Potential fact tables:

- 

Potential dimension tables:

- 

## Required Measures

| Measure | Definition | Notes |
|---|---|---|
|  |  |  |

## Design Style

Preferred style:

- [ ] Executive / minimal
- [ ] Operational / dense
- [ ] Financial / precise
- [ ] Modern corporate
- [ ] Dark theme
- [ ] Light theme
- [ ] Brand-aligned

Notes:

```text

```

## Risks and Open Questions

| Risk / Question | Owner | Needed By |
|---|---|---|
|  |  |  |

## Build Plan

1. Confirm requirements.
2. Inspect source data.
3. Design star schema.
4. Build Power Query transformations.
5. Build semantic model.
6. Create base measures.
7. Create report pages.
8. Validate data.
9. Polish design.
10. Publish to Power BI Service.
11. Configure refresh/security.
12. Review with stakeholders.
