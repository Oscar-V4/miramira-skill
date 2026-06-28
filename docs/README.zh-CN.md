# MiraMira

<p align="center">
  <img src="../assets/miramira-logo.png" alt="MiraMira magic mirror logo" width="240">
</p>

<p align="center">
  <a href="../README.md">한국어</a> |
  <a href="README.en.md">English</a> |
  <b>简体中文</b>
</p>

**"He who asks a question is a fool for five minutes; he who does not remains a fool forever"**

**"提问的人可能只做五分钟的傻瓜，不提问的人却会做一辈子的傻瓜" - 中国谚语**

AI Agent 很强大。但无论多强的 Agent，如果无法清楚理解用户想法背后的语境、背景、偏好和限制，也很难真正做好工作。MiraMira 是一种打破 AI 与用户之间沟通壁垒的方法论。

MIRAMIRA 通过提问，把：
- 模糊的想法提炼成清晰的目的和标准，
- 零散的偏好整理成一致的方向，
- 不明确的请求转化成 Agent 可以实现的规格。
- 如果答案可以通过探索代码库得到，它会先进行探索。
- 它会持续追问，直到达成 shared understanding。

## 快速安装

把下面这段提示词直接复制给 Codex、Claude Code、Antigravity 或其他 Agent 即可。

```text
请查看这个 GitHub repo 并安装 MiraMira agent skill:
https://github.com/Oscar-V4/miramira-skill

请检测你当前运行的 agent 环境并完成安装。
- 如果是 Codex，请安装到 ~/.codex/skills/miramira。
- 如果是 Claude Code，请安装到 ~/.claude/skills/miramira。
- 如果是其他 agent，请确认它是否支持基于 SKILL.md 的 skill 文件夹，并安装到最接近的用户级 skill 目录。
- 如果有专用安装器，请使用它；否则 clone 这个 repo，并把 skills/miramira 文件夹复制到用户 skill 目录。

安装后，请阅读 skills/miramira/SKILL.md 和 README.md，然后说明在这个环境里如何触发该 skill，并进行一段“skill 拆解解说”。
```

直接安装：

Codex:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

Claude Code:

```bash
git clone https://github.com/Oscar-V4/miramira-skill.git
cd miramira-skill
./install.sh --target claude --force
```

安装后重启你的 agent 应用，然后用 `$miramira` 调用。

## Skill 全文

<details>
<summary><code>skills/miramira/SKILL.md</code></summary>

```markdown
---
name: miramira
description: >
  MiraMira. Interview the user relentlessly about a plan or design until reaching
  shared understanding, resolving each branch of the decision tree. Use when user wants to
  stress-test a plan, get grilled on their design, or mentions "MiraMira".
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time.

Use the best available structured question UI when possible: in Codex, prefer
`request_user_input`; in Claude Code, prefer `AskUserQuestion`.

When it helps keep communication with the user clear and aligned, let your question reflect your current understanding, judgment, and uncertainty.

If a question can be answered by exploring the codebase, explore the codebase instead.
```

</details>

## 结构

```text
miramira-skill/
├── README.md
├── docs/
│   ├── README.en.md
│   └── README.zh-CN.md
├── install.sh
└── skills/
    └── miramira/
        ├── SKILL.md
        └── agents/
            └── openai.yaml
```
