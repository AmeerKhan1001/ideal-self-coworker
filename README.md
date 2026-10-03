# Ideal Self Coworker

**A digital coworker modeled on your best version — with portable context, explicit workflows, evaluations, and a self-learning loop.**

Ideal Self Coworker is an open-source, model-agnostic architecture for building a digital coworker around an interpretable model of the human it serves.

It is not trying to clone every current habit. It is trying to help an AI operate according to the human's **best defined standard**: their real context, durable knowledge, principles, operating expectations, workflows, history, and learnings.

The project has two architectural halves:

```text
ideal-self-coworker/
├── AGENTS.md
├── HUMANS.md
├── human-model/
└── workspace/
```

- **`human-model/`** — durable intelligence: what the ideal version of the human should know and how it should operate.
- **`workspace/`** — workbench: evaluations, episodes, learning experiments, artifacts, and outputs.
- **`AGENTS.md`** — instructions for AI agents using the repository.
- **`HUMANS.md`** — instructions for the human who owns and shapes the coworker.

Project packaging such as this README, the license, and `.github/` community files is not a third architectural layer.

## Why this exists

General AI can already reason, write, search, code, and use tools. What it usually lacks is the durable, inspectable context required to operate well **for a particular human in a particular domain**.

The working hypothesis is:

> Better general intelligence + the right human model + explicit workflows + protected evaluations can produce a coworker that becomes more useful without requiring the human to repeatedly re-explain themselves.

The human should not have to manually maintain every context file after every interaction. Real work should generate experience; experience should generate candidate learnings; candidate changes should be evaluated before they are promoted into the durable human model.

## Core loop

```text
Real work
   ↓
Episode / outcome / human correction
   ↓
Candidate learning
   ↓
Small Human Model change
   ↓
Protected evaluations
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

The coworker may propose stronger evaluations, but it must not weaken or silently rewrite the tests used to judge the same change.

## Design principles

1. **Human-defined ideal, not behavioral cloning.** “Best” is defined by the human's principles, desired outcomes, authority boundaries, and evaluations — not inferred from every past behavior.
2. **Durable vs. transient separation.** Stable knowledge lives in `human-model/`; current work lives in `workspace/` or its natural external system.
3. **Interpretable by default.** Important operating knowledge should be readable and auditable as ordinary files.
4. **Retrieve live data from its source.** Do not copy changing facts into the human model when an authoritative system can provide them.
5. **Evaluation before promotion.** Self-learning changes are candidates until they pass relevant regression checks.
6. **Protected principles and authority.** Self-improvement must not optimize away ethics, permissions, privacy, security, or human approval boundaries.
7. **Smallest useful change.** Fix the demonstrated failure; do not redesign the entire repository because a new taxonomy looks cleaner.
8. **Model/runtime independence.** The architecture should survive changes in LLM providers, agents, and interfaces.
9. **One source of truth per fact.** Avoid duplicated context and competing versions.
10. **Human agency remains explicit.** The coworker assists and can become highly proactive, but consequential authority is granted rather than assumed.

## Structure

### Human model

```text
human-model/
├── README.md
├── CONTEXT.md
├── PRINCIPLES.md
├── OPERATING_SPEC.md
├── WORKFLOWS/
│   ├── README.md
│   └── TEMPLATE.md
├── HISTORY.md
└── LEARNINGS.md
```

| File | Purpose |
|---|---|
| `CONTEXT.md` | Durable facts, responsibilities, relationships, systems, constraints, goals, and domain knowledge the coworker cannot safely infer. |
| `PRINCIPLES.md` | Human-owned standards that define what “better” means. Protected from autonomous weakening. |
| `OPERATING_SPEC.md` | How the coworker should reason, communicate, prioritize, act, escalate, and handle uncertainty. |
| `WORKFLOWS/` | Repeatable procedures for recurring outcomes. |
| `HISTORY.md` | Past events and decisions that materially explain the present. Not a diary. |
| `LEARNINGS.md` | Reusable lessons that should change future behavior. |

### Workspace

```text
workspace/
├── README.md
├── evaluations/
│   ├── README.md
│   └── TEMPLATE.md
├── episodes/
│   ├── README.md
│   └── TEMPLATE.md
├── learning/
│   ├── PROTOCOL.md
│   └── results.tsv
├── artifacts/
│   └── README.md
└── outputs/
    └── README.md
