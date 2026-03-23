# Project Manifest

> **Read this first.** Every agent and human reads this file at the start of every session. Do not proceed without checking the current phase, active spec, and any blockers.
> Agents read this file — they never write it. Only the Wrangler updates the manifest.

---

## Project

- **Name**: [project name]
- **Foundation version**: 1.0
- **Last updated**: YYYY-MM-DD
- **Wrangler**: [name or handle]

---

## Current State

- **Phase**: `Planning` | `Implementation` | `Review`
  *(exactly one phase is active at a time)*
- **Active spec**: `specs/[feature-name]/`
- **Status**: `On track` | `Blocked` | `Awaiting sign-off`

---

## Active Agents

| Agent | Status | Last action |
|---|---|---|
| Architect Agent | `active` \| `idle` | [brief description] |
| Developer Agent | `active` \| `idle` | [brief description] |
| Reviewer Agent | `active` \| `idle` | [brief description] |

---

## Last Handoff

- **From**: [Intent Leg | Build Leg | Oracle]
- **To**: [Intent Leg | Build Leg | Oracle]
- **Action**: [Plain-language description — e.g., "requirements.md and design.md approved — implementation may begin"]
- **Date**: YYYY-MM-DD

---

## Open Revision Orders

| # | Issued by | Severity | Routing | Description |
|---|---|---|---|---|
| RO-001 | [Reviewer Agent \| Oracle] | `High` \| `Medium` \| `Low` | `→ Developer Agent` \| `→ Intent Leg` | [Brief description of failure] |

*[None] if no open Revision Orders*

---

## Blockers

- [None] or short description + who needs to resolve it

---

## Completed Features

| Feature | Oracle sign-off | Archived |
|---|---|---|
| `archive/[feature-name]/` | YYYY-MM-DD | ✓ |

---

## Foundation Changelog

| Version | Date | Change |
|---|---|---|
| 1.0 | YYYY-MM-DD | Initial foundations established |
| 1.1 | YYYY-MM-DD | [Description of what changed and why] |

> **Agent instruction:** If the foundation version in this manifest is higher than the version you last read, re-read `foundations/product.md` and `foundations/engineering.md` before proceeding.
