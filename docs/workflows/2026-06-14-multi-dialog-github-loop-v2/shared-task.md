# Shared Task: Multi-Dialog GitHub Loop V2

## Objective

Create a small documentation change that explains the serial Codex multi-dialog collaboration workflow, while proving the roles are scheduled in order.

## Desired Product Change

Add one documentation page:

- `docs/multi-codex-collaboration.md`

The page should explain:

- Controller setup responsibilities.
- Role trigger order.
- Canonical state ownership.
- Worker output ownership.
- GitHub Issue / Branch / PR / Actions closeout.

## Acceptance Criteria

- `architect-output.md` exists before Developer starts.
- `developer-output.md` exists before Acceptance Tester starts.
- `acceptance-output.md` gives an explicit verdict.
- `workflow-state.md` is only updated by Controller.
- `docs/multi-codex-collaboration.md` exists.
- `git diff --check` passes.
- Pull request CI passes.
- Issue `#3` closes after merge.
