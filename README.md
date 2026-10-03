# Ideal Self Coworker

**A digital coworker modeled on your best version — with portable context, explicit workflows, tests, and a self-learning loop.**

Ideal Self Coworker is an open-source, model-agnostic architecture for building a digital coworker around an interpretable model of the human it serves.

It is not trying to clone every current habit. It is trying to help an AI operate according to the human's **best defined standard**: their real context, principles, operating expectations, internal judgment, workflows, history, and learnings.

## Architecture

```text
ideal-self-coworker/
├── AGENTS.md
├── HUMANS.md
├── human-model/
│   ├── CONTEXT.md
│   ├── PRINCIPLES.md
│   ├── OPERATING_SPEC.md
│   ├── TESTS_SPEC.md
│   ├── WORKFLOWS/
│   ├── HISTORY.md
│   └── LEARNINGS.md
└── workspace/
    ├── tests/
    ├── episodes/
    ├── learning/
    ├── artifacts/
    └── outputs/
```

The project has two architectural halves:

- **`human-model/`** — durable intelligence: what the ideal version of the human should know, how it should operate, and how it should judge its own outputs/actions.
- **`workspace/`** — workbench: concrete tests, real-work episodes, learning experiments, artifacts, and outputs.

`AGENTS.md`, `HUMANS.md`, README, license, and `.github/` files are project instructions/packaging rather than a third architectural layer.

## The key distinction: tests spec vs. tests

Humans continuously test their own candidate actions.

You may draft a Teams message, realize it sounds unnecessarily harsh, revise it, check it again, and only then send it. The durable judgment that caused that correction is part of the human being modeled.

Therefore:

> **`human-model/TESTS_SPEC.md` = internal judgment.**  
> **`workspace/tests/` = concrete cases that verify that judgment.**

Example:

```text
Human Model:
Before sending an important message, check truthfulness,
clarity, tone, context, and unnecessary pressure.

Workspace test:
Given this blunt Teams follow-up, notice the tone problem
and revise it appropriately.
```

This keeps the *ability to judge* inside the Human Model while keeping individual regression/scenario cases in the workspace.

## Why this exists

General AI can already reason, write, search, code, and use tools. What it usually lacks is the durable, inspectable context and judgment required to operate well **for a particular human in a particular domain**.

The working hypothesis is:

> Better general intelligence + the right Human Model + explicit workflows + strong tests can produce a coworker that becomes more useful without requiring the human to repeatedly re-explain themselves.

The human should not have to manually maintain every context file after every interaction. Real work should generate experience; experience should generate candidate learnings; candidate changes should be tested before they are promoted into the durable Human Model.

## Core loop

```text
Real work
   ↓
Candidate output/action
   ↓
Internal tests from TESTS_SPEC.md
   ↓
Act / send
   ↓
Outcome / human correction / episode
   ↓
Candidate learning
   ↓
Small Human Model change
   ↓
Concrete workspace tests + regressions
   ↓
┌───────────────┐
│ Better?       │
├───────┬───────┤
│ yes   │ no    │
│ keep  │ revert│
└───────┴───────┘
   ↓
Continue working
```

The coworker may propose stronger tests, but it must not weaken or silently rewrite the concrete test used to judge the same candidate change.

## Human Model

### `CONTEXT.md`

Durable facts, responsibilities, relationships, systems, constraints, goals, and domain knowledge the coworker cannot safely infer.

### `PRINCIPLES.md`

Human-owned standards defining what “better” means. These are protected from autonomous weakening.

### `OPERATING_SPEC.md`

How the coworker should reason, communicate, prioritize, act, escalate, and handle uncertainty.

### `TESTS_SPEC.md`

How the ideal human internally tests whether a candidate output, decision, or action is good enough.

Typical internal checks include:

- truth/evidence,
- outcome fit,
- tone and communication,
- important constraints/trade-offs,
- principles and authority,
- completeness and quality.

### `WORKFLOWS/`

Repeatable procedures for recurring outcomes.

Examples:

- Work: feature development, bug solving, investigation, PR review, deployment.
- Personal: daily brief, financial decision support, travel planning.
- Business: opportunity assessment, customer research, experiments, proposals.

### `HISTORY.md`

