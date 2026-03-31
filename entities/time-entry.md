---
title: Time Entry
aliases:
  - time-entry
created: 2026-03-21
updated: 2026-03-22
tags:
  - entities
  - time-tracking
  - work
type: entity
status: draft
description: >-
  Time on work classified by activity; startAt set when opened, endAt null until the session is closed.
---

# Time Entry

A **Time Entry** records time spent by a [Person](person.md) on a unit of [Work](work.md), classified by an [Activity](activity.md). In the [Main workflow](../processes/main-workflow.md) model, a row **opens** with **start** datetime set and **`endAt` null** while work runs, then **closes** with **`endAt`** (and usually **duration**) set when the session ends—whether the underlying work finished or not. Many entries may refer to the same work item. Time entries support capacity and activity concentration reporting when intervals are **closed** (`endAt` set).

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
        string startAt "segment start datetime e.g. ISO 8601"
        string endAt "segment end datetime null until session closes"
        number duration "optional until close align with startAt and endAt when set"
    }
```
