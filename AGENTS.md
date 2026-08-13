# AI installation contract

When a user gives an AI agent this repository and asks to install the skill:

1. Treat `skills/naive-editorial-avatar` as the only installable skill directory.
2. Prefer the current client's native Agent Skills installer or skill directory when available.
3. Otherwise install it at project scope under `.agents/skills/naive-editorial-avatar`, or at user scope under `~/.agents/skills/naive-editorial-avatar` when the client recognizes the cross-client convention.
4. If the client has no native skill system, keep the folder intact, read `SKILL.md` first, resolve relative paths from the skill directory, and load referenced files on demand.
5. Do not install the repository root, `examples/`, README files, or the license as part of the skill.
6. Preserve and verify these files:
   - `SKILL.md`
   - `agents/openai.yaml` (optional client metadata; harmless to other clients)
   - `assets/synthetic-style-anchor.png`
   - `assets/synthetic-style-range-anchor.png`
   - `references/prompt-blueprint.md`
7. Report the final installed path, the target client, and any validation or capability limitation.

The skill requires an image-capable agent with file access and an image-generation tool that accepts multiple image references. Installation alone does not add those runtime capabilities.

This repository contains no executable installer and requires no package manager. Do not run unrelated scripts or push repository changes unless the user explicitly asks.
