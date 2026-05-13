# SQLBI Reference

## Purpose

This file defines how this Claude Project should use SQLBI as a primary advanced reference source for Power BI modeling, DAX, VertiPaq, semantic model design, and performance optimization.

SQLBI should be treated as the preferred source for deeper reasoning about:

- DAX
- Filter context
- Row context
- Context transition
- CALCULATE
- Iterators
- Time intelligence
- Star schema design
- Semantic model architecture
- Relationship design
- VertiPaq storage engine behavior
- Formula engine vs storage engine concepts
- Performance optimization
- Measure design patterns
- Power BI modeling best practices

Primary source:

<https://www.sqlbi.com/articles/>

Additional useful SQLBI areas:

<https://www.sqlbi.com/topics/dax/>

<https://www.sqlbi.com/topics/data-modeling/>

<https://www.sqlbi.com/topics/optimization/>

<https://www.sqlbi.com/topics/power-bi/>

---

## When to Use SQLBI

Use SQLBI-style reasoning when the user asks about:

1. DAX measures
2. DAX debugging
3. Filter context
4. Row context
5. Context transition
6. CALCULATE behavior
7. Time intelligence
8. Relationship behavior
9. Star schema design
10. Many-to-many relationships
11. Bridge tables
12. Date table design
13. Measures vs calculated columns
14. Performance optimization
15. VertiPaq behavior
16. Model size and cardinality
17. Query performance
18. Semantic model architecture
19. Advanced Power BI modeling
20. Why totals behave differently from row-level values

---

## SQLBI Role in This Project

SQLBI is the advanced technical standard for this project.

Use Microsoft Learn for official product behavior and UI workflows.

Use SQLBI-style reasoning for determining whether the model, relationships, or DAX logic are correct, performant, and maintainable.

Example distinction:

- Microsoft Learn answers: “Where is this feature and how do I use it?”
- SQLBI answers: “Is this the correct model or DAX pattern, and why?”

---

## Core SQLBI-Inspired Principles

## 1. Prefer Star Schema

Default to star schema for Power BI semantic models.

A clean star schema usually has:

- Fact tables for measurable business events
- Dimension tables for descriptive attributes
- One-to-many relationships from dimensions to facts
- Single-direction filtering from dimensions to facts
- A dedicated Date table
- Explicit measures
- Low ambiguity in filter propagation

Recommended pattern:

```text
DimDate       ─┐
DimCustomer   ─┤
DimProduct    ─┤
DimRegion     ─┤
DimEmployee   ─┤
               ├── FactSales
DimChannel    ─┤
DimScenario   ─┘
