# Ticket

A **Ticket** is a work item (e.g. in JIRA) that represents a unit of work. It is grouped under an [[Entity - Epic|Epic]] and can be linked to a [[Entity - Person|Person]] via an [[Entity - Assignment|Assignment]].

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
