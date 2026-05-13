# Power BI Dashboard Requirements Brief
## Project Cost Tracking — Budget, Forecast & Actuals

---

## Dashboard Objective

Provide executive leadership with a single-page portfolio view of project cost health — showing Budget vs Actuals, Forecast vs Budget, and Estimate at Completion (EAC) — with RAG status flagging to surface at-risk projects before month-end.

---

## Target Audience

Executive leadership (C-suite / VP level). Viewers need fast signal, not detail. The dashboard must be scannable in under 60 seconds with clear traffic-light indicators for portfolio health.

---

## Decisions Supported

- Which projects are tracking over budget or off forecast and need intervention?
- Is the portfolio as a whole within budget?
- Where is cost pressure concentrated — by department or cost type?
- Does the current forecast indicate a problem at completion?

---

## Key Business Questions

1. How does current spend compare to budget across the portfolio?
2. Which projects are Red (at risk), Amber (watch), or Green (on track)?
3. Where is the biggest gap between forecast and budget?
4. What is the estimated cost at completion vs original budget?
5. Which departments or cost types are driving overruns?

---

## Required KPIs

| KPI | Definition |
|---|---|
| Budget vs Actuals | Total approved budget minus total actual costs to date |
| Forecast vs Budget | Latest forecast (EAC) compared to original or revised budget |
| Cost at Completion (EAC) | Projected total cost of each project at completion |
| % Budget Consumed | Actuals to date ÷ Total Budget |
| Variance $ | Budget minus Actuals (positive = under, negative = over) |
| Variance % | Variance $ ÷ Budget |
| RAG Status | Derived: Green ≤ 5% over, Amber 5–15% over, Red > 15% over (thresholds TBC with stakeholders) |

---

## Required Dimensions / Slicers

| Dimension | Purpose |
|---|---|
| Project / Project Code | Filter to a specific project or compare across projects |
| Department / Cost Center | Group and filter by owning business unit |
| Cost Type / Category | Break costs into labor, materials, contractors, overhead, etc. |
| Time Period (Month / Quarter / Year) | Filter by fiscal or calendar period |

---

## Source Data

**System:** ERP (SAP, Oracle, or equivalent)

Likely required extracts:

| Extract | Key Fields |
|---|---|
| Project master | Project ID, Project Name, Department, Status, Start/End Date, Approved Budget |
| Actuals | Project ID, Cost Type, Posting Date, Amount |
| Forecast / EAC | Project ID, Cost Type, Forecast Period, Forecast Amount |
| Budget | Project ID, Cost Type, Budget Period, Budget Amount |
| Cost center / department | Cost Center ID, Department Name, Owner |

---

## Recommended Semantic Model

**Pattern:** Star schema — single grain per fact table.

### Fact Tables

| Table | Grain | Key Columns |
|---|---|---|
| FactActuals | One row per project, cost type, posting period | ProjectKey, CostTypeKey, DateKey, ActualAmount |
| FactBudget | One row per project, cost type, budget period | ProjectKey, CostTypeKey, DateKey, BudgetAmount |
| FactForecast | One row per project, cost type, forecast period | ProjectKey, CostTypeKey, DateKey, ForecastAmount |

> **Modeling note:** Three separate fact tables at the same grain (project + cost type + period) is the clean SQLBI-recommended pattern for budget/actuals/forecast. Do NOT union these into one table with a "Type" column — that creates ambiguous aggregations and makes DAX significantly harder to write correctly.

### Dimension Tables

| Table | Key Columns |
|---|---|
| DimProject | ProjectKey, ProjectCode, ProjectName, DepartmentKey, Status, StartDate, EndDate |
| DimDate | DateKey, Date, Month, MonthName, Quarter, Year, FiscalPeriod |
| DimCostType | CostTypeKey, CostCategory, CostSubcategory (Labor, Materials, Contractors, etc.) |
| DimDepartment | DepartmentKey, DepartmentName, CostCenter, Owner |

### Relationships

- DimProject → FactActuals (1:M, ProjectKey)
- DimProject → FactBudget (1:M, ProjectKey)
- DimProject → FactForecast (1:M, ProjectKey)
- DimDate → FactActuals (1:M, DateKey) — active
- DimDate → FactBudget (1:M, DateKey) — active
- DimDate → FactForecast (1:M, DateKey) — active
- DimCostType → all three facts (1:M, CostTypeKey)
- DimDepartment → DimProject (1:M, DepartmentKey)

All relationships: single-direction filtering. No bidirectional unless a specific cross-filter need is identified.

---

## Required Measures

