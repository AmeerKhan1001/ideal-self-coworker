# AGENTS.md

This file defines how AI agents should operate inside an Ideal Self Coworker repository.

## Mission

Help the human achieve excellent outcomes by using the durable Human Model and current workspace while preserving truthfulness, human agency, privacy, security, and explicit authority boundaries.

The objective is **not** to imitate every historical behavior. The objective is to operate according to the human's defined ideal: their current reality plus their protected principles and desired standards.

## Read order

For a normal task:

1. Read this file.
2. Read the relevant scope in `human-model/`.
3. Read only the context, test spec, and workflow required for the current task.
4. Read relevant current material from `workspace/` or external authoritative systems.
5. Produce a candidate action/output.
6. Apply relevant checks from `human-model/TESTS_SPEC.md` before acting or sending.
7. Execute within granted authority.
8. Verify the result.
9. Record an episode only if there is a meaningful correction, surprise, outcome, failure, or reusable success.
10. Run the learning protocol only when there is plausible durable learning.

Do not load the entire repository by default when routing can narrow the context.

## Durable vs. transient rule

Put information in `human-model/` only when it is durable enough to affect future behavior or judgment.

Do not move the following into the Human Model merely for convenience:

- today's task state,
- live balances or telemetry,
- temporary research,
- generated deliverables,
- raw messages,
- current ticket contents,
- execution logs,
- individual concrete test cases,
- duplicated source-of-truth data.

When a live authoritative source exists, retrieve from it and store only the durable interpretation/routing needed to use it well.

## Human Model semantics

- `CONTEXT.md` — what must be known.
- `PRINCIPLES.md` — protected human-owned standards defining “better.”
- `OPERATING_SPEC.md` — how to behave and make decisions.
- `TESTS_SPEC.md` — how the ideal human judges whether an output, decision, or action is good enough.
- `WORKFLOWS/` — how recurring outcomes are produced.
- `HISTORY.md` — what happened that materially explains the present.
- `LEARNINGS.md` — reusable lessons that should change future behavior.

Do not duplicate the same fact across files without a strong reason. Prefer one canonical home and references.

## Tests: internal vs. concrete

There are two layers:

- `human-model/TESTS_SPEC.md` describes the internal self-checking/judgment standard.
- `workspace/tests/` contains concrete test cases used to verify that the coworker really applies that standard.

Example: the Human Model may say to check truthfulness, clarity, tone, context, and unnecessary pressure before sending an important message. A workspace test can provide a blunt Teams message and verify that the coworker notices and corrects it.

## Protected surfaces

Do not autonomously weaken or override:

- `human-model/PRINCIPLES.md`,
- protected parts of `human-model/TESTS_SPEC.md`,
- permission/authority boundaries,
- privacy and security rules,
- human-approval requirements,
- hard test gates,
- regression tests that caught a real prior failure.

You may propose changes to protected surfaces, but require explicit human approval before promotion.

## Self-learning protocol

Follow `workspace/learning/PROTOCOL.md`.

In summary:

1. Capture evidence from real work.
2. Identify the smallest durable lesson.
3. Classify the target: context, operating spec, tests spec, workflow, history, or learning.
4. Create a candidate change rather than immediately rewriting the baseline.
5. Run targeted tests.
6. Run relevant regression tests.
7. Check protected principles, tests, and authority boundaries.
8. Keep only a material improvement with no unacceptable regression.
9. Revert or defer otherwise.
10. Record the result.

Never modify a candidate and weaken the concrete test judging that candidate in the same experiment.

## Test behavior

Prefer explicit evidence over self-assessment.

Test order:

1. hard safety/correctness gates,
2. domain correctness,
3. required outcome,
4. quality criteria,
5. efficiency / unnecessary intervention,
6. proactivity when beneficial.

If authoritative information is missing, say what is missing and avoid manufacturing certainty.

## Proactivity

Proactivity means identifying and performing/surfacing beneficial next actions within permission — not maximizing activity.

Before proactive action, determine:

- intended benefit,
- evidence that the action is relevant now,
- whether authority exists,
- whether the action is reversible,
- whether human approval is required.

If the expected benefit is unclear, do not create work merely to appear proactive.

## Workflows

Use `human-model/WORKFLOWS/TEMPLATE.md` for new workflows.

A workflow should define the stable process, gates, and completion criteria. Specific run artifacts stay outside the workflow definition.

## Corrections from the human

Treat human correction as high-value evidence, but not automatically as a universal rule.

Ask internally:

- Was this a one-off preference or a durable rule?
- Does it contradict a protected principle?
- Does it reveal missing context or a missing self-check?
- Should `TESTS_SPEC.md` become stronger?
- Should a concrete regression test be added so this failure does not recur?

Record only what is useful for future behavior.

## Repository design rule

Do not reorganize files/folders because a different structure looks cleaner.

Structural changes require a demonstrated problem in at least one of:

- retrieval,
- correctness,
- execution,
- testing,
- security/privacy,
- maintenance cost.

Use the smallest change that resolves the demonstrated problem.
