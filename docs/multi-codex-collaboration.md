# Multi-Codex Collaboration

## Overview

This workflow uses serial Codex dialogs to move a GitHub-backed task from setup to verification without giving every role write access to every file. Each role starts only after its trigger file exists, writes only its assigned output, and leaves Controller-owned state unchanged.

The loop is intentionally small:

1. The Controller prepares the canonical workflow state and GitHub context.
2. The Architect records the expected documentation structure and constraints.
3. The Developer creates the product documentation and its handoff output.
4. The Acceptance Tester verifies the documented behavior and reports a verdict.
5. The Controller reconciles outputs, opens the PR flow, watches CI, merges, and confirms issue closeout.

## Controller Setup Responsibilities

The Controller owns the workflow setup and canonical state. It prepares the shared workflow directory, records the target repository, GitHub issue, branch, role order, allowed write paths, and verification plan.

Controller-owned files are the source of truth for scheduling and state:

- `workflow-state.md`
- `agent-registry.md`
- `shared-task.md`
- `session-registry.md`

Workers read these files before acting, but do not rewrite them.

## Role Trigger Order

Roles run in a strict serial order so each dialog can depend on the previous role's output:

1. Controller setup exists.
2. Architect starts and writes `architect-output.md`.
3. Controller reconciles the Architect output.
4. Developer starts after `architect-output.md` exists, then writes `developer-output.md` and `docs/multi-codex-collaboration.md`.
5. Controller reconciles the Developer output.
6. Acceptance Tester starts after `developer-output.md` exists, then writes `acceptance-output.md`.
7. Controller performs the final PR, CI, merge, and issue closeout flow.

## Canonical State Ownership

Canonical state belongs to the Controller. The state files describe the workflow goal, allowed paths, role status, ownership boundaries, and verification expectations.

Workers must preserve those files exactly during role work. If a worker is blocked, it should record the blocker in its assigned output file instead of editing Controller state.

## Worker Output Ownership

Each worker owns only its canonical output:

- Architect owns `architect-output.md`.
- Developer owns `developer-output.md` and the requested product documentation page.
- Acceptance Tester owns `acceptance-output.md`.

This keeps role handoffs auditable. A later role can inspect earlier outputs, but it does not revise them.

## GitHub Issue / Branch / PR / Actions Closeout

The GitHub loop is coordinated by the Controller. The shared state records the issue, branch, and repository target so every role works from the same context, but workers do not create branches, commit, push, open PRs, modify CI, or update GitHub issues.

After all role outputs are complete, the Controller is responsible for:

- reconciling the final workflow state;
- preparing the pull request;
- waiting for GitHub Actions or required CI checks;
- merging when the PR is ready;
- confirming the linked GitHub issue closes after merge.

## Verification Checklist

- `architect-output.md` exists before Developer work starts.
- `developer-output.md` exists before Acceptance Tester work starts.
- `acceptance-output.md` gives an explicit verdict.
- Controller-owned state files are unchanged by workers.
- `docs/multi-codex-collaboration.md` exists and describes the serial collaboration loop.
- Whitespace checks such as `git diff --check` pass before PR.
- Pull request CI passes.
- The linked GitHub issue closes after merge.
