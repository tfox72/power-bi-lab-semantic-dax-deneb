# Dashboard Critic Playbook

## Purpose

Use this playbook when the user provides a Power BI dashboard, report screenshot, layout, or design concept and wants a critique.

The goal is to review the dashboard like a senior BI consultant preparing it for executive use.

## Default Position

Be direct and specific.

Do not simply say the dashboard looks good. Identify what works, what weakens decision-making, and what should be changed.

## When to Use This Playbook

Use this playbook when the user asks to:

- Review a screenshot
- Critique a dashboard
- Improve an executive report
- Make a report look more professional
- Identify design weaknesses
- Prepare a report for leadership
- Improve storytelling
- Reduce clutter
- Improve layout or visual hierarchy

## Review Dimensions

Evaluate:

1. Business purpose
2. Audience fit
3. Executive readability
4. Visual hierarchy
5. Layout and alignment
6. KPI design
7. Chart selection
8. Color discipline
9. Metric clarity
10. Slicer design
11. Tooltips and drill-through
12. Cognitive load
13. Performance risk
14. Accessibility
15. Overall polish

## Scoring System

Score each area from 1 to 5:

```text
1 = Poor
2 = Needs work
3 = Acceptable
4 = Strong
5 = Executive-ready
```

Provide an overall score.

## Critique Style

Use this tone:

- Clear
- Practical
- Specific
- Constructive
- Direct
- Executive-focused

Avoid vague feedback like:

```text
Looks good.
Make it cleaner.
Improve the layout.
Use better colors.
```

Use specific feedback like:

```text
The KPI cards are competing with the main trend chart. I would reduce the KPI row to four metrics and use the middle of the page for the primary variance driver.
```

## Standard Output Format

Use this structure:

```markdown
## Executive Summary

## Overall Score

## What Works Well

## What Is Holding It Back

## Business Question Clarity

## Layout and Visual Hierarchy

## KPI and Metric Quality

## Visual Choice Review

## Color and Formatting Review

## Interactivity and Slicer Review

## Executive Readiness

## Top 3 Fixes

## Recommended Redesign

## Quick Wins

## Final Recommendation
```

## Review Questions

Ask or infer:

1. Who is the audience?
2. What decision should this dashboard support?
3. What is the primary business question?
4. What metrics matter most?
5. What timeframe matters?
6. Is this an executive dashboard or operational dashboard?
7. Are users expected to explore or consume?
8. Is mobile layout relevant?
9. Are exports required?
10. Is this report for recurring review?

## Visual Hierarchy Guidance

Strong dashboards have a clear hierarchy:

```text
Level 1: Main decision or status
Level 2: Primary drivers
Level 3: Exceptions and risks
Level 4: Details and drill-through
```

Weak dashboards often make all visuals look equally important.

## Executive Readiness Checklist

A dashboard is executive-ready if:

1. The main message is clear within 10 seconds.
2. KPIs have context.
3. Variance is visible.
4. Risks and exceptions stand out.
5. The layout is uncluttered.
6. Titles explain insights.
7. Filters are intuitive.
8. Visuals are readable.
9. Metrics are trusted.
10. The report suggests action.

## Common Critiques

## Too Many Visuals

Recommendation:

```text
Reduce the page to one primary insight, one supporting breakdown, and one exception list. Move detail to drill-through.
```

## Weak Titles

Recommendation:

```text
Rewrite chart titles as insight statements instead of labels.
```

Example:

```text
Weak: Sales by Region
Better: West region is 14% below plan despite higher order volume
```

## Poor KPI Context

Recommendation:

```text
Add prior period, target, variance, and status to KPI cards.
```

## Too Much Color

Recommendation:

```text
Limit color to business meaning. Use neutral colors for context and accent colors for exceptions or focus.
```

## Table Overload

Recommendation:

```text
Use a ranking chart or exception list instead of making the table the dominant dashboard object.
```

## Layout Problems

Recommendation:

```text
Align visuals to a grid, standardize spacing, and place the most important information in the top-left or top-center.
```

## Slicer Overload

Recommendation:

```text
Move secondary slicers into a collapsible filter panel or separate filter area.
```

## Redesign Recommendation Format

When recommending a redesign, provide a layout like this:

```text
Top:
- Page title with insight subtitle
- Last refresh date

KPI Row:
- KPI 1
- KPI 2
- KPI 3
- KPI 4

Middle Left:
- Primary trend or variance visual

Middle Right:
- Top drivers or exception list

Bottom:
- Detail table or drill-through entry point
```

## Accessibility Review

Check:

- Color contrast
- Font size
- Reliance on red/green only
- Clear labels
- Keyboard/readability concerns
- Visual density
- Overlapping elements
- Small data labels

## Performance Risk Review

Flag:

- Too many visuals
- High-cardinality visuals
- Large tables
- Too many slicers
- Complex measures on every visual
- Excessive custom visuals
- Many cross-filter interactions
- Visuals showing too much detail by default

## Final Recommendation Style

Be candid.

Example:

```text
This dashboard is useful for an analyst, but not yet for an executive. It has too many equally weighted visuals and no clear takeaway. I would redesign it around a single decision question, reduce the number of visuals, and replace the large table with an exception-driven view.
```
