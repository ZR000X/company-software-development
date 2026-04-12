# Processes

This folder holds **process notes**: written definitions of *how work is done*—preconditions, tools, data shapes, numbered steps, and links to other processes. They are operational siblings to **principles** in [`../principles/`](../principles/), which explain *why* we think a certain way.

Normative rules and Mermaid schema detail also live in **[`../standards/processes.md`](../standards/processes.md)**. This README is the quick, explicit template for authors; when in doubt, the standards file wins.

## Why processes belong in this repository

Following [Written principles and written debate](../principles/01-written-principles.md), durable alignment scales better when expectations are **written**, **reviewable**, and **versioned** (e.g. in Git) than when they exist only in meetings or chat. A process note is the shared baseline: people can read the same steps, propose changes via diff, and link to entities and tools unambiguously.

[Business as process—and process as data](../principles/02-business-as-process-and-process-as-data.md) treats a process as **operations that change the state of the business**—usefully imagined as transactions against an implicit (or explicit) data model. A serious process definition should name **what data or records are read and written**, **what impact** it provides (revenue is not the only kind; alignment, risk reduction, and compliance count), and **what it costs** in **time per run** and **skills** required of the running agent (person, team, or human-supervised automation). The sections below encode that expectation.

[Process versus improvisation](../principles/03-process-vs-improv.md) reminds us that **how much** process to encode depends on context; this template is the shape when you *do* encode a workflow, not a mandate to maximal ceremony everywhere.

## Folder layout

- **`processes/`** (this directory) — Active or adopted process definitions you expect people to follow.
- **`processes/to-do/`** — Drafts and work-in-progress; promote to `processes/` when the note meets the checklist below.

Meta-documents (e.g. [process-dependencies.md](process-dependencies.md)) may sit in `processes/` to describe conventions or aggregate graphs; they are **not** required to use every section of a runnable process.

## Standard structure of a process note

Each **runnable** process is one Markdown file. Use a single **H1** as the process title. The filename should clearly identify the process (often aligned with the H1; kebab-case `.md` is typical).

YAML frontmatter is **optional**. When present, use a consistent key set with nearby process notes (commonly `title`, `aliases`, `created`, `updated`, `tags`, `type`, `status`, `description`). Frontmatter supplements metadata; runnable behavior stays in the H1 + sectioned body.

Sections use **level-2 headings** in this **default order**:

| Order | Heading | Required | Purpose |
| ----- | ------- | -------- | ------- |
| 1 | `## Purpose` | Yes | What the process achieves and why it exists. Optionally point to **Data Model** for what state is touched. |
| 2 | `## Conditions` | Yes | When the process is doable (e.g. Project and Team in context). Use bullets; link to [`../entities/`](../entities/) notes. |
| 3 | `## Tools` | Yes | Tools used, with links to [`../tools/`](../tools/) tool notes (e.g. `[JIRA](../tools/Tool%20-%20JIRA.md)`). If none, state that explicitly. |
| 4 | `## Impact` | Yes | Who benefits, what decisions or outcomes the process enables, and legitimate non-revenue value (risk, compliance, alignment, quality) where relevant. |
| 5 | `## Cost` | Yes | **Runtime (per instance):** order-of-magnitude or range (e.g. minutes to hours), typical cadence, and what drives variance (scope, path). Full P&amp;L is not required—enough to reason about capacity. |
| 6 | `## Skills required` | Yes | Capabilities the **running agent** needs (human, team, or supervised automation). Phrase as skills or competencies, not vague personality traits. Link to [`../entities/skill.md`](../entities/skill.md) when a named [Skill](../entities/skill.md) note exists; otherwise use clear inline labels mappable to skills later. |
| 7 | `## Data Model` | Yes | What logical records, fields, or handoffs are **read or written** (process as data manipulation). Use Mermaid `erDiagram` when it helps (see [standards](../standards/processes.md)). If there is no persistent table, still document **inputs, outputs, and state transitions** in prose or a minimal diagram—the section must not be empty boilerplate. |
| 8 | `## Process` | Yes | Numbered steps to execute in order. |
| 9 | `## Process dependencies` | Yes | Other processes this one depends on, as Markdown links with correct relative paths; if none, write **None.** |

