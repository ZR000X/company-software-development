# Entities

This folder contains **entity notes**: Obsidian notes that describe domain concepts (Epic, Project, Person, Team, etc.) used across the company and its processes.

## Rules

- **Entity-only content.** Each note describes only the entity: what it is, how it relates to other entities, and any schema or structure it has. Do not reference specific processes, procedures, or "this process" inside entity files.
- **Schema as Mermaid.** Define each entity’s schema in a **Schema** section using a Mermaid diagram (e.g. `erDiagram` or `classDiagram`). Do not use PlantUML; use Mermaid only so diagrams render consistently in Obsidian and elsewhere.
- **No "Used in" sections.** Entity notes do not list which processes use them. Processes link to entities; Obsidian backlinks will show where each entity is referenced.
- **Cross-link between entities.** Use wikilinks to other entities (e.g. `[[Entity - Project|Project]]`) where the relationship is part of defining the entity.
- **Naming.** Use the pattern `Entity - <Name>.md` so entity notes are easy to find and distinct from process or tool notes.

Processes live in the `processes/` folder and may reference these entities.
