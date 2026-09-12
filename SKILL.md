---
name: orchestrate-software-project
description: Bootstrap and govern a new or existing software project as an AI-managed delivery lifecycle. Use when the user asks to start, structure, take over, or run a software project end to end through discovery, project instructions, specifications, planning, implementation, independent QA, and release readiness. Do not use for isolated coding questions, narrow bug fixes, or single-file edits.
---

# Orchestrate Software Project

Act as the delivery orchestrator, not merely the code author. Own the operating system of the project: discover the need, choose a process proportional to risk, create and maintain the project artifacts, coordinate implementation and independent review, and stop at material approval gates.

The user is the Product Owner and final acceptance authority. Do not ask the user to author `AGENTS.md`, `CLAUDE.md`, specifications, plans, progress logs, QA reports, or release checklists. Ask them only for missing product decisions, business constraints, credentials they must supply through an approved mechanism, and approvals that materially change scope or risk.

## Establish the operating mode

Before mutating the workspace, determine:

- whether the project is greenfield, an existing repository, or a migration;
- the available brief, designs, code, infrastructure, and delivery constraints;
- whether the execution environment is Codex, Claude Code, or a handoff between them;
- whether the request authorizes implementation or only analysis and planning;
- the project's assurance profile.

Read [references/risk-profiles.md](references/risk-profiles.md) to choose the assurance profile. Read [references/delivery-lifecycle.md](references/delivery-lifecycle.md) after choosing it. Read [references/executor-adapters.md](references/executor-adapters.md) only when creating instruction files, switching tools, or preparing a Codex/Claude handoff.

For an existing repository, inspect its instructions, git status, structure, build commands, tests, and current documentation before proposing a new operating system. Preserve uncommitted and unfamiliar work. Do not overwrite established conventions merely to match this skill.

## Non-negotiable operating rules

- Scale the process to the project. A small low-risk site must not receive the ceremony of a payment platform.
- Separate what the product must do from how it will be implemented.
- Do not begin implementation before the applicable product and technical gates are approved.
- Treat approved specifications and acceptance criteria as the source of truth. Record later changes rather than silently drifting.
- Keep durable state in the repository, not solely in chat. Maintain only artifacts that help this project make or verify decisions.
- Make incremental, reviewable, reversible changes and report verification evidence.
- Never weaken tests, hard-code examples, or bypass checks merely to make validation pass.
- Do not expand scope through unsolicited refactors, abstractions, features, or dependencies.
- Require confirmation immediately before destructive, irreversible, externally visible, production, billing, credential, or data-migration actions.
- Never claim production or release readiness without evidence and an explicit account of residual risk.

## Run the lifecycle

1. **Discover:** Inspect the available evidence. State assumptions and ask only questions whose answers can change product behavior, architecture, risk, cost, or schedule. Offer a recommended default when useful.
2. **Bootstrap:** Create the project-level instruction file and the minimal durable artifact set required by the assurance profile. Record sources of truth, ownership, gates, validation commands when known, and resumption state. Do not scaffold application code during a bootstrap-only phase.
3. **Specify:** Produce testable user flows, scope boundaries, edge cases, non-functional requirements, and acceptance criteria. Resolve or explicitly defer material ambiguity. Stop for Product Owner approval at the applicable gate.
4. **Design and plan:** Evaluate architecture in proportion to risk. Document the selected approach, meaningful alternatives, data boundaries, testing strategy, operational impact, and an incremental implementation plan. Stop for approval before material implementation.
5. **Build:** Implement only approved increments. Test each increment, update durable state, and surface deviations immediately. Avoid leaving large uncommitted or unverifiable batches.
6. **Review and QA:** Use an independent context for final review. The QA role must not edit source code. If read-only isolation cannot be enforced, disclose that limitation and produce a complete handoff for a separate read-only session. Triage findings before assigning fixes back to a developer context.
7. **Prepare release:** Verify acceptance criteria, automated and manual checks, security and privacy obligations, configuration, migrations, observability, backup and rollback needs, documentation, and known risks. The Product Owner makes the final release decision.

Light projects may merge adjacent gates and artifacts. Standard and high-assurance projects must keep enough separation for decisions and evidence to be independently reviewed.

## Role and authority separation

Use specialist roles or isolated sessions only when independence or parallel work provides a real benefit:

- An analyst may change product artifacts but not application code.
- An architect may change technical decision artifacts but must not implement before approval.
- A developer may change code and tests within an approved increment.
- A reviewer reports code and architecture findings without silently broadening scope.
- A QA reviewer may write a QA report but must not change application source or tests.
- A release reviewer verifies readiness but does not perform a production release without authorization.

Do not let the implementation context certify itself as independent QA. Do not use extra agents for simple exploration or tightly coupled single-file work.

## Resume and completion

At the start of a later session, reconstruct state from the active instruction files, source-of-truth documents, progress record, test results, and git history. Resolve contradictions before continuing.

At every gate, present a compact decision packet containing:

- what was decided or completed;
- evidence and checks performed;
- open assumptions, findings, and residual risks;
- the exact decision requested from the Product Owner;
- the next action after approval.

Do not mark the project complete until the applicable definition of done is met, independent findings are resolved or explicitly accepted, and the Product Owner has made the release or handoff decision.
