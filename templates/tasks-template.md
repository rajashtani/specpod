# Implementation Tasks: [Feature Name]

> **Maintained by:** Developer Agent (updated continuously during implementation)
> **Monitored by:** Wrangler (reads this as the live heartbeat — replaces standup)
> **Linked spec:** `specs/[feature-name]/requirements.md`
> **Linked design:** `specs/[feature-name]/design.md`
> **Started:** YYYY-MM-DD | **Target complete:** YYYY-MM-DD

---

## Status Summary

| Metric | Value |
|---|---|
| Total tasks | [N] |
| ✅ Complete | [N] |
| 🔄 In progress | [N] |
| ⏳ Not started | [N] |
| 🚫 Blocked | [N] |
| **Overall progress** | **[N]%** |

---

## Implementation Phases

### Phase 1 — Data Layer

| # | Task | Status | Notes |
|---|---|---|---|
| 1.1 | [e.g., Create migration: add `[field]` to `[table]`] | ⏳ | |
| 1.2 | [e.g., Add `[Model]` with fields from `design.md`] | ⏳ | |
| 1.3 | [e.g., Implement `[Repository]` with CRUD methods] | ⏳ | |
| 1.4 | [e.g., Write unit tests for repository layer] | ⏳ | |

---

### Phase 2 — Service / Business Logic Layer

| # | Task | Status | Notes |
|---|---|---|---|
| 2.1 | [e.g., Implement `[Service]` — happy path] | ⏳ | |
| 2.2 | [e.g., Implement validation logic per FR-001, FR-002] | ⏳ | |
| 2.3 | [e.g., Implement error handling per design.md error table] | ⏳ | |
| 2.4 | [e.g., Write unit tests — covers Scenario: [name] from requirements.md] | ⏳ | |
| 2.5 | [e.g., Write unit tests — covers Scenario: [name] from requirements.md] | ⏳ | |

---

### Phase 3 — API / Interface Layer

| # | Task | Status | Notes |
|---|---|---|---|
| 3.1 | [e.g., Implement `[METHOD] /[path]` endpoint] | ⏳ | |
| 3.2 | [e.g., Add authentication middleware integration] | ⏳ | |
| 3.3 | [e.g., Add input validation per design.md API spec] | ⏳ | |
| 3.4 | [e.g., Write contract tests for all new endpoints] | ⏳ | |

---

### Phase 4 — Integration and Quality

| # | Task | Status | Notes |
|---|---|---|---|
| 4.1 | [e.g., Write integration test: [Scenario name] end-to-end] | ⏳ | |
| 4.2 | [e.g., Run full test suite — target coverage ≥[threshold] from engineering.md] | ⏳ | |
| 4.3 | [e.g., Run linter — zero warnings] | ⏳ | |
| 4.4 | [e.g., Run security scan — zero high/critical findings] | ⏳ | |
| 4.5 | [e.g., Performance validation — [metric] meets [target]] | ⏳ | |

---

## BDD Scenario → Test Coverage Map

> Developer Agent: for each BDD scenario in `requirements.md`, confirm the corresponding test file and test name here.

| BDD Scenario | Test file | Test name | Status |
|---|---|---|---|
| Scenario: [name] | `tests/[path]` | `test_[name]` | ⏳ |
| Scenario: [name] | `tests/[path]` | `test_[name]` | ⏳ |

---

## Active Blockers

> Developer Agent updates this immediately when blocked. Wrangler resolves or escalates.

| # | Blocker | Type | Escalated to | Date raised |
|---|---|---|---|---|
| B-001 | [Description] | `Spec ambiguity` \| `External dependency` \| `Tooling` | [Intent Leg \| Wrangler] | YYYY-MM-DD |

*[None] if no blockers*

---

## Revision Orders Received

| # | Issued by | Description | Resolution | Status |
|---|---|---|---|---|
| RO-001 | [Reviewer Agent \| Oracle] | [What failed] | [How it was fixed] | `Open` \| `Resolved` |

*[None] if no Revision Orders received*

---

## Developer Agent Log

> Running notes — decisions made, alternatives rejected, issues encountered. Wrangler reads these to understand progress without interrupting the agent.

```
YYYY-MM-DD HH:MM — [Task 1.1 complete. Migration creates non-nullable column; added default value to prevent migration failure on existing rows.]
YYYY-MM-DD HH:MM — [Blocker on Task 2.3: requirements.md doesn't specify behaviour when [condition]. Raising as spec ambiguity — escalating to Intent Leg via Wrangler.]
YYYY-MM-DD HH:MM — [...]
```

---

## Handoff Checklist (to Reviewer Agent)

> Developer Agent completes this before requesting Reviewer Agent validation.

- [ ] All tasks in Phases 1–4 marked ✅ Complete
- [ ] BDD Scenario → Test Coverage Map is 100% populated
- [ ] No open blockers
- [ ] `tasks.md` reflects final state accurately
- [ ] Code is committed and available for review

---

*Template version: 1.0 — SpecPod SDD*
