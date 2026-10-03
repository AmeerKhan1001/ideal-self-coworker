# Learning Protocol

This protocol is inspired by the constrained experiment loop popularized by `karpathy/autoresearch`, generalized to an interpretable digital coworker.

The goal is not continuous uncontrolled rewriting. The goal is **bounded, evidence-driven improvement**.

## Trigger

Start a learning cycle only when real work or a test provides plausible durable evidence:

- a human correction,
- a repeated failure,
- a strong reusable success,
- a new durable fact,
- a real-world outcome that changes what good behavior looks like.

If there is no durable lesson, return to work.

## Step 1 — Establish the baseline

Identify the relevant current concrete test(s) in `workspace/tests/` and the baseline result before changing the Human Model.

Also identify the relevant internal checks in `human-model/TESTS_SPEC.md`.

Do not rewrite the judging concrete test to make the candidate easier to pass.

## Step 2 — Extract the smallest lesson

Classify the candidate as one of:

- context,
- operating specification,
- tests specification,
- workflow,
- history,
- reusable learning,
- proposed new concrete test.

Do not redesign unrelated files.

## Step 3 — Check write authority

### Protected: require human approval

- principles,
- ethics,
- permission/authority boundaries,
- privacy/security rules,
- consequential approval policies,
- protected internal tests,
- removing or materially weakening existing regression/hard-gate tests.

### Potentially autonomous after tests

Subject to the domain's risk level:

- context,
- operating guidance,
- non-protected internal test refinements,
- workflows,
- history,
- learnings.

## Step 4 — Create a candidate change

Prefer a branch or otherwise reviewable diff.

One candidate should test one coherent hypothesis where practical.

Record:

- evidence,
- expected improvement,
- files changed,
- relevant tests,
- time/cost budget.

## Step 5 — Run targeted tests

Test the exact failure/outcome the candidate is meant to improve.

If a hard gate fails, reject the candidate.

## Step 6 — Run regressions

Run relevant existing regression/scenario tests to detect collateral damage.

Do not require every possible test for every low-risk change; route to the smallest sufficient regression set.

## Step 7 — Compare

Prefer objective outcomes and paired baseline-vs-candidate comparisons over self-scoring.

A candidate may be promoted only when:

- required hard gates pass,
- the target problem materially improves,
- there is no unacceptable regression,
- protected principles, internal tests, and authority remain intact.

## Step 8 — Keep, revert, or defer

- **Keep** — promote the smallest useful change.
- **Revert** — discard a regression or ineffective change.
- **Defer** — evidence is insufficient or human approval is required.

## Step 9 — Record the experiment

Append a compact row to `results.tsv`.

## Step 10 — Continue real work

Do not let self-improvement consume the majority of the coworker's useful working time.

Use bounded improvement cycles. Real work produces the evidence that makes future learning meaningful.

## Test integrity

The coworker may propose a new test when a failure reveals a missing case. Add or strengthen it as a separate change. Do not allow the current candidate to delete or weaken the concrete test that judges it.

If the failure reveals that the *human's own internal judgment model* was incomplete, propose a corresponding change to `human-model/TESTS_SPEC.md` as well.

## Learning from success

Failures are not the only source of learning. If a successful approach is clearly reusable, encode it as a candidate workflow/operating/tests-spec improvement and test whether it generalizes.
