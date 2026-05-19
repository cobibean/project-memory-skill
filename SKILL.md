---
name: project-memory
description: >-
  Use this skill when starting or finishing substantial project work that would
  benefit from durable continuity across Codex, Claude, or other agent sessions.
  It teaches agents to read recent project memory before work and write concise
  Markdown handoff memory after meaningful work under
  docs/memory/YYYY-MM-DD/descriptive-slug-memory-YYYY-MM-DD.md, including
  decisions, changed files, verification, constraints, open questions, and next
  actions while avoiding secrets and sensitive details.
---

# Project Memory

Use project memory to preserve durable project context for future agents and humans.

Project memory lives at:

```txt
docs/memory/YYYY-MM-DD/descriptive-slug-memory-YYYY-MM-DD.md
```

Memory is append-only by default. Create a new file for new work.
Do not overwrite, delete, or rewrite prior memory unless the user explicitly asks.

## Before Work

For substantial work:

1. Find the project root.
2. Check whether `docs/memory/` exists.
3. If it exists, list recent memory files:

```bash
find docs/memory -type f -name '*.md' | sort | tail -10
```

4. Read the most recent relevant memory files.
5. Read any source-of-truth docs referenced by those files when they matter for
   the task.
6. Briefly summarize the relevant context before acting.

If no memory exists, continue normally.
Do not create memory at the start unless the user asks.

## After Meaningful Work

Create a new memory file when the session produced context future agents would be
annoyed to rediscover.

Use today's local date and create the dated folder if needed:

```txt
docs/memory/YYYY-MM-DD/
```

Use a lowercase descriptive slug:

```txt
docs/memory/2026-05-18/auth-flow-memory-2026-05-18.md
```

Do not write memory for tiny edits, quick answers, routine formatting, or work
that leaves no durable decisions, constraints, verification, or next actions.

## What To Capture

Capture durable context, not a transcript:

- session summary
- decisions made
- files created or changed
- source-of-truth docs
- commands, tests, builds, screenshots, or checks run
- known constraints, gotchas, and failure modes
- open questions
- recommended next work

## What Not To Capture

Do not store:

- secrets, API keys, tokens, passwords, or private credentials
- PHI, unnecessary personal data, or sensitive client details
- raw logs containing secrets or private data
- verbose transcripts
- every routine command
- speculation that will not help the next agent

Mention that a secret was configured or verified without recording the secret
value.

## Memory Template

Use only the sections that matter:

```md
# <Project or Task> Memory - YYYY-MM-DD

## Session summary

## Decisions made

## Files created or changed

## Source-of-truth docs

## Commands and verification

## Known constraints

## Open questions

## Recommended next work
```

## Writing Style

Write Markdown another agent can skim in under two minutes.

Prefer:

- short sections
- bullets for concrete facts
- exact file paths
- exact commands when verification matters
- clear next actions

Avoid:

- long narrative
- duplicated repo docs
- vague claims like "fixed stuff"
- rewriting history from older memory files

## Safety Rules

- Follow stricter local repo instructions first.
- Never overwrite prior memory unless explicitly asked.
- If existing memory must be amended, preserve prior content and add a dated note.
- Redact sensitive values.
- If old memory conflicts with current source-of-truth docs, trust the newer
  source of truth and mention the conflict.
- If work is interrupted, write current status, exact resume instructions, and
  known verification state.
