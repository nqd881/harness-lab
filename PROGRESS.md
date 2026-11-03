# Progress

## Current stage

Harness domain discovery.

## Current objective

Model:

- Idea
- Requirement
- Decision
- Architecture Baseline

For each concept, understand:

- meaning;
- information content;
- lifecycle;
- invariants;
- relationships;
- authority;
- transition requirements.

## Working hypotheses

The first concept investigation proposes:

- Idea represents an opportunity worth investigating, not delivery scope.
- Requirement represents a scoped expected outcome or constraint; acceptance
  authorizes an obligation at a particular revision.
- Decision represents a scoped, authorized resolution with rationale. A common
  concept with kinds is preferred provisionally over separate decision entities.
- Architecture Baseline represents an accepted reference configuration, not the
  live architecture. A candidate and a baseline may not share the same identity.
- Evidence merits first-class consideration where provenance, reuse, challenges,
  and corrections need continuity; its exact identity boundary remains open.

These are hypotheses and may change.

## Important discoveries so far

- Discussion may be an activity rather than a core entity.
- Draft is probably a lifecycle state rather than an entity.
- Lifecycle, consistency, Requirement satisfaction, and architectural conformance
  answer different questions and should not be represented by a single status.
- Requirement implementation progress is not an intrinsic obligation lifecycle.
  Contextual satisfaction assessments refer to exact Requirement/system revisions.
- Upstream changes trigger scoped impact review, not automatic invalidation or
  cascading withdrawal of all downstream commitments.
- Accepted/adopted content and premises are preserved. A new draft does not inherit
  approval or replace the governing revision without an authorized transition.
- Architecture coverage is not satisfaction proof, and Evidence is not authority.
- Human authority must cover the transition's scope; edit permission or authorship
  does not imply approval power. Exact delegation and joint approval remain open.

## Session record: 2026-10-02

Completed the initial investigation of Idea, Requirement, Decision, and
Architecture Baseline. Each entity document now covers definition, purpose,
information, proposed lifecycle, transition invariants, command/event vocabulary,
relationships, human authority, and uncertainties.

The original entity documents were placeholders. The new model is exploratory,
not ratified domain policy. In particular, the five requested challenges now have
explicit working recommendations and unresolved counter-cases: Requirement
implementation status, baseline abstraction, Decision kinds, separate state
dimensions, and first-class Evidence.

Updated the glossary and relationships to align with those recommendations.
Added `docs/domain/state-and-authority.md` for shared revision/approval rules and
`docs/domain/evidence.md` for the supporting Evidence investigation. Expanded
`docs/domain/open-questions.md` with stable question IDs and scenario-based next
steps. No aggregate boundaries, schemas, APIs, or application source were defined.

Verification: a separate read-only review found no actionable internal
contradictions or missing investigation areas; `git diff --check` passed. Changes
are limited to domain documentation and this progress record. `PROJECT_STATE.yaml`
remains unchanged in `domain_discovery`, with implementation prohibited.

## Next

The refused-supersession walkthrough is now documented in CR1-RS. Seek stakeholder
answers on whether successor acceptance defers governing force or immediately adds
an obligation, permitted coexistence and activation conditions, who may set that
policy, and permitted use of the old baseline while its successor is draft.
Examples have not resolved those choices. Assessment entity identity and
evidence/endorsement thresholds remain open; do not infer a release process or
add entities to answer them by default.

Then continue the already planned failed architecture assumption, shared/retracted
Evidence, and partial replacement scenarios. Those were not investigated in CR1.
Record stakeholder resolutions separately from working hypotheses.

## Session record: 2026-10-08

Documented CR1, a hypothetical changed Requirement after implementation, in
`docs/domain/scenarios/changed-requirement-after-implementation.md`. The walkthrough
specifies example scope, actors and mandates, commands, refusal conditions, events,
and impact findings. Its counter-cases cover implemented-but-failing behavior,
different releases and regression, non-comparable Evidence, wrong authority, and
rejection of the proposed change. No stakeholder Decisions were made.

The scenario supports separate lifecycle, consistency, satisfaction, and conformance
dimensions, revision-specific history, scoped review, and scoped authority. It
contradicts shortcuts rather than existing working recommendations: completion is
not satisfaction, old verdicts do not transfer, and build failure alone does not
prove architectural inconsistency. Existing observations can support a new finding
after applicability review without rewriting earlier Evidence or assessments.

Clarified these findings in Requirement invariants and relationships. Updated
state/authority guidance to distinguish accepted successor content from completed
scope transfer, and retained acceptance from continued-use permission. Recorded
focused follow-ups under existing question IDs in `open-questions.md`; all remain
unresolved. The scenario does not settle assessment or candidate entity identity,
atomic replacement semantics, general Decision kinds, or approval thresholds.

Changes are domain documentation only. `PROJECT_STATE.yaml` is unchanged in
`domain_discovery`, with implementation prohibited.

Verification: a separate read-only review found no actionable contradictions,
scope expansion, or accidental policy resolutions. `git diff --check` passed.
No application build or tests apply to this documentation-only investigation.

## Session record: 2026-10-23

