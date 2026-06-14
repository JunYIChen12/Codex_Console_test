# Agent Registry: Multi-Dialog GitHub Loop V2

## Shared Directory

`D:\codexworks\Codex_Console_test\docs\workflows\2026-06-14-multi-dialog-github-loop-v2`

## Global Rules

- Read `workflow-state.md`, `agent-registry.md`, and `shared-task.md` before role work.
- Write only the canonical output file assigned to your role.
- Do not edit Controller-owned canonical files.
- Do not modify source code, package files, runtime config, CI, branches, commits, pushes, PRs, or issues.
- If blocked, write your assigned output with `status: blocked` and stop.

## Roles

| Role | Trigger Condition | Canonical Output | Allowed Writes |
| --- | --- | --- | --- |
| Architect | Controller setup exists | `architect-output.md` | `docs/workflows/2026-06-14-multi-dialog-github-loop-v2/architect-output.md` |
| Developer | `architect-output.md` exists | `developer-output.md` | `docs/workflows/2026-06-14-multi-dialog-github-loop-v2/developer-output.md`, `docs/multi-codex-collaboration.md` |
| Acceptance Tester | `developer-output.md` exists | `acceptance-output.md` | `docs/workflows/2026-06-14-multi-dialog-github-loop-v2/acceptance-output.md` |

## Handoff Order

1. Controller
2. Architect
3. Controller reconciliation
4. Developer
5. Controller reconciliation
6. Acceptance Tester
7. Controller final GitHub PR and merge flow
