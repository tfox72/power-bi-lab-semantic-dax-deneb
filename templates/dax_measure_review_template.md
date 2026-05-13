# DAX Measure Review Template

## Measure Name

```text
[Measure Name]
```

## Current DAX

```DAX
Paste current DAX here
```

## Expected Result

Describe what the measure should return.

## Actual Result

Describe what the measure is returning now.

## Visual Context

Describe where the measure is used:

- Table
- Matrix
- Card
- Line chart
- Bar chart
- Tooltip
- Drill-through page

Include fields on the visual.

## Filter Context

List active filters:

- Slicers
- Page filters
- Report filters
- Visual filters
- Cross-filtering
- Drill-through filters

## Model Context

Relevant tables:

| Table | Role | Notes |
|---|---|---|
| FactExample | Fact |  |
| DimExample | Dimension |  |

Relevant relationships:

| From | To | Cardinality | Filter Direction | Active |
|---|---|---|---|---|
|  |  |  |  |  |

## What the Measure Is Doing

Explain the current logic in plain English.

## Why the Result May Be Wrong

Check:

- Incorrect filter context
- Missing CALCULATE
- Incorrect ALL / REMOVEFILTERS
- Wrong grain
- Missing iterator
- Wrong relationship
- Inactive relationship
- Many-to-many issue
- Calculated column used instead of measure
- Date table issue
- Total-level behavior issue

## Corrected DAX

```DAX
Corrected Measure =
VAR Example =
    [Base Measure]
RETURN
    Example
```

## Explanation of the Fix

Explain:

1. Base expression
2. Filter changes
3. Variables used
4. Total behavior
5. Edge cases

## Filter Context Walkthrough

Describe:

```text
At the row level:
- Filters active:
- Result:

At the total level:
- Filters active:
- Result:

After CALCULATE:
- Filters removed:
- Filters preserved:
- Filters added:
```

## Row Context / Context Transition Notes

Explain if relevant.

Use when the measure includes:

- SUMX
- AVERAGEX
- FILTER
- ADDCOLUMNS
- RANKX
- CALCULATE inside an iterator

## Test Cases

Create these visuals/checks:

1. Detail table by lowest relevant grain.
2. Total card.
3. Matrix with subtotal.
4. Slicer test.
5. Date boundary test if time intelligence is used.
6. Blank/zero denominator test if ratios are used.

## Performance Notes

Check:

- Iterator over large fact table
- FILTER over fact table
- Repeated expensive subexpressions
- High-cardinality fields
- Many-to-many relationships
- Bidirectional filters

## Final Recommendation

State whether the corrected DAX is sufficient or if the semantic model should be changed.
