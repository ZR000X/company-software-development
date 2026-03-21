# Principles

This folder holds **principle notes**: durable essays that state how we think about a topic—arguments, definitions, and heuristics—not step-by-step procedures. For operational workflows, see `processes/`.

## Canonical structure

New principle articles should follow the same shape as:

- [business-as-process-and-process-as-data.md](business-as-process-and-process-as-data.md)
- [process-vs-improv.md](process-vs-improv.md)
- [written-principles.md](written-principles.md)
- [competency-vs-project-teams.md](competency-vs-project-teams.md)

Rough **order of material** (top to bottom):

1. **YAML frontmatter** (Obsidian-friendly)
2. **Intended audience** (one short paragraph, bold label)
3. **Production** callout (GitHub-flavored alert)
4. **Body**: numbered top-level sections, optional nested subsections
5. **References** (final numbered section + footnote definitions)

### 1. Frontmatter

Use a block like this (adjust values per note):

```yaml
---
title: "Short title suitable for display and graph"
aliases:
  - kebab-case-alias
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - principles
  # ...topic tags
type: principle
status: draft   # or published, etc.
description: >-
  One or two lines for search, previews, and graph tools.
---
```

- **`title`**: Human-readable; may match the first section heading (without the leading number).
- **`aliases`**: Stable Obsidian / search names; often the filename stem in kebab-case.
- **`created` / `updated`**: ISO dates; bump `updated` on substantive edits.
- **`tags`**: Always include `principles`; add domains (e.g. `process`, `leadership`).
- **`type`**: `principle` distinguishes these from process notes.
- **`description`**: Multiline string (`>-` or `|`); summarize audience and thesis.

### 2. Intended audience

Immediately after the closing `---`, add a single paragraph:

```markdown
**Intended audience.** One to three sentences naming roles (e.g. IT leadership, delivery leads) and what the note optimizes for. Acknowledge other readers briefly if useful.
```

### 3. Production callout (GitHub-compatible)

Use GitHub’s [alert syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts). The `[!NOTE]` line must stand alone; continuation lines start with `>`.

```markdown
> [!NOTE]
>
> **Production.** Ideas and first draft are human in origin. Editing (structure, wording, and readability) was done with AI assistance and then proofread and accepted by a human. References were researched, selected, and inserted with AI help; treat the bibliography as a working list and verify citations for any formal or legal use.
```

Adjust the **Production.** paragraph if authorship or tooling differs; keep the alert form for consistent rendering on GitHub.

### 4. Section headings and flow

- **Top-level sections** use ATX headings with a **number prefix** and a short title, as the article’s main spine:

  ```markdown
  # 1 Title echoes article theme

  Opening paragraphs: thesis, stakes, or definition.

  Key takeaways

  - Bullet one
  - Bullet two

  # 2 Next major idea

  ...
  ```

- **First section (`# 1 …`)** typically contains the hook and, after one or more paragraphs, a **Key takeaways** block: plain heading `Key takeaways` (no `##`), then an unnumbered bullet list. This matches both reference articles.

- **Further top-level sections** are `# 2`, `# 3`, … in reading order. Titles should be scannable in a table of contents.

- **Nested subsections** use `## N.m Subtitle` when one numbered chapter needs parts (e.g. `## 6.1`, `## 6.2` under `# 6 …`). Shorter articles may use only `# 1` … `# 6` with no `##` children (see [process-vs-improv.md](process-vs-improv.md)).

- **Closing scope** (optional but encouraged): before references, one or two paragraphs stating what the note *does not* try to solve and pointing to other topics or articles.

### 5. References

- Final body section is a numbered heading, e.g. `# 7 References` (number = next in sequence after your last chapter).
- Use **GitHub-style footnotes**: markers in prose `[^1]`, definitions at the bottom:

  ```markdown
  [^1]: Author. *Title*. Publisher/year. Short note. [https://example.org](https://example.org)
  ```

- Keep footnote order aligned with **first appearance** in the text when possible.
- Prefer stable URLs (standards bodies, DOIs, reputable archives).

### 6. Style conventions

- **Bold**: Sparingly—headings carry structure; body text stays mostly plain.
- **Italics**: For emphasis or terms of art on first use, not entire sentences.
- **Links** to other repo notes: relative paths from `principles/`, e.g. `[Title](./other-principle.md)`.
- **Filenames**: Either descriptive kebab-case (`business-as-process-and-process-as-data.md`) or short stem (`process-vs-improv.md`); frontmatter `aliases` should stay stable if the file is renamed.

## Skeleton template

Copy into a new `principles/your-topic.md` and replace placeholders:

```markdown
---
title: "Your principle title"
aliases:
  - your-topic
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - principles
type: principle
status: draft
description: >-
  One-line thesis and who it is for.
---

**Intended audience.** …

> [!NOTE]
>
> **Production.** …

# 1 Your principle title

Opening …

Key takeaways

- …
- …

# 2 Second major section

…

# 3 References

[^1]: …
```

## Drafts in `to-do/`

Rough ideas may live under [to-do/](to-do/) until they match this structure; promote them to `principles/` when they are ready to serve as canonical essays.
