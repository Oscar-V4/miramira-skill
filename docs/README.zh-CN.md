# MiraMira

<p align="center">
  <a href="../README.md">한국어</a> |
  <a href="README.en.md">English</a> |
  <b>简体中文</b>
</p>

**MiraMira 是一个通过苏格拉底式提问来引出用户想法的 Agent Skill。** 🪞  
它简单到不可思议：给它一个计划，它会一次只问一个尖锐问题，并同时给出推荐回答。

- 把想法、计划、设计和产品方向转化成更清晰的问题。
- 沿着决策树一条分支一条分支推进，暴露隐藏前提和模糊点。
- 一次只问一个问题。
- 如果答案能通过本地代码库探索得到，就先探索代码库。
- 保留 Matt Pocock `grill me` 流程的追问压力，同时帮助用户看见更好的答案。

## 快速安装

把下面这段提示词复制给 Codex、Claude Code、Antigravity 或其他 Agent：

```text
请查看这个 GitHub 仓库并安装 MiraMira agent skill:
https://github.com/Oscar-V4/miramira-skill

请检测你当前运行的 agent 环境。
- 如果是 Codex，请安装到 ~/.codex/skills/miramira。
- 如果是 Claude Code，请安装到 ~/.claude/skills/miramira。
- 如果是其他 agent，请确认它是否支持基于 SKILL.md 的 skill 文件夹，并安装到最接近的用户级 skill 目录。
- 如果有内置 skill installer，请优先使用；否则 clone 这个 repo，并把 skills/miramira 复制到用户 skill 目录。

安装后，请阅读 skills/miramira/SKILL.md 和 README.md，然后简短说明：
1. 什么时候应该使用 $miramira
2. 应该怎样给出计划
3. 三个适合第一次测试的提示词
```

直接安装：

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

安装后重启你的 agent 应用，然后用 `$miramira` 调用。

## 什么时候使用

| 场景 | 可以这样说 |
|---|---|
| 想让想法更清晰 | `$miramira 问我关于这个产品想法最应该先回答的问题。` |
| 想找出隐藏前提 | `$miramira 用苏格拉底式提问来审视这个计划，一次一个问题。` |
| 设计感觉模糊 | `$miramira 从这个架构计划里风险最大的模糊点开始问。` |
| 一直拖着不做决定 | `$miramira 用下一个问题和推荐答案来比较这些选项。` |
| 想收紧 PRD | `$miramira 围绕用户价值 grill 这个功能计划。` |

## Skill 全文

标准安装只复制 `skills/miramira`。README 变长不会让已安装的 skill 变重。运行时真正的 skill 表面是 `skills/miramira/SKILL.md`。

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

If a question can be answered by exploring the codebase, explore the codebase instead.
```

</details>
