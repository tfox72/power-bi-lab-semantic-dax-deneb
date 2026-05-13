# Executive Dashboard Layout Template

## Dashboard Name

```text
[Dashboard Name]
```

## Audience

```text
Executives / PMO / Finance / Operations / Sales / Leadership / Board / Other
```

## Business Question

```text
What decision or business question does this dashboard support?
```

## Page Structure

```text
Header
KPI Row
Primary Insight Section
Driver / Breakdown Section
Exception / Risk Section
Detail / Drill-Through Section
```

## Header

Recommended elements:

- Dashboard title
- Insight subtitle
- Reporting period
- Last refresh date
- Optional owner/contact

Example:

```text
Revenue Performance Dashboard
QTD revenue is 8% above plan, driven by Enterprise growth
Last refreshed: [Date/Time]
```

## KPI Row

Use 3 to 5 KPI cards.

| KPI | Current Value | Comparison | Variance | Status |
|---|---:|---:|---:|---|
| Revenue |  | Plan / Prior |  |  |
| Gross Margin % |  | Plan / Prior |  |  |
| Budget Variance |  | Budget |  |  |
| Forecast Accuracy |  | Target |  |  |
| Open Risks |  | Prior |  |  |

KPI card design notes:

- Large current value
- Smaller variance
- Clear label
- Consistent formatting
- Status indicator if needed
- Avoid too many colors

## Primary Insight Section

Purpose:

```text
Show the most important trend, variance, or performance driver.
```

Recommended visual options:

- Line chart
- Bar chart
- Combo chart if necessary
- Waterfall chart
- Deneb custom variance visual
- Small multiples for segment comparison

Visual title format:

```text
[Metric] is [up/down/above/below] [comparison] because of [driver]
```

Example:

```text
Revenue is 8% above plan, driven by Enterprise accounts
```

## Driver / Breakdown Section

Purpose:

```text
Explain what is driving the KPI result.
```

Recommended visual options:

- Ranked bar chart
- Decomposition tree
- Matrix with conditional formatting
- Deneb dumbbell chart
- Deneb slope chart
- Top/bottom exception chart

Common breakdowns:

- Region
- Product
- Customer
- Department
- Vendor
- Project
- Account
- Segment

## Exception / Risk Section

Purpose:

```text
Show where attention is required.
```

Recommended visuals:

- Exception list
- Top risks table
- Over-budget items
- Underperforming categories
- Delayed projects
- Forecast misses
- Outlier scatter plot

Recommended columns:

| Item | Metric | Variance | Owner | Status | Action |
|---|---:|---:|---|---|---|

## Detail / Drill-Through Section

Purpose:

```text
Provide path to detail without overcrowding the main page.
```

Options:

- Small detail table
- Drill-through button
- Tooltip page
- Linked detail page
- Bookmark navigation

Avoid making a detailed table the largest visual on an executive page.

## Slicer / Filter Area

Recommended slicers:

- Date period
- Region
- Department
- Product category
- Scenario
- Business unit

Design rules:

- Put slicers in a consistent location.
- Use a filter panel if there are many slicers.
- Avoid slicers that are rarely used.
- Use default selections carefully.
- Ensure slicers do not break the main story.

## Suggested Wireframe

```text
┌──────────────────────────────────────────────────────────────┐
│ Title: Executive Dashboard                                   │
│ Subtitle / Business Question                    Refresh Date │
├──────────────┬──────────────┬──────────────┬────────────────┤
│ KPI 1        │ KPI 2        │ KPI 3        │ KPI 4          │
├─────────────────────────────────────┬────────────────────────┤
│ Primary Trend / Variance Visual     │ Top Drivers / Ranking  │
│                                     │                        │
├─────────────────────────────────────┼────────────────────────┤
│ Exception / Risk List               │ Slicers / Notes        │
│                                     │                        │
└─────────────────────────────────────┴────────────────────────┘
```

## Visual Standards

- Use clear titles.
- Use consistent spacing.
- Use muted background.
- Use strong contrast for important numbers.
- Avoid unnecessary borders.
- Avoid visual clutter.
- Avoid too many colors.
- Use tooltips for extra detail.
- Use drill-through for transaction-level data.

## Metric Definition Section

Document key metrics:

| Metric | Definition | Source | Notes |
|---|---|---|---|
| Revenue |  |  |  |
| Gross Margin % |  |  |  |
| Budget Variance |  |  |  |

## Success Criteria

- [ ] Executive can understand status in 10 seconds.
- [ ] Main driver is visible.
- [ ] Exceptions are clear.
- [ ] KPIs include context.
- [ ] Layout is clean.
- [ ] Report performance is acceptable.
- [ ] Detail is available but not overwhelming.
- [ ] Report supports a real decision.

## Build Checklist

1. Define business question.
2. Define KPIs.
3. Confirm data model.
4. Create base measures.
5. Build KPI row.
6. Build primary insight visual.
7. Build driver visual.
8. Build exception list.
9. Add slicers.
10. Add tooltips/drill-through.
11. Polish formatting.
12. Validate performance.
13. Review with stakeholders.
