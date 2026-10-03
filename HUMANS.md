# HUMANS.md

This file explains the human's role in an Ideal Self Coworker.

## Your job is not to maintain every file

A mature coworker should learn from normal work. You should not need to remember to update `CONTEXT.md` after every correction.

Your highest-value responsibilities are:

1. Define what “better” means.
2. Set principles and permission boundaries.
3. Define the important internal checks in `human-model/TESTS_SPEC.md`.
4. Give truthful corrections and feedback during real work.
5. Define or approve concrete tests for important outcomes.
6. Retain authority over consequential decisions you have not delegated.
7. Review proposed changes to protected principles, permissions, security/privacy rules, test standards, and hard regression tests.

The coworker should handle much of the mechanical extraction, candidate-learning, testing, and maintenance below that layer.

## Start small

Do not model your entire life or job at once.

Choose one recurring outcome you can judge well. Examples:

- solve a normal bug end-to-end,
- produce a useful daily brief,
- assess a financial decision,
- communicate clearly with a coworker,
- evaluate a business opportunity.

Document enough context, operating behavior, and internal tests to do that one thing well. Add more only when real failures show what is missing.

## Define the ideal carefully

The Human Model should not blindly encode “what I usually do.”

Use this priority order when there is conflict:

1. protected values/principles,
2. desired outcomes and obligations,
3. evidence/current reality,
4. operating standards/workflows/tests,
5. current habits/preferences.

A bad habit should not become a permanent rule simply because it is common.

## Tests are part of the human model too

Humans continuously test their own candidate actions and outputs.

Example: you draft a Teams message, notice that it is too abrupt, revise it, mentally check it again, and then send it. The durable judgment behind that self-correction belongs in `human-model/TESTS_SPEC.md`.

The specific case used to verify that the digital coworker can do the same thing belongs in `workspace/tests/`.

So:

- **Tests spec = internal judgment.**
- **Tests folder = concrete test cases.**

## Give corrections naturally

During work, correct the coworker normally:

- “That repository is not authoritative; this one is.”
- “This needs approval before deployment.”
- “That message sounds too harsh; rewrite it.”
- “That brief includes too much low-value detail.”
- “We assumed demand; we did not validate it.”

A capable learning loop should determine whether the correction is one-off or durable, propose the smallest Human Model/test change, and test it.

## Protect the judge

Do not let the same optimization step freely rewrite both:

- the Human Model candidate, and
- the concrete tests used to declare that candidate better.

New tests are welcome. Weakening/removing meaningful existing regression tests should be reviewed separately.

## Decide what can self-update

A reasonable starting policy:

### Human approval required

- principles,
- ethics,
- authority and permission boundaries,
- privacy/security constraints,
- consequential financial or operational authority,
- protected sections of `TESTS_SPEC.md`,
- removal/weakening of regression tests.

### Test-gated updates may be allowed

- context,
- workflows,
- operating guidance,
- non-protected test refinements,
- history,
- reusable learnings.

Tighten this further in high-risk domains.

## Do not put secrets in the repository

A Human Model can become extremely sensitive. Keep real instances private unless there is a deliberate reason not to.

Do not commit credentials, API keys, private keys, regulated personal data, employer-confidential information, or client secrets unless the repository and environment are explicitly authorized for that data.

## Stop redesigning when it works

Use this maintenance rule:

> Problem → smallest model/workspace change → test → stop.

If the current architecture passes its real tests, use it. Let actual failures define the next change.
