# Processes

This folder contains **process notes**: Obsidian notes that describe how work is done—steps, conditions, tools, and data models for a given workflow.

## Rules

- **Process-centric content.** Each note describes a single process: its purpose, conditions for when it applies, tools used, data model (if any), and the steps to follow. Processes may link to entity notes (`entities/`) and tool notes (`tools/`) in their descriptions.
- **Conditions.** State any preconditions (e.g. a Project in context, a Team of assignable People) so readers know when the process is doable. Link to the relevant entity notes where appropriate.
- **Link to entities and tools.** Use wikilinks to entity notes and tool notes where they are relevant; do not duplicate entity definitions inside process notes.
- **Naming.** Process note filenames should clearly identify the process (e.g. `Periodic Work Management - Task Updates & Alignment across Workers.md`). The first heading is the process title.

## Structure of a process note

A process note typically includes (in order):

- **Purpose** – What the process achieves and why it exists.
- **Conditions** – Preconditions for when the process is doable (e.g. Project and Team in context). Link to relevant entity notes.
- **Tools** – Tools used in the process, with wikilinks to tool notes (e.g. `[[Tool - JIRA|JIRA]]`).
- **Data Model** – (Optional) Schema or structure (e.g. Excel table, JIRA fields). Use Mermaid if needed.
- **Process** – Numbered steps to follow.

## Before committing a new process

Check that your process note:

- Has an **H1** at the top that matches the process title (filename without `.md`).
- Includes **Purpose**, **Conditions**, **Tools** (with wikilinks to tool notes), **Data Model** (if needed), and **Process** (numbered steps).
- Links to entities and tools via wikilinks; does not duplicate their definitions.
- States **Conditions** clearly so readers know when the process is doable (e.g. Project and Team in context).

Entity and tool notes live in the `entities/` and `tools/` folders and contain only definitions; they do not reference specific processes.
