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

Validate the first model through concrete workflows rather than adding more
entities by default. Prioritize changed Requirements after implementation, failed
architecture assumptions, shared/retracted Evidence, and partial replacement.

Use those scenarios to settle assessment identity, baseline/candidate identity,
scope transfer, decision-kind differences, and authority/evidence thresholds.
Record stakeholder resolutions separately from working hypotheses.

## Implementation

Not started and intentionally prohibited.
