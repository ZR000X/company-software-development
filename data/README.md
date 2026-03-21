# Data (canonical ERDs)

This folder holds **`.mmd` files** containing Mermaid `erDiagram` definitions that serve as the **authoritative structural** source for logical tables and entities referenced from **process notes** in [`../processes/`](../processes/).

## Purpose

- **Single place for diagrams** — Review schema changes in one file; diff-friendly; preview in Obsidian, GitHub, or other Mermaid-capable viewers.
- **Reusable** — Other docs or tooling can link to or copy from these files without hunting inside long process notes.

## Relationship to process notes

- The **process** still owns **when** data is read or written, **preconditions**, **tools**, and **steps**.
- The **`.mmd` file** owns **column names, types, and short field descriptions** as expressed in `erDiagram` syntax.
- Process notes should **link** here for the full diagram and keep a **human-readable summary** (e.g. a column/description table) so the process remains reviewable on its own.

## Conventions

- **Naming** — Prefer one logical artifact per file when the concepts differ (e.g. `work-items.mmd` for an Excel/JIRA ticket mirror; a separate file for a steering-report entity).
- **Format** — One fenced `mermaid` block per file, containing an `erDiagram` with the entity block(s) for that artifact. Group multiple entities in one file only when they are always versioned and reviewed together.
- **Syntax** — Follow [`../standards/processes.md`](../standards/processes.md) (Schema / Mermaid): `string`, `number`, `date`; no spaces in entity or field names; no diagram styling directives.

## Linking from `processes/`

From a file in `processes/`, use relative paths such as:

`[../data/work-items.mmd](../data/work-items.mmd)`

## Contents

| File | Describes |
| ---- | --------- |
| [work-items.mmd](work-items.mmd) | `JIRATickets` logical model (JIRA keys in `Ticket_Number`); used in [Workstream management](../processes/workstream-management.md) and for key semantics in [Data fix workflow](../processes/data-fix-workflow.md). |
| [workstream-management-report.mmd](workstream-management-report.mmd) | `WorkstreamManagementReport` logical output for steering visibility in the same process. |
