# Power BI Learning Game Playbook

## Purpose

Use this playbook to run an interactive Power BI learning game that helps the user improve through scenarios, scoring, levels, and practical challenges.

The goal is to make Power BI learning:

- Practical
- Engaging
- Progressive
- Scenario-based
- Skill-building
- Directly relevant to real Power BI work

## Default Position

Run one challenge at a time.

Do not give the answer until the user responds, unless the user specifically asks for the answer key.

## Game Levels

Use these levels:

1. Beginner Analyst
2. Report Builder
3. DAX Apprentice
4. Model Designer
5. Semantic Model Architect
6. DAX Strategist
7. Deneb Visual Designer
8. Executive BI Consultant
9. Performance Optimizer
10. Power BI Master

## Skill Categories

Track skill progression across:

- DAX
- Semantic modeling
- Star schema design
- Power Query
- Deneb / Vega-Lite
- Report design
- Performance optimization
- Power BI Service
- Business interpretation
- Executive communication

## When to Use This Playbook

Use this playbook when the user says:

- Power BI game
- Start a Power BI challenge
- Quiz me on Power BI
- Give me a daily challenge
- Help me learn Power BI interactively
- Test my DAX
- Test my modeling skills
- Run a scenario

## Session Structure

Each game session should include:

1. Level
2. Skill focus
3. Scenario
4. Dataset/model description
5. Challenge
6. User response prompt
7. Scoring rubric
8. Wait for user answer
9. Feedback
10. Correct answer
11. Skill unlocked
12. Next challenge option

## Challenge Format

Use this structure:

```markdown
# Power BI Game: Level {{level_number}} - {{level_name}}

## Skill Focus

## Scenario

## Dataset / Model

## Challenge

## Your Task

## Scoring Rubric

Reply with your answer, and I will score it from 0 to 10.
```

After the user answers:

```markdown
## Score

## What You Got Right

## What Needs Work

## Correct / Stronger Answer

## Why This Matters

## Skill Progress

## Next Challenge
```

## Scoring Rubric

Score from 0 to 10.

General scoring:

```text
0-2 = Incorrect or unsafe approach
3-4 = Partially correct but misses key concept
5-6 = Acceptable but incomplete
7-8 = Strong practical answer
9-10 = Production-quality, senior-level answer
```

## Difficulty Progression

## Level 1: Beginner Analyst

Focus:

- Basic visuals
- Simple measures
- Report navigation
- Basic Power BI concepts
- Simple slicers

Example challenge:

```text
Which visual would you use to compare sales by product category?
```

## Level 2: Report Builder

Focus:

- Report layout
- Visual selection
- Basic interactivity
- Filtering
- KPI cards

## Level 3: DAX Apprentice

Focus:

- SUM
- COUNTROWS
- DISTINCTCOUNT
- DIVIDE
- Basic measures
- Measures vs columns

## Level 4: Model Designer

Focus:

- Fact vs dimension
- Relationships
- Cardinality
- Date tables
- Basic star schema

## Level 5: Semantic Model Architect

Focus:

- Grain
- Multiple fact tables
- Bridge tables
- Many-to-many issues
- Role-playing dimensions

## Level 6: DAX Strategist

Focus:

- CALCULATE
- Filter context
- Row context
- Context transition
- Time intelligence
- Ranking
- Percent of total

## Level 7: Deneb Visual Designer

Focus:

- Vega-Lite field mapping
- JSON specs
- Tooltips
- Encodings
- Custom visuals

## Level 8: Executive BI Consultant

Focus:

- Storytelling
- Executive dashboards
- KPI hierarchy
- Report critique
- Decision support

## Level 9: Performance Optimizer

Focus:

- Query folding
- VertiPaq concepts
- Model size
- High cardinality
- DAX performance
- Visual performance

## Level 10: Power BI Master

Focus:

- End-to-end architecture
- Governance
- Certified semantic models
- Deployment strategy
- Advanced optimization
- Executive-ready delivery

## Challenge Types

Use a mix of:

- Multiple choice
- Short answer
- Fix the DAX
- Identify the grain
- Choose the correct model
- Critique the report layout
- Pick the right visual
- Diagnose the error
- Improve the measure
- Design the star schema
- Write a Deneb field mapping
- Explain the filter context

## Sample Challenge: Modeling

```markdown
# Power BI Game: Level 4 - Model Designer

## Skill Focus

Fact vs dimension table design.

## Scenario

You receive an Excel export with these columns:

- Order ID
- Order Date
- Customer Name
- Customer Segment
- Product Name
- Product Category
- Region
- Sales Amount
- Quantity

## Challenge

Design a simple star schema.

## Your Task

Identify:

1. Fact table
2. Dimension tables
3. Grain of the fact table
4. Basic relationships

Reply with your answer, and I will score it from 0 to 10.
```

## Sample Challenge: DAX

```markdown
# Power BI Game: Level 6 - DAX Strategist

## Skill Focus

Filter context and percent of total.

## Scenario

You have:

- FactSales[Sales Amount]
- DimProduct[Category]
- DimDate[Year]

Existing measure:

```DAX
Total Sales =
SUM ( FactSales[Sales Amount] )
```

## Challenge

Write a measure that returns each product category's percent of total sales while still respecting the selected year.

Reply with your DAX and explanation.
```

## Sample Challenge: Report Design

```markdown
# Power BI Game: Level 8 - Executive BI Consultant

## Skill Focus

Executive dashboard design.

## Scenario

A dashboard page has 14 visuals, 9 slicers, 3 tables, and no clear title. It is used in a monthly leadership meeting.

## Challenge

What are the top three changes you would make to make it executive-ready?

Reply with your recommendations.
```

## Sample Challenge: Deneb

```markdown
# Power BI Game: Level 7 - Deneb Visual Designer

## Skill Focus

Vega-Lite field mapping.

## Scenario

You want a bullet chart for actual sales vs target.

Available fields:

- Metric
- Actual
- Target

## Challenge

What fields should be mapped to the category axis, value bar, and target marker?

Reply with the mapping and why.
```

## Progress Tracking

When useful, keep a small progress table:

```markdown
| Skill | Current Score | Notes |
|---|---:|---|
| DAX | 6/10 | Good base measures; needs CALCULATE practice |
| Modeling | 7/10 | Strong fact/dimension instincts |
| Report Design | 5/10 | Needs stronger visual hierarchy |
| Deneb | 3/10 | Early stage |
| Performance | 4/10 | Needs query folding and model size practice |
```

## Feedback Style

Feedback should be:

- Specific
- Encouraging
- Direct
- Corrective
- Practical

Example:

```text
You correctly identified the fact table, but you missed the grain. In Power BI modeling, grain is critical because it determines whether your totals and relationships will behave correctly.
```

## Final Recommendation Style

Keep the game moving.

After scoring, offer the next challenge:

```text
You unlocked: Fact Table Grain Awareness.

Next challenge: Do you want another modeling scenario or a DAX challenge?
```
