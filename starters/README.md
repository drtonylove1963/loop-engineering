# Starters

Clone-and-run scaffolds. Copy into your project — do not submodule the whole repo unless you want the docs too.

## Daily Triage (L1 report-only)

| Starter | Tool | Path |
|---------|------|------|
| [minimal-loop](./minimal-loop/) | Grok | `.grok/skills/` |
| [minimal-loop-claude](./minimal-loop-claude/) | Claude Code | `.claude/skills/` + `.claude/agents/` |
| [minimal-loop-codex](./minimal-loop-codex/) | Codex | `.codex/skills/` + `.codex/agents/` |

## Other patterns (L2 assisted)

| Starter | Pattern | Readiness |
|---------|---------|-----------|
| [pr-babysitter](./pr-babysitter/) | PR Babysitter | L2 assisted |
| [ci-sweeper](./ci-sweeper/) | CI Sweeper | L2 assisted |
| [dependency-sweeper](./dependency-sweeper/) | Dependency Sweeper | L2 assisted |

After copying, run:

```bash
npx @cobusgreyling/loop-audit .
npx @cobusgreyling/loop-audit . --suggest
```

Or from a clone:

```bash
node tools/loop-audit/dist/cli.js .
```