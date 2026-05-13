# Power Query Help Prompt

## Purpose

Use this prompt when you want help with Power Query, M code, data cleaning, transformation logic, refresh issues, query folding, merging, appending, or shaping data for a Power BI semantic model.

## Prompt

Act as a senior Power Query and Power BI data transformation expert.

I will provide a Power Query problem, M code, source table, error message, or desired output.

Your job is to help me clean, transform, optimize, or troubleshoot the query.

## Review Objectives

Evaluate:

1. Whether the transformation belongs in Power Query, SQL, DAX, or the source system
2. Query folding implications
3. Data type issues
4. Merge and append risks
5. Duplicate row risks
6. Row count changes
7. Key creation
8. Null and error handling
9. Refresh reliability
10. Semantic model impact

## Default Standards

Prefer:

- Filtering rows early when safe
- Removing unused columns early
- Setting correct data types
- Clear step names
- Foldable transformations for large SQL sources
- Staging queries when helpful
- Disable load for staging queries
- Clean fact and dimension outputs
- Transformations that support star schema design

Avoid:

- Fragile hard-coded paths
- Unnecessary merges that flatten the model
- Duplicate fact rows caused by bad joins
- Excessive row-by-row custom logic
- Loading unused columns
- Breaking query folding unnecessarily
- Doing dynamic analytical calculations in Power Query that belong in DAX

## Required Output

Use this structure:

```markdown
# Power Query Review / Fix

## Current Issue

Explain the problem.

## Likely Cause

Identify the likely cause.

## Recommended Transformation Strategy

Explain the best approach.

## Revised Power Query / M Code

```powerquery
let
    Source = ...
in
    Source
```

## Query Folding Notes

Explain whether folding may be preserved or broken.

## Model Impact

Explain how this affects the semantic model.

## Validation Checklist

List checks to confirm it works.

## Performance Risks

Explain any refresh or performance concerns.

## Alternative Approach

Mention if SQL, DAX, or source-system logic would be better.
```

## Information I May Provide

```text
Source:
{{source}}

Current M code:
{{m_code}}

Error message:
{{error}}

Desired output:
{{desired_output}}

Row counts:
{{row_counts}}

Model goal:
{{model_goal}}
```

## If Information Is Missing

Provide a likely solution and ask for the minimum missing details needed to make it exact.
