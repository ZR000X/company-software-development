# Workstream

A **Workstream** is a stream of work with defined statuses and transitions (e.g. development, QA, UAT). [Work](Entity%20-%20Work.md) items flow through it; each transition from one status to the next is typically triggered by a [Process](Entity%20-%20Process.md). A company may operate multiple workstreams (e.g. one for new feature development, one for QA findings, one for UAT requests).

## Schema

```mermaid
erDiagram
    Workstream ||--o{ Work : "contains"
    Workstream {
        string id "identifier"
        string name "e.g. Dev, QA, UAT"
        string statuses "ordered list of status values"
    }
```
