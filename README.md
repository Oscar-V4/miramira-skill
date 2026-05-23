# MIRAMIRA

<p align="center">
  <img src="assets/miramira-logo.png" alt="MiraMira magic mirror logo" width="240">
</p>

<p align="center">
  <b>한국어</b> |
  <a href="docs/README.en.md">English</a> |
  <a href="docs/README.zh-CN.md">简体中文</a>
</p>

**"He who asks a question is a fool for five minutes; he who does not remains a fool forever"**

**"질문하는 사람은 5분 동안 바보일 수 있지만, 질문하지 않는 사람은 평생 바보로 남는다" -중국 속담中**

AI 에이전트는 강력합니다. 하지만 아무리 뛰어난 에이전트도 유저 아이디어의 맥락, 배경, 취향, 제약을 명확히 파악하지 못한다면 제대로 일하기 어렵습니다. MiraMira는 이 AI-User 간 소통의 장벽을 허무는 방법론입니다.

MIRAMIRA는 질문을 통해
- 막연한 아이디어를 명확한 목적과 기준으로,
- 흩어진 취향을 일관된 방향성으로,
- 불분명한 요청을 에이전트가 구현할 수 있는 스펙으로 끌어냅니다.
- 답이 코드베이스 탐색으로 해결될 수 있다면 미리 탐색을 진행합니다.
- shared understanding에 도달할 때까지 집요하게 묻습니다.


## 빠른 설치

아래 프롬프트를 Codex, Claude Code, Antigravity 같은 에이전트에게 그대로 붙여넣으세요.

```text
이 GitHub repo를 확인해서 MiraMira 에이전트 스킬을 설치해줘:
https://github.com/Oscar-V4/miramira-skill

현재 네가 실행 중인 에이전트 환경을 감지해서 설치해.
- Codex 계열이면 ~/.codex/skills/miramira 에 설치해.
- Claude Code 계열이면 ~/.claude/skills/miramira 에 설치해.
- 다른 에이전트면 SKILL.md 기반 스킬 폴더를 지원하는지 확인하고, 가장 가까운 사용자 스킬 위치에 설치해.
- 전용 설치기가 있으면 사용하고, 없으면 repo를 clone한 뒤 skills/miramira 폴더를 사용자 스킬 디렉터리에 복사해.

설치 후 skills/miramira/SKILL.md와 README.md를 읽고, 이 환경에서 스킬을 어떻게 발동시킬 수 있는지와 함께 '스킬 해체 해설'을 진행해줘.
```

직접 설치:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

설치 후 에이전트 앱을 재시작하면 `$miramira`로 호출할 수 있습니다.

## 스킬 전문

<details>
<summary><code>skills/miramira/SKILL.md</code> 전문 보기</summary>

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

## 구조

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
