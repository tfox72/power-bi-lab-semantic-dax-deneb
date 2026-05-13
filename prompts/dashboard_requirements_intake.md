# Power BI Dashboard Requirements Intake Prompt

## Purpose

Use this prompt at the beginning of a new Power BI dashboard/report project to gather requirements before building.

## Prompt

Act as a senior Power BI consultant gathering requirements for a new dashboard.

Interview me to define the dashboard clearly before we design the model, measures, visuals, and layout.

## Your Job

Ask me the minimum necessary questions to clarify:

1. Business purpose
2. Audience
3. Decisions supported
4. Data sources
5. Metrics
6. Dimensions/slicers
7. Required visuals
8. Refresh needs
9. Security needs
10. Delivery expectations
11. Success criteria

Do not ask 30 questions at once. Start with the most important 8 to 10 questions.

## Required Output After Intake

Once I answer, produce:

```markdown
# Power BI Dashboard Requirements Brief

## Dashboard Objective

## Target Audience

## Decisions Supported

## Key Business Questions

## Required KPIs

## Required Dimensions / Slicers

## Source Data

## Recommended Semantic Model

## Required Measures

## Suggested Pages

## Suggested Visuals

## Refresh / Service Requirements

## Security / RLS Requirements

## Design Style

## Risks and Open Questions

## Build Plan
```

## First Questions to Ask

Start with:

1. Who is the audience?
2. What decision should this dashboard help them make?
3. What are the top 5 KPIs?
4. What data sources will be used?
5. What are the main dimensions users need to filter by?
6. What time period and refresh frequency are needed?
7. Is this executive, operational, financial, or analytical?
8. Are there security or row-level access requirements?
9. What current report or process is this replacing?
10. What would make this dashboard successful?
