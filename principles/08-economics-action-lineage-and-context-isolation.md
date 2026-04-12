---
title: "Economics, action lineage, and context isolation"
aliases:
  - economics-action-lineage-and-context-isolation
  - action-lineage
created: 2026-04-12
updated: 2026-04-17
tags:
  - principles
  - information-architecture
  - governance
  - agentic-systems
  - workflows
  - economics
  - operations
  - lineage
type: principle
status: draft
description: >-
  Token economics and accounting; projects versus initiatives; compartmentalisation; action lineage
  from applied work to constitution and economic scope; branching and forks as context hierarchy;
  parallel directory and branch trees in one repository; synthesis with IA, governance, records,
  and operating regimes.
---

**Intended audience.** People designing agent-heavy operating models: technology and enterprise architects, engineering and product leadership, governance owners, and anyone defining how **cost**, **audit**, and **repository structure** should fit together. This installment synthesizes [repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md) and [operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md) into **economics**, **action lineage**, and **deliberate context boundaries**; it is not a substitute for concrete schemas or vendor choices.

> [!NOTE]
>
> **Production.** Ideas and first draft are human in origin. Editing (structure, wording, and readability) was done with AI assistance and then proofread and accepted by a human. References were researched, selected, and inserted with AI help; treat the bibliography as a working list and verify citations for any formal or legal use.

This note is a **principle** essay: it argues for a way to think and govern. Operational “how” documents belong under `processes/` and follow process-note conventions described in [processes/README.md](../processes/README.md), which differ from the shape defined in [the principles README](./README.md).[^1]

# 1 Introduction

Once **governance artifacts** and **operational records** exist (see [repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md)[^2] and [operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md)[^3]), leadership still needs three things: **economic honesty** (what work cost and who sponsored it), **audit narrative** (why a side effect was permitted), and **context discipline** (how to isolate work without fragmenting the org into unreviewable silos). This principle addresses those concerns: **token- and tool-aware economics**, **projects versus initiatives**, **action lineage** as reverse trace from applied work to written obligations and scope, and **branching**—including an example **parallel directory and branch tree**—when a single repository must still **segregate** context.

It is the **synthesis** installment of a three-part arc on the same reading path; for order, use [PRINCIPLES.md](../PRINCIPLES.md). The note remains **non-prescriptive** about vendors, engines, and database schemas while insisting on a coherent **inspectable** stack.

Key takeaways

- **Economics follows the ledger**: treat throughput and tool spend as real employment cost drivers; attach runs to **projects** or **initiatives** so every dollar is explainable when the data allows.
- **Compartmentalize with eyes open**: mono-repos and heavy indexing burn tokens; humans—not automation alone—decide the silo versus shared-context balance, alongside competency and delivery ownership.
- **Action lineage is applied-work lineage**: from an action, trace **how** (workflow, identity, parents) and **why** (policy and constitution references), and outward to **sponsor scope**—the “reverse stack trace” mindset.
- **Branching is a hierarchy lens**: trunk holds founding obligations; branches hold project, initiative, department, or agent context—design merge policy as you would org accountability, not as Git trivia.
- **Parallel trees encode policy**: align directory layout and branch topology only when you have **written rules** for names, lifetimes, and merge tiers; the same policy system that defines records can define when branches must exist.

# 2 Economics, projects, initiatives, and compartmentalization

In AI-heavy work, **employment cost** is often dominated by **token throughput** and tool spend more than by calendar duration. Cost efficiency therefore favors **token efficiency**: targeting valuable activities, strong indexing, and avoiding continuous low-value churn. A repository can sit cheaply until something worthwhile prompts work—continuous busyness is not a virtue the way it sometimes is for salaried human teams.

**Records of work** should support an **accounting regime**: tokens, models, perhaps tool charges, attached to a **scope** so management can relate spend to outcomes. Work should be **categorized** (even purely internal work) so accounts can show **profitability** or defensible **unit economics** when the data allows—so that, in principle, **every dollar or cent of cost** can be explained against **projects** or **initiatives**.

Two fundamental work types help:

