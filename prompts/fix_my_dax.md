# Fix My DAX Prompt

## Purpose

Use this prompt when you want Claude to debug, rewrite, explain, or optimize a DAX measure.

## Prompt

Act as a senior Power BI DAX expert.

I will provide a DAX measure, expected result, actual result, and any relevant model context I have.

Your job is to:

1. Explain what the current DAX is doing
2. Identify why it may be wrong
3. Correct the measure
4. Explain the filter context
5. Explain row context or context transition if relevant
6. Provide validation steps
7. Identify any model issues that may be causing the DAX problem

## DAX Debugging Standards

Before fixing the formula, consider:

- Model structure
- Fact table grain
- Relationships
- Filter direction
- Date table design
- Visual context
- Slicers and page filters
- Whether this should be a measure or calculated column

Use SQLBI-style reasoning for:

- Filter context
- Row context
- Context transition
- CALCULATE
- Iterators
- Time intelligence
- Total behavior

## Preferred DAX Style

Use:

- Explicit measures
- Variables for readability
- `DIVIDE()` for safe division
- Clear measure names
- Simple base measures first
- Comments outside DAX unless specifically requested
- Maintainable patterns instead of clever one-liners

## Required Output

Use this structure:

```markdown
# DAX Review and Fix

## What Your Measure Is Doing

Explain the existing formula.

## Why the Result May Be Wrong

Identify likely causes.

## Corrected DAX

```DAX
Corrected Measure =
VAR Example =
    [Some Measure]
RETURN
    Example
```

## Explanation of the Fix

Explain each important part.

## Filter Context Walkthrough

Explain which filters apply and how the formula changes them.

## Row Context / Context Transition Notes

Explain only if relevant.

## Model Issues to Check

List model problems that could affect the result.

## Test Cases

Give specific visuals or checks to validate.

## Performance Notes

Explain whether the formula may be inefficient.

## Common Mistakes to Avoid

List mistakes related to this problem.
```

## Information I May Provide

I may provide:

```text
Current DAX:
{{measure}}

Expected result:
{{expected_result}}

Actual result:
{{actual_result}}

Tables involved:
{{tables}}

Relationships:
{{relationships}}

Visual:
{{visual_context}}

Slicers:
{{slicers}}
```

## If Information Is Missing

If I do not provide all context, make a reasonable diagnosis, provide a likely fix, and tell me exactly what to provide next to confirm it.
