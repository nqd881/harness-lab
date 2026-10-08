# Architecture Baseline

## Definition

An accepted, versioned reference configuration of architecture descriptions and
applicable Decisions for an explicit system scope and context. It states the
structural commitments against which proposed changes can be assessed.

Working classification: a baseline is a controlled reference artifact with
identity and acceptance history, not the evolving architecture itself. Its
contents may form a graph; that does not establish an aggregate boundary.
Before acceptance, use "baseline candidate." The lifecycle below includes that
candidate as a convenience, not a claim that an unaccepted artifact is a baseline.

## Why this concept exists

The harness needs to know which architectural reference is governing a change,
what Requirements and Decisions it relies on, and what must be reconsidered when
those dependencies change. A live diagram or mutable artifact collection alone
cannot answer "what exactly did we accept?" A baseline is unnecessary if the
domain never needs a controlled reference point; that hypothesis remains testable.

## Information

- Identity/version, purpose, system boundary, and applicability context (such as
  target release, deployment variant, or subsystem).
- Exact revisions of included descriptions: responsibilities, boundaries,
  interactions, interfaces, dependencies, relevant qualities, and constraints.
- Applicable adopted Decisions and accepted Requirement revisions, with coverage
  claims, explicit exclusions, unresolved gaps, and known assumptions.
- Acceptance criteria for this baseline's purpose and risk, rationale, reviewing
  humans, approving authority, and cited Evidence.
- Predecessor/successor references, change summary, and review triggers.

The baseline fixes references; it need not own the descriptions, Requirements,
Decisions, or Evidence. Diagrams and documents are representations, not necessarily
domain entities. Actual deployed structure and conformance assessments are
separate from the intended architectural reference.

## Lifecycle

Proposed states for the candidate/baseline family: `draft`, `in_review`, `accepted`,
`rejected`, `retired`, `superseded`.

- Assemble a candidate in `draft`; submit enters `in_review`.
- Return to `draft` before changing reviewed content; accept or reject a reviewed
  candidate into `accepted` or `rejected`.
- Retire an accepted baseline when it no longer governs its context without a
  replacement; supersede it with an accepted successor for the same context.
- Changing an accepted baseline creates a new candidate/version. The prior
  baseline continues to govern until an authorized replacement or retirement.

`accepted` does not mean deployed, conforms to every Requirement, or has no
pending review. Parallel baselines can govern different scopes or variants.

## Invariants

- A review candidate declares purpose, scope/context, fixed content revisions,
  relevant Requirement/Decision revisions, and known gaps.
- Acceptance needs structural coherence, a coverage account, assessment against
  declared acceptance criteria, and an authorized human record.
- A baseline may deliberately cover only part of the system. Exclusions are
  explicit; a known gap is not a claim of complete coverage or an implicit waiver.
- Blocking conflicts with applicable accepted Requirements or adopted Decisions
  must be resolved before acceptance. A reservation is permitted only if it does
  not disguise such a conflict and has an owner and resolution condition.
- Evidence is proportionate to purpose and risk: review, analysis, prototypes, or
  experiments may suffice. Implementation completion is not universally required.
- Accepted contents and approval premises cannot be replaced by "latest" versions.
  Evidence and representations must remain identifiable even if access is lost.
- At most one baseline governs an identical declared scope/context at a time,
  unless an explicit coexistence policy defines precedence or partitioning.
- Supersession names an accepted successor and its applicability; partial overlap
  requires explicit scope disposition, not accidental loss of coverage.
- Upstream changes and observed implementation drift trigger review. They do not
  rewrite the baseline, prove it invalid, or revoke its acceptance automatically.

## Commands

Candidate command/event pairs:

| Command | Resulting event |
| --- | --- |
| AssembleBaselineCandidate | BaselineCandidateAssembled |
| ReviseBaselineCandidate | BaselineCandidateRevised |
| SubmitBaselineForReview | BaselineReviewRequested |
| ReturnBaselineForRevision | BaselineReturnedForRevision |
| AcceptArchitectureBaseline | ArchitectureBaselineAccepted |
| RejectBaselineCandidate | BaselineCandidateRejected |
| RetireArchitectureBaseline | ArchitectureBaselineRetired |
| SupersedeArchitectureBaseline | ArchitectureBaselineSuperseded |

Implementation conformance assessment is a related activity, not a baseline
lifecycle transition.

## Events

Acceptance records exact contents, scope/context, authority, rationale, Evidence,
and exclusions. Retirement and supersession record changes in governing reference,
not deletion of historical architecture. `ArchitectureBaselineAccepted` does not
mean the system has been built or verified against it.

## Relationships

- Requirements define obligations addressed by the architecture; baseline coverage
  links explain the proposed response and any gaps, not satisfaction.
- Decisions supply applicable choices and rationale. Not every Decision belongs
  to a baseline, and some architecture descriptions may not need a Decision record.
- Ideas can motivate alternatives but do not authorize architecture commitments.
- Architecture descriptions supply fixed representations; Evidence supports
  feasibility/quality claims; conformance assessments compare actual systems
  with this reference.

## Authority

Agents may assemble candidates, analyze coverage, and flag conflicts. Accept,
reject, retire, and supersede require accountable humans with architecture
authority for the affected scope. Changes to product obligations or regulated
constraints additionally need the relevant authority, not just an architect's
approval. Review return follows the review mandate. Exact multi-party approval
policy remains open.

## Open questions

See [A1-A4](../open-questions.md#architecture): whether the baseline is the right
core abstraction, candidate identity, coexistence/partial replacement, and how
intent differs from deployed structure. This model intentionally does not infer
ownership, transactional boundaries, or a single universal system architecture.
