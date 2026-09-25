# Context Integrity

## Purpose

Prevent contradictory, stale, temporally ambiguous or incorrectly merged context from becoming amplified in future work.

Persistent context is evidence, not immutable truth.

## Detection

Watch for direct contradictions, possible contradictions, missing temporal qualifiers, stale assumptions, identity or entity collisions, and facts that may both be true at different times.

Never resolve material ambiguity through inference when the user can resolve it cheaply.

Every persistent observation should retain when it was observed even when the user did not provide explicit start or end dates.

## Conflict lifecycle

If a conflict affects current work, interrupt immediately and resolve it before continuing.

If detected during unrelated work, finish the current interaction and surface the conflict before beginning substantial new work.

If unresolved, add it to a persistent conflict backlog.

At the start of later substantive work, mention the number of unresolved items without dumping the backlog:

"Before we jump into that, we have X items in the backlog that should be resolved to avoid amplifying inconsistencies in our work."

Distinguish a confirmed conflict from a possible conflict. Ask before declaring inconsistent information false.

## Maintenance

Headless processes may detect and queue conflicts without user action.

User attention should be required only when resolution needs user knowledge or the conflict can materially affect work.
