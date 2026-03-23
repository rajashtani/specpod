# Engineering Foundation

> **Read-only for agents.** This file is updated only by humans (Intent Leg, with Architect input). It defines the "How" — the technical stack, patterns, quality standards, and engineering constraints that every implementation must follow.
> When this file changes, the Foundation version in `manifest.md` is bumped and all agents must re-read before proceeding.

---

## Tech Stack

| Layer | Technology | Version | Notes |
|---|---|---|---|
| Language | [e.g., Python] | [e.g., 3.11+] | [Any constraints] |
| Framework | [e.g., FastAPI] | [e.g., 0.111+] | [Any constraints] |
| Database | [e.g., PostgreSQL] | [e.g., 15+] | [Any constraints] |
| Infrastructure | [e.g., AWS, Docker] | — | [Any constraints] |
| Testing | [e.g., pytest] | [e.g., 7.x] | [Any constraints] |

**Forbidden technologies**: [List any explicitly prohibited libraries, frameworks, or patterns and why]

---

## Architectural Patterns

> These are the approved patterns. Deviating requires an explicit architectural decision logged in `design.md`.

- **[Pattern 1]**: [e.g., Repository pattern for all data access — no raw ORM calls in service layer]
- **[Pattern 2]**: [e.g., Feature flags for all non-trivial rollouts]
- **[Pattern 3]**: [e.g., Event-driven updates for cross-service communication]

---

## Code Quality Standards

### Testing

| Metric | Threshold | Enforced by |
|---|---|---|
| Unit test coverage | [e.g., ≥80%] | Reviewer Agent |
| BDD scenario coverage | 100% (all acceptance scenarios must have tests) | Reviewer Agent |
| Contract test coverage | [e.g., ≥90% of API surface] | Reviewer Agent |

### Static Analysis

- **Linter**: [e.g., ruff, eslint, golangci-lint] — zero warnings on merge
- **Type checking**: [e.g., mypy strict, TypeScript strict] — zero errors
- **Security scanning**: [e.g., bandit, semgrep] — zero high/critical findings
- **Complexity threshold**: [e.g., cyclomatic complexity ≤10 per function]

### Code Style

- [Style guide reference or brief summary]
- [Naming conventions]
- [Documentation requirements — e.g., all public APIs must have docstrings]

---

## Performance Standards

| Metric | Target | Measurement method |
|---|---|---|
| [e.g., API response time] | [e.g., <200ms p95] | [e.g., load test in staging] |
| [e.g., Background job duration] | [e.g., <30s] | [e.g., production telemetry] |

---

## Security Standards

- **Authentication**: [Approach — e.g., JWT with 15-min expiry, OAuth2 for external]
- **Authorisation**: [Model — e.g., RBAC with principle of least privilege]
- **Data at rest**: [e.g., AES-256 for all PII fields]
- **Data in transit**: [e.g., TLS 1.3 minimum]
- **Secrets management**: [e.g., No secrets in code; use Vault / AWS Secrets Manager]
- **Input validation**: [e.g., All external input validated at API boundary, never trusted downstream]

---

## Branching and Version Control

- **Branch naming**: [e.g., `feature/[feature-name]`, `fix/[issue-id]`]
- **Commit convention**: [e.g., Conventional Commits — `feat:`, `fix:`, `chore:`]
- **PR requirements**: [e.g., All tests green, Reviewer Agent sign-off, one human approval]
- **Merge strategy**: [e.g., Squash merge to main]

---

## Observability Requirements

- **Logging**: [e.g., Structured JSON logs; all errors logged with correlation ID]
- **Metrics**: [e.g., RED metrics (Rate, Errors, Duration) for all services]
- **Tracing**: [e.g., OpenTelemetry spans for all cross-service calls]
- **Alerting**: [e.g., PagerDuty for p0/p1 errors; Slack for p2]

---

## Definition of Done (Engineering)

A feature is engineering-complete when ALL of the following are true:

- [ ] All BDD acceptance scenarios have passing unit tests
- [ ] Code coverage meets threshold defined above
- [ ] Static analysis passes with zero warnings
- [ ] Security scan clean
- [ ] Performance targets validated
- [ ] `tasks.md` marked 100% complete by Developer Agent
- [ ] Reviewer Agent has issued sign-off (no open Revision Orders)

---

*Foundation version: 1.0 — Last updated: YYYY-MM-DD by [role/name]*
