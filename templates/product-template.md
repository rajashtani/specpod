# Product Foundation

> **Read-only for agents.** This file is updated only by humans (Intent Leg). It defines the "What & Why" of the product — the business context, user needs, compliance constraints, and domain boundaries that every feature must respect.
> When this file changes, the Foundation version in `manifest.md` is bumped and all agents must re-read before proceeding.

---

## Product Overview

**Product name**: [name]
**Domain**: [e.g., healthcare, fintech, logistics, developer tooling]
**One-line purpose**: [What does this product do and for whom?]
**Business model**: [How does it create value? SaaS, internal tool, open source, etc.]

---

## Users and Stakeholders

| Role | Description | Primary needs |
|---|---|---|
| [Primary user] | [Who they are] | [What they need to accomplish] |
| [Secondary user] | [Who they are] | [What they need to accomplish] |
| [Internal stakeholder] | [Who they are] | [What they care about] |

---

## Business Constraints

> These are non-negotiable boundaries that every feature must operate within.

- [ ] [Constraint 1 — e.g., all data must remain within EU jurisdiction]
- [ ] [Constraint 2 — e.g., system must support offline operation]
- [ ] [Constraint 3 — e.g., maximum response time of 200ms p95]

---

## Compliance and Regulatory Requirements

> List all applicable regulations, standards, or internal policies. The Oracle is the authority on these.

| Regulation / Standard | Applies to | Key requirements |
|---|---|---|
| [e.g., GDPR] | [User data handling] | [Right to erasure, data minimisation, consent] |
| [e.g., SOC 2 Type II] | [All infrastructure] | [Access controls, audit logging, encryption] |
| [e.g., Internal policy X] | [Feature category] | [Specific policy requirement] |

**Oracle consultation required for:** [List the feature types or data types that must involve the Oracle in pre-spec review]

---

## Domain Glossary

> Shared vocabulary for specs. Agents must use these terms consistently. Ambiguous language in a spec is a spec defect.

| Term | Definition | Notes |
|---|---|---|
| [Term] | [Precise definition] | [Any disambiguation or context] |
| [Term] | [Precise definition] | [Any disambiguation or context] |

---

## Known Domain Edge Cases

> Real-world conditions that specs must account for. These come from Oracle input and field experience.

- **[Edge case 1]**: [Description and why it matters]
- **[Edge case 2]**: [Description and why it matters]

---

## Out of Scope

> Explicit boundaries on what this product does NOT do. Prevents scope creep in specs.

- [Out-of-scope item 1]
- [Out-of-scope item 2]

---

*Foundation version: 1.0 — Last updated: YYYY-MM-DD by [role/name]*
