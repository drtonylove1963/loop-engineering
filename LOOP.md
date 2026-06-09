# LOOP.md — Loop Engineering Reference

This file documents how the **loop-engineering** reference repository itself is (or will be) operated with loop engineering patterns.

The goal of this repo is to be the canonical, copyable, high-signal collection of patterns, starters, and tooling. It should therefore eat its own dogfood aggressively.

## Intended Loops (phased)

### Daily Triage (L1 → L2)
- Cadence: 1d (or 2h during active development)
- Skill: loop-triage (from `starters/minimal-loop`)
- State: STATE.md (or this file + issues)
- Current phase: Report-only. Human reviews the report each day and decides what to action.
- Handoff: Design decisions, large refactors, new pattern acceptance.

### PR Babysitter (future, L2)
- Cadence: 10–15m during active hours
- Uses the `pr-babysitter` starter + worktrees for any suggested fixes.
- Will live primarily in the GitHub Actions + comments on PRs.
- Strong verifier + explicit allowlist for auto-merge (very small safe changes only).

### Dependency Sweeper (L2, just added)
- Cadence: 6h–1d
- New pattern + starter added in this iteration.
- Focus: patch + low-risk CVE only for the first 30 days.
- Verifier = full `npm ci && npm test` (or the build that exists) in worktree.
- Human gate on anything that touches core packages or majors.

### CI Sweeper / Post-Merge (opportunistic)
- The `validate-patterns.yml` + `audit.yml` workflows in `.github/workflows/` are the beginning of dogfooding these patterns.
- Future: a sweeper that reacts to failing validate/audit runs with minimal doc or link fixes.

## Worktrees

- Any unattended code-change experiment (dependency sweeper, PR babysitter fixes) runs in an **isolated git worktree** per attempt.
- One worktree per fix; discard after verifier REJECT or human escalation.
- Starters document worktree usage per tool — see `starters/minimal-loop-claude/LOOP.md` and `starters/minimal-loop-codex/LOOP.md`.

## Connectors (MCP)

- **MCP not required** for L1 daily triage on this reference repo.
- Optional: GitHub MCP for issue/PR discovery when moving to L2 PR babysitter.
- Scope connectors to read + comment until the loop is trusted.

## Safety & Gates (this repo)

- No auto-merge on main for anything except the most trivial dependency patches (and even those are behind allowlist + verifier today).
- Denylist for this reference: anything touching the showcase HTML/CSS, the core primitives docs, or the audit scoring logic without human review.
- Live loop state: `STATE.md` at repo root (dogfooded). Starters still ship `.example` files for consumers.

## How to run the loops here (for contributors / the maintainer)

See the individual pattern docs and the GitHub Actions.

Quick local check:

```bash
node tools/loop-audit/dist/cli.js . --suggest
```

After changes to patterns, starters, or docs, the `validate-patterns` + `audit` workflows will run automatically on PRs.

## Evolution

We will raise the L level of this repo itself over time and record the journey in `stories/`.

Current target for the reference: solid L2 with excellent observability and zero "I had to hand-hold the loop for an hour" stories.

---

*This file is both documentation and the seed for the loops that will maintain the reference.*
