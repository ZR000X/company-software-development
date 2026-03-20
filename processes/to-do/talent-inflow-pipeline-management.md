# Talent Inflow Pipeline Management

## Purpose

Manage the talent pipeline: plan and execute hiring or development to meet capacity and [Skill](../../entities/skill.md) demand. This process consumes **capacity** and **activity concentration** from [Time and Activity Reporting](./time-and-activity-reporting.md), and uses [Activity](../../entities/activity.md)–[Skill](../../entities/skill.md) mappings (from [Activity Catalogue and Skill Mapping](./activity-catalogue-and-skill-mapping.md)) to translate demand for activities into demand for skills. Outcome: actionable talent decisions (e.g. which roles or skills to hire or develop) informed by where time is spent and which skills are in demand.

## Conditions

This process is doable only when:

- There is ownership of talent or hiring (e.g. a [Team](../../entities/team.md) or role responsible for the pipeline).
- Inputs from [Time and Activity Reporting](./time-and-activity-reporting.md) are available (capacity and activity concentration); optionally, activity–skill mapping is available for skill-level planning.

## Tools

- [Excel](../../tools/Tool%20-%20Microsoft%20Excel.md) (or a dedicated ATS/HR tool) for tracking pipeline stages and candidates. [JIRA](../../tools/Tool%20-%20JIRA.md) may be used for role or hiring work items if the company tracks them there.

## Data Model

Pipeline data is process-specific (e.g. stages, candidates, roles). The key inputs are the outputs of dependent processes: capacity and activity concentration reports, and activity–skill mapping. No separate Mermaid schema is defined here unless the company standardises a pipeline table.

## Process

1. **Review capacity and activity concentration.** Use reports from [Time and Activity Reporting](./time-and-activity-reporting.md) to see where time is spent and which [Activity](../../entities/activity.md) types are in highest demand.

2. **Translate to skill demand (optional).** If [Activity Catalogue and Skill Mapping](./activity-catalogue-and-skill-mapping.md) is in use, combine activity concentration with activity–skill mapping to identify which [Skill](../../entities/skill.md)s are in demand.

3. **Plan pipeline actions.** Decide on hiring or development actions (e.g. roles to fill, skills to develop) based on capacity gaps and skill demand.

4. **Execute and track.** Run the pipeline (sourcing, assessment, hiring or development) and track progress in the chosen tool.

5. **Revisit periodically.** Re-run reporting and this process to adjust the pipeline as capacity and activity concentration change.

## Process dependencies

- [Time and Activity Reporting](./time-and-activity-reporting.md) — source of capacity and activity concentration used to inform talent decisions.
- [Activity Catalogue and Skill Mapping](./activity-catalogue-and-skill-mapping.md) — optional; source of activity–skill mappings for translating activity demand into skill demand.
