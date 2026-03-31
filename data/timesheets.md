---
title: Timesheets
aliases:
  - timesheets
created: 2026-03-21
updated: 2026-03-22
tags:
  - data
  - schema
  - timesheets
  - time-entry
type: data
status: draft
description: >-
  Canonical erDiagram for the logical Timesheets table; supports open intervals (null endAt) until session close.
---

# Timesheets

Canonical `erDiagram` for the logical **`Timesheets`** table: one row per [Time Entry](../entities/time-entry.md) segment. **Many rows may share the same `workRef`.** Rows follow the [Main workflow](../processes/main-workflow.md): **`startAt`** is set when the segment **opens**; **`endAt` is null** while work is in progress; **`endAt`** (and **`duration`** if stored) are set when the session **closes**. Completed rows used for reporting must have **`endAt` populated**.

```mermaid
erDiagram
    Timesheets {
        string id "stable row identifier if the tool provides one"
        string agentRef "agent who logged the time"
        string workRef "work item e.g. JIRA ticket key"
        string activityRef "activity classification from catalogue"
        string startAt "segment start datetime e.g. ISO 8601"
        string endAt "segment end datetime null until session closes"
        number duration "optional until close align with startAt and endAt when set"
    }
```
