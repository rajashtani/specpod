# SpecPod: Specification-Driven Development with the Tripod Model

> A lightweight, auditable SDD framework for agentic software delivery — built for lean teams, regulated domains, and production-grade outcomes.

---

## What is SpecPod SDD?

SpecPod SDD is an opinionated approach to **Specification-Driven Development** (SDD) that puts structured, versioned Markdown specs at the centre of every delivery cycle. Rather than prompting AI agents loosely and iterating by trial and error ("vibe coding"), SpecPod treats the spec as the **contract** — the single source of truth that guides agents deterministically from intent to production code.

SpecPod builds on the 2025–2026 SDD ecosystem (GitHub Spec Kit, Kiro, Tessl, Augment Code) but adds three specific innovations:

1. **The Tripod Team** — a three-human delivery unit with clean adversarial separation of roles
2. **The `.sdd/` Specification Vault** — a folder convention that enforces context hygiene and prevents agent drift
3. **Revision Orders** — a formal feedback artifact that keeps failure routing clean and traceable

---

## Core Principles

| Principle | What it means in practice |
|---|---|
| **Spec is the contract** | No implementation begins without approved `requirements.md` and `design.md` |
| **Green tests are progress** | The only valid progress metric is passing BDD-derived tests — not lines of code |
| **Context hygiene prevents drift** | Completed features are archived, not left active, so agents never carry stale context |
| **Adversarial roles catch failures** | The Reviewer finds failures; it does not confirm success |
| **Human judgment at every gate** | Agents execute; humans approve, route, and sign off |

---

## The Tripod Team

*One Tripod delivers what a two-pizza team used to deliver, with a full auditable spec trail.*

```
            The Anchor
        (Intent Leg — BA/Architect)
               △
              /|\
             / | \
            /  |  \
           /   |   \
          ▽         ▽
   AI Wrangler      Oracle
  (Build Leg)   (Truth Leg — SME)
```

### Why Three?

| Team Size | Fit for Tripod Model? | Reason |
|---|---|---|
| 1–2 | ✗ No | No adversarial check; single point of failure |
| **3** | **✓ Yes** | Clean separation of concerns; built-in adversarial validation |
| 5–8 | Overkill | Coordination overhead returns for most scoped features |
| 10+ | ✗ No | Ceremony and bureaucracy re-emerge |

Three is the smallest stable unit that provides full-cycle accountability without coordination tax. Each leg owns a distinct phase:

---

### Leg 1 — The Intent Leg (Anchor)

**Who:** Business Analyst + Architect (one leg, not one person)

**What they own:**
- `requirements.md` — the feature contract with BDD Given/When/Then acceptance scenarios
- `design.md` — the architectural plan, drafted by Architect Agent, approved by Intent Leg
- Pre-spec Oracle consultation for regulated or domain-specific requirements

**Agent on this leg:** **Architect Agent** — designs solution architecture and validates `design.md` against `foundations/engineering.md`; prohibited from writing implementation code.

---

### Leg 2 — The Build Leg (AI Wrangler)

**Who:** AI Wrangler — an agent orchestrator, not a traditional developer

**Responsibilities split into two categories:**

**Context Stewardship** (structural, partially tool-assisted):
- Maintaining the `.sdd/` Specification Vault — keeping `foundations/` read-only, archiving completed features, keeping `manifest.md` current
- Enforcing session boundaries to prevent context poisoning
- Monitoring `tasks.md` as a real-time progress heartbeat

**Orchestration Judgment** (irreducibly human):
- Deciding when Architect Agent output is sound enough to hand to Developer Agent
- Distinguishing spec ambiguity from implementation failure in Revision Orders
- Detecting context drift mid-feature when agent outputs diverge from spec intent

**Agents on this leg:**
- **Developer Agent** — implements strictly against the approved spec; off-spec deviations trigger automatic Revision Orders
- **Reviewer Agent** — validates BDD-derived unit tests, coverage thresholds, and linting; issues Revision Orders on failure; explicitly instructed to find failures, not confirm success

---

### Leg 3 — The Truth Leg (Oracle)

**Who:** Subject Matter Expert (SME)

**What they own:**
- Pre-spec review of BDD scenarios for real-world validity
- Final adversarial review of features against domain truth
- Security and compliance checks
- Issuance of Revision Orders when real-world validation fails

**The sign-off hierarchy:** Reviewer Agent green ≠ Oracle green. Automated validation is necessary but not sufficient. The Oracle's sign-off triggers archiving.

