# Time and Activity Reporting

## Purpose

Summarise and report on [Time Entry](../../entities/time-entry.md) data to give visibility on **capacity** (e.g. time per [Person](../../entities/person.md) or [Team](../../entities/team.md) per period) and **activity concentration** (which [Activity](../../entities/activity.md) types consume the most time). Outputs feed into talent pipeline management; when combined with [Activity](../../entities/activity.md)–[Skill](../../entities/skill.md) mapping, reports can show skills in demand.

## Conditions

This process is doable only when:

- [Time Entry](../../entities/time-entry.md) data exists (from Personal Time and Task Management).
- Optionally: [Activity](../../entities/activity.md) catalogue and activity–skill mapping exist for skill-level insights and talent pipeline linkage.

## Tools

- [Excel](../../tools/Tool%20-%20Microsoft%20Excel.md) (or a BI or reporting tool) for aggregating time entries and producing reports. Exports from JIRA or the time-tracking tool may be used as the data source.

## Data Model

Reports are built from aggregates of [Time Entry](../../entities/time-entry.md) data:

- **Capacity:** time by person (and optionally team), by period (e.g. week, month).
- **Activity concentration:** time by [Activity](../../entities/activity.md) (which activities consume the most time).
- **Skill demand (optional):** combine activity concentration with [Activity–Skill](../../entities/activity-skill.md) mapping to derive demand for [Skill](../../entities/skill.md)s.

No separate Mermaid schema is required if the report structure is tables or pivots in the chosen tool.

## Process

1. **Extract time entries.** Pull [Time Entry](../../entities/time-entry.md) data from the source (JIRA, Excel, or time-tracking tool) for the reporting period.

2. **Aggregate by capacity dimensions.** Summarise time by person (and optionally team) and by period to show capacity.

3. **Aggregate by activity.** Summarise time by [Activity](../../entities/activity.md) to show activity concentration (which activities are in highest demand).

4. **Produce reports or dashboards.** Publish capacity and activity concentration views (and optionally skill-demand views if activity–skill mapping is used).

5. **Feed actionable insights into talent pipeline.** Use the reports to inform the talent inflow pipeline management process (e.g. skills to hire or develop).

## Process dependencies

- [Personal Time and Task Management](./personal-time-and-task-management.md) — source of [Time Entry](../../entities/time-entry.md) data.
- [Activity Catalogue and Skill Mapping](./activity-catalogue-and-skill-mapping.md) — optional; required for skill-level insights and linking activity concentration to skills for talent pipeline.
