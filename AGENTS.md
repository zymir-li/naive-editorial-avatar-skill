# AI installation contract

When a user gives an AI agent this repository and asks to install the skill:

1. Treat `skills/naive-editorial-avatar` as the only installable skill directory.
2. Prefer the agent's built-in skill installer when available.
3. Otherwise copy that directory to `${CODEX_HOME}/skills/naive-editorial-avatar`; when `CODEX_HOME` is unset, use `~/.codex/skills/naive-editorial-avatar`.
4. Do not install the repository root, `examples/`, README files, or the license as part of the skill.
5. Verify these files after installation:
   - `SKILL.md`
   - `agents/openai.yaml`
   - `assets/synthetic-style-anchor.png`
   - `assets/synthetic-style-range-anchor.png`
   - `references/prompt-blueprint.md`
6. Report the final installed path and any validation error.

This repository contains no executable installer and requires no package manager. Do not run unrelated scripts or push repository changes unless the user explicitly asks.
