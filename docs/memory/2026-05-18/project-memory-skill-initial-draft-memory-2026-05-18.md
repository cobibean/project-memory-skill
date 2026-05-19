# Project Memory Skill Initial Draft Memory - 2026-05-18

## Session summary

- Created the first open-source-ready draft of the `project-memory` skill repo.
- The skill teaches agents to read recent `docs/memory/` files before
  substantial work and write concise handoff memory after meaningful work.
- The design intentionally stays small: one path convention, one template,
  a few examples, and safety rules.

## Decisions made

- Skill name: `project-memory`.
- Recommended public repo name: `project-memory-skill`.
- Memory path convention:
  `docs/memory/YYYY-MM-DD/descriptive-slug-memory-YYYY-MM-DD.md`.
- The `SKILL.md` stays lean and procedural; README/examples explain the public
  repo for humans.
- No scripts are included in v1 because this convention should be drop-in and
  low ceremony.

## Files created or changed

- `SKILL.md`
- `README.md`
- `LICENSE`
- `.gitignore`
- `agents/openai.yaml`
- `templates/memory-template.md`
- `examples/saas-product-memory.md`
- `examples/design-pass-memory.md`
- `examples/agent-workspace-memory.md`
- `docs/launch-checklist.md`
- `docs/memory/2026-05-18/`
  `project-memory-skill-initial-draft-memory-2026-05-18.md`

## Source-of-truth docs

- `SKILL.md` is the source of truth for agent behavior.
- `README.md` is the source of truth for public repo positioning and
  installation.
- `templates/memory-template.md` is the copyable memory file shape.

## Commands and verification

```bash
python3 /Users/cobibean/.codex/skills/.system/skill-creator/scripts/\
quick_validate.py .
rg -n "API|token|secret|password|PHI|private|sk-|BEGIN" .
wc -l SKILL.md README.md templates/memory-template.md examples/*.md \
  docs/launch-checklist.md agents/openai.yaml LICENSE
```

Verification result:

- Skill validation passed.
- Sensitive-term scan only found intentional safety guidance and example
  warnings.

## Known constraints

- The repo has not been initialized with git or published to GitHub yet.
- `SKILL.md` frontmatter cannot contain angle brackets, so the trigger
  description uses a plain path example.
- The skill should not grow into a structured memory database, transcript log,
  or automation system.

## Open questions

- Whether to publish under `project-memory-skill`, `agent-project-memory`, or
  another name.
- Whether to add screenshots or keep the repo text-only.

## Recommended next work

- Initialize git, create the GitHub repo, and publish the first commit.
- Optionally install the skill locally and test it in one active repo.
- Cut a `v0.1.0` release after the first real-world pass.
