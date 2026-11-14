# Example: Cursor reviews an Agent Harness before implementation

## Initial proposal

> Build a calculator agent using LangGraph, MCP, FastAPI, SQLite, OpenTelemetry, and Docker.

## Critical architecture review

**Requirement:** Accept arithmetic requests, calculate reliably, and return validated results.

**Question 1 — Is an LLM necessary?**

For deterministic arithmetic expressions, a safe parser and calculator may be enough. An LLM adds ambiguity and operational cost unless natural-language understanding is a requirement.

**Question 2 — Is MCP necessary?**

For one local calculator tool, a Python function is simpler. MCP is more valuable when standardized interoperability across clients or tool servers is a genuine requirement.

**Question 3 — Is persistence necessary?**

If every calculation is stateless, SQLite checkpoints may not be needed. Add persistence when sessions, multi-step tasks, or recovery become requirements.

## Two options

| Option | Components | When to choose |
| --- | --- | --- |
| Minimal MVP | FastAPI + validated calculator + pytest | Demonstrate safe, deterministic calculation |
| Agent workflow MVP | FastAPI + LangGraph + one tool + tests | Demonstrate state transitions and tool selection |

## P1 — Acceptance criteria

1. Valid expressions produce correct results.
2. Invalid input returns a clear error.
3. No arbitrary code execution is possible.
4. Unit tests cover division by zero, invalid syntax, and input limits.
5. Quick Start commands work in a clean environment.

## P2 — Extension triggers

- Add LangGraph when actual multi-step orchestration is needed.
- Add MCP when external tool interoperability is demonstrated.
- Add SQLite when durable sessions or resumability are needed.
- Add tracing when execution spans multiple services or debugging warrants it.

**Cursor instruction:** Present this assessment first. Wait for approval before implementing the selected option.

*Illustrative design critique, not a benchmark or verified implementation.*
