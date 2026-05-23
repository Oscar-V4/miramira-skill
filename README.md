# MiraMira

<p align="center">
  <img src="assets/miramira-symbol.svg" alt="MiraMira mirror symbol" width="420">
</p>

<p align="center">
  <b>한국어</b> |
  <a href="docs/README.en.md">English</a> |
  <a href="docs/README.zh-CN.md">简体中文</a>
</p>

**MiraMira는 소크라테스식 질문으로 사용자의 아이디어를 효과적으로 이끌어내는 에이전트 스킬입니다.**  
믿을 수 없을 만큼 단순합니다. 계획을 말하면, MiraMira는 한 번에 하나의 날카로운 질문을 던지고, 그 질문에 대한 추천 답까지 함께 제시합니다.

- 아이디어, 계획, 설계, 제품 방향을 더 선명한 질문으로 바꿉니다.
- 결정 트리의 가지를 하나씩 따라가며 숨은 전제와 모호함을 드러냅니다.
- 질문은 한 번에 하나만 던집니다.
- 답이 코드베이스 탐색으로 해결되면 먼저 탐색합니다.
- Matt Pocock의 `grill me` 흐름처럼 집요하게 묻되, 사용자가 스스로 더 나은 답을 보게 만듭니다.

## 빠른 설치

아래 프롬프트를 Codex, Claude Code, Antigravity 같은 에이전트에게 그대로 붙여넣으면 됩니다.

```text
이 GitHub repo를 확인해서 MiraMira 에이전트 스킬을 설치해줘:
https://github.com/Oscar-V4/miramira-skill

현재 네가 실행 중인 에이전트 환경을 감지해서 설치해.
- Codex 계열이면 ~/.codex/skills/miramira 에 설치해.
- Claude Code 계열이면 ~/.claude/skills/miramira 에 설치해.
- 다른 에이전트면 SKILL.md 기반 스킬 폴더를 지원하는지 확인하고, 가장 가까운 사용자 스킬 위치에 설치해.
- 전용 설치기가 있으면 사용하고, 없으면 repo를 clone한 뒤 skills/miramira 폴더를 사용자 스킬 디렉터리에 복사해.

설치 후 skills/miramira/SKILL.md와 README.md를 읽고,
1. 언제 $miramira를 쓰면 좋은지
2. 어떤 식으로 계획을 던지면 좋은지
3. 첫 테스트 프롬프트 3개
를 짧게 알려줘.
```

직접 설치:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Oscar-V4/miramira-skill \
  --path skills/miramira
```

설치 후 에이전트 앱을 재시작하면 `$miramira`로 호출할 수 있습니다.

## 언제 쓰면 좋은가

| 상황 | 이렇게 말하면 됩니다 |
|---|---|
| 아이디어를 더 명확하게 만들고 싶을 때 | `$miramira 이 제품 아이디어에서 가장 먼저 답해야 할 질문을 던져줘.` |
| 계획의 숨은 전제를 찾고 싶을 때 | `$miramira 이 계획을 소크라테스식으로 질문해줘. 한 번에 하나씩.` |
| 설계가 애매하게 느껴질 때 | `$miramira 이 아키텍처 계획에서 가장 위험한 모호함부터 물어봐줘.` |
| 결정을 미루고 있을 때 | `$miramira 이 선택지를 비교할 수 있게 다음 질문과 추천 답을 줘.` |
| PRD나 기능 범위를 다듬을 때 | `$miramira 이 기능 계획을 사용자 가치 기준으로 grill해줘.` |

## 스킬 전문

표준 설치 명령은 `skills/miramira` 폴더만 설치합니다. 루트 README가 길어져도 설치된 스킬이 자동으로 더 무거워지지는 않습니다. 에이전트가 실제로 스킬로 읽는 핵심 파일은 `skills/miramira/SKILL.md`입니다.

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
