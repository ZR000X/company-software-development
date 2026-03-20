# Time Entry

A **Time Entry** records time spent by a [Person](person.md) on a unit of [Work](work.md), classified by an [Activity](activity.md). It has a duration and a period (e.g. date or week). Time entries enable "time against work" tracking and support capacity and activity concentration reporting.

## Schema

```mermaid
erDiagram
    Person ||--o{ TimeEntry : "logs"
    Work ||--o{ TimeEntry : "has time logged"
    Activity ||--o{ TimeEntry : "classifies"
    TimeEntry {
        string id "identifier"
        string personRef "person who logged the time"
        string workRef "work item"
        string activityRef "activity classification"
        number duration "time spent e.g. hours"
        date period "date or period"
    }
```
