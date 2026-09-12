# Executor Adapters

Use one neutral delivery method while expressing persistent instructions in the executor's native format. Do not maintain duplicated rule bodies that can drift.

## Codex execution

- Use a concise root `AGENTS.md` for repository-wide, always-applicable instructions.
- Use nested instruction files only when a subtree has genuinely different commands or constraints.
- Keep long product requirements, plans, findings, and temporary state in project documents rather than `AGENTS.md`.
- Verify which instruction sources are active when precedence is uncertain.
- Because a newly created instruction chain may not govern the already-running bootstrap context, finish the bootstrap gate and begin the approved implementation in a fresh Codex session that loads the new files.

When this skill is running inside the project Codex session, operate the lifecycle directly. Do not merely generate prompts for another Codex instance unless the user explicitly requests a handoff.

## Claude Code execution

- Use a concise project `CLAUDE.md` for always-applicable project instructions.
- Use path-scoped Claude rules or invoked skills for conditional procedures rather than expanding the root file indefinitely.
- Keep product requirements and delivery state in ordinary project documents.
- After bootstrap approval, begin implementation in a fresh session and verify that the intended project memory files loaded.

If this skill is invoked from Codex only to prepare a Claude Code project, produce a single bootstrap handoff for Claude instead of creating Claude's project artifacts on its behalf. Claude must inspect the target workspace and create its own operating files.

## Dual-tool project

Prefer a tool-neutral `AGENTS.md` as the canonical shared instruction body and a small `CLAUDE.md` that imports or points to it using the mechanism supported by the installed Claude Code version. Put only Claude-specific additions in `CLAUDE.md`.

Before choosing this arrangement, verify the current executor supports the intended import behavior. If it does not, use a shared neutral document referenced by two minimal wrappers and add a drift check to project maintenance.

Do not place role-specific temporary identities such as "you are the QA" in the shared root instructions. Supply those through the isolated role/session configuration so the same repository can support analysts, developers, reviewers, and QA without contradictory rules.

## Independent QA boundary

Prompt-only read-only language is not a security boundary. Prefer an actual read-only environment, permission profile, sandbox, separate worktree with protected source, or review facility that cannot mutate the implementation.

If the executor cannot enforce read-only access:

1. Finish implementation and record the exact revision under review.
2. Create a complete QA handoff containing sources of truth, setup commands, acceptance criteria, known limitations, and required report format.
3. Ask the user to start a separate review session with source mutation disabled where possible.
4. Require the reviewer to report any accidental mutation and discard that review run.
5. Return findings to the orchestrator for triage; only a developer context applies fixes.

## Handoffs

A handoff must be self-contained but not copy the entire repository context. Include:

- target repository and revision;
- role, authority, and prohibited actions;
- required source-of-truth files;
- exact objective and stopping condition;
- setup and verification commands when known;
- expected output artifact;
- open risks or assumptions that affect the task.

The receiving executor must inspect the actual files before making claims or changes.
