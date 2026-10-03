# Tests

Concrete test cases used to verify that the coworker behaves according to the Human Model, especially `human-model/TESTS_SPEC.md`.

The distinction is:

- **`human-model/TESTS_SPEC.md`** — the human's internal quality/judgment standard.
- **`workspace/tests/`** — specific cases that test whether the digital coworker applies that standard.

## Test types

- **Hard-gate tests** — must-pass constraints such as authorization, source correctness, non-fabrication, security, or required approvals.
- **Scenario tests** — representative situations with expected behavior/outcomes.
- **Regression tests** — cases added after a real failure so it does not recur.
- **Comparison tests** — compare a candidate Human Model against the current baseline.
- **Outcome tests** — use observed real-world results when available.

## Protection rule

Do not let a candidate Human Model change silently weaken or remove the test used to judge that same candidate.

Use `TEMPLATE.md` to add a test.
