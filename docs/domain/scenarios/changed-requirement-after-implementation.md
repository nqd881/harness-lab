# Changed Requirement After Implementation

## Status and scope

Scenario CR1, investigated on 2026-10-08. This is a hypothetical walkthrough of
the exploratory model, not an actual product evaluation, stakeholder Decision,
or approved policy. Findings validate internal distinctions under the assumptions
below; they do not establish universal rules or resolve the linked questions.

Scope: tighten one whole Requirement after an implementation has been evaluated.
Trace its review, replacement, satisfaction findings, and impacts on one Decision
and baseline. Partial replacement, Evidence retraction, and architecture redesign
are not investigated here. No new entities or implementation boundaries are assumed.

## Example assumptions

- Context C is the planned standard deployment of a search service. The obligation
  is internally chosen, not contractual or regulatory. Existing production use
  and release authorization are outside this walkthrough.
- Requirement R revision 1 (R1) is accepted for C. For a fixed representative
  workload W at 100 requests per second, the 95th-percentile response time must
  not exceed 500 ms. W specifies inputs, environment, warm-up, observation window,
  and treatment of errors. The example assumes W is an adequate evaluation method.
- R revision 2 (R2) changes only the threshold to 300 ms, with the same C and W.
  Treating this as a revision of R is an example assumption, not a resolution of S3.
- Decision D1 is adopted for C: retain the current search structure rather than
  introduce an alternative. Its rationale relies on sufficient response-time
  margin against R1, not an intrinsic prohibition on improving performance.
- Accepted baseline B1 fixes description revision A1, D1, and coverage of R1
  for C. It does not contain a hard 500 ms minimum or prove satisfaction.
- System revision S1 implements A1. Evidence E1 contains a reproducible measurement
  of 420 ms under W, with source, system revision, method, time, and limitations.
  Assessment F1 records R1/S1/W as `satisfied`. An external delivery record says
  the implementation work is complete; this is not another Requirement state.
- A separate structural review finds S1 conforms to B1 within its stated coverage.
  The response-time measurement alone is not that conformance finding.

The identifiers distinguish records and subjects for reasoning. They do not decide
whether assessments or baseline candidates have independent entity identity.

## Actors and mandates

| Actor | Example mandate | Limit |
| --- | --- | --- |
| Priya, product owner | Accept and supersede this internal obligation for C | Cannot accept architecture or authorize release by this mandate |
| Arun, architect | Review architecture impacts and accept a baseline for C | Cannot accept or waive R2 by architecture authority alone |
| Eva, evaluator | Record scoped findings and justify Evidence applicability | Findings do not approve obligations or deployment |
| Dev, developer | Implement changes and report external delivery progress | Code completion and authorship confer no approval authority |
| Assistant agent | Draft, request review, collect observations, and flag impacts | Cannot originate binding human authorization |

These mandates are stipulated for the example. Their establishment, delegation,
and any required joint approval remain W2/D3 questions.

## Walkthrough

Successful events use the existing discovery vocabulary. A refused request emits
none of the listed success events; no refusal-event model is introduced.

| Step | Actor and command | Guards and refusal conditions | Successful event and finding |
| --- | --- | --- | --- |
| 1. Draft tightening | Agent requests `ReviseRequirement` to create R2 | Preserve R1 and F1; identify changed threshold, unchanged context, rationale, and proposed whole-scope replacement. Refuse an in-place overwrite of accepted R1. | `RequirementRevised`: R2 is draft; R1 remains accepted and governing. |
| 2. Examine prospective impact | Agent requests `FlagDependencyImpact`; Arun reviews D1/B1 against proposed R2 | Identify the exact premise and proposed context. Refuse a claim that the draft already governs, or that every linked record is invalid. | `DependencyImpactFlagged`: compatibility with proposed R2 needs review; old findings against R1 are retained. |
| 3. Submit | Agent requests `SubmitRequirementForReview` for R2 | State criterion, C, W, source, known performance gap, feasibility risks, and replacement scope. Missing evaluation conditions block review. | `RequirementReviewRequested`: R2 is in review. |
| 4. Accept future obligation | Priya requests `AcceptRequirement` for exact reviewed R2 | Check her mandate, evaluability, desirability, and a reasoned feasibility account. For this example, a scoped analysis identifies a plausible improvement path; Priya explicitly acknowledges S1 fails R2. Do not hide a blocker as a reservation or treat acceptance as permission to deploy S1. | `RequirementAccepted`: R2 is accepted, not satisfied; B1 does not change lifecycle. |
| 5. Replace whole obligation | Priya requests `SupersedeRequirement` for R1 with accepted R2 | Map all R1 scope to R2, preserve history, and record authorized disposition. Refuse a draft successor or missing scope mapping. | `RequirementSuperseded`: R1 no longer governs C after replacement; F1 remains a historical R1/S1 finding. |
| 6. Reassess existing observation | Eva requests `RecordSatisfactionAssessment` for R2/S1/W using E1 | Verify unchanged W, exact system revision, coverage, provenance, and fitness of E1 for the new claim. Refuse a `satisfied` verdict copied from F1: 420 ms exceeds 300 ms. | `RequirementSatisfactionAssessed`: F2 is `not_satisfied` for R2/S1/W; E1 and F1 are not rewritten or retracted. |
| 7. Record dependency review | Arun requests `RecordConsistencyAssessment` for D1 and B1 against R2 | Review the margin premise and architectural coverage separately. E1 establishes a build shortfall, not an architectural impossibility. Record limits rather than invent a decisive conclusion. | `ConsistencyAssessed`: D1's R1 margin rationale is insufficient for R2; B1's support for R2 remains unresolved pending analysis. D1 stays adopted and B1 accepted. |
| 8. Prepare, but do not approve, a successor | Agent requests `AssembleBaselineCandidate` for candidate BC2 | Fix proposed description and applicable Decision revisions, R2 coverage, and gaps. Do not copy B1 approval or claim draft BC2 replaces it. | `BaselineCandidateAssembled`: BC2 is draft. Its design and acceptance are beyond this walkthrough. |

