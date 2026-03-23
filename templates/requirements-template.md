# Feature Requirements: [Feature Name]

> **Owned by:** Intent Leg
> **Status:** `Draft` | `Oracle Reviewed` | `Approved` | `Implemented` | `Archived`
> **Approved by:** [BA/Architect name] on YYYY-MM-DD
> **Oracle reviewed:** `Yes` | `No` | `Not required` — [Oracle name] on YYYY-MM-DD

---

## Overview

**Feature ID**: `[###-feature-slug]`
**Parent epic / initiative**: [Link or reference]
**Priority**: `P0` | `P1` | `P2` | `P3`

### Problem Statement

[1–3 sentences. What user problem does this feature solve? What is the current pain point?]

### Proposed Solution

[1–3 sentences. What will the system do to solve this problem? Avoid implementation details here — that's for `design.md`.]

### Success Definition

[How will we know this feature is working correctly in production? What does "done" look like from a user perspective?]

---

## Users Affected

| User role | Impact | Notes |
|---|---|---|
| [Role from product.md] | [How they are affected] | [Any caveats] |

---

## Functional Requirements

> Each requirement must be testable. Vague requirements ("the system should be fast") are spec defects.

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| FR-001 | [The system SHALL ...] | `Must` \| `Should` \| `May` | [Any clarification] |
| FR-002 | [The system SHALL ...] | `Must` \| `Should` \| `May` | [Any clarification] |

---

## Non-Functional Requirements

| Category | Requirement | Source |
|---|---|---|
| Performance | [e.g., Feature endpoint responds in <200ms p95] | `foundations/engineering.md` |
| Security | [e.g., All inputs validated; auth required] | `foundations/engineering.md` |
| Compliance | [e.g., All PII fields encrypted at rest] | `foundations/product.md` |
| Accessibility | [e.g., WCAG 2.1 AA for all UI elements] | [Reference] |

---

## BDD Acceptance Scenarios

> These scenarios are the **contract**. The Reviewer Agent derives unit tests from them. The Oracle validates real-world correctness against them. They cannot be vague.
> Format: Feature, Background (if needed), then Scenarios using Given/When/Then/And/But.

---

### Scenario Group: [Primary happy path]

```gherkin
Feature: [Feature name]
  As a [user role]
  I want to [action]
  So that [benefit]

  Background:
    Given [shared precondition for all scenarios in this group]
    And [additional shared precondition]

  Scenario: [Descriptive name — what situation and what outcome]
    Given [system state or user context]
    When [user action or system event]
    Then [observable outcome]
    And [additional observable outcome if needed]

  Scenario: [Another happy path variant]
    Given [...]
    When [...]
    Then [...]
```

---

### Scenario Group: [Error and edge cases]

```gherkin
  Scenario: [Descriptive name for error case]
    Given [...]
    When [invalid action or edge condition]
    Then [system handles it correctly — specific error, message, or fallback]
    And [system state is unchanged / consistent]

  Scenario: [Domain-specific edge case — flagged by Oracle if applicable]
    Given [...]
    When [...]
    Then [...]
```

---

### Scenario Group: [Compliance / security scenarios]

```gherkin
  Scenario: [Unauthorised access attempt]
    Given [user without required permission]
    When [they attempt the action]
    Then [access is denied]
    And [the attempt is logged with [required fields]]

  Scenario: [Data validation]
    Given [...]
    When [invalid data is submitted]
    Then [specific validation error is returned]
    And [no data is persisted]
```

---

## Oracle Consultation Notes

> Complete this section when Oracle input was sought before locking the spec.

**Consulted:** `Yes` | `No`
**Consultation date:** YYYY-MM-DD
**Oracle:** [name/role]

**Questions raised:**
- [Question 1]
- [Question 2]

**Oracle findings that influenced the spec:**
- [Finding 1 → how it changed the requirements or BDD scenarios]
- [Finding 2 → how it changed the requirements or BDD scenarios]

**Compliance constraints identified:**
- [Any compliance constraints the Oracle surfaced, now reflected in requirements above]

---

## Out of Scope for This Feature

> Explicit boundaries prevent scope creep during implementation.

- [Out of scope item 1]
- [Out of scope item 2]

---

## Dependencies

| Dependency | Type | Status | Notes |
|---|---|---|---|
| [Feature / service / API] | `Internal` \| `External` | `Available` \| `Pending` | [Any notes] |

---

## Open Questions

> Unresolved questions that must be answered before this spec can be approved. An approved spec has zero open questions.

| # | Question | Owner | Due |
|---|---|---|---|
| Q1 | [Question] | [Intent Leg \| Oracle] | YYYY-MM-DD |

---

*Template version: 1.0 — SpecPod SDD*
