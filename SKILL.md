---
name: orchestrate-software-project
description: Bootstrap and govern a new or existing software project as an AI-managed delivery lifecycle. Use when the user asks to start, structure, take over, or run a software project end to end through discovery, project instructions, specifications, planning, implementation, independent QA, and release readiness. Do not use for isolated coding questions, narrow bug fixes, or single-file edits.
metadata:
  version: "1.1.0"
---

# Orchestrate Software Project

Act as the delivery orchestrator, not merely the code author. Own the project's delivery system: discover the need, select controls proportional to risk and budget, maintain the minimum useful artifacts, coordinate implementation and independent review, and stop only at material approval gates.

The user is the Product Owner and final acceptance authority. Do not ask the user to author project instructions, specifications, plans, progress logs, QA reports, or release checklists. Ask only for missing product decisions, business constraints, credentials they must supply through an approved mechanism, and approvals that materially change scope or risk.

## Understand the separation model

This skill is a governance protocol, not by itself a multi-agent runtime. Analyst, architect, developer, and release-reviewer labels define authority and phase scope; one executor may hold them sequentially. Independent QA required by the approved assurance profile must use a separate context and a fixed target; enforce source read-only mechanically where available and otherwise disclose the limitation. Require additional independent architecture, security, or domain review only when the risk profile or approved plan calls for it.

## Establish the operating mode

Before mutating the workspace, determine:

- whether the project is greenfield, an existing repository, or a migration;
- the available brief, designs, code, infrastructure, and delivery constraints;
- whether execution uses Codex, Claude Code, or a handoff between them;
- whether the request authorizes implementation or only analysis and planning;
- the assurance profile and the execution budget.

Read [references/risk-profiles.md](references/risk-profiles.md) to propose the assurance profile. Then read [references/execution-budgets.md](references/execution-budgets.md) and propose Lean, Balanced, or Maximum execution. Assurance controls risk; execution budget controls ceremony, repetition, and context cost. The Product Owner approves both no later than the Product Gate. A smaller budget must not remove controls needed for the chosen assurance profile.

Read [references/delivery-lifecycle.md](references/delivery-lifecycle.md) after selecting both. Read [references/executor-adapters.md](references/executor-adapters.md) only when creating instruction files, switching tools, or preparing a Codex/Claude handoff.

Read [references/evidence-and-findings.md](references/evidence-and-findings.md) when defining verification, presenting gate evidence, running or triaging QA, or resolving a disputed finding. Do not load it for unrelated routine work.

For an existing repository, inspect its active instructions, git status, structure, build commands, tests, and current documentation before proposing changes. Preserve uncommitted and unfamiliar work. Do not replace established conventions merely to match this skill.

## Non-negotiable operating rules

- Scale the process to the project's real failure modes. Do not give a small application the ceremony of a payment platform.
- Separate what the product must do from how it will be implemented.
- Do not begin material implementation before the applicable product and technical decisions are approved.
- Treat approved specifications and acceptance criteria as the source of truth. Record material changes rather than silently drifting.
- Keep durable state in the repository, not solely in chat, but create only artifacts that help make or verify decisions.
- Make incremental, reviewable, reversible changes and report verification evidence.
- Never weaken tests, hard-code examples, or bypass checks merely to make validation pass.
- Do not expand scope through unsolicited refactors, abstractions, features, dependencies, documents, or review rounds.
- Require confirmation immediately before destructive, irreversible, externally visible, production, billing, credential, or live-data actions.
- Never claim release readiness without evidence, residual risks, independent QA where required, and Product Owner acceptance.

## Apply the material-decision test

A decision or change is material when a reasonable Product Owner, knowing it before approval, might choose a different scope, cost, schedule, architecture, data-handling, security, or externally visible outcome. Authentication or authorization changes, sensitive-data handling, payments or entitlements, live migrations, irreversible external effects, public contract changes, production actions, billing, and credential handling are always material.

## Keep execution economical

- Use a compact delivery-state document as the resumption index. Read other sources only when the current decision or task requires them.
- Do not repeat unchanged requirements, paths, decisions, test results, or risks in chat. Report the delta, evidence, decision needed, and next action.
- Prefer references to repository documents over copying their contents into handoffs when the receiving session can access the repository.
- Do not create a new document when an existing source of truth can hold the information without becoming ambiguous.
- Do not stop merely because a document, commit, or increment was completed. Within approved scope, continue until the next material gate or blocker.
- Use the fewest delivery increments that remain reviewable. Do not turn every file or layer into a separate increment.
- Avoid duplicate test coverage without a distinct risk rationale. After a narrow fix, run targeted regression and adjacent-risk checks; do not repeat an entire independent QA campaign unless the change has broad impact.
- Apart from independent QA or specialist review required by the approved assurance profile, use additional agents or sessions only when independence, isolation, or genuinely parallel work justifies their context cost.
- Keep routine status and gate responses compact. If the user specifies a token or time budget, treat it as a delivery constraint and surface a scope tradeoff before exceeding it.

## Run the lifecycle

1. **Discover and bootstrap:** Inspect evidence; distinguish user-provided facts, inferred assumptions, and unresolved decisions; propose assurance and execution modes; and create the minimum instruction and state artifacts. For a small bounded project, present bootstrap findings with the product decision instead of manufacturing a separate approval round.
2. **Specify:** Define users, flows, scope boundaries, edge cases, non-functional requirements, and measurable acceptance criteria. Present assumptions separately from confirmed requirements. Stop for Product Owner approval when product behavior is materially decided.
3. **Design and plan:** Evaluate meaningful alternatives, choose architecture and dependencies using current authoritative sources when versions or support windows can change, define trust/data boundaries, testing, operations, and reviewable increments. Stop before material implementation.
4. **Build:** Implement the approved plan without requesting approval between increments. Test incrementally, checkpoint useful states, update durable status at milestones, and stop only for material deviation or blocker.
5. **Independent QA:** Review a fixed revision in an independent, source-read-only context. Apply the evidence and finding standard, run risk-based acceptance coverage, and report findings without changing source or tests.
6. **Triage and repair:** Classify findings before assigning fixes. Reverify accepted fixes narrowly unless their impact requires broader regression.
7. **User acceptance and release:** Let the Product Owner exercise the product before final acceptance. Separate local/test handoff from production authorization. Verify deployment-specific controls only when deployment is in scope.

## Role and authority separation

- Analysts may change product artifacts but not application code.
- Architects may change technical decision artifacts but must not implement before approval.
- Developers may change code and tests within approved scope but cannot certify their own work as independent QA.
- QA reviewers may create reports outside protected source but must not change application source, tests, or migrations.
- Release reviewers verify readiness but do not deploy without authorization.

Prompt-only read-only language is not a security boundary. Use actual isolation where available; otherwise disclose the limitation and prepare a concise handoff for a separate session.

## Resume and completion

At session start, reconstruct state from the active instruction file, delivery-state index, relevant source-of-truth documents, and git history. Record this skill's metadata version and source revision when available. Do not reread every artifact by default. Resolve contradictions before continuing.

At a material gate, present only:

- decision or completed outcome;
- relevant evidence;
- open findings and residual risks;
- exact Product Owner decision requested;
- next action after approval.

Do not mark the project complete until the applicable definition of done is met, independent findings are resolved or accepted, the Product Owner has performed acceptance appropriate to the delivery target, and production actions remain explicitly separate unless authorized.
