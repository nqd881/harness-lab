# Open Questions

All questions below remain unresolved. Working positions are hypotheses from the
first concept investigation, not stakeholder-approved Decisions. IDs support
cross-references; a question is not resolved merely because a preferred answer
is documented.

## Domain boundary

- **B1: What belongs inside the harness?** Does it own delivery work, system/build
  identity, evaluations, and release authorizations, or only reference them?
  Working position: do not infer ownership from a necessary relationship.
  Test against an external issue tracker, test service, and regulatory approval.
- **B2: Which concepts merit independent identity?** The four core candidates
  may mix entities and reference artifacts. Question, Revision, Trace Link,
  Authority, and assessments are still supporting candidates. Determine which
  have their own continuity, commands, and histories rather than assigning each
  a separate entity by default.

## Idea

- **I1: When is a suggestion an Idea?** What investigation or history justifies
  independent identity rather than a note? Test a casual suggestion, duplicate
  capture, and long-lived opportunity.
- **I2: What does pursuit commit to?** Working position: permission to develop
  commitments, not delivery. Can an agent begin bounded exploration, and at what
  cost/risk does human authorization become necessary? Must a pursued Idea
  eventually have a Requirement, or can investigation legitimately end otherwise?
- **I3: How do intent changes, splitting, and merging behave?** When is this a
  new Idea rather than a revision? How are duplicate dispositions and downstream
  provenance preserved? Current states do not yet model merge/abandonment explicitly.

## Requirement

- **R1: Does implementation status belong to Requirement?** Working recommendation:
  no. Delivery activity describes work; satisfaction assesses a Requirement
  revision in a particular system context. Does a satisfaction assessment need
  independent identity/lifecycle, and where is delivery progress owned? Validate
  with implemented-but-failing, satisfied-in-one-release-only, and later-regression
  examples. Evidence of code completion alone cannot answer these cases.
- **R2: What is the applicability unit?** Can one obligation span several releases,
  deployments, or tenants without separate identity? How do partial satisfaction,
  non-testable obligations, and conflicting assessment results aggregate without
  an unjustified universal "done" status?
- **R3: How do obligation sources affect authority?** Do legal, contractual,
  stakeholder, and internally chosen Requirements have different acceptance,
  withdrawal, or waiver rules? Who can accept reservations, and what must block
  acceptance? A local scope owner cannot silently waive an external obligation.
- **R4: How do refinement and partial supersession work?** When does a split create
  new Requirements instead of revisions, and how is retained scope accounted for?
  Is explicit draft abandonment needed? Test replacement of only one clause of
  an accepted multi-part obligation.

## Decision

- **D1: Is Decision one concept or several?** Working recommendation: common
  resolution/rationale/authority semantics with product, domain, architecture,
  and governance kinds. Split only if concrete cases show irreconcilable lifecycle,
  binding force, evidence, or reversibility rules. Compare a product scope choice,
  domain definition, technology tradeoff, and compliance ruling.
- **D2: Is approval itself a Decision?** Working position: always preserve an
  authorization record, but create a separate Decision only for a consequential
  question/tradeoff. What threshold avoids both duplicate approval records and
  lost rationale? Can one resolution authorize several transitions without
  bypassing each transition's guards?
- **D3: How are joint and external authorities represented?** What happens with
  disagreement, delegated mandates, quorum, or a binding external ruling? Who can
  revoke each kind, and how is an unresolved conflict escalated?

## Architecture

- **A1: Is ArchitectureBaseline the correct core abstraction?** Working position:
  it is an accepted reference configuration, not the evolving architecture graph.
  Are Architecture Description, Architecture Model, or Architecture Commitment
  needed as separate concepts? If no workflow needs a fixed acceptance point,
  should baseline be derived rather than independently managed? Graph structure
  alone does not answer the aggregate/ownership question.
- **A2: Is a baseline candidate the same entity as an accepted baseline?** The
  proposed lifecycle treats them together for discovery, while reserving the word
  baseline for acceptance. Does identity track each version, a baseline family,
  or a separate proposal? Test a rejected candidate and two parallel proposals.
- **A3: How do scope and coexistence work?** Working guard: one governing baseline
  for an identical context unless precedence/partitioning is explicit. How are
  variants, layered subsystem references, partial replacements, and migration
  periods governed? Is retirement allowed while a deployed system still depends
  on the reference?
- **A4: How do intent and actual structure relate?** Who owns conformance findings,
  drift handling, and architecture exceptions? When does observed drift require
  a new baseline versus correction of implementation? Baseline acceptance alone
  is neither deployment nor Requirement satisfaction.

## Evidence

- **E1: Should Evidence be first-class?** Working recommendation: yes when reuse,
  provenance, challenges, and corrections have independent history. Is an Evidence
  item an observation, source artifact, report, or bundle? Separate claim-specific
  interpretation from source identity. Test one report with contradictory findings
  and one test run reused by several assessments.
- **E2: What makes Evidence sufficient?** How do risk, provenance, method,
  coverage, uncertainty, and age affect an approval? Who defines acceptance
  policies, and when must a human endorse an automated evaluation?
- **E3: Who may challenge, retract, or correct Evidence?** How are retention,
  restricted access, unavailable external sources, and producer disagreements
  handled without rewriting the basis of earlier approvals?

## State and revision

- **S1: Separate lifecycle and consistency?** Working recommendation: yes, also
  separate satisfaction and conformance. Is consistency a per-concept summary or
  a scoped assessment of particular claims? How do incomplete coverage, conflicting
  reviewers, and different contexts combine? Test an accepted but inconsistent
  baseline without automatically revoking its historical acceptance.
- **S2: How is review freshness determined?** Which changes trigger `needs_review`,
  who can resolve it, and when does pending review block further approvals or use
  of an existing reference? Historical acceptance and permission for continued
  use may need separate rules; no generic "stale means invalid" rule is assumed.
- **S3: What distinguishes a revision from a new concept?** How are corrections,
  substantive changes, rejected proposals, and reconsideration recorded? Define
  atomic scope transfer/approval semantics at the domain level before deciding
  any implementation boundaries.

## Workflow and authority

- **W1: Global phases or independent lifecycles?** Working recommendation:
  independent revision lifecycles coordinated by meaningful dependencies. Do
  release-level or compliance gates additionally need a cross-concept process?
  Validate a Requirement revision while its replacement baseline is still draft.
- **W2: Which actions can be delegated?** Initial safety hypothesis reserves binding
  commitments and reversals for accountable humans. Can policy authorize bounded
  agent dispositions, and how is the mandate established? Specify reviewer
  permissions, cross-scope approvals, emergency changes, and escalation without
  equating edit access with authority.

## Next discovery scenarios

Walk through a changed Requirement after implementation, a failed architecture
assumption, retracted Evidence used by multiple Decisions, and a partial baseline
replacement. Record concrete actors, commands, refusal conditions, events, and
impact findings; then revise hypotheses that do not survive these cases.