```

| Area | Purpose |
|---|---|
| `evaluations/` | Protected quality bar: scenario tests, hard gates, regression cases, and outcome criteria. |
| `episodes/` | Compact records of meaningful work experiences, corrections, surprises, and outcomes. |
| `learning/` | The candidate-change → evaluate → keep/revert protocol. |
| `artifacts/` | Intermediate work that has no better authoritative home. |
| `outputs/` | Human-facing results that need a local home; otherwise outputs should go directly to their natural destination. |

## Quick start

### 1. Create a private instance

This public repository is a framework/template. A real human model can contain highly sensitive information. Prefer creating a **private repository** for your actual coworker unless you intentionally want the contents public.

### 2. Define your ideal

Start with `human-model/PRINCIPLES.md`. Write only principles you genuinely want the coworker to preserve. Define permission and approval boundaries in `OPERATING_SPEC.md`.

### 3. Add only useful context

Populate `CONTEXT.md` with durable information that materially changes decisions or execution. Do not create an autobiography or data dump.

### 4. Pick one proven workflow

Choose one recurring outcome you already understand — for example bug solving, a daily brief, financial decision support, client research, or proposal development — and instantiate `human-model/WORKFLOWS/TEMPLATE.md`.

### 5. Write evaluations before self-learning

Use `workspace/evaluations/TEMPLATE.md` to define what good performance looks like. Include hard failure gates where appropriate.

### 6. Work normally

Let the coworker do real work. Meaningful corrections, surprises, and outcomes become episodes.

### 7. Learn conservatively

Follow `workspace/learning/PROTOCOL.md`: extract the smallest candidate model change, run targeted and regression evaluations, keep improvements, and revert regressions.

## Using this across domains

The architecture is domain-general. The content is not.

Examples:

- **Work:** context + workflows may dominate: feature development, bug solving, investigation, PR review, deployment.
- **Personal:** context + operating spec may dominate: responsibilities, planning, daily briefs, financial decision support.
- **Business:** history + learnings + evidence discipline may dominate: opportunity assessment, experiments, offers, customer feedback.

### Recommended trust-boundary rule

Use one repository per **trust/confidentiality boundary**, not necessarily one repository per life category.

For example:

```text
# Employer-controlled environment
work-ideal-self-coworker/
├── human-model/
└── workspace/

# Personal environment (if appropriate)
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

A useful test:

- **“Would this still matter months from now?”** → probably `human-model/`.
- **“Is this about today's task/run?”** → probably `workspace/` or an external system.
- **“Can it be fetched live from an authoritative source?”** → keep it there; store only the routing/interpretation needed to use it.
- **“Is this a rule for producing an artifact?”** → human model/workflow.
- **“Is this the artifact produced for a specific case?”** → workspace or natural destination.

Example:

```text
How to produce QA cases        → human-model/WORKFLOWS/
QA cases for ticket ABC-123    → workspace/ or ticketing system

How to assess an opportunity   → human-model/WORKFLOWS/
Research for one opportunity   → workspace/artifacts/ or research system
```

## Self-learning safety model

Not all files have equal write authority.

### Human approval required by default

- `PRINCIPLES.md`
- permission and authority boundaries
- privacy/security rules
- consequential-action policies
- evaluation removals or material weakening

### Eligible for evaluation-gated learning

Depending on the domain and risk level:

