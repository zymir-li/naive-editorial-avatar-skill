# Naive Editorial Avatar Skill

[English](README.md) · [简体中文](README.zh-CN.md)

A portable [Agent Skill](https://agentskills.io/) that turns a real-person portrait into one identity-preserving square avatar in a calibrated naive hand-drawn editorial style.

## Preview

| Synthetic source portrait | Avatar result |
|---|---|
| <img src="examples/source-portrait.png" alt="Synthetic source portrait" width="420"> | <img src="examples/avatar-result.png" alt="Naive editorial avatar result" width="420"> |

The portrait controls who is drawn. A fictional AI-generated style anchor controls the drawing language. A second fictional range anchor verifies that the same style can support different ages, gender presentations, hairstyles, skin tones, and clothing without becoming an anatomy template.

## Compatibility

The skill follows the open Agent Skills directory format:

- `SKILL.md` contains portable metadata and instructions.
- `references/` contains the prompt blueprint.
- `assets/` contains the synthetic calibration images.
- `agents/openai.yaml` is optional OpenAI/Codex interface metadata; other agents may ignore it.

To execute the complete workflow, an agent needs file and image access plus an image-generation tool that accepts multiple reference images. An agent can install and read the skill without those capabilities, but it cannot produce the final avatar.

## Install with an AI agent

Send the repository URL to your agent with this request:

```text
Install the Agent Skill from:
https://github.com/zymir-li/naive-editorial-avatar

Follow the repository's AGENTS.md. Install only
skills/naive-editorial-avatar using this client's native skill installer
or skill directory, preserve all references and assets, verify the required
files, and report the installed path.
```

An agent with an installer or filesystem access can complete this directly. Installation paths vary by client.

## Manual installation

Copy `skills/naive-editorial-avatar` into a skill directory recognized by your agent.

For cross-client project installation, use:

```text
<your-project>/.agents/skills/naive-editorial-avatar/
```

For cross-client user installation, use:

```text
~/.agents/skills/naive-editorial-avatar/
```

Some clients also use a product-specific skill directory. Prefer that location when its documentation requires one. Restart the client or begin a new session if the skill is not discovered immediately.

The installed skill must contain:

```text
naive-editorial-avatar/
├── SKILL.md
├── agents/openai.yaml
├── assets/synthetic-style-anchor.png
├── assets/synthetic-style-range-anchor.png
└── references/prompt-blueprint.md
```

If your agent has no native skill system, give it the folder and ask it to read `SKILL.md` first, resolve relative paths from that file's directory, and load the referenced assets when instructed.

## Use

Upload a portrait and ask:

```text
Use the naive-editorial-avatar skill to turn this portrait into a square
hand-drawn editorial avatar while preserving the person's identity.
```

Clients that support explicit skill invocation may also accept `$naive-editorial-avatar`.

The skill produces one finished image by default. It protects identity, limits reference-image leakage, and applies separate acceptance gates for style and recognizability. User photos remain task-local and must never be added to the reusable skill or its package.

## Repository layout

- `skills/naive-editorial-avatar/` — the portable installable skill.
- `examples/` — the synthetic source/result pair used in this README.
- `AGENTS.md` — client-neutral installation instructions for AI agents.

## License

The repository is available under the [MIT License](LICENSE), including its fictional AI-generated calibration and example images. No real person's likeness is bundled with the skill.
