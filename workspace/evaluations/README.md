# Evaluations

Evaluations define what good performance means independently of a candidate Human Model change.

## Types

- **Hard gates** — must-pass constraints such as authorization, source correctness, non-fabrication, security, tests, or required approvals.
- **Scenario evaluations** — representative situations with expected behavior/outcome.
- **Regression evaluations** — cases added after a real failure so it does not recur.
- **Quality comparisons** — paired comparisons of candidate vs. baseline.
- **Outcome evaluations** — observed real-world results when available.

## Protection rule

Do not let a candidate Human Model change silently weaken/remove the evaluation used to judge that same candidate.

Use `TEMPLATE.md` to add an evaluation.
