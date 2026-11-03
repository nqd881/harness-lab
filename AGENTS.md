# Agent Instructions

## Purpose

This repository is being used to discover and model the domain of a
software-development harness.

We are NOT currently implementing the harness application.

The current goal is to understand the domain well enough that an
implementation can later be derived from it.

## Start every session by reading

1. `PROJECT_STATE.yaml`
2. `PROGRESS.md`
3. `docs/domain/glossary.md`
4. Relevant files under `docs/domain/`

Do not assume conversation history is authoritative project state.

Persist important knowledge in the repository.

## Current scope

We are modeling concepts involved in managing software development.

Current core candidates include:

- Idea
- Requirement
- Question
- Decision
- Architecture Baseline
- Evidence
- Revision
- Trace Link
- Actor / Authority

These are hypotheses, not fixed design.

Challenge them when appropriate.

## Domain discovery rules

Do not jump directly to database schemas, APIs, classes, frameworks,
microservices, or implementation.

Prefer questions such as:

- What does this concept mean?
- Why does it exist?
- What information belongs to it?
- What lifecycle does it have?
- What invariants apply?
- What commands change it?
- What events result?
- What other concepts depend on it?
- What evidence is needed for a transition?
- Who has authority to perform the transition?

Distinguish carefully between:

- domain entity;
- value/object concept;
- lifecycle state;
- activity/process;
- artifact;
- evidence;
- event;
- command.

For example, "Draft" may be a state rather than an entity, and
"Discussion" may be an activity rather than a core entity.

## Modeling discipline

Do not treat the existing model as correct merely because it already
exists.

Record disagreement and uncertainty in:

`docs/domain/open-questions.md`

Do not silently resolve important ambiguity.

## Changes

When modifying a domain concept:

1. explain the reason;
2. consider effects on related concepts;
3. update relationships/invariants when necessary;
4. update `PROGRESS.md`;
5. leave unresolved questions explicit.

## Current implementation restriction

Do NOT create application source code unless `PROJECT_STATE.yaml`
explicitly changes the project into an implementation phase.

For now, work only on domain discovery and modeling.

## Git task-completion workflow

This is standing authorization to synchronize local `main` before new work and
to commit, push, and open draft PRs for successfully completed work units on
dedicated task branches. Apply it automatically; the user should not need to run
Git commands or invoke `/finish-task`, the explicit entry point to the same workflow.
Honor any newer user instruction and all required tool permissions/approvals.
This workflow does not authorize domain-policy decisions or application code.

### Before starting a new work unit

1. Inspect `git status --short --branch`, `git diff`, `git diff --cached`,
   `git remote -v`, and `git branch --show-current`.
2. Stop on any dirty working tree (including staged/untracked files), conflicts,
   detached HEAD, or unexpected/missing `origin`. Expected origin is
   `https://github.com/nqd881/harness-lab.git`. Report the exact blocker without
   altering or absorbing existing work.
3. Check `gh` availability/authentication. Identify the previous task from the
   current branch, or task/progress history if already on `main`. If one exists,
   query its PR with `gh pr list --repo nqd881/harness-lab --head <previous-task>
   --state all --json number,state,mergedAt,baseRefName,url`. Require a confirmed
   merge into `main`; stop for an open/draft, closed-unmerged, missing, or ambiguous
   PR, failed lookup, or unclear task ownership. Never interpret a lookup error
   as no PR, or infer a merge from local history alone.
4. Run `git fetch origin`, `git switch main`, then
   `git merge --ff-only origin/main`, stopping on failure. Require local `main`
   to equal `origin/main` afterward; stop if ahead/diverged. Never reset, rebase,
   force-update, discard work, or push directly to `main` to make synchronization
   succeed.
5. Create a fresh, uniquely named `task/<short-description>` branch from that
   synchronized `main` using `git switch -c`. Record its starting commit and scope.
   Never carry a previous task's unmerged commits into the new unit.

Resuming the same task is distinct from starting a new one: establish its branch,
starting commit, and owned paths before editing or finishing; stop on unrelated
changes or unclear ownership. Do not synchronize `main` mid-task.

### After successful work, before reporting completion

1. Run checks appropriate to the task. For documentation, review consistency,
   scope, and links and run `git diff --check`. If verification fails or work is
   incomplete, stop before committing and report the problem.
2. Update `PROGRESS.md` for substantive domain work, retaining explicit
   uncertainties. Workflow-only work may record its setup and verification there.
   Preserve `domain_discovery` and `implementation.allowed: false` unless the
   user explicitly authorizes a project-phase change.
3. Inspect `git status --short --branch`, `git diff`, `git diff --cached`,
   `git log --oneline -10`, and the task diff from its recorded starting commit.
   Inspect new/untracked files too. Check every proposed file for credentials,
   tokens, private keys, sensitive data, generated files, and unintended changes.
   If any unrelated changes or suspected secrets appear, stop and report them.
4. Confirm the current branch is the task's `task/*` branch and `origin` is the
   intended GitHub repository. Never automatically commit or push on `main` or
   any other non-task branch. Stage only explicit task-owned paths with
   `git add -- <paths>`; never use blanket staging (`git add .` or `git add -A`).
5. Review `git diff --cached --check`, `git diff --cached --stat`, and the full
   `git diff --cached` again for secrets and scope before committing. If there
   is no task diff, report a no-op; do not create an empty commit.
6. Create a meaningful, concise commit matching the repository's style. Honor
   hooks; never skip them. If a hook fails, inspect its effects and fix only
   task-owned problems, reverify, restage, and retry with a new commit command.
   Do not amend existing commits automatically.
7. Inspect the resulting commit and worktree. Push only the verified task branch
   using `git push --set-upstream origin HEAD:refs/heads/task/<actual-name>`
   (substitute the exact current branch). Never force-push, reset, discard work,
   bypass permissions/approvals, or automatically approve or merge a PR. Stop on
   conflicts, non-fast-forward rejection, authentication failure, or permission
   denial; preserve any local commit and report the exact blocker.
8. After a successful push, verify that `git ls-remote --heads origin
   refs/heads/task/<actual-name>` reports the same hash as `git rev-parse HEAD`.
   Do not claim remote success without confirmation.
9. Before PR creation, inspect status, branch tracking, recent history, every
   task commit, and the full diff against fetched `origin/main`. Use
   `gh pr list --repo nqd881/harness-lab --head <actual-task-branch> --state all
   --json number,state,baseRefName,url,isDraft` to check for an existing PR.
   Reuse its URL if it is open and targets `main`; stop on a closed/merged PR,
   mismatched base, or ambiguous results. Create only after a successful empty
   lookup; never create duplicates.
10. If none exists, run `gh pr create --repo nqd881/harness-lab --draft --base main
    --head <actual-task-branch> --title <task-summary> --body <task-report>`.
    Include the summary, changed files, verification commands/results, and unresolved
    questions (explicitly none if appropriate). Verify the PR's head, base, draft
    status, and URL with `gh pr view`. If reusing a PR, preserve user-authored details
    when updating task evidence. Never automatically mark ready, approve, or merge.
11. If `gh` is unavailable or authentication, permission, or API access fails,
    preserve the pushed branch and report the blocker without bypassing controls.
    If creation fails/times out, re-query before any retry to avoid duplicates.
    Report the branch, commit, checks, confirmed push status, and PR URL or exact
    blocker. Leave the task branch checked out.

Run this workflow once at successful task completion, not on each file edit,
assistant turn, or `session.idle` event. Read-only tasks with no changes need no
commit. This is agent-directed automation, not an unconditional event hook;
permissions and agent adherence still determine whether it executes.
