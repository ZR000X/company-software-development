---
title: "Operational regime, execution, and records of work"
aliases:
  - operational-regime-and-records-of-work
created: 2026-04-12
updated: 2026-04-17
tags:
  - principles
  - governance
  - agentic-systems
  - workflows
  - operations
type: principle
status: draft
description: >-
  Operational regime as team orchestration; agent-centric pull versus workflow-centric triggers;
  workstreams, cycles, and reviewable change; meetings as forums; pull requests and durable
  traces; logical single system of record; records of work with reason and constitution or policy
  references as first-class fields; metadata for operations and accounting.
---

**Intended audience.** People designing agent-heavy operating models: technology and enterprise architects, engineering and product leadership, governance owners, and anyone defining how work is scheduled, reviewed, and persisted. This installment assumes the **written governance stack** in [repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md) and explains how **regimes**, **execution**, and **records of work** make that stack operational. It is not a substitute for concrete schemas or vendor choices.

> [!NOTE]
>
> **Production.** Ideas and first draft are human in origin. Editing (structure, wording, and readability) was done with AI assistance and then proofread and accepted by a human. References were researched, selected, and inserted with AI help; treat the bibliography as a working list and verify citations for any formal or legal use.

This note is a **principle** essay: it argues for a way to think and govern. Operational “how” documents belong under `processes/` and follow process-note conventions described in [processes/README.md](../processes/README.md), which differ from the shape defined in [the principles README](./README.md).[^1]

# 1 Introduction

[Repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md) answers **where** knowledge lives and **what** written stack (constitution, policies, identities, workflows) orients agents. None of that matters if work never moves on a predictable cadence or if runs leave no durable, query-able trace. This principle is about **motion and evidence**: the **operational regime** (how items enter queues and schedules), the **operating model** motifs that keep multi-agent work legible (including synchronous “meetings”), and the **minimum bar for execution**—usually **pull requests** for durable repo change plus **records of work** whose fields already encode *why* something was allowed, not only *what* happened.

Read together with the governance-stack note, it completes the “paper constitution” side of agentic operations: definitions are written, then **regimes and records** show how they were honored in practice. Step 8 on the same reading path in [PRINCIPLES.md](../PRINCIPLES.md) carries cost, audit lineage, and repository context boundaries; this file stands alone as the operational and persistence layer any serious agent program will need.

Key takeaways

- **Regime is orchestration**: routines, queues, parallelism, and backoff are how the team decides what runs when; mixing **agent-centric pull** and **workflow-centric triggers** without clarity creates double work or blind spots.
- **Continuous agents map to workstreams and cycles**: identity-bound **base workflows**, repeated **cycles**, reflection, bounded identity amendment, tool use, and work-item progression—tuned so concurrency stays policy-shaped.
- **Reviewability is the default**: durable changes to governed artifacts should flow through **pull requests** unless policy explicitly exempts low-risk steps; **isolation branches** follow **written branching policy**, not ad hoc naming.
- **Records are a logical system of record**: a central database or equivalent store scales finance and operations, but every maturity level still owes a **single logical place** for work metadata.
- **Reason and governance pointers are data, not prose**: constitution and policy references, stable IDs, and structured reasons belong in the **schema** of a classified record—so audits do not depend on chat reconstruction alone.

# 2 Operational regime and the operating model

An **operational regime** is how work enters motion: routines, queues, parallelism, and backoff. Treat the **operational regime as team orchestration**: it decides what runs when, with what concurrency, and under which guardrails. Two complementary patterns often coexist:

- **Agent-centric pull** — An agent runs a standing workflow and picks work items assigned to it.
- **Workflow-centric trigger** — An event or schedule starts a workflow that then invokes the right agents.

Both are legitimate; mixing them without clarity causes double work or blind spots. At team scale, this is **orchestration** in the same sense as a human operating model.

