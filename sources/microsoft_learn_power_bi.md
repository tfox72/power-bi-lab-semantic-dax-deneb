# Microsoft Learn Power BI Reference

## Purpose

This file defines how this Claude Project should use Microsoft Learn as an official reference source for Power BI.

Microsoft Learn should be treated as the primary source for official Microsoft guidance on:

- Power BI Desktop
- Power BI Service
- Power Query
- Data modeling basics
- DAX basics
- Reports
- Dashboards
- Workspaces
- Data refresh
- Sharing and collaboration
- Deployment concepts
- Governance and administration
- Microsoft Fabric and Power BI integration when relevant

Primary source:

<https://learn.microsoft.com/en-us/training/powerplatform/power-bi>

Additional Microsoft Learn areas that may be useful:

<https://learn.microsoft.com/en-us/power-bi/>

<https://learn.microsoft.com/en-us/training/browse/?products=power-bi>

---

## When to Use Microsoft Learn

Use Microsoft Learn when the user asks about:

1. Official Power BI feature behavior
2. How to perform tasks in Power BI Desktop
3. How to use Power BI Service
4. Workspaces, apps, dashboards, and reports
5. Refresh behavior
6. Sharing and permissions
7. Dataflows
8. Deployment pipelines
9. Power Query basics
10. Data modeling basics
11. Certification-style learning
12. Microsoft-recommended workflows
13. Power BI UI steps
14. Licensing or service capability questions, with verification if current details matter

---

## How to Use Microsoft Learn in This Project

When answering Power BI questions, use Microsoft Learn for official product guidance.

Prefer Microsoft Learn for:

- UI workflows
- Feature explanations
- Official terminology
- Product limitations
- Power BI Service behavior
- Refresh and gateway concepts
- Workspace and app behavior
- Role and permission concepts
- Microsoft Fabric integration
- Certification-style explanations

Use Microsoft Learn together with SQLBI when the topic involves both product behavior and deeper modeling or DAX reasoning.

Example:

- For “How do I create a relationship in Power BI?” use Microsoft Learn.
- For “What relationship structure should I use for this model?” use SQLBI-style modeling guidance.
- For “Why is this DAX measure returning the wrong total?” use SQLBI-style DAX reasoning.
- For “Where do I configure scheduled refresh?” use Microsoft Learn.

---

## Key Power BI Areas to Track

## 1. Power BI Desktop

Use Microsoft Learn to explain:

- Importing data
- Connecting to data sources
- Transforming data
- Creating visuals
- Creating relationships
- Building reports
- Publishing to Power BI Service

When helping the user with Power BI Desktop, provide:

1. Direct answer
2. Menu path or UI location when known
3. Recommended workflow
4. Common mistake
5. Verification step

Example response structure:

```text
In Power BI Desktop, go to:
Home > Transform Data

Recommended workflow:
1. Connect to the source.
2. Clean and shape data in Power Query.
3. Load only the tables and columns needed.
4. Build relationships in Model view.
5. Create explicit DAX measures.
6. Build report visuals.
