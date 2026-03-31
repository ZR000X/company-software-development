---
title: Data fix workflow
aliases:
  - data-fix-workflow
created: 2026-03-21
updated: 2026-03-21
tags:
  - processes
  - data
  - jira
type: process
status: draft
description: >-
  Controlled data fixes tied to JIRA tickets, with snapshots, DEV deploy, and ticket updates.
---

# Data fix workflow

## Purpose

Apply **controlled data fixes** that are tied to a tracked [Ticket](../../entities/ticket.md) in [JIRA](../../tools/Tool%20-%20JIRA.md). The workflow gathers context, snapshots affected data **before** changes, implements and reviews the change, deploys to **DEV**, and updates the ticket so the next owner has a clear handoff. **State touched** (JIRA keys, backups, datasets) is summarized under **Data Model**.

## Conditions

This process is doable only when:

- A JIRA **ticket exists** for the data fix and describes (or can describe) what must change.
- The implementer can access **JIRA**, the **affected datasets**, the path to **deploy to DEV**, and their **tooling** (e.g. Cursor or another IDE).
- The scope of **affected datasets** is clear enough to take **meaningful backups** before modification.

## Tools

- [JIRA](../../tools/Tool%20-%20JIRA.md) — Authoritative work item for the fix, comments, status, and assignee.
- **Backup storage** — Location for JSON snapshot files (see **Data Model** and **Process** step 4).
- **DEV environment** — Target for deploying the change when applicable.
- **Cursor** (or another IDE with AI assist) — Optional accelerator for editing; human review remains required.

## Impact

- **Traceability** — Every fix is anchored to a JIRA ticket, not a silent edit.
- **Recovery** — Pre-change JSON snapshots support rollback or comparison if something goes wrong.
- **Handoffs** — Ticket updates and reassignment make the next step obvious for other [People](../../entities/person.md).
- **Quality** — Explicit review and DEV deployment reduce the chance of unvetted changes reaching wider use.

## Cost

**Runtime (typical instance):** often **tens of minutes to a few hours**, depending on how much discovery is needed, how large or complex the datasets are, how deep the review is, and how involved DEV deployment is. Simple, well-specified fixes sit at the low end; cross-team clarification or large exports sit at the high end.

## Skills required

Capabilities the running agent needs (mappable to [Skill](../../entities/skill.md) notes as you add them):

- **JIRA hygiene** — Comments, status, assignee, and subtasks kept accurate.
- **Stakeholder communication** — Fast clarification when requirements are ambiguous.
- **Data and backup discipline** — Naming and storing snapshots consistently before mutating data.
- **Careful implementation and self-review** — Own correctness before deploy; use tooling without skipping review.
- **DEV deployment** — Know how to promote the change to DEV safely for your stack.

## Data Model

### JIRA ticket keys

JIRA issue keys used in this process (for the ticket itself and in backup filenames) follow the same semantics as **`Ticket_Number`** on the **`JIRATickets`** logical entity. The canonical `erDiagram` lives in [../../data/work-items.md](../../data/work-items.md). Conventions for data notes: [../../data/README.md](../../data/README.md).

**Backup files:** before changing data, write one JSON snapshot per affected dataset (or agreed slice), named:

`YYYY-MM-DD-<JIRA-KEY>.json`

Example: `2026-03-16-FS-1234.json`. The `<JIRA-KEY>` segment must match the project key + number form you use in JIRA and align with `Ticket_Number` in [work-items.md](../../data/work-items.md).

### Artifacts this process reads and writes

| Artifact | Role |
| -------- | ---- |
| JIRA ticket | Read for scope; write comments, status, assignee, checklists, doc links |
| Pre-change JSON backups | Write before mutation; read only if comparing or rolling back |
| Affected datasets | Read pre-state from backups’ source; write the applied fix |
| DEV deployment | Write/publish the change per your environment’s mechanism |

No separate `change-log.csv` (or equivalent) is required by this process.

## Process

1. **Confirm the ticket.** A JIRA ticket exists and identifies the data fix (scope, acceptance, or a path to get there).

2. **Understand the ask.** If anything is unclear, **comment on the ticket** and **reach out** to the right people for quick clarification.

3. **Record context on the ticket.** Add or update the ticket with what you learned in step 2 so the record stays complete.

4. **Snapshot before change.** For each affected dataset (or agreed unit), create a backup file named `YYYY-MM-DD-<JIRA-KEY>.json` capturing state **before** the change. Use the same JIRA key form as `Ticket_Number` in [../../data/work-items.md](../../data/work-items.md). Complete this **before** applying the fix.

5. **Implement and review.** Make the change (e.g. using Cursor for speed). **Review** the diff or result and **take responsibility** for accuracy.

6. **Deploy to DEV.** Deploy the change to **DEV** as required by your environment and the ticket.

7. **Close the loop in JIRA.** Comment with what changed, set the **correct status**, **reassign** to the next person who must act, and update **checklists**, **subtasks**, and **documentation links** on the ticket as needed.

Testing, promotion beyond DEV, and production decisions are **out of scope** for this note: they should be done, tracked, and decided in a **separate process**.

## Process dependencies

**None.**
