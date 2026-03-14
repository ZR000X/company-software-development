# Membership

A **Membership** links a [Person](person.md) to a [Team](team.md) with a specific [Role](role.md) and an optional description. It represents that a person is part of a team in a given capacity.

## Schema

```mermaid
erDiagram
    Person ||--o{ Membership : "has"
    Team ||--o{ Membership : "has"
    Role ||--o{ Membership : "used in"
    Membership {
        string id "identifier"
        string personRef "person"
        string teamRef "team"
        string roleRef "role"
        string description "optional description"
    }
```
