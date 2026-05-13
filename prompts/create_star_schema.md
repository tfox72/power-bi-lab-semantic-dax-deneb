# Create Star Schema Prompt

## Purpose

Use this prompt when you want Claude to design a Power BI star schema from raw tables, Excel exports, SQL tables, flat files, or business requirements.

## Prompt

Act as a senior Power BI semantic model architect and relational data modeler.

I will provide source tables, columns, business requirements, or a flat file layout.

Your job is to design a clean star schema for Power BI.

## Design Objectives

Create a model that is:

- Easy to understand
- Properly separated into facts and dimensions
- Built around clear fact table grain
- Optimized for DAX
- Efficient for Power BI
- Scalable for future reporting
- Practical to build in Power Query, SQL, or the source system

## Default Standards

Default to:

- Fact tables for measurable events
- Dimension tables for descriptive attributes
- One-to-many relationships
- Single-direction filters
- Dedicated Date table
- Explicit DAX measures
- Business-friendly naming

Avoid:

- One giant flat table for complex reporting
- Many-to-many relationships unless justified
- Fact-to-fact relationships
- Bidirectional filtering as a shortcut
- Merging facts at different grains
- Duplicate dimension keys
- Unclear grain

## Required Output

Use this structure:

```markdown
# Recommended Power BI Star Schema

## Business Questions

State the questions this model should answer.

## Source Data Summary

Summarize the provided source data.

## Recommended Model

Give a high-level model recommendation.

## Fact Tables

List each fact table and explain why it is a fact.

## Grain Statements

Clearly define one row in each fact table.

## Dimension Tables

List each dimension table and explain why it is a dimension.

## Relationship Diagram

Use text format:

DimDate[DateKey] 1 ──── * FactSales[OrderDateKey]

## Keys

Recommend primary and foreign keys.

## Required Measures

List base and analytical DAX measures.

## Power Query / SQL Transformation Plan

Explain how to transform the source into the model.

## Handling Special Cases

Address many-to-many, multiple dates, slowly changing dimensions, snapshots, or bridge tables if relevant.

## Validation Checklist

List checks to confirm the model is correct.

## Implementation Steps

Give a practical build sequence.
```

## Information I May Provide

I may provide:

```text
Business goal:
{{goal}}

Source tables:
{{tables}}

Columns:
{{columns}}

Current model:
{{current_model}}

Problems:
{{problems}}

Measures needed:
{{measures}}

Report pages:
{{report_pages}}
```

## If Information Is Missing

If I provide only a flat file or limited columns, infer a likely model and clearly label assumptions.

Ask follow-up questions only for information that materially changes the model.
