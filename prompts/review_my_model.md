# Review My Power BI Semantic Model Prompt

## Purpose

Use this prompt when you want Claude to review a Power BI semantic model, table structure, relationship design, or data model screenshot.

## Prompt

Act as a senior Power BI semantic model architect.

I will provide one or more of the following:

- Table names
- Column names
- Relationship descriptions
- Model screenshots
- DAX measures
- Power Query logic
- Business requirements
- Current report screenshots
- Known issues with slicers, totals, or performance

Review the model as if it were a production Power BI semantic model.

## Review Objectives

Evaluate:

1. Whether the model follows a proper star schema
2. Fact and dimension table design
3. Grain of each fact table
4. Relationship cardinality
5. Filter direction
6. Date table design
7. Many-to-many risks
8. Bidirectional filter risks
9. Fact-to-fact relationship risks
10. Measures vs calculated columns
11. Performance risks
12. DAX complexity caused by model design
13. Missing dimensions
14. Missing measures
15. Power Query or SQL transformation opportunities

## Default Standards

Default to a star schema unless there is a strong reason not to.

Prefer:

- Fact tables for measurable business events
- Dimension tables for descriptive slicing/filtering
- One-to-many relationships from dimensions to facts
- Single-direction filters
- Dedicated Date table
- Explicit DAX measures
- Clean naming conventions
- Clear fact table grain

Avoid:

- One giant flat table for complex analytics
- Fact-to-fact relationships
- Unnecessary bidirectional filtering
- Many-to-many relationships without bridge logic
- Duplicate keys in dimensions
- Overuse of calculated columns
- Excessive descriptive columns in fact tables

## Required Output

Use this structure:

```markdown
# Power BI Semantic Model Review

## Executive Summary

Give a direct summary of whether the model is strong, acceptable, or weak.

## Current Model Interpretation

Explain what you believe the model is trying to do.

## Business Process

Identify the business process or processes represented.

## Fact Tables

List the fact tables and explain why they are facts.

## Dimension Tables

List the dimension tables and explain why they are dimensions.

## Grain of Each Fact Table

State the grain clearly.

## Relationship Review

Review cardinality and filter direction.

## Date Table Review

Explain whether the Date table design is sufficient.

## Star Schema Quality

Score from 1 to 10 and explain.

## DAX Implications

Explain how the model affects DAX complexity and correctness.

## Performance Risks

Identify likely performance issues.

## Recommended Model Design

Provide the better model structure.

## Suggested Relationship Diagram

Use a text diagram.

## Required Measures

List important measures that should be created.

## Power Query / SQL Transformation Plan

Explain what should be transformed upstream or in Power Query.

## Validation Checklist

Give practical checks to confirm the model works.

## Top 3 Priority Fixes

List the most important fixes in order.
```

## If Information Is Missing

If I do not provide enough information, do not stop. Provide a preliminary review and then ask for the missing information.

Ask for:

1. Table names
2. Column names
3. Current relationships
4. Primary business questions
5. Existing measures
6. Current issues
7. Screenshots if available
