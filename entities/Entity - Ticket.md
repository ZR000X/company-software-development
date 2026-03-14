# Ticket

A **Ticket** is a work item (e.g. in JIRA) that represents a unit of work. It is grouped under an [Epic](Entity%20-%20Epic.md) and can be linked to a [Person](Entity%20-%20Person.md) via an [Assignment](Entity%20-%20Assignment.md).

## Schema

```mermaid
erDiagram
    Epic ||--o{ Ticket : "groups"
    Ticket {
        string id "e.g. JIRA key"
        string summary "title or summary"
        string status "current status"
        string assigneeRef "optional assigned person"
        string epicRef "parent epic"
    }
```
