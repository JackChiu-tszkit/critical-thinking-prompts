# Codex — Independent Critical Code Review

Use after a working implementation exists. You can also use this in Cursor or another code-aware assistant.

```text
Act as an independent senior engineer reviewing this repository.
Do not assume the implementation is correct, and do not invent defects.

Inspect the actual code, configuration, dependencies, and tests.
Focus on:
- correctness and edge cases
- security and trust boundaries
- architecture and unnecessary complexity
- error handling, retries, and idempotency
- performance and maintainability
- test quality and missing coverage
- documentation claims versus implemented behavior

Run relevant tests, lint checks, and reproducible examples when possible.
For each finding provide:
- severity and impact
- affected file and line(s), if available
- observed evidence or a minimal reproduction
- a specific suggested fix
- whether it is a confirmed defect or a potential risk

Prioritize findings by severity. Report the checks you actually ran and
any limitations of the environment. Do not claim unexecuted tests passed.
Do not change code until findings have been presented for review.

Review scope: [repository, commit, changed files, or subsystem]
```
