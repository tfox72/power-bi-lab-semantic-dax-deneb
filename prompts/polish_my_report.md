# Polish My Power BI Report Prompt

## Purpose

Use this prompt when you want Claude to review and improve the design, layout, visual hierarchy, and executive polish of a Power BI report page or dashboard.

## Prompt

Act as a senior Power BI report designer and executive dashboard consultant.

I will provide a screenshot, description, wireframe, or list of visuals from a Power BI report.

Your job is to make the report more polished, professional, and executive-ready.

## Review Objectives

Evaluate:

1. Business clarity
2. Audience fit
3. Main decision supported
4. Layout
5. Visual hierarchy
6. KPI quality
7. Visual selection
8. Color usage
9. Typography
10. Spacing and alignment
11. Slicers and interactivity
12. Tooltip and drill-through opportunities
13. Cognitive load
14. Performance risk
15. Overall executive readiness

## Default Design Standards

A strong Power BI report should:

- Answer a clear business question
- Prioritize the most important metrics
- Use a clean visual hierarchy
- Use fewer visuals with more impact
- Use insight-driven titles
- Use consistent spacing
- Use a restrained color palette
- Avoid clutter
- Use slicers intentionally
- Move detail to drill-through or tooltips
- Be understandable within 10 seconds

## Required Output

Use this structure:

```markdown
# Power BI Report Design Review

## Executive Summary

Give a direct assessment.

## Overall Design Score

Score from 1 to 10.

## What Works Well

List strengths.

## What Is Holding It Back

List key weaknesses.

## Business Clarity

Explain whether the report answers a clear question.

## Layout and Visual Hierarchy

Explain how the page guides or fails to guide the viewer.

## KPI and Metric Quality

Review KPI cards and metric context.

## Visual Choice Review

Explain which visuals work and which should change.

## Color and Formatting Review

Review color, typography, spacing, and polish.

## Slicers and Interactivity

Review filters, slicers, tooltips, bookmarks, and drill-through.

## Performance and Usability Risks

Identify design choices that may hurt performance or usability.

## Top 3 Priority Fixes

Give the highest-impact changes.

## Recommended Redesign

Provide a proposed layout.

## Suggested Visual Changes

List specific replacements or formatting improvements.

## Final Recommendation

Give a concise plan to make it executive-ready.
```

## Recommended Layout Format

When suggesting a redesign, use:

```text
Header:
- Title
- Subtitle / business question
- Last refresh date

Top Row:
- KPI 1
- KPI 2
- KPI 3
- KPI 4

Middle Left:
- Primary trend or driver visual

Middle Right:
- Ranking, breakdown, or exception list

Bottom:
- Detail table, drill-through entry point, or notes
```

## If Reviewing a Screenshot

Be specific about:

- What to move
- What to remove
- What to resize
- What to retitle
- What visual to replace
- What should be emphasized
- What should be pushed into detail

## If No Screenshot Is Provided

Ask for a screenshot, or review based on the described layout.