1. **Projects** — Customer-driven or company-driven efforts with defined goals and timelines; they **end**, with outputs handed to a **sponsor**—a **customer** or an **internal business leader**—even when “income” is revenue and “expense” is internal cost allocation plus tokens and time. Lessons learned may remain in the knowledge base; the delivered product or decision belongs to the sponsor.
2. **Initiatives** — Investments that may not yield a single tangible artefact but **improve organizational structure** or **accumulate knowledge and expertise**. They are harder to prove in the short term; the thesis is that they **eventually pay for themselves** by making type-(1) work more profitable, safer, or faster—and they should still be traceable in the ledger of work.

Projects may each have a repository or live in a central one; **initiatives** often fit a **central organizational** repository—but **information overload** rises with monorepo scale, and **indexing** itself consumes tokens. How much structure and indexing to maintain versus how much to improvise around search is a terrain judgment.[^4] Humans accountable for architecture should lead **compartmentalisation** decisions: the balance between silos and shared context is not solvable by automation alone. Org patterns such as competency versus delivery lines—see [competency lines and project delivery](./04-competency-vs-project-teams.md)—interact with how cost and quality are owned.[^5]

Policies should make operations traceable to **projects** or **initiatives** so spend can be explained, compared, and improved.

# 3 Action lineage

With the **governance stack** in [repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md), **human bootstrap and authority** there, the **operational regime** in [operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md), **execution and records of work** there, and **economics**—projects, initiatives, and scope—in the preceding section of this essay, **action lineage** names how those layers connect for audit.

**Action lineage** is the **data lineage of applied work**: from each **action** taken (tool call, merge, ticket transition, configuration change, or other side effect), you can trace **how** it happened—workflow step, identity, parent runs—and **why** it was permitted, all the way to the **obligations** the organization has written for itself.

Treat **reason** primarily as **reference**, not only as narrative. A reason should point at **policies** and **standards** under `standards/` (or your equivalent) and ultimately at the **constitution**, so “because I felt like it” cannot masquerade as governance. At the same time, each record should link outward to **project** or **initiative** scope (and sponsor), so economic and delivery narratives stay connected to technical traces—as the economics and scope layer above requires for accounting.

The mental model is a **stack trace in reverse**: start at the **leaf**—the record of work or the lowest-level action log—and follow parent pointers through nested workflow runs, approvals, and policy gates until you reach the **trunk** of authority (constitution and top-level policies) and the **branch** of business context (which portfolio effort paid for the run). Each frame in that trace should carry the **reason references** that justified moving to the next frame.

This is worth maintaining when the **marginal cost** of storing those references is small relative to the cost of an unexplained action in production or in audit. Where storage or ergonomics pinch, policy should say which action classes require **full** lineage and which may use lighter links—another terrain judgment tied to risk.

# 4 Context management and branching as organizational hierarchy

For **context isolation**, prefer **branching** or **forking** within a repository when that suffices: it can **substitute** for multiplying repositories while keeping a single system of review. **Multiple repositories** remain valid—especially when legal, regulatory, or trust boundaries demand it—but they **often mirror the human structure** of the organization, which can be clarity or friction depending on discipline.

A productive metaphor: treat **`main`** (or an equivalently protected trunk) as the locus of the **constitution**, founding **policies**, and baseline **workflows**; treat **branches** as contexts for **projects**, **initiatives**, **departments**, or even **individual agents** when isolation helps review. **Branching strategy as organizational hierarchy** is a design lens: it forces questions about what may merge back, who approves, and how long divergent context may live. It is not a mandate that every team literalize departments as Git branches.

Choosing how much structure to encode—versus improvising—is situational; [process versus improvisation](./03-process-vs-improv.md) applies as much to branch policy as to human ceremony.[^4]

# 5 Parallel directory trees and branch naming (example convention)

One practical way to live inside a **single repository** while keeping **context separate** is to make the **directory layout** and the **branch topology** tell the same story. Adopt a **written policy** for branch names, allowed prefixes, lifetime, and which directories are authoritative on which branches—so agents and humans do not have to infer structure from tribal memory.

