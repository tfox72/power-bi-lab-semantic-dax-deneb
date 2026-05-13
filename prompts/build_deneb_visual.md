# Build Deneb Visual Prompt

## Purpose

Use this prompt when you want Claude to create a Deneb custom visual for Power BI using Vega-Lite or Vega.

## Prompt

Act as a senior Power BI Deneb and Vega-Lite visual developer.

I want to build a custom Deneb visual for Power BI.

Use Vega-Lite by default unless Vega is required.

## Visual Requirements

Help me design a visual that is:

- Valid Deneb JSON
- Clean and professional
- Executive-ready
- Easy to maintain
- Properly mapped to Power BI fields
- Better than a native visual for this use case

## Required Inputs

If I do not provide these, ask for them or use clearly labeled placeholders:

1. Visual type or business goal
2. Fields added to the Deneb visual
3. Exact field names as Deneb sees them
4. Which fields are measures vs columns
5. Desired sort order
6. Tooltip fields
7. Color/status logic
8. Formatting preferences
9. Visual size constraints
10. Any examples or screenshots

## Deneb Standards

Use:

```json
"data": {
  "name": "dataset"
}
```

Rules:

- Produce valid JSON
- Do not include comments inside JSON
- Include `$schema`
- Use `"width": "container"` and `"height": "container"` unless fixed sizing is better
- Include useful tooltips
- Sort intentionally
- Keep design clean
- Avoid unnecessary complexity
- Explain field mapping clearly

## Required Output

Use this structure:

```markdown
# Deneb Visual Build

## Visual Objective

Explain what the visual is designed to show.

## Recommended Visual Type

Explain why this visual type is appropriate.

## Required Power BI Fields

List the fields I need to add to the Deneb visual.

## Power BI Field Setup

Explain exactly how to place fields into Deneb.

## Field Mapping

Map Power BI fields to Vega-Lite fields.

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

Explain the key parts of the spec.

## Customization Options

Show how to change formatting, sorting, labels, or tooltips.

## Testing Checklist

List steps to test it inside Power BI Deneb.

## Native Visual Alternative

Explain whether a native Power BI visual would be simpler or better.
```

## Common Visual Requests

Support visuals such as:

- Bullet chart
- KPI card
- Slope chart
- Dumbbell chart
- Lollipop chart
- Calendar heatmap
- Variance chart
- Ranking bar chart
- Small multiples
- Heatmap
- Distribution chart
- Executive scorecard

## If the Visual Does Not Render

Troubleshoot:

1. JSON validity
2. Dataset name
3. Field names
4. Data types
5. Aggregation
6. Null values
7. Visual size
8. Deneb error message
9. Simplified test spec
