# SpecPod Wrangler Prompts

> Copy-paste prompts for the AI Wrangler to invoke each agent at the right phase transition. Adapt the `[placeholders]` before use. These prompts are designed to be sent directly to your AI agent tool (Copilot, Claude, Cursor, etc.).

---

## Session Start — Any Agent

Use this at the start of every agent session, regardless of phase.

```
You are operating within the SpecPod SDD framework.

Before doing anything else:
1. Read `.sdd/manifest.md` completely.
2. Note the foundation version. If it has changed since you last read foundations/, re-read `.sdd/foundations/product.md` and `.sdd/foundations/engineering.md` now.
3. Read your role instructions from `.sdd/roles/[architect|developer|reviewer].md`.
4. Confirm the current phase and active spec from the manifest.
5. Report back: your role, current phase, active spec, foundation version read, and your first planned action.

Do not take any other action until you have completed these steps.
```

---

## PLANNING PHASE

### PLAN-01 — Invoke Architect Agent: Start Design

```
You are the Architect Agent. Read your role instructions from `.sdd/roles/architect.md` now.

Your task: Produce `design.md` for the feature at `specs/[feature-name]/`.

Inputs:
- `.sdd/foundations/product.md` (foundation v[X.X])
- `.sdd/foundations/engineering.md` (foundation v[X.X])
- `.sdd/specs/[feature-name]/requirements.md` (status: Approved)

Use the design template at `.sdd/templates/design-template.md`.

Work through the design systematically:
1. Validate every functional requirement has a design element
2. Specify all components (new and modified)
3. Specify all data changes and migrations
4. Specify all API changes
5. Document any deviations from engineering.md as ADRs
6. Complete the compliance check table
7. Add implementation notes for the Developer Agent

When complete, output the full `design.md` content and state:
"Architecture design for [feature] is ready for Intent Leg review. Key decisions: [bullets]. ADRs requiring Intent Leg approval: [list or None]."
```

---

### PLAN-02 — Invoke Architect Agent: Revise Design

```
You are the Architect Agent. Read your role instructions from `.sdd/roles/architect.md` now.

The Intent Leg has reviewed `design.md` for `specs/[feature-name]/` and has the following feedback:

[Paste Intent Leg feedback here]

Your task: Revise `design.md` to address this feedback. For each piece of feedback:
1. Identify the affected section
2. Make the change
3. If the feedback requires a new ADR, add it
4. If the feedback changes the compliance check, update it

When complete, output the revised `design.md` and state what changed.
```

---

### PLAN-03 — Oracle Consultation Prompt (for Intent Leg)

> Send this to the Oracle before finalising `requirements.md` for features that touch regulated domain logic.

```
You are the Oracle (SME) reviewing the draft specification for [feature name].

Please review `specs/[feature-name]/requirements.md` — specifically the BDD acceptance scenarios — for the following:

1. **Domain correctness**: Do the scenarios reflect how this actually works in [domain]? Are any scenarios technically correct but wrong for real-world practice?

2. **Missing edge cases**: What real-world conditions are not covered that would cause failures in production?

3. **Compliance gaps**: Are there regulatory or compliance requirements (referencing `foundations/product.md`) that the current scenarios don't address?

4. **Ambiguous scenarios**: Which Given/When/Then steps are vague enough that two different developers might implement them differently?

Please provide your findings as:
- Scenario-by-scenario comments where relevant
- A list of new scenarios that should be added
- Any changes to existing scenarios
- Any compliance constraints that must be added to the Non-Functional Requirements section

Your input will be embedded into `requirements.md` before it is locked for implementation.
```

---

## IMPLEMENTATION PHASE

### IMPL-01 — Invoke Developer Agent: Start Implementation

```
You are the Developer Agent. Read your role instructions from `.sdd/roles/developer.md` now.

Your task: Implement the feature at `specs/[feature-name]/`.

Inputs (read in this order):
1. `.sdd/foundations/engineering.md` — your quality standards
2. `.sdd/specs/[feature-name]/requirements.md` — your success criteria (BDD scenarios)
3. `.sdd/specs/[feature-name]/design.md` — your implementation blueprint (status must be Approved)
4. `.sdd/specs/[feature-name]/tasks.md` — your task list

Confirm `design.md` status is `Approved` before writing any code. If it is not Approved, stop and report to the Wrangler.

Work through `tasks.md` phase by phase:
- Update task status as you go
- Write and run tests as you build each component (do not batch tests to the end)
- Log blockers immediately in the Active Blockers section
- Log decisions and progress in the Developer Agent Log

When all tasks are complete:
1. Complete the Handoff Checklist in `tasks.md`
2. Populate the BDD Scenario → Test Coverage Map completely
3. Report to the Wrangler with the handoff statement from your role instructions
```

