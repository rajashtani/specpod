# Revision Order [RO-###]

> **A Revision Order is a formal failure record.** It is not a suggestion. The routing decision determines who resolves it.
> Revision Orders are closed only when the failure is resolved and re-validated by the issuer.

---

## Header

| Field | Value |
|---|---|
| **RO ID** | RO-[###] |
| **Feature** | `specs/[feature-name]/` |
| **Issued by** | `Reviewer Agent` \| `Oracle` |
| **Issued on** | YYYY-MM-DD |
| **Severity** | `P0 — Blocker` \| `P1 — High` \| `P2 — Medium` \| `P3 — Low` |
| **Routing** | `→ Developer Agent` \| `→ Intent Leg (spec ambiguity)` |
| **Status** | `Open` \| `In resolution` \| `Closed` |

---

## Failed Requirement

**Reference:** [Exact citation — e.g., `requirements.md: Scenario: Unauthorised access attempt` or `engineering.md: Code coverage ≥80%`]

**Requirement text:**
> [Paste the exact text of the requirement, BDD scenario, or engineering standard that was not met]

---

## Failure Description

### Observed Behaviour

[What the system actually does. Be specific — include error messages, test output, or observed state where relevant.]

```
[Paste relevant test output, error logs, or observed behaviour here]
```

### Expected Behaviour

[What the system should do according to the spec, BDD scenario, or engineering standard.]

### Reproduction Steps

1. [Step 1]
2. [Step 2]
3. [Step 3 — what you see vs. what you expect]

---

## Routing Decision

**Wrangler determination:** `Implementation failure` | `Spec ambiguity`

**Rationale:**
[Why this is an implementation failure OR a spec ambiguity. This is the Wrangler's most critical judgment call. Be explicit.]

**If spec ambiguity:** The Developer Agent MUST NOT attempt to resolve this by guessing intent. Implementation is paused until the Intent Leg updates `requirements.md` and re-approves.

**If implementation failure:** The Developer Agent resolves this against the existing approved spec. No spec changes are needed.

---

## Resolution

> Completed by the resolving party (Developer Agent or Intent Leg) when the failure is fixed.

**Resolved by:** [Developer Agent | Intent Leg]
**Resolution date:** YYYY-MM-DD

**What was changed:**
[Description of the fix — code change, test update, or spec clarification]

**Re-validation required from:** [Reviewer Agent | Oracle]

---

## Re-Validation

**Re-validated by:** [Reviewer Agent | Oracle]
**Re-validation date:** YYYY-MM-DD
**Outcome:** `✅ Closed — failure resolved` | `🔄 Still failing — see RO-[###] for follow-up`

---

*Template version: 1.0 — SpecPod SDD*
