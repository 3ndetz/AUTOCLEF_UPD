# Git workflow rules

## Structure

Root repo (`AUTOCLEF_UPD`) contains 3 submodules:
- `altoclef` → `3ndetz/altoclef` branch `main`
- `Tungsten` → `3ndetz/Tungsten` branch `altoclef-compat`
- `baritone_altoclef` → `3ndetz/baritone_altoclef` (remote `fork`) branch `1.19.4`

## Commit & push order

1. Make changes inside submodule
2. `git add` + `git commit` + `git push` **inside the submodule**
3. Go to root repo: `git add <submodule>` + `git commit` + `git push` — updates the pointer

**Always push submodule FIRST, then update root repo.**

## baritone_altoclef special case

- `origin` = MiranCZ (upstream), `fork` = 3ndetz (ours)
- Push to `fork`: `git push fork 1.19.4`
- Tracking is set to `fork/1.19.4`

## What goes in root repo

- `.gitmodules`, `.gitignore`
- `CLAUDE.md`, `RULES.md`, `DEVELOP.md`, `PROJECT_OVERVIEW.md`, `PROGRESS.md`
- `.vscode/` configs, `.code-workspace`
- `.claude/` settings
- Submodule pointers (updated after each submodule push)

## What does NOT go in root repo

- `autoclef/` (old, gitignored)
- `old/` (gitignored)
- Build artifacts, `.gradle/`, `build/`