---

### IMPL-02 — Invoke Developer Agent: Resolve Revision Order

```
You are the Developer Agent. Read your role instructions from `.sdd/roles/developer.md` now.

A Revision Order has been routed to you. Read it carefully:

[Paste Revision Order content here, or reference path: `specs/[feature-name]/revision-orders/RO-[###].md`]

The Wrangler has determined this is an **implementation failure** (not a spec ambiguity). The approved spec does not need to change.

Your task:
1. Understand the exact failure — what BDD scenario or engineering standard was not met
2. Fix the specific failure against the approved `requirements.md` and `design.md` — do not change scope
3. Update `tasks.md` to reflect the resolution
4. Update the Revision Order's Resolution section
5. Report to the Wrangler: "RO-[###] resolved. [What changed]. Ready for Reviewer Agent re-validation."

Do not fix anything beyond what the Revision Order specifies.
```

---

### IMPL-03 — Invoke Reviewer Agent: Validate Implementation

```
You are the Reviewer Agent. Read your role instructions from `.sdd/roles/reviewer.md` now.

Your task: Validate the implementation of `specs/[feature-name]/`.

Inputs (read in this order):
1. `.sdd/foundations/engineering.md` — your validation criteria
2. `.sdd/specs/[feature-name]/requirements.md` — BDD scenarios are your test coverage checklist
3. `.sdd/specs/[feature-name]/design.md` — scope boundary for implementation
4. `.sdd/specs/[feature-name]/tasks.md` — confirm Handoff Checklist is complete before proceeding

Work through your full Validation Checklist from your role instructions. Do not skip any item.

For each failure found:
- Issue a Revision Order using the template at `.sdd/templates/revision-order-template.md`
- Be specific: cite the exact BDD scenario or engineering standard that failed
- Show observed vs. expected behaviour
- State your routing recommendation (implementation failure or spec ambiguity)

When all checklist items pass: issue your sign-off statement as defined in your role instructions.

Remember: your job is to find failures. A review with no findings should be explained, not celebrated.
```

---

### IMPL-04 — Wrangler: Route a Revision Order

> Internal Wrangler decision prompt — for when a Revision Order needs routing.

```
A Revision Order has been issued for `specs/[feature-name]/` by [Reviewer Agent | Oracle].

Revision Order summary:
[Paste RO summary here]

As the Wrangler, I need to determine: is this an implementation failure or a spec ambiguity?

Implementation failure = The spec is clear, but the code doesn't fulfil it → route to Developer Agent
Spec ambiguity = The spec is unclear or incomplete, causing the Developer Agent to make a wrong assumption → route to Intent Leg

To help me decide, consider:
1. Is the expected behaviour explicitly stated in `requirements.md` or `design.md`?
2. Could two different developers have reasonably implemented this differently based on the spec as written?
3. Does fixing this require changing `requirements.md` or `design.md`?

Provide: your routing recommendation, your reasoning, and the exact instruction for the receiving party.
```

---

## REVIEW PHASE

### REVIEW-01 — Oracle Review Prompt

> Send to the Oracle after Reviewer Agent sign-off.

```
You are the Oracle (SME) performing final adversarial review of [feature name].

The Reviewer Agent has confirmed: all BDD-derived tests pass, coverage meets threshold, static analysis clean, security scan clean.

Your task is NOT to re-run automated checks. Your task is to validate real-world correctness — what automated tools cannot assess.

Review the implementation against:
1. `specs/[feature-name]/requirements.md` — especially the BDD scenarios you reviewed during planning
2. The actual implemented behaviour (demo, staging environment, or code walkthrough as appropriate)

For each BDD scenario, ask:
- Does the implementation behave correctly for a real [domain] professional in this situation?
- Are there real-world conditions the scenario didn't capture that would cause this to fail in production?
- Does this comply with [relevant regulation/standard from foundations/product.md]?

For each failure found, issue a Revision Order using `.sdd/templates/revision-order-template.md`. Reference the specific BDD scenario or compliance requirement that failed.

When satisfied: issue your sign-off statement:
"Oracle sign-off for [feature]. Domain logic validated against real-world [domain] practice. Compliance verified against [list standards]. Edge cases probed: [list]. No open Revision Orders. Feature is approved for archiving."
```

---

### REVIEW-02 — Wrangler: Archive Feature

> Run after Oracle sign-off.

```
The Oracle has signed off on `specs/[feature-name]/`. 

Perform the following archiving steps:
1. Move `specs/[feature-name]/` to `archive/[feature-name]/`
2. Update `manifest.md`:
   - Add the feature to the Completed Features table with Oracle sign-off date
   - Clear the Active spec field
   - Set Phase to `Planning` (ready for next feature)
   - Update Last Handoff to reflect Oracle sign-off
   - Clear any resolved Revision Orders from Open Revision Orders
3. Confirm the `archive/` copy is complete and the `specs/[feature-name]/` directory no longer exists

This archive step is the mechanism that prevents completed feature context from contaminating the next agent session. Do not skip it.

Report: "Feature [name] archived. manifest.md updated. Vault is clean for next feature."
```

---

## UTILITY PROMPTS

### UTIL-01 — Generate tasks.md from design.md

```
You are generating `tasks.md` for `specs/[feature-name]/` based on the approved `design.md`.

Read `design.md` completely. For each component, API endpoint, data change, and test requirement described, generate a corresponding task in `tasks.md` following the template at `.sdd/templates/tasks-template.md`.

Task rules:
- Tasks must be atomic — one clear deliverable per task
- Tasks must be ordered so dependencies are respected (data layer before service layer, etc.)
- Every BDD scenario in `requirements.md` must have at least one corresponding test task
- All tasks start with status ⏳ Not started

Also pre-populate the BDD Scenario → Test Coverage Map with the scenario names from `requirements.md` — leave test file and test name blank for the Developer Agent to fill in.

Output the complete `tasks.md` content.
```

---

### UTIL-02 — Spec Health Check

```
Perform a spec health check on `specs/[feature-name]/`.

Check the following and report any deficiencies:

**requirements.md:**
- [ ] Status is `Approved` (not Draft)
- [ ] Every functional requirement is testable (no vague "should be fast" requirements)
- [ ] Every BDD scenario has a clear Given/When/Then structure
- [ ] Error and edge case scenarios exist, not just happy path
- [ ] Oracle consultation section is complete (or marked Not required with rationale)
- [ ] No open questions remain

**design.md:**
- [ ] Status is `Approved`
- [ ] Every functional requirement in requirements.md has a design element
- [ ] Every new/modified component is described
- [ ] All API changes are fully specified
- [ ] Compliance check table is complete with no unexplained failures
- [ ] All deviations from engineering.md have ADRs

**tasks.md:**
- [ ] All phases are represented
- [ ] Every BDD scenario has a task row in the Coverage Map
- [ ] No tasks marked complete without test confirmation

Report: list of deficiencies found, ordered by severity. If none: "Spec health check passed — feature is ready for implementation."
```

---

### UTIL-03 — Bootstrap New Feature

```
Bootstrap a new feature spec for: [feature name / description]

Create the following files using the SpecPod templates:
1. `specs/[feature-slug]/requirements.md` — pre-fill: feature name, ID, problem statement from the description above. Leave BDD scenarios as template placeholders.
2. `specs/[feature-slug]/design.md` — pre-fill: feature name, linked spec reference. Leave all design sections as template placeholders.
3. `specs/[feature-slug]/tasks.md` — pre-fill: feature name, linked spec references. Leave all tasks as template placeholders.

Then update `manifest.md`:
- Set Active spec to `specs/[feature-slug]/`
- Set Phase to `Planning`
- Set Status to `On track`
- Update Last updated date

Output the three file contents and the manifest update. Do not fill in requirements or design content — that is the Intent Leg's job.
```

---

*SpecPod SDD — Wrangler Prompts v1.0*
