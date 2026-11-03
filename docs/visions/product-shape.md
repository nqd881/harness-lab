# Agent Harness — Product Shape

**Status:** Proposed product vision and candidate system shape; **not** an approved implementation architecture\
**Project:** Harness Development (`harness-lab`)\
**Recorded:** 2026-11-01\
**Current project stage:** Harness-domain discovery; software implementation is not yet authorized

## 1. Product definition

The intended end product is a **reusable, executable, stateful software-development harness** that governs how AI agents help move an application from an initial idea through discovery, requirements, architecture, implementation, verification, release, operation, change, and maintenance.

Its purpose is to make AI-assisted engineering **reliable, recoverable, traceable, evidence-based, and subject to explicit authority**.

The harness is **not** a replacement for Claude Code or OpenCode, a collection of clever prompts, or the application being built. Coding agents are workers *inside* the harness. The application is the output *managed by* the harness.

Conceptual layers:

```text
Human / stakeholder authority
             |
             v
Harness interface (candidate: CLI first; dashboard later)
             |
             v
Harness core: domain, state, policies, workflows,
              traceability, verification, evidence
             |
             v
Agent/tool adapters (Claude Code, OpenCode, Git, tests, CI)
             |
             v
Application repository: code + durable project knowledge
```

## 2. Intended capabilities

These are **candidate logical responsibilities**, not necessarily independent services or finalized code modules.

| Capability | Responsibility | Example question |
| --- | --- | --- |
| Domain and state | Manage identities, revisions, lifecycles, relationships, decisions, requirements, baselines, questions, and historical findings. | Which requirement revision governs this scope? |
| Workflow and transitions | Evaluate commands, guards, invariants, and allowed transitions without imposing a universal waterfall. | May this baseline be accepted now? |
| Policy and authority | Determine what agents may do, what requires approval, and who is authorized for each transition. | Can this actor approve this change? |
| Agent execution | Prepare bounded tasks and relevant context; invoke agents; record work and outcomes. | What may the coding agent work on next? |
| Traceability and impact | Connect upstream intent to decisions, architecture, code, verification, and releases; identify dependencies to reconsider when something changes. | What is affected by R17 revision 2? |
| Verification and evidence | Associate scoped findings and independent checks with exact requirement/system revisions and evaluation contexts. | What evidence supports the satisfaction claim? |
| Project knowledge and recovery | Preserve authoritative project knowledge in the repository and support reliable fresh-session continuation. | Can a new agent recover and resume safely? |

The mature product may additionally support release, operational feedback, and maintenance workflows. These are long-term scope, not Harness v0 commitments.

## 3. Candidate tangible product

A plausible distribution has **two parts**:

1. **An installable Harness application**, exposing an interface (initial candidate: CLI) and a modular core for domain state, guarded operations, authority checks, traceability, evidence, and agent/tool adapters.
2. **Repository-local, durable project artifacts** that a fresh agent and a human can inspect. These include project state, instructions, requirements, decisions, architecture records, work records, and verification evidence.

Illustrative package shape (names and layout are provisional):

```text
agent-harness/
  cli/
  core/
    domain/
    state/
    workflow/
    policy/
    traceability/
    verification/
  agents/
  integrations/
  templates/
  tests/
```

Illustrative target application repository:

```text
my-application/
  src/
  tests/
  AGENTS.md
  CLAUDE.md
  .harness/           # possible state/config/work/evidence home
  docs/
    requirements/
    decisions/
    architecture/
```

These trees are **design sketches only**. There is no accepted choice of storage engine, framework, orchestration runtime, or exact directory structure.

## 4. Candidate user experience

A developer initializes the harness in an existing or new repository. The harness can report current state, available and blocked work, required human decisions, and verification status. An authorized agent receives a bounded task and relevant durable context; it performs the work and returns artifacts and claims. The harness evaluates required checks, records findings, and permits subsequent transitions only when their guards and authority requirements are satisfied.

Possible CLI verbs, **illustrative and not implemented**:

```text
harness init
harness status
harness next
harness impact R17
harness verify
```

An optional later dashboard could visualize dependencies, work, approval requests, and evidence. It should not create a competing source of truth.

## 5. Harness v0 — recommended first vertical slice

The first useful implementation should be deliberately narrow: **govern one real software change from a durable requirement through authorized work and independently verifiable evidence**, including a clean fresh-agent handoff.

Candidate acceptance tests:

1. A fresh agent recovers project state and the next permitted action from the repository without prior chat context.
2. Invalid or unauthorized transitions are rejected with an understandable reason.
3. A coding agent can complete a bounded, authorized change and persist its work.
4. An implementation claim alone does not satisfy a requirement; scoped evidence and a check are needed.
5. Revising a requirement preserves historical revisions and findings while identifying affected dependencies for review.
6. A human-controlled decision cannot be silently fabricated by an AI agent.
7. The harness mechanisms can be reused on another small project without rebuilding the methodology.

**Validation deliverable:** use Harness v0 to develop a small real application and record harness failures and improvements. A reliable webhook delivery platform has been considered, but no test application has been selected.

## 6. Established direction versus open design choices

### Established project direction

- The repository is the persistent project system of record; conversation memory is not authoritative.
- Claude Code/OpenCode are workers within the harness, not the harness itself.
- Domain discovery precedes implementation.
- Important history, revisions, evidence, and scoped findings should not be silently rewritten.
- Lifecycle state, requirement satisfaction, consistency, conformance, and governing applicability must not be casually collapsed into a single status.
- Authority is specific to the transition and context; agents cannot invent stakeholder authorization.
- Fresh-agent recovery and evidence-based completion are first-class quality properties.
- Real scenarios should test the model before automation is built around it.

### Proposals, **not accepted decisions**

- CLI-first, local-first installable product with a modular core.
- The exact seven capability boundaries in this document.
- A `.harness/` folder and the example package trees.
- Specific CLI commands, dashboards, and adapters.
- The precise feature set and completion criteria for Harness v0.

### Explicitly unresolved or deferred

- Requirement acceptance versus governing/activation policy, including refused supersession.
- Aggregate and bounded-context boundaries; detailed commands, events, guards, and invariants.
- Storage model (files, database, graph, etc.), event sourcing/CQRS, workflow/orchestration framework, multi-agent scheduling, and service topology.
- Exact authority delegation, release governance, operational feedback, and UI choices.

## 7. Current position and next step

**Today:** The project is in `domain_discovery`; implementation is disallowed under the existing project-state rules. The existing repository harness (`AGENTS.md`, `CLAUDE.md`, `PROJECT_STATE.yaml`, `PROGRESS.md`, and domain documents) is a research and recovery scaffold, **not the final executable product**.

The CR1 changed-requirement scenario produced key insights about revision-specific satisfaction, preserved evidence, downstream review, and transition authority. The immediate domain question is what happens when a successor Requirement is accepted but supersession of its predecessor is refused. The agent should expose coherent policy alternatives and seek legitimate human decisions rather than choose stakeholder policy unilaterally.

After sufficient scenario validation, consolidate the domain language, bounded contexts, commands/events, authority rules, and guards; then design and implement Harness v0 and test it against a small real application.

---

**Use of this document:** A stable description of the intended **product boundary and candidate shape** for future discussions. It is not authorization to begin coding and must not override a newer accepted decision or the repository's current `PROJECT_STATE.yaml` / `PROGRESS.md`.

**Source:** Harness Development project handoff and product-shape discussion, 2026-11-01.
