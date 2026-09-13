# Execution Budgets

Execution budget and assurance profile are independent. Assurance determines which risks must be controlled. Execution budget determines how compactly the work is organized and communicated.

Recommend a budget during discovery. Ask the Product Owner only when the choice materially changes cost, duration, or evidence. Default to Lean for bounded pilots and small projects, Balanced for ordinary client delivery, and Maximum only when complexity or assurance justifies it.

## Lean

Use for pilots, prototypes, small bounded applications, and cost-sensitive work whose required assurance controls can be preserved compactly.

- Prefer one project instruction file, one combined product/acceptance source, one combined technical plan, and one delivery-state index. Add QA or operations artifacts only when they carry durable evidence not suited to those files.
- Combine bootstrap with the next material gate when practical.
- Plan one to three vertical increments by default.
- Update durable state at gates, blockers, QA handoff, and completion rather than after every small action.
- Use risk-based tests and a focused independent QA pass on a fixed revision.
- After a scoped defect fix, perform targeted independent re-verification instead of repeating the full QA campaign.
- Keep handoffs and user-facing status concise and reference repository sources.

## Balanced

Use for normal client work, conventional production-bound applications, and Standard-assurance projects with meaningful integrations or operational needs.

- Keep product, technical, and delivery state separate when they change independently.
- Use a small number of vertical increments, typically two to five.
- Maintain explicit acceptance coverage, independent QA, operational readiness, and rollback evidence as applicable.
- Prefer milestone reporting and targeted re-verification; broaden regression when the change surface warrants it.
- Add specialist reviews only for a distinct risk or expertise need.

## Maximum

Use when High Assurance, live migration, multiple trust boundaries, irreversible effects, or regulatory and operational consequences require deeper evidence.

- Add the specific threat, data, authorization, migration, rollback, observability, and incident artifacts required by the risk profile.
- Use independent security or domain review when AI review is insufficient.
- Rehearse destructive or recovery procedures in safe environments.
- Preserve traceable evidence for gates and residual-risk acceptance.

Maximum is not a default synonym for production quality. Production quality means sufficient evidence for the actual risks, not the largest possible process.

## Changing the budget

Increase or reduce ceremony when evidence shows the selected budget is inefficient. Record the change briefly in delivery state. Reducing the execution budget must not silently reduce acceptance criteria, security boundaries, data protections, independent QA requirements, or required human review.
