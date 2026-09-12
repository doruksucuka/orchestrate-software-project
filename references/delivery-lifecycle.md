# Proportional Delivery Lifecycle

The lifecycle defines decision gates, not a mandatory pile of documents. Create the smallest durable artifact set that preserves scope, reasoning, evidence, and resumption state.

## Greenfield bootstrap

Before application scaffolding:

1. Confirm the workspace boundary and whether it is truly empty.
2. Capture the raw brief and identify its source.
3. Record material assumptions and discovery questions.
4. Select and record the assurance profile.
5. Create the executor's project instruction file.
6. Create only the project artifacts needed for the profile.
7. Present the bootstrap/discovery gate and stop.

The agent owns these artifacts. The Product Owner supplies decisions and approvals, not document drafting labor.

## Existing repository or migration bootstrap

Before changing established files:

1. Read active agent instructions and repository documentation.
2. Inspect git status and preserve user work.
3. Discover the build, test, lint, type-check, runtime, and deployment paths.
4. Run safe baseline checks when authorized and practical.
5. Map current architecture, external systems, data, and known gaps.
6. Reconcile requested behavior with actual behavior before proposing new rules.
7. Present an adoption or migration plan and stop at the applicable gate.

Do not replace working project conventions merely because this reference uses different filenames.

## Suggested artifact sets

### Light

A single `docs/project.md` may combine brief, scope, acceptance criteria, plan, decisions, and known risks. Add a short progress or release section only if the work spans sessions.

### Standard

Keep distinct sources of truth when they change independently. A typical set is:

- product brief or specification;
- acceptance criteria;
- architecture and data model;
- implementation plan and progress state;
- decision records for consequential changes;
- test strategy and QA findings;
- release checklist.

Names and layout may follow repository conventions.

### High assurance

Add only the risk artifacts that apply, such as a threat model, data map, authorization matrix, migration runbook, rollback plan, integration contracts, security findings, operational readiness evidence, or incident procedure.

## Required decision gates

### Product gate

Confirm users, goals, in-scope behavior, exclusions, important edge cases, non-functional requirements, and measurable acceptance criteria. Light projects may combine this with the technical gate.

### Technical gate

Confirm the selected approach, meaningful alternatives, data and trust boundaries, dependency choices, test strategy, delivery increments, operational consequences, and unresolved risks.

### Change-control gate

Stop when new information materially changes scope, cost, schedule, architecture, data handling, security posture, or the assurance profile. Record the decision rather than silently editing history.

### QA triage gate

Classify independent findings:

- **Critical:** release-blocking security, privacy, data-loss, financial, authorization, or core-function failure.
- **High:** major accepted behavior fails or a serious regression has no safe workaround.
- **Medium:** meaningful defect with bounded impact or a reasonable workaround.
- **Low:** minor usability, maintainability, documentation, or cosmetic issue.

Distinguish a defect against an approved requirement from a new feature request. The Product Owner approves scope changes and risk acceptance. Send accepted fixes to a developer context, then rerun targeted regression and independent verification.

### Release gate

Present evidence for the definition of done, acceptance coverage, automated and manual results, security and accessibility checks, configuration, migrations, monitoring, backup and rollback, documentation, open findings, and residual risk. Do not deploy merely because the gate packet is complete.

## Durable state

Keep progress useful for a fresh session:

- completed and current increment;
- pending decisions and blockers;
- last verified commands and results;
- known failing checks;
- next safe action;
- relevant commit or branch state.

Use git as a traceable checkpoint mechanism when available, but do not commit, rewrite, push, or publish without matching the user's authorization and repository norms.
