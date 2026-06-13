# SUMMARY.md

> **A cheat sheet for AI agents that reduces unnecessary repo scans.**

When an AI agent opens your project, it typically scans every file to understand
the codebase. That wastes tokens, time, and money. SUMMARY.md gives agents a
map — they read **one file** and jump directly to the code they need, scanning
only when necessary.

## What It Is

A single `SUMMARY.md` file at the root of your repo that tells AI agents:

- What the project is and what it's built with
- Where every major piece of code lives
- Key architectural patterns to understand
- Common gotchas and pitfalls
- How to navigate by task ("change the chat UI? → go here")

## Why It Works

Agents are trained to read project root files (README.md, AGENTS.md, CLAUDE.md,
CONTRIBUTING.md) before exploring. If SUMMARY.md answers their orientation
questions, they skip the expensive `grep`/`glob`/`read` scanning phase for
everything they already know.

**Estimated savings:** 50-90% fewer tokens on initial orientation, depending on
repo size.

## Quick Start

1. Copy `SUMMARY_TEMPLATE.md` to your repo root as `SUMMARY.md`
2. Fill in the `{{PLACEHOLDERS}}` with your project's specifics
3. Commit and push
4. **Activate it** -- add an agent rule so AI agents actually read it (see below)

That's it. No build step, no config, no runtime dependency.

## Agent Activation

Creating `SUMMARY.md` is only half the step. AI agents won't read it unless their
rules tell them to. Add the following to your project-level or global `AGENTS.md`:

```markdown
## Codebase Orientation

- **Project Summary (`SUMMARY.md`):** Always check the workspace root for
  `SUMMARY.md` at session initialization. Read it before exploring the codebase
  -- it provides a source map so you can navigate directly to relevant files
  instead of scanning every directory. If the project doesn't have one, offer
  to create it from a template.
```

Without this rule, `SUMMARY.md` sits silently at the repo root and most agents
will never see it.

## Template

See [`SUMMARY_TEMPLATE.md`](./SUMMARY_TEMPLATE.md) for the full annotated template.

## License

CC0 1.0 Universal — public domain. Use it, modify it, sell it, do whatever you
want. No attribution required (though appreciated).

See [`LICENSE`](./LICENSE) for the full legal text.

## Who Made This

Created by [Toshon Jennings](https://github.com/toshon-jennings) because watching
AI agents recursively list every directory in a 6,000-file repo was painful.

## Related

- [AGENTS.md](https://agents.md/) — a convention for agent instruction files
- [CLAUDE.md](https://docs.anthropic.com/en/docs/claude-code/settings#claudemd) — Claude Code's project-level memory
- [Cursor Rules](https://docs.cursor.com/context/rules-for-ai) — Cursor's AI instruction system