# Project Memory Skill

A tiny agent skill for durable project memory.

Agents read recent memory before substantial work and write a short handoff note afterward under:

```txt
docs/memory/YYYY-MM-DD/descriptive-slug-memory-YYYY-MM-DD.md
```

The point is simple: help future Codex, Claude, and other coding-agent sessions
recover decisions, constraints, verification, and next actions without rereading
the whole repo from scratch.

## Why This Exists

Agent context resets are expensive. A small Markdown memory habit compounds into
better collaboration:

- fewer repeated discoveries
- clearer project continuity
- safer handoffs between agents and humans
- less guessing after long-running or multi-day work

This is not a diary, transcript, or full knowledge-management system.
It is a boring continuity convention.

## Install

Copy `SKILL.md` into your agent skills folder or into any skill-distribution
mechanism your agent supports.

For Codex-style local skills, a typical destination is:

```txt
~/.codex/skills/project-memory/SKILL.md
```

You can also copy the convention into a repo-level `AGENTS.md`, `CLAUDE.md`,
or contributor guide if that is how your project gives agents instructions.

For agents that do not support formal skills, paste this into your project
instructions:

```md
Before substantial work, check for recent project memory:

find docs/memory -type f -name '*.md' | sort | tail -10

Read the most recent relevant memory files before acting.
After meaningful work, write a concise new memory file at:

docs/memory/YYYY-MM-DD/descriptive-slug-memory-YYYY-MM-DD.md

Capture decisions, files changed, verification, constraints, open questions,
and recommended next work. Do not store secrets, credentials, PHI, private
tokens, raw sensitive logs, or verbose transcripts.
```

## Convention

Before substantial work:

```bash
find docs/memory -type f -name '*.md' | sort | tail -10
```

Read the most recent relevant files, then continue with the task.

After meaningful work, create a new file:

```txt
docs/memory/2026-05-18/runtime-contract-memory-2026-05-18.md
```

Keep it concise. Capture what the next agent should know, not everything that happened.

Do not write memory for tiny edits, quick answers, or routine work with no
durable decisions, constraints, verification, or next actions.

## What Goes In Memory

- session summary
- decisions made
- files created or changed
- source-of-truth docs
- commands and verification
- known constraints
- open questions
- recommended next work

## What Does Not Go In Memory

- secrets, tokens, keys, or private credentials
- PHI or unnecessary sensitive details
- raw logs with private data
- verbose transcripts
- routine command spam

## Repo Contents

```txt
SKILL.md                         # The drop-in skill
templates/memory-template.md     # Copyable memory template
examples/                        # Example memory files for common repo types
docs/launch-checklist.md         # Publishing checklist
agents/openai.yaml               # Optional Codex UI metadata
```

## Adapting By Project Type

For SaaS/product repos, capture scope decisions, schema/API changes, auth or
billing constraints, migrations, and verification commands.

For design or marketing sites, capture brand decisions, approved assets,
client-sensitive placeholders, screenshot verification, and visual gotchas.

For agent/workspace repos, capture operational state, live paths, background
jobs, exact resume commands, and safety constraints.

## License

MIT
