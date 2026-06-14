status: completed

## Recommended Document Structure

- Overview
- Controller setup responsibilities
- Role trigger order
- Canonical state ownership
- Worker output ownership
- GitHub Issue / Branch / PR / Actions closeout
- Verification checklist

## State Ownership Rules

- Controller owns `workflow-state.md`, `agent-registry.md`, `shared-task.md`, and `session-registry.md`.
- Architect owns only `architect-output.md`.
- Developer owns `developer-output.md` and `docs/multi-codex-collaboration.md`.
- Acceptance Tester owns only `acceptance-output.md`.
- Workers must not rewrite Controller-owned files or other role outputs.

## Trigger Order

1. Controller setup
2. Architect output
3. Controller reconciliation
4. Developer output and documentation change
5. Controller reconciliation
6. Acceptance Tester verdict
7. Controller PR, CI, merge, and issue closeout

## Developer Constraints

- Modify only `developer-output.md` and `docs/multi-codex-collaboration.md`.
- Do not modify Controller-owned files, `architect-output.md`, `acceptance-output.md`, source code, package files, runtime config, CI, branches, commits, pushes, PRs, or issues.
- Keep the documentation small, operational, and aligned with the canonical workflow files.

## Acceptance Focus

- Required role outputs exist in order.
- `docs/multi-codex-collaboration.md` covers the requested workflow topics.
- State ownership is clear.
- No forbidden files were modified.
- `git diff --check` and PR CI pass.
- Issue `#3` closes after merge.
