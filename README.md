# Power BI Lab

A working set of instructions, playbooks, prompts and templates for doing Power BI work with an AI assistant: semantic models, star schemas, DAX, Power Query, Deneb visuals and executive report design.

It is set up as a project workspace. Load `PROJECT_INSTRUCTIONS.md` as the assistant's instructions, add the folders as project files, and then ask in plain language or paste one of the prompts.

## What is in it

| Folder | Contents |
|---|---|
| `playbooks/` | Step-by-step workflows the assistant follows: DAX debugging, semantic model review, star schema design, Deneb visual building, dashboard critique, Power Query optimisation, report style, and a ten-level learning game. |
| `prompts/` | Ready-to-paste prompts that start a session, such as `fix_my_dax.md`, `review_my_model.md`, `build_deneb_visual.md` and `dashboard_requirements_intake.md`. |
| `templates/` | Blank forms and starting specs: star schema blueprint, model and measure review templates, a report design checklist, and Deneb spec templates including a bullet chart. |
| `sources/` | Which reference to use for which question: Microsoft Learn for product behaviour, SQLBI for DAX and modelling, the Deneb and Vega-Lite documentation for custom visuals. |
| `outputs/` | Worked examples produced with the lab. |

`PROJECT_INDEX.md` lists every file and when to use it.

## Examples

- [`outputs/deneb_specs/rag_kpi_card_actuals_vs_budget.json`](outputs/deneb_specs/rag_kpi_card_actuals_vs_budget.json): a Deneb KPI card showing actuals against budget with red, amber and green status.
- [`outputs/dashboard_critiques/project_cost_dashboard_requirements.md`](outputs/dashboard_critiques/project_cost_dashboard_requirements.md): requirements for a project cost dashboard, written from the intake prompt.

## Sources

Microsoft Learn (Power BI), SQLBI, and the Deneb, Vega and Vega-Lite documentation. The lab points to these sources; it does not copy them.
