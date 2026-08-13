# Naive Editorial Avatar

[English](README.md) · [简体中文](README.zh-CN.md)

一个可移植的开放格式 [Agent Skill](https://agentskills.io/)：把真人照片转换为一张保留本人特征的方形头像，风格是稚拙、极简、带编辑插画感的手绘表达。

## 效果预览

| AI 生成的虚构原始照片 | 头像结果 |
|---|---|
| <img src="examples/source-portrait.png" alt="AI 生成的虚构原始照片" width="420"> | <img src="examples/avatar-result.png" alt="稚拙极简手绘头像结果" width="420"> |

用户照片决定“画谁”，一张 AI 生成的虚构风格锚点决定“怎么画”。另一张虚构范围锚点用于验证年龄、性别表达、发型、肤色和服装变化后仍属于同一画风，不作为人物结构模板。

## 兼容性

这个 Skill 遵循开放的 Agent Skills 目录格式：

- `SKILL.md`：可跨 Agent 使用的元数据和执行说明。
- `references/`：提示词模板。
- `assets/`：AI 生成的虚构校准图。
- `agents/openai.yaml`：OpenAI/Codex 的可选界面元数据，其他 Agent 可以忽略。

要完整执行头像生成流程，Agent 需要具备文件与图片读取能力，以及支持多张参考图的图像生成工具。缺少这些能力的 Agent 仍然可以安装和理解 Skill，但无法产出最终头像。

## 交给 AI 自动安装

把仓库链接和下面这段话发给你的 Agent：

```text
请安装这个仓库里的 Agent Skill：
https://github.com/zymir-li/naive-editorial-avatar

按照仓库根目录 AGENTS.md 执行，只安装
skills/naive-editorial-avatar。使用当前客户端原生的 Skill 安装器
或 Skill 目录，保留全部 references 和 assets；校验必需文件后，
告诉我最终安装路径。
```

拥有安装器或本地文件权限的 Agent 可以直接完成。不同客户端的安装路径可能不同。

## 手动安装

把 `skills/naive-editorial-avatar` 复制到当前 Agent 能够识别的 Skill 目录。

跨客户端的项目级安装位置：

```text
<你的项目>/.agents/skills/naive-editorial-avatar/
```

跨客户端的用户级安装位置：

```text
~/.agents/skills/naive-editorial-avatar/
```

部分客户端还使用自己的专属目录；如果它的官方文档另有要求，优先使用专属目录。如果没有立即识别，重启客户端或新建一次会话。

安装后的目录必须包含：

```text
naive-editorial-avatar/
├── SKILL.md
├── agents/openai.yaml
├── assets/synthetic-style-anchor.png
├── assets/synthetic-style-range-anchor.png
└── references/prompt-blueprint.md
```

如果 Agent 没有原生 Skill 系统，把整个目录交给它，要求它先读取 `SKILL.md`，以该文件所在目录为基准解析相对路径，并在指令要求时加载对应素材。

## 使用

上传一张真人照片，然后说：

```text
使用 naive-editorial-avatar Skill，把这张照片转换成方形手绘编辑头像，
同时保留本人的辨识度。
```

支持显式 Skill 调用的客户端也可以使用 `$naive-editorial-avatar`。

Skill 默认只生成一张完成图。它会保护人物身份、限制参考图串脸，并分别检查风格一致性与人物辨识度。用户照片只能在当前生成任务中临时使用，不能加入可复用 Skill 或发布包。

## 仓库结构

- `skills/naive-editorial-avatar/`：可移植、可安装的 Skill 本体。
- `examples/`：README 使用的虚构输入/输出示例。
- `AGENTS.md`：供 AI 读取的客户端中立安装说明。

## 协议

整个仓库采用 [MIT License](LICENSE)，包括其中 AI 生成的虚构校准图和示例图，可以免费使用、修改和分发。Skill 不包含任何真人肖像素材。