```dax
-- Base measures
Total Budget = SUM( FactBudget[BudgetAmount] )
Total Actuals = SUM( FactActuals[ActualAmount] )
Total Forecast (EAC) = SUM( FactForecast[ForecastAmount] )

-- Variance measures
Budget Variance $ = [Total Budget] - [Total Actuals]
Budget Variance % = DIVIDE( [Budget Variance $], [Total Budget] )
Forecast Variance $ = [Total Budget] - [Total Forecast (EAC)]
Forecast Variance % = DIVIDE( [Forecast Variance $], [Total Budget] )
% Budget Consumed = DIVIDE( [Total Actuals], [Total Budget] )

-- RAG Status (project-level)
RAG Status =
VAR _VariancePct = [Budget Variance %]
RETURN
    SWITCH(
        TRUE(),
        _VariancePct < -0.15, "Red",
        _VariancePct < -0.05, "Amber",
        "Green"
    )

-- RAG counts (for portfolio summary)
Red Project Count =
CALCULATE( DISTINCTCOUNT( DimProject[ProjectKey] ), [RAG Status] = "Red" )
Amber Project Count =
CALCULATE( DISTINCTCOUNT( DimProject[ProjectKey] ), [RAG Status] = "Amber" )
Green Project Count =
CALCULATE( DISTINCTCOUNT( DimProject[ProjectKey] ), [RAG Status] = "Green" )
```

> RAG thresholds (±5% / ±15%) should be confirmed with stakeholders before finalizing.

---

## Suggested Pages

### Page 1: Portfolio Summary (Primary executive page)
The only page leadership needs. Everything else is drill-through.

### Page 2: Project Detail (Drill-through)
Accessible by right-clicking a project row on Page 1. Shows cost breakdown by cost type and period for a single project. Not a main navigation page.

---

## Suggested Visuals — Page 1: Portfolio Summary

**Layout: Top → Center → Bottom**

| Zone | Visual | Purpose |
|---|---|---|
| Top bar | 4 KPI cards | Total Budget / Total Actuals / Total EAC / Portfolio Variance % |
| Top right | 3 RAG count cards | Red / Amber / Green project counts |
| Center left | Clustered bar chart | Budget vs Actuals vs Forecast by Project (sorted by variance desc) |
| Center right | Matrix / table | Project list with RAG icon, Budget, Actuals, EAC, Variance %, % Consumed |
| Bottom left | Stacked bar | Actuals by Cost Type (Labor, Materials, etc.) |
| Bottom right | Trend line | Monthly actual spend vs budget over selected period |
| Slicers (top) | Department, Cost Type, Time Period | Filter bar across top of page |

> RAG icon in the matrix should use conditional formatting (background color) — Red / Amber / Green fills on the Variance % column. Keep it simple: no custom icons needed for an executive view.

---

## Refresh / Service Requirements

| Item | Recommendation |
|---|---|
| Refresh frequency | Daily scheduled refresh (minimum); weekly may be acceptable for exec use |
| Source connection | ERP direct connector or scheduled export to SharePoint/SQL staging layer |
| Service delivery | Publish to Power BI Service workspace; share via App or direct workspace access |
| Alerts | Consider Data Alerts on Red project count KPI card |

---

## Security / RLS Requirements

No RLS required — all executives see the full portfolio. If this changes (e.g., regional leaders added later), RLS by DimDepartment[Owner] is straightforward to add.

---

## Design Style

| Element | Recommendation |
|---|---|
| Background | Light neutral (#F5F5F5 or white) |
| Font | Segoe UI, consistent sizing (Title: 18pt, Section: 12pt, Body: 10pt) |
| Color palette | Green (#107C10), Amber (#FF8C00), Red (#D13438) for RAG; neutral blue (#0078D4) for chart bars |
| KPI cards | No borders; large metric, small label below |
| Grid lines | Remove from all charts; use white space instead |
| Page title | "Project Portfolio — Cost Health" with period label |
| No pie charts | Use bar charts for category comparison |

---

## Risks and Open Questions

| Risk / Question | Action Required |
|---|---|
| RAG thresholds not confirmed | Agree ±5% / ±15% cutoffs with finance before build |
| ERP extract format unknown | Confirm whether data comes as direct connector, scheduled CSV, or staging DB |
| Budget versions (original vs revised) | Clarify whether "Budget" means original approved or latest revised budget |
| Forecast update frequency | Who updates the forecast, and how often? Manual entry or system-generated? |
| Fiscal vs calendar year | Confirm whether DimDate should use fiscal periods |
| Project status definition | What counts as "active" vs "closed" — should closed projects appear? |

---

## Build Plan

**Phase 1 — Data & Model (Week 1–2)**
- [ ] Extract and profile ERP data (actuals, budget, forecast, project master)
- [ ] Build Power Query transformations for each source
- [ ] Build star schema: 3 fact tables + 4 dimension tables
- [ ] Create DimDate with fiscal period support
- [ ] Validate relationships and grain

**Phase 2 — Measures (Week 2)**
- [ ] Build all base and variance measures
- [ ] Build RAG Status measure
- [ ] Validate measures against known data in ERP

**Phase 3 — Report Build (Week 3)**
- [ ] Build Page 1: Portfolio Summary
- [ ] Build Page 2: Project Detail (drill-through)
- [ ] Apply conditional formatting for RAG
- [ ] Apply design standards

**Phase 4 — Review & Deploy (Week 4)**
- [ ] Stakeholder review with sample data
- [ ] Confirm RAG thresholds
- [ ] Publish to Power BI Service
- [ ] Schedule refresh
- [ ] Deliver to executive audience

