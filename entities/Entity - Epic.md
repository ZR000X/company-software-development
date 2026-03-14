# Epic

An **Epic** in JIRA groups related work. There are 1–many Epics per [Project](Entity%20-%20Project.md). [Tickets](Entity%20-%20Ticket.md) in an Epic can be reflected in an Excel table (e.g. on a JIRA sheet).

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

The *Ticket* in the diagram refers to the [Ticket](Entity%20-%20Ticket.md) entity.
