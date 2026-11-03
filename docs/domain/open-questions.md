# Open Questions

All questions below remain unresolved. Working positions are hypotheses from
concept investigation and scenario walkthroughs, not stakeholder-approved Decisions.
IDs support cross-references; a question is not resolved merely because a preferred
answer is documented.

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
  an unjustified universal "done" status? Can two compatible accepted revisions
  govern one context together, or can an accepted successor await governing force?
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
  whether successor acceptance, beginning of governing force, and predecessor
  scope transfer must coincide, and what governs if they do not, before deciding
  any implementation boundaries. Revision continuity alone does not answer this.

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

The changed-Requirement scenario now has an initial walkthrough in
[CR1](scenarios/changed-requirement-after-implementation.md) and a focused refused
supersession follow-up in [CR1-RS](scenarios/refused-requirement-supersession.md).
Resolve their activation and continued-use questions with stakeholders before
treating the replacement workflow as settled. Failed architecture assumptions,
retracted Evidence used by multiple Decisions, and partial baseline replacement
remain uninvestigated here.

## CR1 findings: changed Requirement

CR1 is a hypothetical model test, not stakeholder approval. It supports existing
recommendations but resolves none of the question IDs above.

- **R1/B2:** Different Requirement/system revisions need distinguishable assessment
  records. This does not yet establish an independently managed assessment entity
  or ownership of delivery work.
- **R2/S1:** Opposite findings in different releases cannot be reduced to one
  Requirement status. Aggregation across contexts and conflicting reviewers remains
  open. A failing build alone does not establish baseline inconsistency.
- **S2/W1:** Draft impacts are prospective, not activation of a new obligation.
  Which approvals or uses of the old baseline must pause pending review, and who
  can authorize continued use without waiving R2?
- **S3/W1:** The walkthrough identifies successor acceptance and predecessor scope
  transfer separately. Must they take effect together? If the successor is accepted
  but supersession is refused, which obligation governs and how is overlap exposed?
  The example's assumed revision continuity does not settle identity boundaries.
- **E2/W2:** Existing measurements can be reinterpreted after applicability review,
  without transferring old verdicts. What makes a feasibility account sufficient
  for accepting R2 while the current build fails, and when must an accountable
  human endorse the new satisfaction finding?

## CR1-RS findings: refused supersession

[CR1-RS](scenarios/refused-requirement-supersession.md) tests Arun's request to
supersede R1 using Priya's R2 acceptance as supposed authorization. The mapping is
complete, but his mandate does not cover obligation disposition. Refusal leaves
both revisions accepted and R1 governing; R2's governing effect is not determined
by the refusal. No question ID is resolved and no policy branch is selected.

- **R2/S3/W1:** Does acceptance authorize future force pending explicit activation,
  or immediately add a current obligation until the predecessor is ended? The
  former permits accepted/non-governing R2; the latter makes both revisions govern.
  The thresholds in this example are compatible, not an implicit priority rule.
  Which coexistence is permitted, for how long, and on what conditions? If policy
  instead forbids two accepted revisions, how is the already recorded acceptance
  handled without rewriting history?
- **R2/S1/S3:** Authorization, scope/condition match, and present governing force
  answer different questions. Can force be determined from known policy and
  authorization, or does the domain need an independently managed lifecycle?
  What does "applicable" mean in each claim? The walkthrough establishes neither
  a new entity nor a universal activation transition.
- **R3/S3/W1:** Is an unspecified governing effect a blocking ambiguity under the
  acceptance guard, or is the relevant policy merely missing from the supplied
  record? If acceptance should have been blocked, who classifies and authorizes
  disposition of the already recorded acceptance without rewriting history?
- **W2/D3:** Who may set acceptance-effect/coexistence policy for C? Priya's example
  mandate permits this obligation's acceptance and supersession, not implicitly
  general policy-setting. What explicit authorization resolves a pending case,
  and when would joint or delegated authority be required?
- **S2/W1:** D1/B1 must expose accepted R2, refused transfer, and unresolved force
  without changing fixed premises. Which uses of B1 are permitted under each
  policy branch while BC2 is draft, and who can authorize them? Continued use is
  not implied by retained acceptance or refusal of Requirement supersession.
- **R2/W2:** An agent needs the exact acceptances, scope, disposition refusal and
  failed guard, governing basis or uncertainty, and authority to resolve it. Which
  authoritative policy/conditions let it distinguish accepted/non-governing from
  accepted/force-unknown? A bare `accepted` label cannot do that; no implementation
  design is established by this information need.

Next focused step: obtain stakeholder determinations on these policy alternatives
and mandates. The refusal case has been walked through; it must not be repeated
as if examples alone could ratify activation or continued-use policy.