Investigated only CR1's accepted-successor/refused-supersession case in
`docs/domain/scenarios/refused-requirement-supersession.md` (CR1-RS). Arun's request
has an accepted successor and complete scope mapping, but lacks obligation-
disposition authority. Refusal leaves R1 governing and both revisions accepted;
it neither rejects R2 nor undoes its acceptance. A separate guard check distinguishes
an invalid scope/revision account from this unauthorized request.

Compared two unselected policy possibilities: R2 is an authorized future obligation
that remains non-governing until authorized activation, or acceptance makes R2
immediately govern alongside R1 until R1 is ended. The compatible 500/300 ms
criteria do not establish universal precedence. Per-revision lifecycles can
describe the two acceptances but cannot determine the governing set without the
missing policy. Clarified authorization, scope/condition match, and present force
as separate questions without deciding independent lifecycles or adding entities.
Also exposed whether undefined governing effect should have blocked acceptance;
missing policy information alone does not establish a defect in the earlier action.

Documented downstream D1/B1 review, preserved Evidence/verdicts, an explicit agent
briefing that exposes unresolved force, and the different mandates needed for
policy, obligation disposition, and architecture actions. Updated the Requirement,
glossary, relationships, state/authority guidance, CR1 cross-reference, and existing
open-question IDs. No stakeholder Decisions were made; activation, coexistence,
continued-use permissions, and policy-setting authority remain unresolved.

Changes are domain/scenario/progress documentation only. `PROJECT_STATE.yaml`
remains unchanged in `domain_discovery`, with implementation prohibited.

Verification: reviewed consistency with the related Requirement, Decision,
baseline, relationship, and authority guidance, plus cross-references and change
scope. `git diff --check` and a separate whitespace check of the new scenario
passed. No application build or tests apply to this documentation-only work.

## Workflow setup: 2026-11-03

Configured agent-directed automatic Git task completion in `AGENTS.md`, with
`.opencode/commands/finish-task.md` as an explicit entry point to the same
workflow. Successful work units are verified, reviewed for scope and secrets,
committed with explicit path staging, and pushed only to dedicated `task/*`
branches. Conflicts, unrelated changes, authentication/permission failures, and
unclear task ownership stop the workflow. Required approvals remain in force.

Setup branch: `task/configure-git-completion`, starting at
`b728d5fe0c67c3629283bed5c770e7a5f99e12f5` on clean `main`, matching remote
`main`. Scope: agent instructions, the completion command, and this workflow
record. Expected origin: `https://github.com/nqd881/harness-lab.git`.

OpenCode 1.19.4 successfully loaded the command through `opencode debug config`;
checked command discovery, the `build` agent, workflow reference, and argument
placeholder. GitHub authentication and remote read access were verified before
changes. Final diff/scope review and commit/push confirmation are reported in
the setup task's completion report. No new permission overrides, plugins, or
edit/idle hooks were added. Restart OpenCode to load the new command.

This is a persistent agent instruction, not a guaranteed task-completion event
hook. Future execution still depends on agent adherence and required permissions;
loading the command does not establish reliability across future sessions.
The setup task itself exercises the automatic completion workflow.

No domain policies or application source changed. `PROJECT_STATE.yaml` remains
unchanged in `domain_discovery`, with `implementation.allowed: false`.

## Workflow update: 2026-11-03

Scope: extend the Git instructions in `AGENTS.md` and the existing
`.opencode/commands/finish-task.md` entry point with automatic draft PR creation
and safe local `main` synchronization. Start branch:
`task/automate-pr-and-main-sync`, based on synchronized `main` at
`86d3a4850382b60556c6d35b3e5621c25c5cd885`. Before branching, confirmed a clean
worktree, the expected origin, authenticated GitHub access, and previous task
PR #1 merged into `main`; fetch and `--ff-only` synchronization succeeded.

New work requires a clean tree and a confirmed merged previous-task PR. Open,
closed-unmerged, missing/ambiguous PRs and failed lookups stop it. Local `main`
must fast-forward to and equal `origin/main` before a fresh task branch is made.
Completion checks for an existing PR, reuses an open PR targeting `main`, or
creates a draft with summary, changed paths, checks, and unresolved questions.
Failures preserve local commits/pushed branches; no automatic readiness, approval,
merge, permission bypass, or duplicate PR creation is authorized.

Validation: OpenCode 1.19.4 loaded the revised command through
`opencode debug config`; checked the `build` agent, argument placeholder, workflow
reference, draft-PR instructions, and PR-URL reporting. Reviewed dirty/unmerged/
ambiguous/failing-lookup stop paths, ahead/diverged `main`, existing-PR reuse, and
creation-timeout re-query handling. Confirmed `main` equals `origin/main`, checked
`gh pr create --help` flags, and passed `git diff --check`. These failure paths
were reviewed without injecting failures into the real repository. The actual
task exercises commit, push/hash confirmation, and PR creation; final results
belong in its PR and completion report, with no separate test PRs.

Restart OpenCode to load the revised command. Execution remains agent-directed
and subject to agent adherence, GitHub availability, and required permissions.
No domain policy or application source changes are in scope; `PROJECT_STATE.yaml`
is unchanged, retaining `domain_discovery` and `implementation.allowed: false`.

## Implementation

Not started and intentionally prohibited.