This pattern **specializes** the generic idea—raised in [operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md)—of a **dedicated isolation branch** named by **repository branching policy**: here, directory names and branch families are aligned on purpose.

Illustrative pattern (names are examples; encode your own in policy):

- **Projects** — A `projects/` directory on disk sits alongside a long-lived **`projects`** branch (or integration line) that aggregates “all active project work.” Each project has a **subdirectory** (for example `projects/acme-rollout/`) and a matching **project branch** (for example `project/acme-rollout`) where that project’s definitions and artefacts evolve. When **unit work** starts—a ticket, initiative slice, or experiment—open a **child branch off the project branch**, scoped to that work item; when the item is finished, **merge the child into the project branch** and delete or archive the child according to policy. When the **project** completes, **merge the project branch into `projects`**, then into **`main`** (or your trunk) under whatever release governance you use.
- **Agents** — Similarly, an `agents/` tree can pair with an **`agents`** integration branch: one **subdirectory per agent** (`agents/billing-bot/`) and one **long-lived branch per agent** when isolation helps (for example `agents/billing-bot`). Agent-specific prompts, overrides, and local notes stay mergeable without contaminating unrelated agents’ context.
- **Initiatives and other domains** — The same idea extends to `initiatives/`, `departments/`, or other top-level slices: a **family branch**, **per-entity branches**, then **per-work-item branches** that merge upward.

The invariant is **hierarchical merging**: short-lived branches absorb into their **parent** branch (work item → project; project → projects line; projects line → trunk), so context stays **partitioned** during execution but **reintegrates** when work is done. That matches how organizations expect accountability to roll up.

This convention is **not** the only valid Git layout; it is one **branching strategy that makes sense** when the goal is **segregation of context without multiplying repositories**. Choosing how strictly to mirror directories and branches—versus looser naming—is situational; the same policy system that defines **records of work** can define **when** a new branch is required and **who** may merge at each tier.

# 6 Closing scope

This note does not prescribe a specific database schema, orchestration engine, or model provider. It argues for a coherent stack—IA at two scales, orchestration with clear authority, written governance, durable records with reasons, economic tagging, **action lineage**, and deliberate context boundaries—so agentic operations remain inspectable and improvable over time.

# 7 What this trilogy asserts

The following takeaways summarize the **combined** argument across [repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md), [operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md), and this essay:

- Treat **inter-repo** layout as org-level IA and **intra-repo** layout as team-level IA; both need deliberate owners.
- **Humans** are accountable orchestrators of **AI agents**; **agents** orchestrate LLM prompts and **token** consumption; **LLMs** emit **tokens**, which are the **quantization** of **recorded knowledge** once persisted—not **authoritative** decisions unless you deliberately delegate. **Applied** knowledge is what workflows *do*; **authoritative** knowledge is what the organization *commits to* as obligation.
- A **constitution** plus **policies**, **identities**, and **workflows** form a written stack that agents should load as context; humans **bootstrap** purpose-specific workflows and stay in the loop as **governance authority** for high-stakes change.
- An **operational regime** (routines, queues, parallelism, meetings) is **team orchestration**; execution should emit **records of work** whose **persistence data model** treats **reason** and policy or constitution references as **first-class fields**.
- **Projects** and **initiatives** ground **economics** and accounting; **action lineage** then ties **actions** and records back through policies to the constitution and across to that economic scope.
- **Branching** (or forks) is a hierarchy-of-context design lens; **parallel directory and branch trees** are one concrete pattern when one repository should still **segregate** context.

# 8 References

[^1]: Principle essays follow [the principles README](./README.md); process notes follow [processes/README.md](../processes/README.md).

[^2]: [Repository information architecture and the agent governance stack](./06-repository-ia-and-agent-governance-stack.md).

[^3]: [Operational regime, execution, and records of work](./07-operational-regime-and-records-of-work.md).

[^4]: For when to encode process versus improvise, see [process versus improvisation: know the terrain](./03-process-vs-improv.md).

[^5]: For competency versus delivery ownership, see [competency lines and project delivery](./04-competency-vs-project-teams.md).
