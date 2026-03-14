# Entities

This folder contains **entity notes**: Obsidian notes that describe domain concepts (Epic, Project, Person, Team, etc.) used across the company and its processes.

## Rules

- **Entity-only content.** Each note describes only the entity: what it is, how it relates to other entities, and any schema or structure it has. Do not reference specific processes, procedures, or "this process" inside entity files.
- **Schema as Mermaid.** Define each entity’s schema in a **Schema** section using a Mermaid diagram (e.g. `erDiagram` or `classDiagram`). Do not use PlantUML; use Mermaid only so diagrams render consistently in Obsidian and elsewhere.
- **No "Used in" sections.** Entity notes do not list which processes use them. Processes link to entities; Obsidian backlinks will show where each entity is referenced.
- **Cross-link between entities.** Use standard Markdown links to other entities (e.g. `[Project](project.md)`) so links work on GitHub and in Obsidian.

## Naming conventions

- **Filenames:** Use **kebab-case** (e.g. `business-rule.md`, `assignment.md`). Do **not** include the word "entity" in the filename.
- **Cross-links:** When linking between entity notes in this folder, use the filename only: `[Project](project.md)`, `[Business Rule](business-rule.md)`.

Processes live in the `processes/` folder and may reference these entities. From other folders, link to entities with paths like `../entities/process.md`.
