# Deneb Visual Requirements Template

## Visual Objective

Describe what the visual should communicate.

```text
This visual should show:
```

## Business Question

```text
What business question does this visual answer?
```

## Recommended Visual Type

Select one:

- Bar chart
- Bullet chart
- Dumbbell chart
- Slope chart
- Lollipop chart
- Heatmap
- Calendar heatmap
- KPI card
- Distribution chart
- Small multiple
- Custom visual

## Power BI Fields Added to Deneb

| Field Name in Deneb | Source Table/Measure | Type | Purpose |
|---|---|---|---|
| Category |  | Nominal | Category axis |
| Value |  | Quantitative | Main value |
| Target |  | Quantitative | Target marker |
| Date |  | Temporal | Time axis |
| Segment |  | Nominal | Color/grouping |

## Field Mapping

| Visual Role | Field |
|---|---|
| Category |  |
| X-axis |  |
| Y-axis |  |
| Value |  |
| Target |  |
| Tooltip |  |
| Color/status |  |
| Sort |  |

## Data Assumptions

- [ ] Values are already aggregated by Power BI.
- [ ] Values are raw columns and need aggregation in Vega-Lite.
- [ ] Field names match Deneb dataset exactly.
- [ ] Null values are handled.
- [ ] Date field is recognized as a date.
- [ ] Sort order is defined.

## Vega-Lite Starter Spec

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "name": "dataset"
  },
  "width": "container",
  "height": "container",
  "mark": {
    "type": "bar",
    "tooltip": true
  },
  "encoding": {
    "x": {
      "field": "Value",
      "type": "quantitative",
      "axis": {
        "title": null,
        "format": ",.0f"
      }
    },
    "y": {
      "field": "Category",
      "type": "nominal",
      "sort": "-x",
      "axis": {
        "title": null
      }
    },
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
  }
}
```

## Formatting Requirements

| Item | Requirement |
|---|---|
| Number format |  |
| Percentage format |  |
| Currency format |  |
| Axis labels |  |
| Data labels |  |
| Tooltip fields |  |
| Sort order |  |
| Color rules |  |

## Testing Checklist

- [ ] JSON is valid.
- [ ] Visual renders in Deneb.
- [ ] Field names match exactly.
- [ ] Tooltips show correct values.
- [ ] Sort order is correct.
- [ ] Formatting is readable.
- [ ] Cross-filtering works.
- [ ] Visual answers the business question.
- [ ] Native Power BI alternative was considered.
