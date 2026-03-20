# Processes

This folder contains **process notes**: Obsidian notes that describe how work is done—steps, conditions, tools, and data models for a given workflow.

## Rules

- **Process-centric content.** Each note describes a single process: its purpose, conditions for when it applies, tools used, data model (if any), and the steps to follow. Processes may link to entity notes (`entities/`) and tool notes (`tools/`) in their descriptions.
- **Conditions.** State any preconditions (e.g. a Project in context, a Team of assignable People) so readers know when the process is doable. Link to the relevant entity notes where appropriate.
- **Link to entities and tools.** Use standard Markdown links to entity notes and tool notes where they are relevant (e.g. `[JIRA](../tools/Tool%20-%20JIRA.md)` from a process file). Entity links use `../entities/<kebab-name>.md` (e.g. `../entities/process.md`). See [entities/README.md](../entities/README.md) for entity naming conventions. Do not duplicate entity definitions inside process notes.
- **Naming.** Process note filenames should clearly identify the process (e.g. `Periodic Work Management - Task Updates & Alignment across Workers.md`). The first heading is the process title.

## Structure of a process note

A process note typically includes (in order):

- **Purpose** – What the process achieves and why it exists.
- **Conditions** – Preconditions for when the process is doable (e.g. Project and Team in context). Link to relevant entity notes.
- **Tools** – Tools used in the process, with standard Markdown links to tool notes (e.g. `[JIRA](../tools/Tool%20-%20JIRA.md)`).
- **Data Model** – (Optional) Schema or structure (e.g. Excel table, JIRA fields). Use Mermaid per the schema standards below.
- **Process** – Numbered steps to follow.
- **Process dependencies** – List other processes this process depends on. Use standard Markdown links to the process notes (e.g. from a file in `processes/to-do/`, link to another process in the same folder with `./other-process-name.md`, or use the path that resolves correctly to the target process file). If there are no dependencies, state "None." This allows building a process dependency graph.

## Definition / lifecycle process notes

When a process note **defines a lifecycle or status model** (e.g. Workstream Lifecycle Definition):

- Include a **status transition table** (e.g. Status From, Status To, Process).
- Include a **Mermaid schema** (e.g. `erDiagram` for the status-transition table) per the Schema (Mermaid) standards below.
- Use **standard Markdown links** for all entity references; ensure linked entity notes exist in `entities/` (no Obsidian wikilinks; no broken links).
- Follow the same standard sections (Purpose, Conditions, Tools if applicable, Data Model, Process) where they apply.

## Schema (Mermaid) standards

When a process note includes a **Data Model** with a Mermaid diagram for a table or schema:

- **Use `erDiagram`** for table/schema definitions (one entity per table; each row in the table is an instance of that entity).
- **Entity block:** `EntityName {` … `}` where `EntityName` is the table or concept name (e.g. `JIRATickets`, `WorkstreamLifecycleDefinition`).
- **Fields:** one line per column in the form `type fieldName "description"` (e.g. `string statusFromRef "source status"`). Use a short type (`string`, `number`, `date`) and a quoted description so the diagram is self-explanatory.
- **Node IDs and labels:** no spaces in entity or field names; use camelCase or PascalCase. Use double quotes for descriptions or labels that contain special characters (parentheses, slashes, etc.).
- **No styling:** do not add `style`, `classDef`, or theme-specific colors so diagrams render consistently in GitHub and Obsidian.

## Before committing a new process

Check that your process note:

- Has an **H1** at the top that matches the process title (filename without `.md`).
- Includes **Purpose**, **Conditions**, **Tools** (with links to tool notes), **Data Model** (if needed), **Process** (numbered steps), and **Process dependencies**.
- States **Process dependencies** clearly: list dependencies with standard Markdown links to other process notes (using the correct relative path from this process file); if the process has no dependencies, state "None."
- Links to entities and tools via standard Markdown links; does not duplicate their definitions.
- States **Conditions** clearly so readers know when the process is doable (e.g. Project and Team in context).

For **lifecycle/definition notes**, also check: status transition table is present; Mermaid schema matches the table; entity links use standard Markdown and targets exist in `entities/`.

Entity and tool notes live in the `entities/` and `tools/` folders and contain only definitions; they do not reference specific processes.
