## Harness experiment — CR1 execution recovery

Date: 2026-10-08

### Setup

A completely fresh agent session was started with no previous
conversation context.

The agent recovered project state from the repository and proposed
continuing the changed-Requirement scenario from PROGRESS.md.

### Observed behavior

The agent:

- correctly recovered domain_discovery;
- respected implementation prohibition;
- selected the expected next scenario;
- kept PROJECT_STATE.yaml unchanged;
- persisted scenario findings;
- preserved unresolved questions;
- distinguished hypotheses from accepted policy;
- performed read-only review and git diff verification.

### Domain discoveries

The scenario strengthened these hypotheses:

- Requirement lifecycle is distinct from satisfaction.
- Satisfaction is revision/context specific.
- Historical Evidence can remain valid after Requirement revision.
- Requirement acceptance and governing applicability may be distinct.
- Downstream architecture should be reviewed rather than automatically invalidated.
- Authority is transition-specific.

### Harness failures observed

None critical in this session.

### Risks to watch

- Domain vocabulary is expanding quickly.
- Candidate concepts such as Assessment must not automatically become entities.
- Scenario prose is becoming large; future harness versions may need more structured representations.

### Result

Execution recovery: PASS.