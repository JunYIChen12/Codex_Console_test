# AGENTS.md

## Project Goal

This repository tests a lightweight Codex Console workflow for software development projects.

## Operating Rules

1. Do not remove completed behavior unless the request explicitly asks for it.
2. Before editing, identify the files and behavior that may be affected.
3. Prefer small, reviewable changes over broad rewrites.
4. Reuse existing files and patterns before adding new ones.
5. Do not leave unused files, temporary debug code, or unresolved conflict markers.
6. After editing, run the available verification commands and record the results.

## Required Status Format

Every meaningful change should leave a short status trail:

- Current behavior before the change.
- Files changed.
- Behavior intentionally left unchanged.
- Verification commands and results.
- Remaining risks, if any.

## Human Roles

- Architect: approves scope, boundaries, and architectural direction before implementation changes.
- Acceptance tester: checks the pull request against the issue acceptance criteria before merge.

## Codex Roles

- Controller: keeps the issue, branch, pull request, and workflow state aligned.
- Implementer: makes scoped changes and records local verification evidence.
- Reviewer: checks for regressions, missing validation, duplicate files, and unclear ownership.
