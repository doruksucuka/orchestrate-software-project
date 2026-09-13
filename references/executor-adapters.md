# Executor Adapters

Use one neutral delivery method while expressing persistent instructions in the executor's native format. Do not maintain duplicated rule bodies that can drift.

## Codex execution

- Use a concise root `AGENTS.md` for repository-wide, always-applicable instructions.
- Use nested instruction files only when a subtree has genuinely different commands or constraints.
- Keep long product requirements, plans, findings, and temporary state in project documents rather than `AGENTS.md`.
- Verify which instruction sources are active when precedence is uncertain.
- Because a newly created instruction chain may not govern the already-running bootstrap context, begin approved implementation in a fresh Codex session that loads the new files.

When this skill runs inside the project Codex session, operate the lifecycle directly. Do not generate prompts for another Codex instance unless the user requests a handoff or role isolation requires it.

## Claude Code execution

- Use a concise project `CLAUDE.md` for always-applicable project instructions.
- Use path-scoped Claude rules or invoked skills for conditional procedures rather than expanding the root file indefinitely.
- Keep product requirements and delivery state in ordinary project documents.
- After bootstrap approval, begin implementation in a fresh session and verify that the intended project memory files loaded.

If Codex is preparing a Claude Code project, produce a single bootstrap handoff instead of creating Claude's project artifacts on its behalf. Claude must inspect the target workspace and create its own operating files.

## Dual-tool project

Prefer a tool-neutral `AGENTS.md` as the canonical shared instruction body and a small `CLAUDE.md` that imports or points to it using a mechanism supported by the installed Claude Code version. Put only Claude-specific additions in `CLAUDE.md`.

If reliable import is unavailable, use one shared neutral document referenced by two minimal wrappers and add a drift check. Do not place temporary identities such as "you are the QA" in shared root instructions; supply them through the isolated session.

## Independent QA boundary

Prompt-only read-only language is not a security boundary. Prefer a read-only environment, permission profile, protected snapshot, separate worktree, or review facility that cannot mutate implementation.

If read-only access cannot be enforced:

1. Record the exact revision under review.
2. Put stable QA scope and commands in repository documents when they will be reused.
3. Start a separate review session with mutation disabled where possible.
4. Require the reviewer to report accidental mutation and discard that run.
5. Return findings for triage; only a developer context applies fixes.

## Compact handoffs

A handoff is self-contained when the receiver can locate the target and its authoritative instructions; it does not need to duplicate accessible repository content. Include only:

- repository, branch, and exact revision;
- role boundaries and prohibited actions;
- relevant source-of-truth paths;
- objective and stopping condition;
- output artifact or response expected;
- only setup details or risks not already recorded.

Do not inline acceptance criteria, test matrices, or long command lists already available to the receiving session. The receiver must inspect referenced files before making claims. After a scoped fix, hand off the failed criterion and adjacent risk rather than the complete original QA campaign.
