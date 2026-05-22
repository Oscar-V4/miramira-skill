# MiraMira

<p align="center">
  <a href="../README.md">한국어</a> |
  <b>English</b> |
  <a href="README.zh-CN.md">简体中文</a>
</p>

**MiraMira is a mirror-like agent skill that grills a plan one question at a time.**  
It is almost aggressively simple: give it a plan, and it reflects the next important question back to you with a recommended answer.

- Compresses plans, designs, product direction, and technical choices into sharper questions.
- Walks the decision tree one branch at a time.
- Asks only one question at a time.
- Explores the codebase first when the answer can be found locally.
- Reinterprets Matt Pocock's `grill me` flow through a mirror concept.

## Quick Install

Paste this prompt into Codex, Claude Code, Antigravity, or another agent:

```text
Please inspect this GitHub repo and install the MiraMira agent skill:
https://github.com/Oscar-V4/miramira-skill

Detect the agent environment you are running in.
- If this is Codex, install it into ~/.codex/skills/miramira.
- If this is Claude Code, install it into ~/.claude/skills/miramira.
- If this is another agent, check whether it supports SKILL.md-based skill folders and install it in the closest user-level skill location.
- Use a built-in skill installer if available; otherwise clone the repo and copy skills/miramira into the user skill directory.

After installation, read skills/miramira/SKILL.md and README.md, then briefly explain:
1. when I should use $miramira
2. how I should present a plan
3. three starter prompts to test it
```

Direct install:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

Restart your agent app after installation, then invoke `$miramira`.

## When To Use It

| Situation | Say this |
|---|---|
| You want to test whether an idea holds | `$miramira Grill this product idea one question at a time.` |
| A design feels vague | `$miramira Start with the riskiest ambiguity in this architecture plan.` |
| You are delaying a decision | `$miramira Compare these options through the next question and recommended answer.` |
| You are tightening a PRD | `$miramira Grill this feature plan around user value.` |
| You want a pre-implementation check | `$miramira Ask the one question I should answer before implementing this.` |

## Full Skill Text

Standard installs copy only `skills/miramira`. A long README does not make the installed skill heavier. The runtime skill surface is `skills/miramira/SKILL.md`.

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
