# MiraMira

<p align="center">
  <img src="../assets/miramira-logo.png" alt="MiraMira magic mirror logo" width="240">
</p>

<p align="center">
  <a href="../README.md">한국어</a> |
  <b>English</b> |
  <a href="README.zh-CN.md">简体中文</a>
</p>

**"He who asks a question is a fool for five minutes; he who does not remains a fool forever"**

**"The one who asks may be a fool for five minutes, but the one who does not ask remains a fool forever" - Chinese proverb**

AI agents are powerful. But even the strongest agent struggles when it cannot clearly understand the context, background, taste, and constraints behind a user's idea. MiraMira is a methodology for breaking down that communication barrier between AI and user.

Through questions, MIRAMIRA draws out:
- vague ideas into clear purpose and criteria,
- scattered preferences into a consistent direction,
- ambiguous requests into specs an agent can implement.
- If the answer can be found through codebase exploration, it explores first.
- It asks relentlessly until shared understanding is reached.

## Quick Install

Paste the prompt below directly into Codex, Claude Code, Antigravity, or another agent.

```text
Please inspect this GitHub repo and install the MiraMira agent skill:
https://github.com/Oscar-V4/miramira-skill

Detect the agent environment you are running in and install it.
- If this is Codex, install it into ~/.codex/skills/miramira.
- If this is Claude Code, install it into ~/.claude/skills/miramira.
- If this is another agent, check whether it supports SKILL.md-based skill folders and install it in the closest user-level skill location.
- Use a dedicated installer if one is available; otherwise clone the repo and copy the skills/miramira folder into the user skill directory.

After installation, read skills/miramira/SKILL.md and README.md, then explain how to invoke the skill in this environment and give a "skill teardown commentary."
```

Direct install:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

Restart your agent app after installation, then invoke `$miramira`.

## Full Skill Text

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

## Structure

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
