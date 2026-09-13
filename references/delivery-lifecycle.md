# Proportional Delivery Lifecycle

The lifecycle defines material decisions, not a mandatory pile of documents or approval turns. Create the smallest durable artifact set that preserves scope, reasoning, evidence, and resumption state. Apply the selected execution budget from [execution-budgets.md](execution-budgets.md).

## Bootstrap

For greenfield work, confirm the workspace boundary, capture the brief, record material assumptions, select assurance and execution modes, and create the executor instruction file plus minimum sources of truth. Do not scaffold application code during a bootstrap-only phase.

For an existing repository or migration, first read active instructions, inspect git status, preserve user work, discover validation and deployment paths, run safe baseline checks when authorized, and reconcile requested behavior with actual behavior.

Bootstrap is not automatically a separate approval gate. In a bounded Lean project, combine its findings with the Product Gate unless a workspace, risk, or authorization decision requires an earlier stop.

## Compact artifact sets

### Lean execution

Usually keep:

- the executor instruction file;
- a combined product and acceptance source;
- a combined technical plan;
- a delivery-state index when work spans sessions.

Add a separate QA report, operations guide, or release record only when it preserves evidence that would otherwise be lost or ambiguous.

### Balanced execution

Keep product requirements, technical decisions, and delivery state separate. Acceptance criteria may live with product requirements; architecture, data model, test strategy, and increments may share one technical plan. Add operations, QA, or release artifacts only as their independent lifecycle warrants.

### Maximum execution

Add only risk-specific artifacts such as a threat model, data map, authorization matrix, migration rehearsal, rollback plan, integration contracts, security findings, operational readiness evidence, or incident procedure. Any assurance profile may force a specific artifact even under a smaller execution budget; record that exception rather than weakening the control.

## Material gates

### Product Gate

Confirm users, goals, in-scope behavior, exclusions, important edge cases, non-functional requirements, and measurable acceptance criteria. Combine with bootstrap or technical approval when the project is small and the decision remains clear.

### Technical Gate

Confirm the selected approach, meaningful alternatives, data and trust boundaries, dependency choices, test strategy, delivery increments, operational consequences, and unresolved risks. Once approved, implementation may proceed across planned increments without repeated permission.

### Change-Control Gate

Stop only when new information materially changes scope, cost, schedule, architecture, data handling, security posture, assurance profile, or an external authorization. Record the decision without rewriting history.

### QA Triage Gate

Classify independent findings:

- **Critical:** release-blocking security, privacy, data-loss, financial, authorization, or core-function failure.
- **High:** major accepted behavior fails or a serious regression has no safe workaround.
- **Medium:** meaningful defect with bounded impact or a reasonable workaround.
- **Low:** minor usability, maintainability, documentation, or cosmetic issue.

Distinguish a defect from a new feature request. Send accepted fixes to a developer context. For a narrow fix, independently reverify the failed criterion and adjacent risk; repeat broad QA only if the change surface warrants it.

### Acceptance and Release Gate

Before final acceptance, give the Product Owner a runnable target and a short user acceptance path. Distinguish:

- implementation complete;
- independent QA complete;
- Product Owner acceptance complete;
- production release authorized and performed.

Do not collapse these states or imply production approval from a local/test handoff. When deployment is in scope, present applicable configuration, migration, monitoring, backup, rollback, security, accessibility, and residual-risk evidence. Do not deploy merely because the packet is complete.

## Durable state

Use one compact state index for:

- current phase and execution budget;
- approved decisions and pending material decisions;
- current revision and branch;
- last relevant validation results;
- open findings, blockers, and residual risks;
- next safe action.

Update it at meaningful milestones, not after every command. Use git as a traceable checkpoint when available, but do not commit, rewrite, push, publish, or deploy without matching authorization and repository norms.
