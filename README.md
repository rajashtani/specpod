# SpecPod SDD Toolkit

> Specification-Driven Development for lean agentic teams. Built for regulated, production-grade environments.

---

## What's in This Toolkit

```
SpecPod/
├── specpod-sdd.md                 ← The methodology (start here)
│
├── foundations/                   ← Templates for the global read-only rules
│   ├── product-template.md        ← What & Why (business context, compliance)
│   └── engineering-template.md    ← How (tech stack, quality standards)
│
├── templates/                     ← Fill-in-the-blank templates for every artifact
│   ├── manifest-template.md       ← The "front desk" — project state tracker
│   ├── requirements-template.md   ← Feature contract with BDD scenarios
│   ├── design-template.md         ← Architecture plan (Architect Agent → Intent Leg)
│   ├── tasks-template.md          ← Living implementation progress doc
│   ├── revision-order-template.md ← Formal failure record
│   └── oracle-signoff-template.md ← Final sign-off and archive trigger
│
├── roles/                         ← Agent persona instructions (paste into system prompt)
│   ├── architect.md               ← Architect Agent: design only, no implementation code
│   ├── developer.md               ← Developer Agent: implement strictly to spec
│   └── reviewer.md                ← Reviewer Agent: find failures, validate tests
│
└── prompts/
    └── wrangler-prompts.md        ← Copy-paste prompts for every workflow phase
```

---

## Quick Start

### Step 1 — Set up the vault

Copy the `.sdd/` folder structure to your project root:

```
your-project/
└── .sdd/
    ├── manifest.md            ← From manifest-template.md
    ├── foundations/
    │   ├── product.md         ← From product-template.md
    │   └── engineering.md     ← From engineering-template.md
    ├── roles/
    │   ├── architect.md       ← From roles/architect.md
    │   ├── developer.md       ← From roles/developer.md
    │   └── reviewer.md        ← From roles/reviewer.md
    ├── specs/
    └── archive/
```

### Step 2 — Fill in your foundations

1. Complete `foundations/product.md` — your business context, users, compliance requirements, domain glossary
2. Complete `foundations/engineering.md` — your tech stack, quality thresholds, patterns, standards
3. Set foundation version to `1.0` in `manifest.md`

### Step 3 — Bootstrap your first feature

Use prompt `UTIL-03` from `prompts/wrangler-prompts.md` to create the feature folder structure.

### Step 4 — Run the Tripod workflow

| Phase | Prompt to use |
|---|---|
| Planning — design | `PLAN-01` — Invoke Architect Agent |
| Planning — Oracle consultation | `PLAN-03` — Oracle Consultation |
| Implementation — start | `IMPL-01` — Invoke Developer Agent |
| Implementation — review | `IMPL-03` — Invoke Reviewer Agent |
| Implementation — route failure | `IMPL-04` — Route Revision Order |
| Review — Oracle sign-off | `REVIEW-01` — Oracle Review |
| Archive | `REVIEW-02` — Archive Feature |

---

## The Three Rules

1. **No implementation without approved `requirements.md` and `design.md`**
2. **No Oracle sign-off without Reviewer Agent sign-off first**
3. **Archive completed features before starting the next one**

---

## Adapting to Your Tools

SpecPod is tool-agnostic. The `.sdd/` vault and Markdown templates work with any AI coding tool:

- **GitHub Copilot** — paste agent role instructions as workspace instructions; use `@workspace` references to spec files
- **Cursor** — add `.sdd/roles/` instructions to `.cursorrules`; reference specs in agent mode
- **Claude** — paste role instructions as system prompt; reference spec files in context
- **Kiro** — use `.sdd/` as your spec source; map Kiro's steering files to `foundations/`
- **Any agentic IDE** — the Wrangler prompts are designed to be copied directly into the agent chat

---

## Relationship to Other Frameworks

| Framework | How SpecPod relates |
|---|---|
| **GitHub Spec Kit** | SpecPod adds team structure (Tripod), adversarial agent roles, and context hygiene (archive pattern) |
| **Kiro** | SpecPod's methodology is Kiro-compatible; use Kiro's IDE features with SpecPod's vault structure |
| **Tessl** | SpecPod is a lightweight workflow pattern, not a platform — complementary |

---

*SpecPod SDD Toolkit v1.0 — 2026*
