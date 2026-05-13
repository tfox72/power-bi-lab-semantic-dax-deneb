# Deneb Visual Builder Playbook

## Purpose

Use this playbook when creating, reviewing, troubleshooting, or improving Deneb visuals for Power BI using Vega or Vega-Lite.

The goal is to create visuals that are:

- Valid Deneb specs
- Executive-ready
- Clean and professional
- Easy to maintain
- Properly mapped to Power BI fields
- Useful beyond what native Power BI visuals can easily provide

## Default Position

Use Vega-Lite by default.

Use Vega only when the visual requires:

- More advanced interactivity
- Signals
- Lower-level mark control
- Complex layered behavior
- Functionality Vega-Lite cannot express cleanly

## When to Use This Playbook

Use this playbook when the user asks to:

- Build a Deneb visual
- Create a Vega-Lite JSON spec
- Create a Vega JSON spec
- Improve a Power BI visual with Deneb
- Build a custom KPI card
- Build a bullet chart
- Build a dumbbell chart
- Build a slope chart
- Build a lollipop chart
- Build a heatmap
- Troubleshoot a blank Deneb visual
- Create custom tooltips
- Make a visual look more executive-ready

## Required Inputs

Ask for or infer:

1. Visual goal
2. Power BI fields added to Deneb
3. Field names exactly as Deneb sees them
4. Measures vs columns
5. Desired chart type
6. Sort behavior
7. Tooltip fields
8. Color rules
9. Size constraints
10. Whether the visual needs to respect cross-filtering

If the field names are unknown, ask for them before creating final JSON.

## Core Deneb Assumptions

Default data reference:

```json
"data": {
  "name": "dataset"
}
```

Deneb receives data from the fields placed into the Deneb visual in Power BI.

Do not invent fields without clearly labeling them as placeholders.

## JSON Rules

- JSON must be valid.
- Do not put comments inside JSON.
- Use double quotes.
- Use `"data": {"name": "dataset"}`.
- Include `$schema`.
- Use readable indentation.
- Put explanations outside the JSON block.

Bad:

```json
{
  // comments break JSON
  "data": {"name": "dataset"}
}
```

Good:

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "name": "dataset"
  }
}
```

## Required Output Format

When creating a visual, use:

```markdown
## Visual Objective

## Required Power BI Fields

## Power BI Field Setup

## Vega-Lite JSON

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "name": "dataset"
  }
}
```

## How It Works

## Customization Options

## Testing Checklist
```

Use `Vega JSON` instead of `Vega-Lite JSON` only when Vega is required.

## Field Type Guide

Use these Vega-Lite types:

```text
nominal      = categories, names, labels
ordinal      = ordered categories
quantitative = numeric measures
temporal     = dates and times
```

Examples:

```json
{
  "field": "Category",
  "type": "nominal"
}
```

```json
{
  "field": "Total Sales",
  "type": "quantitative"
}
```

```json
{
  "field": "Date",
  "type": "temporal"
}
```

## Preferred Visual Patterns

## Executive Bar Chart

Use for category ranking.

Required fields:

```text
Category
Value
```

## Bullet Chart

Use for actual vs target.

Required fields:

```text
Metric
Actual
Target
```

## Dumbbell Chart

Use for comparing two values by category.

Required fields:

```text
Category
Start Value
End Value
```

## Slope Chart

Use for showing change between two periods.

Required fields:

```text
Category
Period
Value
```

## Heatmap

Use for intensity across two categorical dimensions.

Required fields:

```text
X Category
Y Category
Value
```

## Calendar Heatmap

Use for daily values over time.

Required fields:

```text
Date
Value
```

## KPI Card

Use for custom executive KPI display.

Required fields:

```text
Metric Name
Value
Variance
Variance %
Target
```

## Tooltip Standards

Always include useful tooltips.

Common tooltip fields:

- Category
- Date
- Value
- Target
- Variance
- Variance %
- Rank
- Segment
- Status

Example:

```json
"tooltip": [
  {
    "field": "Category",
    "type": "nominal"
  },
  {
    "field": "Value",
    "type": "quantitative",
    "format": ",.0f"
  }
]
```

## Sorting Standards

Always sort intentionally.

Examples:

```json
"sort": "-x"
```

```json
"sort": "-y"
```

For custom business order, use a sort column if available.

## Axis Standards

Remove unnecessary axis titles when context is clear.

```json
"axis": {
  "title": null
}
```

Common formats:

```json
"format": ",.0f"
```

```json
"format": ".1%"
```

```json
"format": "$,.0f"
```

## Responsive Sizing

Default to:

```json
"width": "container",
"height": "container"
```

If rendering issues occur, recommend explicit dimensions:

```json
"width": 600,
"height": 350
```

## Aggregation Guidance

If Deneb receives a DAX measure already aggregated by Power BI, do not add unnecessary aggregation.

If Deneb receives raw row-level columns, specify aggregation:

```json
{
  "aggregate": "sum",
  "field": "Sales Amount",
  "type": "quantitative"
}
```

Always clarify whether the field is:

- A DAX measure
- A raw column
- A summarized field
- A calculated column

## Native Visual vs Deneb Decision

Use native Power BI visuals when:

- The chart is simple
- Maintenance matters more than custom design
- Native formatting is sufficient
- Business users may need to modify it easily

Use Deneb when:

- Native visuals cannot produce the desired layout
- Custom labels or marks are needed
- The visual needs professional polish
- A custom analytical visual is required
- Layered marks improve interpretation
- The visual should replace a cluttered table or gauge

## Troubleshooting Blank Deneb Visuals

Check:

1. Is the JSON valid?
2. Does it include the correct schema?
3. Is the dataset named `"dataset"`?
4. Do field names match exactly?
5. Are numeric fields typed as quantitative?
6. Are date fields typed as temporal?
7. Is the visual too small?
8. Are fields summarized unexpectedly?
9. Are nulls causing issues?
10. Is the mark type valid?
11. Is there a Deneb error message?
12. Does a simple test spec work?

Simple test spec:

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "name": "dataset"
  },
  "mark": "point",
  "encoding": {
    "x": {
      "field": "Category",
      "type": "nominal"
    },
    "y": {
      "field": "Value",
      "type": "quantitative"
    }
  }
}
```

## Design Standards

Deneb visuals should be:

- Clean
- Minimal
- Professional
- Easy to read
- Consistent with the report
- Clear in business meaning
- Not overly decorative

Avoid:

- Too many colors
- Too many encodings
- Tiny labels
- Excessive legends
- Visual tricks with no business value
- Hard-to-maintain JSON
- Overbuilding when a native visual would work

## Validation Checklist

When finalizing a Deneb visual, verify:

1. JSON is valid.
2. Field names match Deneb dataset.
3. Visual renders in Power BI.
4. Tooltips show useful context.
5. Sorting is correct.
6. Formatting is readable.
7. Cross-filtering behaves as expected.
8. Visual answers the intended business question.
9. Visual is not overly complex.
10. Native visual alternative was considered.

## Final Recommendation Style

Be honest when Deneb is unnecessary.

Example:

```text
Deneb can do this, but a native bar chart is probably the better choice unless you need custom labels or a specific executive layout. I would use Deneb only if the native visual cannot meet the formatting requirement.
```
