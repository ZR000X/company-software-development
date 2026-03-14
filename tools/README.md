# Tools

This folder contains **tool notes**: Obsidian notes that describe which tools are used (JIRA, Excel, SharePoint, Teams, etc.) and how they fit into workflows.

## Rules

- **Tool-only content.** Each note describes what the tool is and what it is used for. Do not duplicate process steps or entity definitions inside tool files.
- **Naming.** Use the pattern `Tool - <Name>.md` so tool notes are easy to find and distinct from entity or process notes.
- **Optional "Used in".** Tool notes may optionally link to processes that use them (e.g. "Used in [Process name](../processes/Process%20name.md)"). Processes link to tools; Obsidian backlinks also show where each tool is referenced.
- **Cross-link to processes.** When a tool is used in a specific process, you may add a short "Used in" line with a standard Markdown link to that process note, so links work on GitHub and in Obsidian.
- **Link to entities.** When linking to entity notes, use `../entities/<kebab-name>.md` (e.g. `../entities/person.md`). See [entities/README.md](../entities/README.md) for entity naming conventions.

Entity and process notes live in the `entities/` and `processes/` folders. Processes reference tools here; tools may reference processes for context.
