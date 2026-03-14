# Epic

An **Epic** in JIRA groups related work. There are 1–many Epics per [Project](project.md). [Tickets](ticket.md) in an Epic can be reflected in an Excel table (e.g. on a JIRA sheet).

## Schema

```mermaid
erDiagram
    Project ||--o{ Epic : "contains"
    Epic ||--o{ Ticket : "groups"
    Epic {
        string id "JIRA epic key"
        string name "epic name"
        string projectRef "parent project"
    }
```

The *Ticket* in the diagram refers to the [Ticket](ticket.md) entity.
