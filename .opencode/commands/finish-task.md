---
description: Verify completed work, commit and push the task branch, and open or reuse its draft PR
agent: build
---

Complete the current work unit using the Git task-completion workflow in
`AGENTS.md`. Read the repository instructions and current project state first.

Task context supplied by the user: $ARGUMENTS

Establish the task branch, starting commit, and owned paths from the current
session before staging anything. If ownership or the base cannot be established,
stop and explain the blocker. Do not treat every dirty file as task-owned.

Verify the work, inspect all changes for scope and secrets, update `PROGRESS.md`
for substantive domain work, stage explicit paths, review the staged diff,
commit, push the task branch to `origin`, and confirm the remote commit hash.
Then check for an existing PR and reuse it, or create a draft PR targeting `main`
using `gh`, following the PR reporting and failure rules in `AGENTS.md`.
Honor required permissions and all stop conditions in `AGENTS.md`.

Report the branch, commit, verification results, confirmed push status, and PR URL
or exact blocker. This command finishes the current task; the new-work preflight
in `AGENTS.md` checks its merge and fast-forwards local `main` before creating the
next task branch. Preserve the project's domain-discovery restrictions.
