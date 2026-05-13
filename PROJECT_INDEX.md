# Power BI Lab — Project Index

A practical reference for what every file and folder does and when to use each one.

---

## 📁 sources/

**What it's for:** Defines the authoritative references this project uses. These files tell me which source to draw from for which type of question, and how to prioritize them.

| File | Purpose | Use When |
|---|---|---|
| `source_map.md` | Master map of which source to use for which topic | You want to know where a specific type of answer comes from |
| `sqlbi_reference.md` | How to use SQLBI — DAX, VertiPaq, modeling, filter context | Advanced DAX, semantic modeling, performance optimization |
| `microsoft_learn_power_bi.md` | How to use Microsoft Learn — official Power BI guidance | Feature questions, UI workflows, Power BI Service, licensing |
| `deneb_reference.md` | How to use Deneb/Vega/Vega-Lite documentation | Building or troubleshooting any Deneb custom visual |

---

## 📁 playbooks/

**What it's for:** Step-by-step operating procedures I follow when you ask me to do something complex. Each playbook is a structured workflow for a specific type of task. These run in the background — you don't need to reference them directly.

| File | Purpose | Use When |
|---|---|---|
| `dax_debugger.md` | Systematic DAX diagnosis and fix workflow | You share a broken or wrong DAX measure |
| `semantic_model_architect.md` | Full model review and design workflow | You share a model for review or are designing from scratch |
| `star_schema_designer.md` | Converting raw/messy data into a clean star schema | You share flat files, SQL exports, or business requirements |
| `deneb_visual_builder.md` | End-to-end Deneb visual creation workflow | You want a custom Vega-Lite visual built |
| `dashboard_critic.md` | Structured report/dashboard critique workflow | You share a report screenshot or layout for feedback |
| `report_style_guide.md` | Design standards for executive-ready reports | You want design guidance or polish on a report page |
| `power_query_optimizer.md` | Power Query/M diagnosis and optimization workflow | You share M code or transformation logic to improve |
| `power_bi_learning_game.md` | Interactive 10-level learning game workflow | You start a game session |

---

## 📁 prompts/

**What it's for:** Ready-to-use prompts for common tasks. Copy one of these into the chat (or just describe what you want — I'll know which one applies) to kick off a structured session.

| File | Purpose | Use When |
|---|---|---|
| `fix_my_dax.md` | Paste a DAX measure and get a full debug + rewrite | Your measure is returning wrong results or errors |
| `review_my_model.md` | Share your model structure for a full architectural review | You want an honest assessment of your semantic model |
| `create_star_schema.md` | Submit raw tables or requirements and get a star schema design | Starting a new model or refactoring a bad one |
| `build_deneb_visual.md` | Request a Deneb custom visual with full spec | You need a chart type Power BI can't do natively |
| `daily_power_bi_coach.md` | Trigger a daily lesson on any Power BI topic | You want a focused 5–10 minute learning session |
| `power_bi_game_session.md` | Start a scored, leveled game session | You want to learn through challenges and scenarios |
| `dashboard_requirements_intake.md` | Gather requirements before building a new dashboard | Starting a new report project |
| `polish_my_report.md` | Submit a report for design critique and improvement suggestions | Your report works but doesn't look executive-ready |
| `performance_review.md` | Diagnose slow reports, heavy DAX, or slow refresh | You have performance problems anywhere in the stack |
| `power_query_help.md` | Get help with M code, transformations, or query folding | You're stuck in Power Query |
| `power_bi_service_help.md` | Get help with workspaces, refresh, apps, or deployment | You have a Power BI Service or governance question |

---

## 📁 templates/

**What it's for:** Fill-in-the-blank structured documents for common Power BI deliverables. Use these to give me well-organized inputs, or as starting points for your own documentation.

| File | Purpose | Use When |
|---|---|---|
| `dax_measure_review_template.md` | Structured format for submitting a DAX measure for review | You want a thorough DAX analysis, not just a quick fix |
| `semantic_model_review_template.md` | Full model review document with all key dimensions | You want a written model assessment you can save or share |
| `star_schema_blueprint_template.md` | Blueprint document for a new star schema design | Designing or documenting a new model |
| `dashboard_requirements_template.md` | Intake form for a new dashboard project | Kicking off a new report — captures audience, KPIs, filters |
| `executive_dashboard_layout_template.md` | Layout planning template for an executive dashboard | Mapping out what goes where before building in Power BI |
| `report_design_checklist.md` | Pre-publish checklist for report quality and polish | Before you share or publish any report |
| `deneb_visual_requirements_template.md` | Structured brief for requesting a Deneb visual | When you want a custom visual built and need to spec it out |
| `deneb_spec_template.json` | Blank Vega-Lite JSON starting point for a new Deneb visual | When building a custom Deneb visual from scratch |
| `deneb_bullet_chart_template.json` | Pre-built Vega-Lite bullet chart spec | When you need a bullet chart specifically |
| `power_query_transformation_template.md` | Structured brief for a Power Query transformation | Describing what a query needs to do before writing M code |

---

## 📁 outputs/

**What it's for:** Where I save completed work from our sessions. Organized by work type so you can find past deliverables easily.

| Subfolder | What Gets Saved There |
|---|---|
| `dax_reviews/` | Debugged and optimized DAX measures |
| `model_review/` | Semantic model assessments and star schema designs |
| `deneb_specs/` | Completed Vega-Lite JSON specs |
| `dashboard_critiques/` | Report and dashboard critique write-ups |
| `learning_sessions/` | Daily lessons, game session recaps |
| `power_query_reviews/` | Optimized M code and transformation write-ups |

---

*Last updated: May 2026*
