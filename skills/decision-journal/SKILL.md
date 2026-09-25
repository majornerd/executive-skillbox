# Decision Journal

## Purpose

Maintain a low-weight, append-only evidence stream of decisions and judgment calls.

Capture decisions, deliberate non-decisions, alternatives, assumptions, rationale and later outcomes when they naturally emerge from work.

Do not turn journaling into work for the user.

## Principles

- Append rather than rewrite history.
- Preserve what was believed when the decision was made.
- Record deliberate decisions not to decide.
- Treat entries as evidence, not permanent conclusions about the user.
- Keep journal influence on the user model low.
- Ask only when missing information materially affects usefulness.
- Outcome maintenance should be headless whenever possible.

## Suggested record

```json
{
  "observed_at": "",
  "context": "",
  "decision": "",
  "type": "decision | judgment | non-decision",
  "alternatives": [],
  "rationale": [],
  "assumptions": [],
  "confidence": null,
  "outcome": null
}
```

Later outcome observations should append to history rather than silently rewriting the original decision.
