# Assurance Profiles

Choose the lightest profile that still controls the project's real failure modes. Classify from evidence, not budget, prestige, or code volume alone. The executor proposes the profile and rationale; the Product Owner approves it no later than the Product Gate.

## Mandatory floors

- Authentication, private user data, ordinary personal data, an admin area, or persistent business workflow requires at least **Standard**.
- Payments or entitlements, regulated or highly sensitive data, authorization across tenants, destructive live-data migration, critical identity, or irreversible external actions require **High Assurance**.

Do not lower these floors to satisfy an execution budget. When discovery reveals a trigger, raise the proposed profile immediately and record the decision. Reducing an approved profile requires Product Owner approval and a rationale showing the trigger no longer applies.

## Decision dimensions

Evaluate:

- **Data:** public content; ordinary contact data; accounts or private user data; regulated, health, identity, financial, or children's data.
- **Transactions:** no persistent business state; reversible workflow state; orders, money, entitlements, contracts, or irreversible actions.
- **Access:** public-only; a single trusted operator; multiple roles, tenants, organizations, or privileged administrators.
- **Integrations:** none; a conventional low-impact service; multiple stateful systems, webhooks, payments, ERP, identity, or production APIs.
- **Operational impact:** disposable prototype; business-supporting application; revenue, safety, legal, or mission-critical workflow.
- **Change context:** clean greenfield; documented repository; legacy, migration, live-data, or dirty-worktree change.
- **Uncertainty:** clear bounded request; material product choices remain; domain or technical feasibility is unknown.

## Light

Use only when failure is low-impact and the work has no authentication, personal or sensitive data, money movement, persistent business workflow, destructive migration, or critical integration.

Typical examples: a static marketing site, a local prototype, a small public content tool.

Expected controls:

- short product brief with acceptance criteria;
- compact technical plan;
- build, lint, type, functional, accessibility, and visual checks where relevant;
- a focused independent review;
- a short release or handoff checklist.

Record a rationale for each check category omitted as not applicable. Combine documents and gates when that improves clarity.

## Standard

Use when the project contains ordinary accounts or personal data, persistent business workflows, an admin area, a CMS, an e-commerce catalog without novel payment logic, or one or more meaningful integrations, while failures remain recoverable.

Typical examples: a CMS-backed corporate site, a quote-management app, a conventional Shopify implementation, an internal dashboard.

Expected controls:

- distinct product requirements and acceptance criteria;
- documented architecture and data model;
- authorization and data-boundary review where applicable;
- incremental implementation plan;
- automated and manual test strategy;
- independent code review and QA;
- configuration, migration, backup, rollback, and release notes as applicable.

## High assurance

Use when any single failure mode can cause significant financial, privacy, security, legal, data-loss, multi-tenant, or operational harm.

Typical examples: payment or entitlement systems, health or financial workflows, multi-tenant SaaS authorization, migrations against live customer data.

Expected additional controls:

- threat model and abuse cases;
- data classification, retention, privacy, and trust-boundary mapping;
- explicit authorization matrix;
- migration rehearsal, backup verification, and tested rollback;
- integration contract and failure-mode testing;
- security-focused review independent from implementation;
- staging evidence, observability, incident and recovery considerations;
- human specialist review when domain correctness, compliance, or security requires expertise beyond the available agents.

Do not imply that an AI review replaces legal, compliance, penetration-testing, or other required professional assurance.

## Profile changes

Reassess when scope or evidence changes. Increasing assurance may add controls; reducing it requires the explicit approval described above.