An **idealized visualization** for **continuous** agent operation ties the regime to **[workstreams](../entities/workstream.md)** (streams of work with defined statuses through which **work items** move). Each **software agent** runs the **base workflow** anchored in its **identity**; it is **assigned to one or many** workstreams. Under the regime it **runs repeatedly**—for example **once per minute** when a pass is cheap, or less often when a pass is long—with the interval set so the next invocation does not overlap the previous one unless policy allows parallelism. A **cycle** is **one execution** of that **base workflow**. Within a cycle, the base workflow may include **reflection** prompts, **decide** whether to **amend its identity** (within policy), **invoke tools**, and **advance or complete** the **work item** in scope for that cycle. Beyond the work item itself, it may update its **personal** area of the repository—for example by opening or refreshing a **pull request** against a **dedicated isolation branch** named by **repository branching policy**—then write its **record of work**, and **finalize** a **pull request** against the **work item’s** integration branch so the outcome remains **reviewable** like other execution.

Taking inspiration from human organizations, an **operating model**—here aligned with the **operational regime**—can include **meetings** and **focus sessions**. In this vocabulary, a **meeting** is a synchronous workflow bounded in time, with an agenda and a **minimal** number of parallel conversation threads so attention does not fragment without limit. **Meetings are modeled as a forum**: a **cluster of group chats**. Use **open-ended** group chats for continuous inter-agent communication; use **closed-ended** group chats for agenda-specific work. **Scheduled**, **recurring meetings** belong in the regime the same way cron or queue consumers do. Written baselines before synchronous work remain valuable; they are the same discipline as in [written principles and written debate](./01-written-principles.md), adapted to agent forums.[^2]

# 3 Execution, pull requests, and records of work

A workflow run is rarely “only” text generation. It is a sequence that may include branching decisions, tool calls, human checkpoints, and narrative output. **Usually**, when a run should change durable definitions or artifacts in the repository, the outcome includes opening a **pull request** so the constitution, policies, identities, workflows, or other tracked definitions evolve through inspection and history. Policy may exempt low-risk or microscopic steps; the default posture is **reviewable change**, not silent drift.

At a **minimum**, serious execution should emit a **record of work**. Enterprises should plan for a **central database** (or an operationally equivalent **central store** with query, retention, and access controls) so records stay aggregatable for operations and finance; smaller teams may start lighter, but the **logical** requirement—a **single system of record** for work metadata—remains.

The **core data model** used for tracking should treat **reason** and references to **constitution** or **policy** clauses as **first-class fields**, not optional free text. Every **classified** record of work should be **traceable to the constitution**—directly or through explicit workflow and policy references—so audits can answer *why this was allowed to happen* without reconstructing chat logs alone.

Such a record should carry metadata sufficient for operations and accounting, for example:

- time range and identifiers (run id, workflow ref, identity ref, repository ref, branch or fork)
- model identifiers and **token** counts (input and output where available)
- links to artifacts (PR URL, commit hashes, attachments)
- scope: **project** or **initiative** (and customer or internal sponsor where relevant)
- pointers to downstream API calls or child workflow runs
- **reason** fields tied to **workflow generation** (when definitions were created or changed), **decisions**, and **actions**—including, where helpful, automated steps (why this branch, why this policy path). Prefer **stable references** (paths, clause IDs, commit hashes of the governing text) over paraphrase alone, so lineage stays checkable after documents move.

Regulations and **data model** expectations for those records belong in **policies**, not scattered in prompts. The idea that processes change business state—and therefore deserve explicit data thinking—is developed in [business as process—and process as data](./02-business-as-process-and-process-as-data.md).[^3] The repo-centric execution pattern appears in [agentic architecture as repository and workflows](./05-agentic-architecture-as-repo-and-workflows.md), including the expectation that runs leave durable traces.[^4]

# 4 References

[^1]: Principle essays follow [the principles README](./README.md); process notes follow [processes/README.md](../processes/README.md).

[^2]: For durable written alignment and meetings on top of text, see [written principles and written debate](./01-written-principles.md).

[^3]: For processes as state change, impact versus cost, and governance maturity, see [business as process—and process as data](./02-business-as-process-and-process-as-data.md).

[^4]: For repository layout, workflows, and run logging, see [agentic architecture as repository and workflows](./05-agentic-architecture-as-repo-and-workflows.md).
