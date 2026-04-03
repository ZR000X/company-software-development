---
title: Customer workstream inflow (CustomerWorkstreamInflowRow)
aliases:
  - customer-workstream-inflow
created: 2026-04-02
updated: 2026-04-03
tags:
  - data
  - schema
  - intake
  - customer
type: data
status: draft
description: >-
  Canonical erDiagram for customer-provided intake rows before or alongside JIRA ticket logging;
  includes classification feedback to the customer and ticket references for accepted work.
---

# Customer workstream inflow (CustomerWorkstreamInflowRow)

Logical **`CustomerWorkstreamInflowRow`** table: one row per line on a **customer-provided issue list** processed by [Customer-facing workstream inflow validation workflow](../processes/workflows/customer-facing-workstream-inflow-validation-workflow.md). This is **upstream** of the **`JIRATickets`** mirror in [work-items.md](work-items.md): when an item is accepted as work and a JIRA issue is created, **`Ticket_Number_Ref`** aligns with **`Ticket_Number`** in that schema.

**Dual outcomes per row:** (1) **`Classification_Feedback_To_Customer`** — text suitable to return to the customer (classification, Epic, acceptance or rejection rationale). (2) **`Ticket_Number_Ref`** and **`Date_Logged`** — the **authoritative JIRA key** for tracked work (**new or pre-existing** issue). **Multiple rows** may share the **same** **`Ticket_Number_Ref`** when several customer lines are **merged** into one ticket, or when an **existing** issue already covers the request. Rows with a key populated are the usual input slice for [Workstream inflow ticket grooming workflow](../processes/workflows/workstream-inflow-ticket-grooming-workflow.md).

```mermaid
erDiagram
    CustomerWorkstreamInflowRow {
        number Line_Number "Row index in the customer list"
        string Module "Functional or product module"
        string Epic "Target Epic key or label after validation"
        string Issue_Name "Short title or summary from the customer"
        string Priority "Customer or assessed priority"
        string Classification "Enhancement Bug Defect Task or team vocabulary"
        string Validation_Status "In-review triaged awaiting-customer etc"
        string Category "Customer or internal category"
        string Issue_Description "Full description text"
        string Action_Owner "Accountable role or person for this line"
        date Date_Received "When the customer line was received"
        string Assigned "Proposed or internal assignee before grooming"
        string Validation_Outcome "Accepted-as-work duplicate-of-existing invalid out-of-scope needs-more-info etc"
        string Classification_Feedback_To_Customer "What is communicated back on classification Epic and acceptance"
        string Ticket_Number_Ref "Empty until linked; new or existing JIRA key; shared across merged rows; aligns with JIRATickets Ticket_Number"
        date Date_Logged "When the key was first set for this row in this intake run"
    }
```