Do not use a separate `## Behavioural` section; supersede it with **Skills required**.

### Relative links

From a file in **`processes/`**:

- Entities: `../entities/<name>.md`
- Tools: `../tools/Tool%20-%20<Name>.md` (match actual filenames)
- Another process in `processes/`: `./other-process.md`

From a file in **`processes/to-do/`**:

- Same entity/tool patterns (`../entities/`, `../tools/`)
- Peer in `to-do/`: `./sibling.md`
- Adopted process in parent folder: `../adopted-process.md`

Do not use Obsidian wikilinks in committed notes; use standard Markdown links only.

### Lifecycle / definition processes

When the note **defines a status model** (e.g. [workstream-lifecycle-definition.md](workstream-lifecycle-definition.md)):

- Include a **status transition table** (e.g. Status From, Status To, Process).
- Include a **Mermaid `erDiagram`** that matches that table (see [standards](../standards/processes.md)).
- Use the same runnable sections where they apply, including **Impact** (shared vocabulary, enforcement surface, who consumes the model), **Cost** (effort to maintain or apply the definition), and **Skills required** (who can author or steward lifecycles).
- Still use **Purpose**, **Conditions**, **Tools** (if any), **Data Model**, **Process**, and **Process dependencies** where they apply.

### Mermaid (`erDiagram`) summary

- One entity block per table or concept; each **row** in the real-world table is an **instance** of that entity.
- Fields: `type fieldName "short description"` per line; use `string`, `number`, `date`; no spaces in names (camelCase / PascalCase).
- No `style`, `classDef`, or theme colors (GitHub/Obsidian consistency).

Full detail: [`../standards/processes.md`](../standards/processes.md) (Schema section).

## Process dependency graph

Every runnable note must include **`## Process dependencies`** so the graph stays maintainable. Summaries or diagrams may be maintained in [process-dependencies.md](process-dependencies.md); individual notes remain the source of truth for their own dependencies.

## Checklist before you commit a new process

- [ ] **H1** matches the process title (and filename is clear).
- [ ] **Purpose**, **Conditions**, **Tools**, **Impact**, **Cost**, **Skills required**, **Data Model**, **Process**, and **Process dependencies** are present (Tools can say “None” if appropriate).
- [ ] **Data Model** explicitly describes state read or written—not an empty placeholder.
- [ ] **Process dependencies** lists linked processes or **None.**
- [ ] Entity and tool links use Markdown and resolve to real files; definitions are not duplicated from `entities/` / `tools/`.
- [ ] **Data Model** and Mermaid (if any) follow [`../standards/processes.md`](../standards/processes.md).
- [ ] For lifecycle notes: transition table + `erDiagram` align.

## Skeleton template

```markdown
# My Process Title

## Purpose

… (optionally: state touched in detail under **Data Model**.)

## Conditions

This process is doable only when:

- … link to [Entity](../entities/entity.md) …

## Tools

- [Tool](../tools/Tool%20-%20Tool.md) — …

## Impact

- …

## Cost

**Runtime (typical instance):** … (range, cadence, variance drivers)

## Skills required

- … (link [Skill](../entities/skill.md) when a named skill note exists)

## Data Model

Describe inputs, outputs, and records or handoffs read/written. Add a Mermaid `erDiagram` per
../standards/processes.md when useful — copy the pattern from
workstream-lifecycle-definition.md or workflows/workstream-ticket-update-workflow.md.

## Process

1. …
2. …

## Process dependencies

- [Other process](./other-process.md)

Or: **None.**
```

## See also

- [`../standards/processes.md`](../standards/processes.md) — full rules and “before committing” list
- [`../entities/README.md`](../entities/README.md) — entity naming
- [`../principles/README.md`](../principles/README.md) — how principle essays differ from processes
