# Repository Maintenance

This document is a repeatable maintenance checklist for documentation consistency and standards compliance across the repository.

## Purpose

Keep repository documentation healthy over time by regularly checking:

- Relative link correctness in nested folders.
- Consistent schema field naming between process docs and canonical data notes.
- Process section structure and step readability.
- Standards and README policy alignment across major documentation areas.

## Suggested cadence

- **After doc edits:** run the quick checks for affected areas.
- **Weekly:** run the full checklist.
- **Before merging documentation PRs:** run full checklist + manual review.

## Priority scope to monitor

- `processes/workflows/workstream-ticket-update-workflow.md`
- `processes/workflows/main-workflow.md`
- `processes/workflows/data-fix-workflow.md`
- `data/README.md`
- `processes/README.md`
- `standards/processes.md`
- `tools/README.md`
- `data/work-items.md`

## Quick checks (5-10 minutes)

1. **Relative links in nested docs**
   - Ensure links from nested folders use correct path depth (for example, from `processes/workflows/`: `../../entities/...`, `../../tools/...`, `../../data/...`).

2. **Canonical field keys**
   - In workflow docs, prefer canonical keys from `data/work-items.md`:
   - `Ticket_Number`
   - `Today_Status`
   - `Yesterday_Status`
   - If display labels are used, include explicit mapping text.

3. **Process-step clarity**
   - Top-level process lists remain sequential.
   - Nested list numbering resets correctly within each parent step.

## Full checklist (15-30 minutes)

1. **Link target scan**
   - Verify Markdown links in changed files resolve to existing targets.
   - Spot-check links recently edited.

2. **Standards conformance**
   - Confirm required runnable process sections exist and remain in expected order:
   - `Purpose`, `Conditions`, `Tools`, `Impact`, `Cost`, `Skills required`, `Data Model`, `Process`, `Process dependencies`.
   - Confirm `Data Model` sections are substantive.

3. **Policy consistency**
   - Confirm `processes/README.md` and `standards/processes.md` agree on:
   - Frontmatter policy (optional).
   - Tool-note backlinks (`Used in` optional; no process-step duplication in tool notes).

4. **Lifecycle term hygiene**
   - Ensure status examples are clearly marked as examples or mapped to lifecycle definitions where applicable.

## Helpful commands

Run from repo root:

```powershell
rg "(\.\./entities/|\.\./tools/|\.\./data/)" processes/workflows
```

```powershell
rg "Ticket Number|Today Status|Yesterday Status" processes/workflows
```

```powershell
rg "^## (Purpose|Conditions|Tools|Impact|Cost|Skills required|Data Model|Process|Process dependencies)$" processes/workflows/*.md
```

```powershell
rg "Used in|frontmatter|YAML frontmatter" processes/README.md standards/processes.md tools/README.md
```

## Exit criteria for a maintenance pass

- No broken links in the monitored scope.
- No unintended drift from canonical field keys.
- Process steps and nested lists are readable and sequential.
- Standards and README guidance remain internally consistent.
