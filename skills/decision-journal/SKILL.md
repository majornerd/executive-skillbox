# Decision Journal

## Purpose

Maintain a low-weight, append-only evidence stream of decisions and judgment calls.

Capture decisions, deliberate non-decisions, alternatives, assumptions, rationale and later outcomes when they naturally emerge from work.

Do not turn journaling into work for the user.

## Shared context

Decision and outcome records use the provenance, time, confidence and lifecycle semantics in the [Shared Context and Evidence Contract](../../architecture/context-evidence-contract.md).

A decision is evidence about a choice. Do not automatically convert one decision into a durable claim about the user's personality, knowledge or future behavior.

## Principles

- Append rather than rewrite history.
- Preserve what was believed when the decision was made.
- Record deliberate decisions not to decide.
- Treat entries as evidence, not permanent conclusions about the user.
- Keep journal influence on the user model low.
- Ask only when missing information materially affects usefulness.
- Outcome maintenance should be headless whenever possible.

## Suggested decision payload

The shared evidence envelope should contain a decision payload such as:

```json
{
  "context": "",
  "decision": "",
  "type": "decision | judgment | non-decision",
  "alternatives": [],
  "rationale": [],
  "assumptions": [],
  "outcome": null
}
```

Later outcome observations should append to history rather than silently rewriting the original decision.
