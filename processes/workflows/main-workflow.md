---
title: Main workflow
aliases:
  - main-workflow
  - agent-time-tracking-workflow
created: 2026-03-21
updated: 2026-03-22
tags:
  - processes
  - time-tracking
  - activity
  - meta
type: process
status: draft
description: >-
  Base operating loop for an agent: open a timesheet row, substitute another workflow for the work,
  then close the row when the session ends—whether work finished or not.
---

# Main workflow

## Purpose

Define the **default operating loop** for any **agent** (per the [Processes README](../README.md): person, team, or human-supervised automation). This workflow is not “log after the fact only”: it **frames** how the agent works. Each pass through the loop **opens** a [Time Entry](../../entities/time-entry.md) on the logical **Timesheets** table **before** the substantive work, leaves **`endAt` unset (null)** while work runs, then **closes** the row when the session ends—whether the underlying work was **completed**, **interrupted**, **blocked**, or paused by choice. A **substitution step** stands in for whichever concrete process applies (coding, [Data fix workflow](./data-fix-workflow.md), etc.), so this note is the **main** workflow inside which other workflows run. A human agent is a [Person](../../entities/person.md). Outcome: auditable segments of time against [Work](../../entities/work.md) and [Activity](../../entities/activity.md), feeding [Time and activity reporting](./time-and-activity-reporting.md).

## Conditions

This process is doable only when:

- An **agent** is in context (`agentRef`).
- You can name the [Work](../../entities/work.md) (e.g. [Ticket](../../entities/ticket.md)) and [Activity](../../entities/activity.md) for **this session slice** before the substitution step.
- The tool supports **creating a row with a null `endAt`** and **updating it later** (or an equivalent pattern).
- An [Activity](../entities/activity.md) catalogue exists (see Process dependencies).

## Tools

- [JIRA](../../tools/Tool%20-%20JIRA.md) and/or [Excel](../../tools/Tool%20-%20Microsoft%20Excel.md) (or another time-tracking store) that can hold **Timesheets**-shaped rows with nullable `endAt` until updated.

## Impact

- **Traceability** — Every substituted workflow run is tied to an explicit open–closed time segment on a work item.
- **Reporting** — [Time and activity reporting](./time-and-activity-reporting.md) receives completed intervals (`startAt` and `endAt` both set) when sessions are closed properly.
- **Honest partial work** — Incomplete work still yields a closed segment for the time actually spent, instead of only logging when work is “done.”

## Cost

**Runtime:** unbounded per loop—driven entirely by the substituted workflow and how long the session lasts. **Overhead** of this shell is small: **1–3 minutes** to open and later close a row if the tool is at hand; failing to close rows leaves **open intervals** that break reporting until corrected.

## Skills required

- **Session discipline** — Always **close** the row opened this session (set `endAt`) when stopping, even on interrupt or failure.
- **Substitution judgment** — Pick the right concrete workflow for the ticket or task and execute it inside the loop.
- **Work and activity choice** — Align `workRef` and `activityRef` with what you are about to do in the substitution step.
- **Tool proficiency** — Create partial rows and patch them without losing the row id needed for the final update.

## Data Model

Each loop pass targets one **Timesheets** row: **`startAt`** set when the row is **opened** (before substitution); **`endAt` null** while the substituted workflow runs; **`endAt`** and **`duration`** (if stored) set when the session **ends**. Many rows may share the same `workRef`. Canonical fields: [../../data/timesheets.md](../../data/timesheets.md).

## Process

1. **Select work and activity for this session.** Choose the [Work](../../entities/work.md) (e.g. ticket) and the [Activity](../../entities/activity.md) that describe the slice of effort you are about to spend.

2. **Open a timesheet row (before substitution).** Insert a **Timesheets** row with `agentRef`, `workRef`, `activityRef`, **`startAt`** set to now (or agreed session start), and **`endAt` left null**. Keep the **row identifier** (`id` or tool key) for the closing step. Optionally leave **duration** unset until close.

3. **Substitute: run the workflow required for the work.** *Replace this step with the concrete process* that matches the task (e.g. implement a feature, run [Data fix workflow](./data-fix-workflow.md), facilitate a meeting). Work for some time; the underlying item may **not** be finished when you stop.

4. **Close the timesheet row (end of main-workflow session).** When you stop this session—for **any** reason (completed work, interrupt, cannot continue, end of day)—update **the same row**: set **`endAt`**, and set **`duration`** if your model stores it explicitly (it should be consistent with `startAt` and `endAt`).

5. **Loop or stop.** If you will start another session (same or different work), return to **step 1**. Otherwise end.

## Process dependencies

- [Activity Catalogue and Skill Mapping](../to-do/activity-catalogue-and-skill-mapping.md) — so [Activity](../../entities/activity.md) values exist for step 1.
