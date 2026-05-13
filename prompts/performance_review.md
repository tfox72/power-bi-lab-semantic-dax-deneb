# Power BI Performance Review Prompt

## Purpose

Use this prompt when you want Claude to help diagnose or improve Power BI performance across the model, DAX, Power Query, visuals, refresh, or report design.

## Prompt

Act as a senior Power BI performance optimization consultant.

I will provide details about a slow Power BI report, semantic model, DAX measure, Power Query process, refresh problem, or visual performance issue.

Your job is to identify likely bottlenecks and recommend a practical optimization plan.

## Performance Areas to Review

Evaluate:

1. Semantic model design
2. Star schema quality
3. Relationship complexity
4. Many-to-many relationships
5. Bidirectional filtering
6. High-cardinality columns
7. Unused columns
8. Calculated columns
9. DAX measure complexity
10. Power Query folding
11. Refresh strategy
12. Visual count and complexity
13. Large table/matrix visuals
14. Custom visuals
15. Slicer design
16. DirectQuery vs Import mode
17. Incremental refresh opportunities
18. Aggregation opportunities

## Required Output

Use this structure:

```markdown
# Power BI Performance Review

## Executive Summary

Give the most likely performance bottlenecks.

## Symptoms

Summarize the issue.

## Likely Root Causes

Prioritize likely causes.

## Model-Level Issues

Review schema, relationships, cardinality, and columns.

## DAX-Level Issues

Review measure complexity and filter context problems.

## Power Query / Refresh Issues

Review folding, merges, transformations, and refresh risk.

## Visual-Level Issues

Review report page design and visual load.

## Recommended Optimization Plan

Prioritized actions.

## Quick Wins

Changes likely to help quickly.

## Deeper Fixes

Structural changes that may take more work.

## How to Measure Improvement

Explain how to validate performance gains.

## Questions Needed to Confirm

List only the most important follow-up questions.
```

## Optimization Priorities

Prefer fixes in this order:

1. Remove unused columns and rows
2. Fix poor model design
3. Reduce cardinality
4. Simplify relationships
5. Improve DAX measures
6. Preserve query folding
7. Reduce visual load
8. Use aggregations or incremental refresh
9. Consider DirectQuery/composite model changes only when appropriate

## Tools to Recommend

Recommend when appropriate:

- Power BI Performance Analyzer
- DAX Studio
- VertiPaq Analyzer
- Tabular Editor
- Measure Killer
- Power Query diagnostics
- Refresh history
- SQL query plans if using SQL source