Past events and decisions that materially explain the present. Not a diary.

### `LEARNINGS.md`

Reusable lessons extracted from experience that should change future behavior.

## Workspace

### `tests/`

Concrete scenario, regression, comparison, hard-gate, and outcome tests.

### `episodes/`

Compact records of meaningful work experiences, corrections, surprises, failures, and reusable successes.

### `learning/`

The candidate-change → test → keep/revert protocol.

### `artifacts/`

Intermediate work that has no better authoritative home.

### `outputs/`

Human-facing results that need a local home. Prefer natural destinations such as code hosts, ticketing systems, email, document systems, CRMs, or deployment systems when appropriate.

## Design principles

1. **Human-defined ideal, not behavioral cloning.** “Best” is defined by principles, desired outcomes, authority boundaries, internal tests, and real-world evidence — not every past behavior.
2. **Durable vs. transient separation.** Stable knowledge/judgment lives in `human-model/`; current work lives in `workspace/` or an authoritative external system.
3. **Interpretable by default.** Important operating knowledge should remain readable and auditable as ordinary files.
4. **Retrieve live data from its source.** Do not copy changing facts into the Human Model when an authoritative system can provide them.
5. **Test before promotion.** Self-learning changes remain candidates until relevant targeted/regression tests pass.
6. **Protected principles and authority.** Self-improvement must not optimize away ethics, permissions, privacy, security, or human-approval boundaries.
7. **Protect the judge.** A candidate change must not weaken the concrete test judging that same change.
8. **Smallest useful change.** Fix the demonstrated failure; do not redesign the entire repo because a new taxonomy looks cleaner.
9. **Model/runtime independence.** The architecture should survive changes in model providers, agents, and interfaces.
10. **Human agency remains explicit.** Consequential authority is granted rather than assumed.

## Quick start

### 1. Create a private instance

This public repository is a framework/template. A real Human Model can contain highly sensitive information. Prefer a **private repository** for your actual coworker unless you intentionally want the contents public.

### 2. Define the ideal

Start with:

- `human-model/PRINCIPLES.md`
- `human-model/OPERATING_SPEC.md`
- `human-model/TESTS_SPEC.md`

Define what matters, how the coworker should operate, how the ideal human would judge candidate outputs/actions, and what authority is granted.

### 3. Add only useful context

Populate `CONTEXT.md` with durable information that materially changes decisions or execution. Do not create an autobiography or data dump.

### 4. Pick one proven workflow

Use `human-model/WORKFLOWS/TEMPLATE.md` for one recurring outcome you already understand.

### 5. Add concrete tests

Use `workspace/tests/TEMPLATE.md` to create representative tests, especially for high-value or previously failed scenarios.

### 6. Work normally

Let the coworker do real work. Meaningful corrections, surprises, and outcomes become episodes.

### 7. Learn conservatively

Follow `workspace/learning/PROTOCOL.md`: extract the smallest candidate Human Model change, run targeted/regression tests, keep improvements, and revert regressions.

## Using this across domains

The architecture is domain-general. The content is not.

A recommended rule is **one repository per trust/confidentiality boundary** rather than necessarily one repo per life category.

For example:

```text
# Employer-controlled environment
work-ideal-self-coworker/
├── human-model/
└── workspace/

# Personal environment, if appropriate
personal-ideal-self-coworker/
├── human-model/
│   ├── personal/
│   └── business/
└── workspace/
    ├── personal/
    └── business/
```

If personal and business information require different privacy boundaries, split them too.

## What belongs where?

Useful tests:

- **Would this durable knowledge/judgment still matter months from now?** → probably `human-model/`.
- **Is this about today's task/run or one concrete test scenario?** → probably `workspace/`.
- **Can it be fetched live from an authoritative source?** → keep it there; store only the routing/interpretation required to use it well.
- **Is this a rule for producing/judging an artifact?** → Human Model.
- **Is this the artifact/test instance itself?** → Workspace or natural external destination.

Example:

```text
How to produce QA cases          → human-model/WORKFLOWS/
How to judge whether QA is good  → human-model/TESTS_SPEC.md
QA cases for ticket ABC-123      → workspace/ or ticketing system
Regression case for bad QA       → workspace/tests/
```

## Self-learning safety model

