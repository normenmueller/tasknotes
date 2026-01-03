# Workspace Layout

- `./main` → Upstream baseline mirror (read-only working tree).
- `./intg` → Integration working tree of the fork (default checkout: `intg` branch).
- `./drft/{feat, fix, ...}-<feature>` → Draft feature worktrees (not yet published).
- `./preq/{feat, fix, ...}-<feature>` → Feature worktrees for published PRs.
- `./trunk.bak` → READ ONLY! Old fork used for reference.

# Project Overview

- TaskNotes is a bases-based task management plugin where each task lives as a separate note with YAML frontmatter.
- Key features include calendar integration, Kanban boards, time tracking, and a Pomodoro timer.
- This fork exists to implement fixes and enhancements and propose them upstream via PRs.

# Required Behavior for Codex

- Act as a top-tier Obsidian/TypeScript/HTML5/CSS engineer and software architect.
- Apply strong design-pattern and best-practice judgment; prioritize robustness, clarity, and maintainability.
- Be meticulous with test coverage, regressions, and compatibility with `./main`.
- Ask clarifying questions when needed before making risky changes.
- Keep changes minimal and targeted unless explicitly asked to refactor.
- Use Conventional Commit messages with **lowercase** type prefix (e.g., `fix:`, `feat:`, `docs:`, `chore:`).
- Always propose a commit message first and wait for explicit user approval before committing.

# Workflow (Strict)

## Mirrors and Branches

- `./main` is a **read-only mirror** of `upstream/main`. Never commit here.
- `./intg` is the fork working tree with branch `intg` for **integration only**. Do not base PRs on `intg`.
- Feature branches **must** be created from `upstream/main` (not from `intg`).
- The fork's `origin/main` is kept in sync with `upstream/main` (fast-forward or force-with-lease when required).

## Feature Branch Process

Feature branches are created from `upstream/main` and worked on only via their matching worktree in `./drft/{feat, fix, ...}-<feature>`. Move to `./preq/` only once the feature is ready to publish as a PR. Merge to `intg` only when explicitly requested and **always** via `--no-ff`.

1) `git -C ./intg fetch upstream`
2) `git -C ./intg branch {feat, fix, ...}-<feature> upstream/main`
3) `git -C ./intg worktree add ./drft/{feat, fix, ...}-<feature> {feat, fix, ...}-<feature>`
4) Work only inside `./drft/{feat, fix, ...}-<feature>`.
5) Run relevant tests.
6) When ready to publish, move the worktree: `git -C ./intg worktree move ./drft/{feat, fix, ...}-<feature> ./preq/{feat, fix, ...}-<feature>`
7) Open PR from the feature branch to upstream.

## PR Documentation (Mandatory)

- Each feature branch **must** include a `PR.md` at repo root.
- `PR.md` content and structure **must** follow the established pattern:

```
# <branch-name>

## <Short title>

<1–3 sentence summary>

Examples (illustrative):

- Example 1
- Example 2

## Changelog

- Bullet list of changes

## Tests

- List of tests run (or "Not run")
```

- `Pull Request.md` is deprecated. Always use `PR.md`.
- Once a PR is open, **do not rewrite history** on that feature branch (no rebases, no force-pushes) unless explicitly instructed.

## Integration Changelog

## Integration (Strict)

### Rules

- **Never** cherry-pick feature commits into `./intg`.
- **Always** merge feature branches into `./intg` using `--no-ff` so branch labels remain visible in history.
- `./intg` may be rebuilt from `upstream/main` when requested, then features are re-merged with `--no-ff` in the desired order.
- Merge commits must use the message format: `Merge branch '<feature-branch>' of github.com:normenmueller/tasknotes into intg`.

### Merge Steps (when requested)

1) `git -C ./intg fetch origin <feature-branch>`
2) `git -C ./intg merge --no-ff origin/<feature-branch>`

### Integration Changelog

- In `./intg`, maintain a `CHANGELOG.md` that **aggregates** merged feature summaries.
- After merging a feature into `intg`, copy its `PR.md` summary/changelog into `CHANGELOG.md`, then **remove `PR.md`** from `intg` to avoid conflicts.
- Order entries **newest first** (most recent feature at the top of the `Unreleased` section).
- Commit the integration update with a `chore:` message (e.g., `chore: update integration changelog (<feature>)`).

## Roadmap (Ordering)

- In `./ROADMAP.md` under `## Status`, list completed items **newest first**.

# Quality Attributes to Prioritize

- Robustness
- Modularity
- Maintainability
- Naming consistency
- Standards compliance
- Scalability
- Performance / responsiveness
- Resource efficiency

# Working Conventions

- Keep code and documentation in English; use German for chat communication.
- Prefer minimal, focused changes over broad refactors unless requested.
- Keep behavior aligned with upstream unless a fork-specific deviation is required.
