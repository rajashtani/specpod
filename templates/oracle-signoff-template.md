# Oracle Sign-Off: [Feature Name]

> This document records the Oracle's final adversarial review and formal sign-off. It is issued after the Reviewer Agent has issued automated sign-off. Oracle sign-off triggers archiving of the feature.

---

## Header

| Field | Value |
|---|---|
| **Feature** | `specs/[feature-name]/` |
| **Oracle** | [Name / role] |
| **Review date** | YYYY-MM-DD |
| **Reviewer Agent sign-off** | YYYY-MM-DD |
| **Outcome** | `✅ Approved — archive` \| `🔄 Revision required — see ROs below` |

---

## Review Scope

> Confirm what was reviewed. The Oracle reviews real-world correctness — not automated test results.

- [ ] Implemented behaviour reviewed via: `[demo / staging / code walkthrough]`
- [ ] BDD scenarios in `requirements.md` validated against real-world practice
- [ ] Compliance requirements from `foundations/product.md` verified
- [ ] Domain-specific edge cases probed
- [ ] Security implications assessed for domain context

---

## BDD Scenario Review

| Scenario | Real-world correct? | Notes |
|---|---|---|
| Scenario: [name] | `✓ Yes` \| `✗ No — RO issued` | [Any observations] |
| Scenario: [name] | `✓ Yes` \| `✗ No — RO issued` | [Any observations] |

---

## Compliance Verification

| Requirement | Verified? | Notes |
|---|---|---|
| [Compliance item from product.md] | `✓ Yes` \| `✗ No` | [Observation] |

---

## Edge Cases Probed

> List the real-world conditions the Oracle tested beyond the specified BDD scenarios.

| Edge case | Behaviour | Acceptable? |
|---|---|---|
| [Description] | [What the system did] | `✓ Yes` \| `✗ No — RO issued` |

---

## Revision Orders Issued

| RO # | Severity | Description | Status |
|---|---|---|---|
| RO-[###] | P[0-3] | [Brief description] | `Open` \| `Resolved` |

*[None] if no Revision Orders issued*

---

## Oracle Sign-Off Statement

> This section is completed only when all scenarios pass, all compliance is verified, and all Revision Orders are closed.

"Oracle sign-off for **[feature name]**. Domain logic validated against real-world **[domain]** practice. Compliance verified against: **[list standards]**. Edge cases probed: **[count]** — all acceptable. No open Revision Orders.

This feature is approved for archiving."

**Signed:** [Oracle name/role]
**Date:** YYYY-MM-DD

---

## Archiving Instruction

> Upon Oracle sign-off, the Wrangler moves `specs/[feature-name]/` to `archive/[feature-name]/` and updates `manifest.md`.

- [ ] Feature folder moved to `archive/`
- [ ] `manifest.md` updated — Completed Features table, Active spec cleared, Phase reset

---

*Template version: 1.0 — SpecPod SDD*