- `CONTEXT.md`
- `OPERATING_SPEC.md`
- `WORKFLOWS/`
- `HISTORY.md`
- `LEARNINGS.md`

A candidate still must pass relevant evaluations and must not contradict protected constraints.

## Evaluation model

Do not reduce all human work to one arbitrary score. Prefer:

1. **Hard gates** — conditions that must never fail: correct source, no fabricated facts, required approvals, security/privacy boundaries, tests passing where applicable.
2. **Scenario evaluations** — representative cases with expected behavior.
3. **Regression evaluations** — previously solved failures that must stay solved.
4. **Quality comparisons** — correctness, completeness, clarity, maintainability, intervention required, beneficial proactiveness.
5. **Real-world outcomes** — when available, observed results outrank synthetic confidence.

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

Ideal Self Coworker synthesizes and extends ideas from two major stepping stones:

### Interpretable Context Methodology (ICM) — Jake Van Clief / Clief Notes

ICM demonstrates how ordinary folders and readable files can route AI to the right context and workflow stage, keeping the system auditable and portable rather than hiding behavior inside a large agent framework. Jake Van Clief's **“Customizing for Your Use Case”** material is a useful example of shaping filesystem workflows around the actual process rather than forcing one universal taxonomy.

- Clief Notes / ICM: https://www.skool.com/cliefnotes
- “3.2 Customizing for Your Use Case”: https://www.skool.com/cliefnotes/classroom/036893d9?md=1285fe09df7943e79e5d71c68b8b3ccb

### `autoresearch` — Andrej Karpathy

`autoresearch` demonstrates a constrained autonomous improvement loop: keep the evaluator stable, expose a bounded mutable surface, run repeated experiments, measure, retain improvements, and discard regressions. Ideal Self Coworker generalizes that pattern from model-training research to an interpretable human-model/workspace architecture.

- https://github.com/karpathy/autoresearch

This project is an independent synthesis and is not affiliated with or endorsed by Jake Van Clief, Clief Notes, Andrej Karpathy, or their projects.

## What this project is not

- Not a digital-twin claim that faithfully recreates a person.
- Not an excuse to upload private life or employer-confidential data into public repositories.
- Not a substitute for authorization, professional responsibility, or human judgment.
- Not a mandate to automate every workflow.
- Not a generic memory dump.
- Not tied to one model provider, IDE, agent, or SaaS platform.
- Not permission for an agent to alter its own ethics, authority, or evaluator until it passes.

## Project status

**Experimental / early architecture.** The current goal is to validate whether this two-part architecture produces durable improvements across real personal, business, and work use cases without becoming an unmaintainable context dump.

## Roadmap

### v0.1 — Architecture

- [x] Human Model / Workspace separation
- [x] Human and agent operating guides
- [x] Workflow, evaluation, and episode templates
- [x] Evaluation-gated learning protocol
- [x] Domain adaptation guidance

### v0.2 — Reference implementations

- [ ] Work-domain example using a fictional software-engineering environment
- [ ] Personal-domain example using synthetic/non-sensitive data
- [ ] Business-domain example showing fact → hypothesis → experiment → learning
- [ ] Example evaluation runner independent of model provider

### v0.3 — Self-learning harness

- [ ] Machine-readable candidate-change format
- [ ] Evaluation runner / regression report
- [ ] Protected-file policy enforcement
- [ ] Branch-based keep/revert learning loop
- [ ] Cost/time budgets for improvement experiments

## Contributing

Contributions are welcome, especially:

- clearer domain examples,
- evaluation patterns,
- privacy/security improvements,
- self-learning safeguards,
- empirical reports of what does and does not work,
- minimal tooling that preserves the filesystem-first design.

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

## Security and privacy

Do not report vulnerabilities containing real personal, employer, client, financial, or credential data in public issues. See [`.github/SECURITY.md`](.github/SECURITY.md).

## License

MIT. See [`LICENSE`](LICENSE).
