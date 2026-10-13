# custom-fabric-patterns

My custom [fabric](https://github.com/danielmiessler/fabric) patterns — also an Obsidian vault.

## Layout

- `patterns/` — the actual patterns. This folder is registered in fabric via
  `CUSTOM_PATTERNS_DIRECTORY` in `~\.config\fabric\.env`, so **only pattern
  folders belong here** (fabric lists every subfolder as a pattern).
- Each pattern = one folder with a `system.md` inside.
- Custom patterns with the same name as an upstream pattern override it.

## Updating

- Upstream patterns: `fabric --updatepatterns` (pulls from danielmiessler/fabric)
- These patterns: edit in Obsidian, then commit & push this repo.
