# Power Query Transformation Template

## Transformation Objective

Describe what this query should produce.

```text
This query transforms [source] into [final table] for use as [fact/dimension/staging] table.
```

## Source Information

| Source | Details |
|---|---|
| Source type | Excel / CSV / SQL / SharePoint / Folder / API / Other |
| Source name |  |
| Table/file name |  |
| Refresh frequency |  |
| Import mode | Import / DirectQuery / Composite |
| Gateway required | Yes / No |

## Current Problem

Describe the issue:

```text

```

## Desired Output

Describe the final table shape:

| Column | Data Type | Purpose | Notes |
|---|---|---|---|
|  |  |  |  |

## Transformation Steps

Recommended sequence:

1. Connect to source.
2. Filter rows early if safe.
3. Remove unused columns.
4. Rename columns.
5. Set data types.
6. Clean text values.
7. Create keys if needed.
8. Merge or append if needed.
9. Unpivot or pivot if needed.
10. Add structural calculated columns.
11. Remove intermediate columns.
12. Validate row counts.
13. Load final table only.

## Power Query / M Code

```powerquery
let
    Source = null
in
    Source
```

## Query Folding Notes

Check:

- [ ] Source supports query folding.
- [ ] Filters are applied early.
- [ ] Column selection is applied early.
- [ ] View Native Query remains available where expected.
- [ ] Non-folding steps occur as late as possible.
- [ ] Heavy transformations are pushed to SQL/source where practical.

## Merge Review

If using merge:

| Check | Result |
|---|---|
| Join keys have same data type |  |
| Lookup side key is unique |  |
| Join type is correct |  |
| Row count before merge |  |
| Row count after merge |  |
| Merge does not duplicate fact rows |  |

## Append Review

If using append:

| Check | Result |
|---|---|
| Column names align |  |
| Data types align |  |
| Source identifier added if needed |  |
| Duplicate rows handled |  |
| Grain remains consistent |  |

## Data Quality Checks

- [ ] Nulls handled.
- [ ] Errors handled.
- [ ] Data types correct.
- [ ] Duplicate keys resolved.
- [ ] Row counts validated.
- [ ] Totals reconcile.
- [ ] Unexpected blanks reviewed.
- [ ] Date parsing verified.
- [ ] Currency/number parsing verified.

## Model Impact

Explain how this query supports the model:

```text
Final table type: Fact / Dimension / Staging
Related tables:
Expected relationships:
Expected measures:
```

## Performance Risks

List risks:

- 
- 
- 

## Validation Checklist

- [ ] Query refreshes successfully.
- [ ] Row count is expected.
- [ ] Column count is expected.
- [ ] Data types are correct.
- [ ] Keys are valid.
- [ ] Totals match source.
- [ ] Query folding is acceptable.
- [ ] Staging queries have load disabled if appropriate.
