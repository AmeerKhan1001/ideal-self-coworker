# HUMANS.md

This file explains the human's role in an Ideal Self Coworker.

## Your job is not to maintain every file

A mature coworker should learn from normal work. You should not need to remember to update `CONTEXT.md` after every correction.

Your highest-value responsibilities are:

1. Define what “better” means.
2. Set principles and permission boundaries.
3. Give truthful corrections and feedback during real work.
4. Define or approve evaluations for important outcomes.
5. Retain authority over consequential decisions you have not delegated.
6. Review proposed changes to protected principles, permissions, security/privacy rules, and evaluation quality bars.

The coworker should handle much of the mechanical extraction, candidate-learning, testing, and maintenance below that layer.

## Start small

Do not model your entire life or job at once.

Choose one recurring outcome you can judge well. Examples:

- solve a normal bug end-to-end,
- produce a useful daily brief,
- assess a financial decision,
- evaluate a business opportunity.

Document enough context and operating behavior to do that one thing well. Add more only when real failures show what is missing.

## Define the ideal carefully

The Human Model should not blindly encode “what I usually do.”

Use this priority order when there is conflict:

1. protected values/principles,
2. desired outcomes and obligations,
3. evidence/current reality,
4. operating standards/workflows,
5. current habits/preferences.

A bad habit should not become a permanent rule simply because it is common.

## Give corrections naturally

During work, correct the coworker normally:

- “That repository is not authoritative; this one is.”
- “This needs approval before deployment.”
- “That brief includes too much low-value detail.”
- “We assumed demand; we did not validate it.”

A capable learning loop should determine whether the correction is one-off or durable, propose the smallest model change, and test it.

## Protect the judge

Do not let the same optimization step freely rewrite both:

- the Human Model candidate, and
- the evaluations used to declare that candidate better.

New evaluations are welcome. Weakening/removing meaningful existing evaluations should be reviewed separately.

## Decide what can self-update

A reasonable starting policy:

### Human approval required

- principles,
- ethics,
- authority and permission boundaries,
- privacy/security constraints,
- consequential financial or operational authority,
- removal/weakening of regression tests.

### Evaluation-gated updates may be allowed

- context,
- workflows,
- operating guidance,
- history,
- reusable learnings.

Tighten this further in high-risk domains.

## Do not put secrets in the repository

A Human Model can become extremely sensitive. Keep real instances private unless there is a deliberate reason not to.

Do not commit credentials, API keys, private keys, regulated personal data, employer-confidential information, or client secrets unless the repository and environment are explicitly authorized for that data.

## Stop redesigning when it works

Use this maintenance rule:

> Problem → smallest model/workspace change → evaluate → stop.

If the current architecture passes its real evaluations, use it. Let actual failures define the next change.
