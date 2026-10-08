# Evidence

## Working conclusion

Evidence deserves first-class domain consideration because the same observation
can support several claims, be challenged later, and require provenance when a
commitment is reviewed. Merely attaching a document to a Requirement loses why it
was relevant. This is a recommendation, not promotion to a settled core entity.

Counterexample: if Evidence is only a one-time citation with no independent
history, reuse, or reassessment, a value/reference concept may be sufficient.
Independent identity must earn its place through domain behavior, not because
the harness can store files.

## Meaning and information

Evidence is identifiable information supporting or challenging a claim in a
context. Examples include an experiment result, stakeholder statement, analysis,
test observation, or review finding. An artifact is its representation; an
evaluation interprets it. A failed test is still Evidence. Confidence is a
judgment about a claim, not an inherent truth score on an Evidence item.

Candidate information:

- Identity and source/content revision or stable reference; observation time,
  recording time, author/producer, and method.
- Subject and environment: relevant Requirement, system, Decision, description,
  or baseline revisions; assumptions and evaluation conditions.
- Observed result, limitations, reproducibility information when applicable, and
  accessibility constraints.
- Links to the particular claims supported or challenged, each with interpretation,
  context, assessor, and any confidence/rationale.
- Challenges, corrections, and replacement references without erased provenance.

An item can support one claim and challenge another. A new Requirement does not
alter the historical observation; it may make an interpretation inapplicable.

## Lifecycle and invariants under investigation

Candidate provenance states are `recorded`, `retracted`, and `superseded`.
`challenged` is better modeled as an open challenge, not necessarily a global
state. Availability and fitness-for-use are independent, contextual concerns.

- Record preserves source, observation, context, and the distinction between
  observation and interpretation. Unknown provenance is stated explicitly.
- Retraction preserves the item and reason; replacement preserves the old result
  and identifies corrected Evidence. Neither deletes dependent decisions.
- Linking Evidence specifies a claim and relevance, not just an attachment.
- Evidence required for a transition must be inspectable or its limitations and
  permitted access conditions explicitly acknowledged by the reviewing authority.
- Challenged or retracted Evidence triggers review of dependent claims; it does
  not automatically prove their negation.
- Evidence sufficiency depends on claim, purpose, risk, method, and applicability.
  Quantity of citations is not an acceptance threshold.

## Commands, events, and authority

Candidate pairs: `RecordEvidence` / `EvidenceRecorded`, `LinkEvidenceToClaim` /
`EvidenceLinkedToClaim`, `ChallengeEvidence` / `EvidenceChallenged`,
`RetractEvidence` / `EvidenceRetracted`, and `SupersedeEvidence` /
`EvidenceSuperseded`. Producers and agents may record observations; permitted
reviewers may challenge them. Who may retract an observation or endorse its
interpretation remains open. No Evidence action independently grants human
authority to accept an obligation, adopt a choice, or activate a baseline.

## Related concepts and open questions

Idea value judgments, Requirement feasibility and satisfaction, Decision premises,
and baseline acceptance all use Evidence for different claims. Acceptance records
must preserve the specific Evidence relied upon and the interpretation at that
time. See [E1-E3](open-questions.md#evidence) for identity boundaries, sufficiency,
and correction/access authority. This file explores the supporting candidate
without changing the project's declared core candidates.