### Human approval required by default

- `PRINCIPLES.md`,
- ethics,
- authority/permission boundaries,
- privacy/security rules,
- consequential-action policies,
- protected portions of `TESTS_SPEC.md`,
- removal/material weakening of hard/regression tests.

### Test-gated updates may be allowed

Depending on the domain and risk level:

- `CONTEXT.md`,
- `OPERATING_SPEC.md`,
- non-protected `TESTS_SPEC.md` refinements,
- `WORKFLOWS/`,
- `HISTORY.md`,
- `LEARNINGS.md`.

## Proactivity

Proactivity is separate from self-learning.

A proactive coworker can continuously ask, within its permissions:

```text
Observe permitted sources
        ↓
Understand current state + Human Model
        ↓
Is there a beneficial action?
        ↓
Prepare candidate
        ↓
Run relevant internal tests
        ↓
Act or surface it within authority
        ↓
Verify outcome
        ↓
Record meaningful episode
        ↓
Learn when warranted
```

The goal is not activity for its own sake. A proactive action should have a clear expected benefit.

## Stepping stones and acknowledgements

Ideal Self Coworker synthesizes and extends ideas from two major stepping stones.

### Interpretable Context Methodology (ICM) — Jake Van Clief / Clief Notes

ICM demonstrates how ordinary folders and readable files can route AI to the right context and workflow stage, keeping the system auditable and portable rather than hiding behavior inside a large agent framework. Jake Van Clief's **“Customizing for Your Use Case”** material is a useful example of shaping filesystem workflows around the actual process rather than forcing one universal taxonomy.

- Clief Notes / ICM: https://www.skool.com/cliefnotes
- “3.2 Customizing for Your Use Case”: https://www.skool.com/cliefnotes/classroom/036893d9?md=1285fe09df7943e79e5d71c68b8b3ccb

### `autoresearch` — Andrej Karpathy

`autoresearch` demonstrates a constrained autonomous improvement loop: keep the judge stable, expose a bounded mutable surface, run repeated experiments, measure, retain improvements, and discard regressions. Ideal Self Coworker generalizes that pattern from model-training research to an interpretable Human Model / Workspace architecture.

- https://github.com/karpathy/autoresearch

This project is an independent synthesis and is not affiliated with or endorsed by Jake Van Clief, Clief Notes, Andrej Karpathy, or their projects.

## What this project is not

- Not a digital-twin claim that faithfully recreates a person.
- Not an excuse to upload private life or employer-confidential data into public repositories.
- Not a substitute for authorization, professional responsibility, or human judgment.
- Not a mandate to automate every workflow.
- Not a generic memory dump.
- Not tied to one model provider, IDE, agent, or SaaS platform.
- Not permission for an agent to alter its own ethics, authority, or tests until it passes.

## Project status

**Experimental / early architecture.** The current goal is to validate whether this two-part architecture produces durable improvements across real personal, business, and work use cases without becoming an unmaintainable context dump.

## Roadmap

### v0.1 — Architecture

- [x] Human Model / Workspace separation
- [x] Human and agent operating guides
- [x] Human `TESTS_SPEC.md` + concrete workspace test model
- [x] Workflow, test, and episode templates
- [x] Test-gated learning protocol
- [x] Domain adaptation guidance

### v0.2 — Reference implementations

- [ ] Work-domain example using a fictional software-engineering environment
- [ ] Personal-domain example using synthetic/non-sensitive data
- [ ] Business-domain example showing fact → hypothesis → experiment → learning
- [ ] Example test runner independent of model provider

### v0.3 — Self-learning harness

- [ ] Machine-readable candidate-change format
- [ ] Test runner / regression report
- [ ] Protected-file policy enforcement
- [ ] Branch-based keep/revert learning loop
- [ ] Cost/time budgets for improvement experiments

## Contributing

Contributions are welcome, especially clearer domain examples, test patterns, privacy/security improvements, self-learning safeguards, empirical results, and minimal tooling that preserves the filesystem-first design.

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

## Security and privacy

Do not report vulnerabilities containing real personal, employer, client, financial, or credential data in public issues. See [`.github/SECURITY.md`](.github/SECURITY.md).

## License

MIT. See [`LICENSE`](LICENSE).
