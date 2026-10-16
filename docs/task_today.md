# Active Task
Task ID: T-001
Status: Ready
Goal: Inspect the current repository and report the safest implementation starting point.

## Context
Read `prd.md` and `implementation_plan.md` before making changes.

## Requirements
- Inspect the current working directory, repository structure, Git status, and existing project instructions.
- Identify whether Rust, Python, Docker, and database tooling are installed or configured.
- Identify existing files and code that can be reused.
- Do not overwrite or delete existing work.
- Do not implement the whole application in this task.
- Do not claim commands succeeded unless they were run and their output checked.

## Deliverables
1. A concise repository/environment summary.
2. A list of confirmed existing components and missing components.
3. Proposed Phase 1 changes with exact file paths.
4. Any blockers or decisions that require user input.
5. Suggested updates to `implementation_plan.md` based on observed facts.

## Acceptance criteria
- [ ] Repository facts are evidence-based.
- [ ] No application code changed unless needed for a minimal inspection artifact and approved.
- [ ] Risks and unknowns are clearly separated from facts.
- [ ] Next task is small enough to complete and verify in one focused session.

## Reference files
- `prd.md`
- `implementation_plan.md`
- `audit.md`
- `bugs.md`
- `testing.md`
