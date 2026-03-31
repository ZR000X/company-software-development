---
title: Data (canonical ERDs)
aliases:
  - data-readme
created: 2026-03-21
updated: 2026-03-22
tags:
  - data
  - schema
  - mermaid
type: documentation
status: draft
description: >-
  Canonical Markdown data notes with Mermaid erDiagrams for logical tables referenced from process notes.
---

# Data (canonical ERDs)

This folder holds **Markdown (`.md`) files** whose body includes a Mermaid `erDiagram` that serves as the **authoritative structural** source for logical tables and entities referenced from **process notes** in [`../processes/`](../processes/).

## Purpose

- **Single place for diagrams** — Review schema changes in one file; diff-friendly; preview in Obsidian, GitHub, or other Mermaid-capable viewers.
- **Reusable** — Other docs or tooling can link to or copy from these files without hunting inside long process notes.

## Relationship to process notes

- The **process** still owns **when** data is read or written, **preconditions**, **tools**, and **steps**.
- The **data note** (this folder’s `.md` file) owns **column names, types, and short field descriptions** as expressed in `erDiagram` syntax inside a fenced `mermaid` block.
- Process notes should **link** here for the full diagram and keep a **human-readable summary** (e.g. a column/description table) so the process remains reviewable on its own.

## Conventions

- **Naming** — Prefer one logical artifact per file when the concepts differ (e.g. `work-items.md` for an Excel/JIRA ticket mirror; a separate file for a steering-report entity).
- **Format** — One fenced `mermaid` block per file (after an optional title and short intro), containing an `erDiagram` with the entity block(s) for that artifact. Group multiple entities in one file only when they are always versioned and reviewed together.
- **Syntax** — Follow [`../standards/processes.md`](../standards/processes.md) (Schema / Mermaid): `string`, `number`, `date`; no spaces in entity or field names; no diagram styling directives.

## Linking from `processes/`

From a file in `processes/`, use relative paths such as:

`[../data/work-items.md](../data/work-items.md)`

## Contents

| File | Describes |
| ---- | --------- |
| [work-items.md](work-items.md) | `JIRATickets` logical model (JIRA keys in `Ticket_Number`); used in [Workstream ticket update workflow](../processes/workflows/workstream-ticket-update-workflow.md) and for key semantics in [Data fix workflow](../processes/workflows/data-fix-workflow.md). |
| [timesheets.md](timesheets.md) | `Timesheets` logical model ([Time Entry](../entities/time-entry.md)–shaped rows: `agentRef`, `workRef`, `activityRef`, `startAt`, nullable `endAt` until close, duration; many rows per `workRef`); canonical schema for [Main workflow](../processes/main-workflow.md). |
| [workstream-management-report.md](workstream-management-report.md) | `WorkstreamManagementReport` logical output for steering visibility in the same process. |
