# Naive Editorial Avatar

[English](README.md) · [简体中文](README.zh-CN.md)

一个 Codex Skill：把真人照片转换为一张保留本人特征的方形头像，风格是稚拙、极简、带编辑插画感的手绘表达。

## 效果预览

| AI 生成的虚构原始照片 | 头像结果 |
|---|---|
| <img src="examples/source-portrait.png" alt="AI 生成的虚构原始照片" width="420"> | <img src="examples/avatar-result.png" alt="稚拙极简手绘头像结果" width="420"> |

用户照片决定“画谁”，一张 AI 生成的虚构风格锚点决定“怎么画”。另一张虚构范围锚点用于验证年龄、性别表达、发型、肤色和服装变化后仍属于同一画风，不作为人物结构模板。

## 交给 AI 自动安装

把仓库链接和下面这段话一起发给能够安装 Codex Skill 的 AI 编程助手：

```text
请安装这个仓库里的 naive-editorial-avatar Skill：
https://github.com/zymir-li/naive-editorial-avatar

按照仓库根目录 AGENTS.md 执行，只把 skills/naive-editorial-avatar
安装为名为 naive-editorial-avatar 的 Skill；校验必需文件后，告诉我安装路径。
```

拥有 Skill 安装器或本地文件权限的 AI 可以直接完成；没有安装权限的 AI 只能给出操作说明。

## 手动安装

1. 下载或克隆这个仓库。
2. 把 `skills/naive-editorial-avatar` 复制到 `${CODEX_HOME}/skills/naive-editorial-avatar`。
3. 如果没有设置 `CODEX_HOME`，使用 `~/.codex/skills/naive-editorial-avatar`。
4. 如果没有立即显示，重启 Codex。

安装后的目录应当是：

```text
naive-editorial-avatar/
├── SKILL.md
├── agents/openai.yaml
├── assets/synthetic-style-anchor.png
├── assets/synthetic-style-range-anchor.png
└── references/prompt-blueprint.md
```

## 使用

上传一张真人照片，然后说：

```text
使用 $naive-editorial-avatar 把这张照片转换成方形手绘编辑头像，同时保留本人的辨识度。
```

Skill 默认只生成一张完成图。它会保护人物身份、限制参考图串脸，并分别检查风格一致性与人物辨识度。用户照片只能在当前生成任务中临时使用，不能加入可复用 Skill 或发布包。

## 仓库结构

- `skills/naive-editorial-avatar/`：可安装的 Skill 本体，不依赖可执行安装脚本。
- `examples/`：README 使用的输入/输出示例。
- `AGENTS.md`：供 AI 读取的确定性安装说明。

## 协议

整个仓库采用 [MIT License](LICENSE)，包括其中 AI 生成的虚构校准图和示例图，可以免费使用、修改和分发。Skill 不包含任何真人肖像素材。
