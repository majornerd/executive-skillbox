# Shared Context and Evidence Contract

## Purpose

Provide a common language for persistent context across Executive Skillbox.

This is infrastructure, not a user-facing skill. It defines what evidence means and how skills exchange it without prescribing a database, memory product or storage engine.

The contract exists to prevent separate skills from creating incompatible versions of the user, their decisions or their history.

## Principles

- Persistent context is evidence, not immutable truth.
- Preserve provenance.
- Preserve time.
- Preserve uncertainty.
- Preserve disagreement.
- Never silently convert inference into fact.
- Append meaningful history rather than rewriting it away.
- User corrections are evidence and should affect confidence immediately.
- Storage implementation is replaceable. Semantics are not.
- Collect only context that can improve the work or relationship.

## Evidence record

A conforming observation should be representable as:

```json
{
  "id": "",
  "observed_at": "",
  "effective_from": null,
  "effective_to": null,
  "subject": "",
  "predicate": "",
  "value": null,
  "kind": "stated | observed | inferred | decision | outcome | external",
  "source": {
    "type": "conversation | artifact | system | external",
    "reference": null
  },
  "context": null,
  "confidence": "low | medium | high",
  "status": "active | superseded | disputed | stale | unresolved",
  "related": [],
  "notes": null
}
```

Implementations may add fields. They should not remove the semantic distinctions above when those distinctions are known.

## Time

`observed_at` records when the system learned or observed something.

`effective_from` and `effective_to` describe when the claim is true when known.

These are different.

"I am CEO of X" observed today does not prove the role began today. Record the observation date and leave the start date unknown unless evidence establishes it.

Missing temporal information should remain missing rather than being invented.

Two apparently contradictory observations may both be true at different times.

## Evidence kinds

**stated** - the user explicitly said it.

**observed** - behavior or work directly demonstrated it.

**inferred** - the advisor derived it from other evidence.

**decision** - the user or authorized actor made a choice or deliberate non-choice.

**outcome** - later evidence about what followed a decision or action.

**external** - evidence came from an outside artifact or source.

Kinds describe provenance, not reliability. A stated belief can be mistaken. An inference can be strong. Preserve both kind and confidence.

## Confidence

Confidence describes confidence in the claim represented by the record, not confidence in the user.

Prefer natural-language confidence unless an implementation has a reason to require numeric values.

Confidence should change when evidence changes.

Do not manufacture precision.

## Status and history

Do not delete inconvenient history simply because newer evidence differs.

Use status to preserve lifecycle:

- **active** - currently usable evidence
- **superseded** - newer evidence replaces it
- **disputed** - evidence or the user contests it
- **stale** - age or changed conditions reduce usefulness
- **unresolved** - material ambiguity remains

A correction should normally create or preserve enough history to understand what changed.

## Conflicts

A conflict is a relationship between evidence records, not permission to choose whichever claim seems more plausible.

Classify before resolving:

- direct contradiction
- possible contradiction
- temporal ambiguity
- entity ambiguity
- interpretation disagreement
- stale evidence
- unresolved provenance

When resolution affects current work and the user can resolve it cheaply, ask.

When it does not affect current work, queue it for Context Integrity rather than interrupting.

Never treat disagreement over interpretation, values, priorities or risk tolerance as a factual contradiction.

## Derived user-model claims

User Model entries should reference the evidence that supports them.

A model claim may summarize multiple observations, but it must remain distinguishable from those observations.

Example:

```json
{
  "claim": "prefers concise executive communication",
  "confidence": "high",
  "evidence": ["obs-17", "obs-42", "obs-81"],
  "last_evaluated_at": ""
}
```

Do not let a derived claim become its own circular evidence.

## Decisions

Decision Journal records use the same provenance and time semantics.

A decision is evidence about a choice. It is weak evidence about personality, knowledge or future choices unless repeated observations support that inference.

Outcomes append to decisions. They do not rewrite what was known when the decision was made.

## Learning

TeachGap may consume evidence of a possible knowledge gap.

Completing a TeachGap is not evidence of mastery.

Future demonstrated use is stronger evidence than lesson completion.

Disagreement is not evidence of a knowledge gap.

## Professional signal

Professional Presence may consume demonstrated work, decisions, outcomes and explicit user claims.

Public-facing recommendations should distinguish aspiration from demonstrated evidence.

Do not convert private or sensitive context into public signal merely because it exists in the shared context layer.

## Privacy boundary

Availability is not permission.

Skills should consume only the context needed for their purpose.

Sensitive observations should not automatically propagate into user-facing output or public-facing artifacts.

## Portability

The contract should work whether context is stored in files, a database, model memory, a vector store, an event log or another system.

A conforming implementation should be able to export evidence without losing provenance, temporal meaning, confidence, status or relationships.

## Success

The shared context layer succeeds when different skills can reason from the same evidence without silently changing what that evidence means.
