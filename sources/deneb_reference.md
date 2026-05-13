
# `sources/deneb_reference.md`

```markdown
# Deneb, Vega, and Vega-Lite Reference

## Purpose

This file defines how this Claude Project should use Deneb, Vega, and Vega-Lite for Power BI custom visuals.

Deneb should be treated as the primary custom visual framework for this project when native Power BI visuals are not sufficient.

Use Deneb for:

- Custom Power BI visuals
- Vega-Lite JSON visual specs
- Vega JSON visual specs
- Pixel-level formatting control
- Executive-style visuals
- Advanced chart types
- Custom tooltips
- Small multiples
- Heatmaps
- Bullet charts
- Slope charts
- Dumbbell charts
- Lollipop charts
- Calendar heatmaps
- Distribution visuals
- Custom KPI cards
- Specialized analytical visuals

Primary sources:

https://deneb.guide/

https://deneb-viz.github.io/

Vega-Lite documentation:

https://vega.github.io/vega-lite/

Vega documentation:

https://vega.github.io/vega/

---

# When to Use Deneb

Use Deneb when the user asks for:

1. A custom visual in Power BI
2. A visual that native Power BI cannot easily create
3. A more polished executive visual
4. A custom KPI card
5. A bullet chart
6. A slope chart
7. A dumbbell chart
8. A lollipop chart
9. A calendar heatmap
10. A distribution chart
11. A custom variance visual
12. A more flexible tooltip experience
13. A Vega-Lite spec
14. A Vega spec
15. Better control over labels, marks, axes, spacing, or conditional formatting

Use native Power BI visuals first when they can do the job clearly and maintainably.

Use Deneb when it materially improves:

- Clarity
- Design quality
- Analytical value
- Maintainability
- Interactivity
- Layout control

---

# Deneb Role in This Project

Deneb is the custom visual engine for Power BI reports.

Use it when:

- Native visuals are too limited
- The report needs a professional custom look
- The visual needs advanced encoding
- The user wants a Vega-Lite or Vega JSON spec
- The user wants reusable visual patterns

Default to Vega-Lite unless Vega is specifically required.

Use Vega when:

- More advanced interactions are required
- Fine-grained control is needed
- Vega-Lite cannot express the desired visual clearly
- The visual requires lower-level control over marks, signals, or complex interactivity

---

# Core Deneb Assumptions

## 1. Deneb Uses a Power BI Dataset

Assume Deneb receives data from fields added to the Deneb visual in Power BI.

Default dataset reference:

```json
"data": {
  "name": "dataset"
}
