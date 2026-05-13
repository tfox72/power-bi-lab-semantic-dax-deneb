# Power BI Report Style Guide Playbook

## Purpose

Use this playbook when designing, reviewing, or improving Power BI report pages and dashboards.

The goal is to make reports:

- Executive-ready
- Visually polished
- Easy to understand
- Decision-focused
- Consistent
- Low clutter
- High signal-to-noise
- Aligned to business questions

## Default Position

Every report page should answer a clear business question.

Every visual should earn its place.

A report is not just a collection of charts. It is a decision-support product.

## When to Use This Playbook

Use this playbook when the user asks to:

- Improve report design
- Make a dashboard look professional
- Review a screenshot
- Choose visual types
- Build an executive dashboard
- Create a report layout
- Improve color, spacing, or hierarchy
- Reduce clutter
- Design KPI pages
- Create a report theme
- Polish a Power BI page before presenting it

## Core Design Principles

1. Start with the decision the report supports.
2. Use layout to guide the eye.
3. Put the most important information first.
4. Use fewer visuals with clearer meaning.
5. Use action-oriented titles.
6. Use consistent colors and spacing.
7. Avoid decorative clutter.
8. Make comparisons obvious.
9. Use tooltips and drill-through for detail.
10. Optimize for the audience, not the report builder.

## Executive Dashboard Layout

Recommended structure:

```text
Header:
- Page title
- Business question or subtitle
- Last refresh date

Top row:
- 3 to 5 KPI cards
- Each KPI should show value, variance, and status when useful

Middle:
- Primary trend, comparison, or driver visual

Right side:
- Ranking, exception list, or key breakdown

Bottom:
- Detail table, decomposition, notes, or drill-through entry point
```

## Page Title Standards

Weak title:

```text
Sales
```

Better title:

```text
Sales are 8% above plan, driven by Enterprise accounts
```

Weak title:

```text
Expenses by Department
```

Better title:

```text
Facilities and IT account for 62% of expense variance
```

Use titles that communicate the insight, not just the metric name.

## KPI Card Standards

Good KPI cards include:

- Current value
- Comparison value
- Variance
- Variance %
- Trend or status indicator when useful
- Clear label
- Consistent formatting

Avoid:

- Too many KPI cards
- KPI cards with no comparison
- Large numbers without context
- Mixed units without clear labels

Recommended KPI row:

```text
Revenue | Gross Margin % | Budget Variance | Open Risk Items | Forecast Accuracy
```

## Visual Selection Rules

Use line charts for:

- Trends over time
- Seasonality
- Movement across periods

Use bar charts for:

- Rankings
- Comparisons across categories
- Top/bottom analysis

Use matrices/tables for:

- Detail lookup
- Audit trails
- Operational review
- Export-style analysis

Use scatter plots for:

- Relationships between two measures
- Outlier detection
- Segmentation

Use maps only when:

- Geography is central to the analysis
- Location patterns matter

Use Deneb when:

- Native visuals cannot create the desired analytical pattern
- Custom polish or advanced layout is required
- A compact executive visual would improve communication

Avoid:

- Pie charts with many categories
- Donut charts used as decoration
- 3D visuals
- Excessive gauges
- Too many slicers
- Overloaded combo charts
- Tables used as dashboards

## Color Standards

Use restrained color.

Recommended approach:

- Neutral background
- Dark text
- One primary accent color
- One warning color
- One negative color
- One positive color
- Limited category colors

Rules:

1. Color must mean something.
2. Do not use rainbow palettes unless categories require it.
3. Red and green should be reserved for meaningful status.
4. Use muted colors for context and stronger colors for focus.
5. Maintain contrast and readability.

## Typography Standards

Use consistent hierarchy.

Recommended:

```text
Page title: largest
Section headers: medium
Visual titles: clear and readable
Axis labels: readable
Data labels: used selectively
Footnotes: small but legible
```

Avoid:

- Tiny axis labels
- Too many font sizes
- Decorative fonts
- Overuse of bold text
- Long titles that wrap awkwardly

## Spacing and Alignment

Rules:

1. Align visuals to a grid.
2. Use consistent margins.
3. Leave enough whitespace.
4. Group related items together.
5. Keep slicers in a consistent area.
6. Avoid visuals touching each other.
7. Use containers or backgrounds sparingly.
8. Make sections visually distinct.

## Slicer Standards

Slicers should be:

- Necessary
- Clear
- Grouped logically
- Consistent across pages
- Not overwhelming

Common slicers:

- Date
- Region
- Department
- Product Category
- Customer Segment
- Scenario

Avoid:

- Too many slicers on the main page
- Slicers that duplicate visual filters
- Slicers with unclear names
- Slicers that break the story

## Tooltip Standards

Use tooltips to provide detail without clutter.

Good tooltip content:

- Metric definition
- Current value
- Prior period value
- Variance
- Rank
- Trend
- Contextual notes

Avoid tooltips that simply repeat the visual.

## Drill-Through Standards

Use drill-through for:

- Detail views
- Transaction lists
- Customer/product/project details
- Root-cause analysis
- Operational follow-up

Do not cram all detail into the executive summary page.

## Report Review Rubric

Score each page from 1 to 5:

1. Business clarity
2. Visual hierarchy
3. Layout
4. Visual choice
5. Color discipline
6. Metric clarity
7. Slicer usability
8. Tooltip usefulness
9. Executive usefulness
10. Performance risk

Then provide:

- Overall score
- Top 3 fixes
- Quick wins
- Structural redesign suggestions
- Visual replacements
- Layout recommendation

## Standard Report Review Output

Use this format:

```markdown
## Executive Summary

## Overall Design Score

## What Works Well

## Main Issues

## Business Clarity

## Layout and Visual Hierarchy

## Visual Selection

## Color and Formatting

## Slicers and Interactivity

## Metric Clarity

## Performance and Usability Risks

## Top 3 Priority Fixes

## Recommended Page Layout

## Suggested Visual Changes

## Final Recommendation
```

## Common Report Problems

## Problem: Too Much on One Page

Fix:

- Move details to drill-through
- Use tooltips
- Split into summary and detail pages
- Reduce number of visuals
- Prioritize the main business question

## Problem: Visuals Lack Context

Fix:

- Add variance
- Add target
- Add prior period
- Add benchmark
- Add title that explains the insight

## Problem: Page Looks Unprofessional

Fix:

- Align to grid
- Reduce colors
- Improve spacing
- Use consistent fonts
- Remove borders
- Replace cluttered visuals
- Use a cleaner background

## Problem: Executive Cannot Tell What Matters

Fix:

- Rewrite titles as insights
- Add KPI status
- Highlight exceptions
- Use ranking visuals
- Add a decision-focused summary

## Final Recommendation Style

Be direct but constructive.

Example:

```text
The report has useful data, but it does not yet look executive-ready. The main issue is visual hierarchy: everything appears equally important. I would rebuild the page around one primary business question, a KPI row, one main driver visual, and a short exception list.
```
