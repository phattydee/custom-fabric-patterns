# custom-fabric-patterns

My custom [fabric](https://github.com/danielmiessler/fabric) patterns — also an Obsidian vault.

## Layout

- `patterns/` — the actual patterns. This folder is registered in fabric via
  `CUSTOM_PATTERNS_DIRECTORY` in `~/.config/fabric/.env`, so **only pattern
  folders belong here** (fabric lists every subfolder as a pattern).
- Each pattern = one folder with a `system.md` inside.
- Custom patterns with the same name as an upstream pattern override it.

## Set up on a new machine

1. **Install fabric** (requires [Go](https://go.dev)):

   ```sh
   go install github.com/danielmiessler/fabric/cmd/fabric@latest
   ```

2. **First-run setup** — configures your AI vendor(s) and API keys, and creates
   the config dir (`~/.config/fabric` on macOS/Linux,
   `%USERPROFILE%\.config\fabric` on Windows):

   ```sh
   fabric --setup
   ```

3. **Clone this repo** anywhere you like:

   ```sh
   git clone https://github.com/phattydee/custom-fabric-patterns
   ```

4. **Point fabric at the patterns** — add one line to
   `~/.config/fabric/.env` (Windows: `%USERPROFILE%\.config\fabric\.env`),
   using the path to the cloned repo's `patterns/` folder:

   ```ini
   CUSTOM_PATTERNS_DIRECTORY=/path/to/custom-fabric-patterns/patterns
   ```

5. **Load the upstream patterns** (265+ of them, kept separate from yours):

   ```sh
   fabric --updatepatterns
   ```

6. **Verify:**

   ```sh
   fabric -l                      # should list ~268 patterns, including:
   fabric -l | grep -E "create-skill|sop|script2social"
   fabric -p sop --stream "test"  # custom patterns always override upstream namesakes
   ```

Notes:
- Do **not** put pattern folders anywhere else in this repo — only inside
  `patterns/` (dot-folders like `.git`/`.obsidian` at the registered level
  would show up as bogus patterns).
- Optional: open the repo root in [Obsidian](https://obsidian.md) as a vault
  for comfortable editing; commit and push when done.

## Updating

- Upstream patterns: `fabric --updatepatterns` (pulls from danielmiessler/fabric)
- These patterns: edit in Obsidian, then commit & push this repo.
- On other machines: `git pull` in the cloned repo — fabric picks up changes
  immediately, nothing to re-register.
