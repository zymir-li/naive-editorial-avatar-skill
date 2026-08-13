# Naive Editorial Avatar

[English](README.md) · [简体中文](README.zh-CN.md)

A Codex skill that turns a real-person portrait into one identity-preserving square avatar in a calibrated naive hand-drawn editorial style.

## Preview

| Synthetic source portrait | Avatar result |
|---|---|
| <img src="examples/source-portrait.png" alt="Synthetic source portrait" width="420"> | <img src="examples/avatar-result.png" alt="Naive editorial avatar result" width="420"> |

The portrait controls who is drawn. A fictional AI-generated style anchor controls the drawing language. A second fictional range anchor verifies that the same style can support different ages, gender presentations, hairstyles, skin tones, and clothing without becoming an anatomy template.

## Install with an AI agent

Send the repository URL to an AI coding agent that can install Codex skills, together with this request:

```text
Install the naive-editorial-avatar skill from
https://github.com/zymir-li/naive-editorial-avatar

Follow the repository's AGENTS.md. Install only the folder
skills/naive-editorial-avatar as a skill named naive-editorial-avatar,
verify its required files, and report the installed path.
```

An agent with a skill installer or local filesystem access can complete the installation directly. An agent without installation access can only provide instructions.

## Manual installation

1. Download or clone this repository.
2. Copy `skills/naive-editorial-avatar` to `${CODEX_HOME}/skills/naive-editorial-avatar`.
3. If `CODEX_HOME` is not set, use `~/.codex/skills/naive-editorial-avatar`.
4. Restart Codex if the skill does not appear immediately.

The installed skill folder should contain:

```text
naive-editorial-avatar/
├── SKILL.md
├── agents/openai.yaml
├── assets/synthetic-style-anchor.png
├── assets/synthetic-style-range-anchor.png
└── references/prompt-blueprint.md
```

## Use

Upload a portrait and ask:

```text
Use $naive-editorial-avatar to turn this portrait into a square hand-drawn editorial avatar while preserving the person's identity.
```

The skill produces one finished image by default. It protects identity, limits reference-image leakage, and uses explicit acceptance gates for both style and recognizability. User photos remain task-local and must never be added to the reusable skill or its package.

## Repository layout

- `skills/naive-editorial-avatar/` — the installable skill; no executable installer is required.
- `examples/` — the source/result pair used in this README.
- `AGENTS.md` — deterministic installation instructions for AI agents.

## License

The repository is available under the [MIT License](LICENSE), including its fictional AI-generated calibration and example images. No real person's likeness is bundled with the skill.
