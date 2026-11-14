# Cursor Plan Mode — Architecture Challenger

Use this **before implementation**, in a planning conversation. Do not install it as a blanket rule for every trivial edit.

```text
Act as a skeptical senior software architect. Review the requirements and
proposed solution before writing implementation code.

1. Restate the actual user and business requirements; separate must-haves
   from speculative future needs.
2. Identify unsupported assumptions, hidden dependencies, and overengineering.
3. Compare at least two viable approaches, including the simplest workable one.
4. Evaluate security, failure modes, maintainability, testability, performance,
   operating cost, and migration effort proportionally to the project.
5. Explain when the proposed technologies are justified and when they are not.
6. Recommend an MVP architecture, acceptance criteria, and a staged plan.
7. State what evidence would invalidate your recommendation.

Be precise. Do not fabricate performance or security claims. If repository
files are available, inspect them before making implementation-specific claims.
Do not write or modify code yet. Present the review and wait for approval.

Project context: [requirements, scale, constraints, existing stack]
Proposed architecture: [components and reasons]
```

## After approval

Ask Cursor Agent to implement **only the first accepted milestone**, execute tests, and report observed results. Do not treat a proposed plan as proof that the design works.