Steps 4 and 5 identify separate domain obligations, not an implementation ordering
or atomicity specification. The completed example assumes an explicitly authorized
whole-scope replacement. Whether acceptance and activation must coincide, and how
an intermediate overlap is governed if supersession fails, remain S3/W1 questions.
Acceptance alone must not be reported as a completed replacement.

No universally sufficient feasibility threshold is inferred from step 4. If the
example analysis is inadequate under the applicable risk policy, acceptance must
wait. A known failure of the current build is not automatically a contradiction
in a future obligation, but authority cannot make that build satisfy the criterion.

## Impact at the stopping point

| Subject | Preserved lifecycle/history | Scoped finding or limitation |
| --- | --- | --- |
| R1 | Superseded after explicit whole-scope transfer; acceptance retained | F1 still says S1 satisfied R1 under W at the evaluation time |
| R2 | Accepted | S1 does not satisfy it under W; acceptance is not fulfillment |
| E1 | Original observation preserved | Supports F1 and the contrary R2 verdict F2 through different interpretations |
| D1 | Adopted with its original premises intact | R1 margin cannot justify an R2 margin claim; replacement or reaffirmation needs further review |
| B1 | Accepted; fixed R1/D1/A1 references retained | Compatibility with R2 needs review; neither automatic retirement nor proof of continued-use permission |
| BC2 | Draft | Does not govern in place of B1 or prove satisfaction |

For D1, a failed margin claim is not proof that the selected structural choice is
inconsistent with R2. If a later analysis establishes a specific contradiction,
record `inconsistent` for that scope, then seek the appropriate authorized
disposition. If adequate analysis instead supports the same choice, record its
new basis without rewriting D1's historical rationale. How that reaffirmation
relates to resolution identity remains open.

## Counter-cases within CR1

- **Implemented but failing:** the completed delivery record for S1 coexists with
  F2 `not_satisfied`. Changing R2's lifecycle to "implemented" would lose this fact.
- **Different releases and later regression:** suppose E2 measures system revision
  S2 at 280 ms under W and E3 measures later S3 at 350 ms. Separate R2/S2/W and
  R2/S3/W findings are respectively `satisfied` and `not_satisfied`. R2 remains
  accepted. Neither result changes F2, authorizes release, or provides a universal
  "done" status. These are hypothetical branches, not work performed in CR1.
- **Non-comparable Evidence:** if R2 also changed workload or error treatment, E1
  might be insufficient. Do not infer failure or success just from comparing
  thresholds; record the coverage gap and seek applicable Evidence.
- **Wrong authority:** Arun or the agent attempts `AcceptRequirement` using a review
  finding as authorization. Refuse without Priya's explicit appropriate mandate;
  no `RequirementAccepted` event occurs. Likewise Priya's obligation approval
  cannot accept BC2 under her stipulated product-only mandate.
- **Proposed change rejected:** if Priya rejects R2 during review instead, R1
  continues to govern and F1 remains applicable to R1/S1/W. Prospective review
  records are retained but must not be mistaken for a changed governing premise.

## Findings and remaining questions

CR1 supports separating lifecycle, satisfaction, consistency, and conformance;
preserving revision-specific approvals; scoped impact review; and transition-specific
authority. None of those existing recommendations was contradicted by this example.

The counter-cases invalidate shortcuts, not ratified project policy: completion
means satisfaction; a new threshold rewrites past verdicts; old Evidence is either
automatically sufficient or always unusable; a failing build proves architectural
inconsistency; and one approval activates all related commitments.

The example requires distinguishable assessment records for historical claims but
does not demonstrate that an assessment needs its own entity lifecycle (R1/B2).
It also does not settle multi-context aggregation (R2/S1), sufficient feasibility
Evidence or human endorsement (E2/W2), replacement activation and failed scope
transfer (S3/W1), or continued use of a baseline pending review (S2/W1).
Candidate identity (A2) and general Decision-kind differences (D1) are not tested.

Next within this investigation: obtain stakeholder answers on when R2 becomes
governing and what blocks use of B1 while BC2 is draft. Test a refused supersession
before claiming the full replacement workflow is settled. See the CR1 findings in
[open questions](../open-questions.md#cr1-findings-changed-requirement).
