# Human Model

The Human Model is the durable, interpretable representation of the human standard the coworker should operate from.

It is not a complete copy of a person. Store only information that materially changes future reasoning, judgment, or execution.

## Contents

- `CONTEXT.md` — durable reality the coworker needs to know.
- `PRINCIPLES.md` — human-owned definition of “better.”
- `OPERATING_SPEC.md` — expected behavior, reasoning, communication, prioritization, and authority boundaries.
- `TESTS_SPEC.md` — how the ideal human internally judges whether an output, decision, or action is good enough.
- `WORKFLOWS/` — recurring ways of producing outcomes.
- `HISTORY.md` — past events/decisions that explain the present.
- `LEARNINGS.md` — reusable lessons that should affect future behavior.

## Tests spec vs. tests folder

`TESTS_SPEC.md` is part of the Human Model because self-checking and quality judgment are part of the human being modeled.

Concrete test cases live in `workspace/tests/` because they are external cases used to verify that the digital coworker actually applies that judgment.

## Rule

If something is primarily about a specific current run, task, ticket, decision, experiment, test case, or output, it probably belongs in `workspace/` or its authoritative external system instead.