---

## The Three Phases

| Phase | Owner | Activity | Artifact Produced |
|---|---|---|---|
| **Planning** | Intent Leg | Analyse requirements; consult Oracle if needed; write BDD scenarios; validate architecture | `requirements.md`, `design.md` |
| **Implementation** | Build Leg | Orchestrate Developer Agent; Reviewer Agent validates; Wrangler routes failures | `tasks.md` (live), production code |
| **Review** | Truth Leg | Oracle validates domain logic and real-world correctness; issues Revision Orders or signs off | Revision Orders or Oracle sign-off |

> **Governance gate:** `design.md` is drafted by the Architect Agent, then approved by the Intent Leg before a single line of implementation code is written. This is non-negotiable.

### When is a Tripod Done?

A feature is complete when:
1. Specs are approved and version-controlled
2. All BDD scenarios and derived tests are green
3. The Oracle has signed off against real-world truth

---

## The Specification Vault (`.sdd/`)

```
.sdd/
├── manifest.md                  ← The "front desk" — read first, every session
├── foundations/                 ← Global rules (read-only for agents)
│   ├── product.md               ← What & Why (business context, compliance, constraints)
│   └── engineering.md           ← How (tech stack, patterns, standards, quality thresholds)
├── roles/                       ← Agent persona instructions
│   ├── architect.md             ← Validate design.md against engineering.md; no implementation code
│   ├── developer.md             ← Execute tasks.md strictly; never go off-spec
│   └── reviewer.md              ← Find failures; validate BDD-derived tests; issue Revision Orders
├── specs/                       ← Active feature work
│   └── [feature]/
│       ├── requirements.md      ← Contract: BDD scenarios + acceptance criteria
│       ├── design.md            ← Plan: architecture (Architect Agent → Intent Leg approval)
│       └── tasks.md             ← Living progress doc (Developer Agent updates)
└── archive/                     ← Completed features (moved here after Oracle sign-off)
    └── [feature]/               ← Identical structure; read-only after archiving
```

**Four design decisions that matter more than the folder names:**

1. **`foundations/` is read-only for agents.** Only humans update global standards. The foundation version in `manifest.md` signals when agents must re-read this folder.

2. **`roles/` makes agent behaviour deterministic across sessions.** Every session starts from the same ground rules regardless of what happened in previous sessions.

3. **`archive/` solves context poisoning.** Resolved features are moved, not deleted. Leaving completed specs active causes agents to re-apply old constraints to new features.

4. **`manifest.md` is the front desk.** Agents read the manifest first — not the whole directory — to orient themselves at the start of every session.

---

## Revision Orders

A Revision Order is the formal feedback artifact issued when a feature fails validation.

**Who issues them:**
- **Reviewer Agent** — for unit test failures, coverage gaps, linting violations (mechanical, deterministic criteria)
- **Oracle** — for domain logic failures, real-world correctness violations, compliance gaps (requires human judgment)

**What a Revision Order contains:**
- Reference to the specific BDD scenario, acceptance criterion, or engineering standard that failed
- Observed behaviour vs. expected behaviour
- Routing decision: implementation failure (→ Developer Agent) or spec ambiguity (→ Intent Leg)

**The Wrangler's routing responsibility:** Getting this routing right is the most critical judgment call the Wrangler makes. Misrouting loops the Developer Agent indefinitely or masks a genuine spec gap.

---

## Scaling: Parallel Tripods

For larger systems, multiple Tripods operate in parallel, each owning a distinct bounded context or service boundary.

- All Tripods share a common `foundations/` (same `product.md` and `engineering.md`)
- Each Tripod maintains its own `specs/` and `archive/`
- Cross-cutting concerns are resolved by updating `foundations/` (with a version bump), not by adding inter-team ceremony

---

## Relationship to Other SDD Frameworks

| Framework | Scope | SpecPod Difference |
|---|---|---|
| GitHub Spec Kit | Templates + CLI bootstrapping | SpecPod adds human team structure (Tripod) and adversarial agent roles |
| Kiro | IDE-integrated spec-to-code | SpecPod is tool-agnostic; works across any agent/IDE |
| Tessl | AI-native dev platform | SpecPod is a lightweight pattern, not a platform |
| Augment Code | Context engine | SpecPod's `.sdd/` vault provides explicit context management |

SpecPod does not compete with these tools — it is an opinionated team and workflow pattern that can be used alongside any of them.

---

*SpecPod SDD — © 2026. Built on the shoulders of the SDD community.*
