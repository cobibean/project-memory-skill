# Project Memory Skill README Visual Memory - 2026-05-18

## Session summary

- Added the Project Memory Skill visual to the public repo so it appears when
  people land on the GitHub README.
- Tracked the image as a repo asset for reuse as the GitHub social preview.

## Decisions made

- Asset path:
  `assets/project-memory-skill-social-preview.png`.
- README places the image directly below the H1 so it is visible immediately.
- GitHub social preview is controlled by repository settings, not by README
  Markdown, so the tracked asset is ready for that setting but does not set it
  automatically.

## Files created or changed

- `README.md`
- `assets/project-memory-skill-social-preview.png`
- `docs/memory/2026-05-18/project-memory-skill-readme-visual-memory-2026-05-18.md`

## Commands and verification

```bash
file assets/project-memory-skill-social-preview.png
sips -g pixelWidth -g pixelHeight assets/project-memory-skill-social-preview.png
```

## Recommended next work

- Upload `assets/project-memory-skill-social-preview.png` as the repository
  social preview image in GitHub settings.
