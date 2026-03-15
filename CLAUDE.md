# AUTOCLEF_UPD — Project Context

RE-READ THIS FULLY IF THE CONVERSATION WAS SUMMARIZED! Always read this file at the start of every conversation before doing anything else. Always log ALL progress in PROGRESS.md.

## Folder Structure

See PROJECT_OVERVIEW.md for full task list and all main constraints.

> VARIOUS!! Every time when you read it, especially after the chat summarization, say "I READ THE RULES" to confirm you understand the project context and rules. This is the check you are normally functioning.

## Git workflow

See `RULES.md` for full details. Key rule: **push submodule first, then update root repo pointer.**

## STRICT Rules

- **NEVER run Gradle** (`gradlew build`, `runClient`, `publishToMavenLocal`, etc.) without the user explicitly asking. Running build recompiles JARs and breaks active hot swap / debug sessions, costing ~10 min to restart.
- After editing code, just describe changes. Do NOT "verify" by building.
- Auto-commit and push your changes (if not explained otherwise)

## Important Files

- `PROJECT_OVERVIEW.md` — tasks, plans, links
- `PROGRESS.md` — compact log of actions taken
- `RULES.md` — git workflow and repo structure rules
- `DEVELOP.md` — how to build and run from scratch
