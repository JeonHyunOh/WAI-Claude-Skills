# Intent Engineering Skills for Claude Code

[한국어](#한국어) | English

---

## English

Claude Code skills that combine **Roboco's Intent Engineering** and **Andrej Karpathy's LLM coding guidelines** into a practical framework.

### The Problem

LLMs fail in predictable ways:
- Run with hidden assumptions without surfacing them
- Overcomplicate code with speculative abstractions
- Touch code they shouldn't when editing
- Execute tasks without clear success criteria

### The Solution

Two complementary frameworks, combined:

| Framework | What it does |
|-----------|-------------|
| **Intent Engineering** (Roboco) | Structures *what humans define* — Why/What/Not before any implementation |
| **Karpathy Guidelines** | Structures *how the LLM behaves* — during execution |

Together: humans set the intent boundary, the LLM executes within it.

### Skills

#### `/intent-init` — New Projects

For starting from scratch. Runs an intent interview, then generates `INTENT.md` + `CLAUDE.md`.

```
아이디어 → 의도 인터뷰 (Why/What/Not) → INTENT.md + CLAUDE.md
```

#### `/intent-apply` — Existing Projects

For projects already in progress. Analyzes the codebase, retroactively builds the intent document, and wires in the combined framework.

```
코드베이스 분석 → 역산 인터뷰 → INTENT.md + CLAUDE.md 생성/병합
```

### Install

Copy each skill into your global Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/intent-init ~/.claude/skills/intent-apply

curl -o ~/.claude/skills/intent-init/SKILL.md \
  https://raw.githubusercontent.com/JeonHyunOh/WAI-Claude-Skills/main/skills/intent-init/SKILL.md

curl -o ~/.claude/skills/intent-apply/SKILL.md \
  https://raw.githubusercontent.com/JeonHyunOh/WAI-Claude-Skills/main/skills/intent-apply/SKILL.md
```

Then in any Claude Code session:

```
/intent-init    ← new project
/intent-apply   ← existing project
```

### What Gets Created

**`INTENT.md`** — the living intent document:
```markdown
## Why
[누가, 어떤 고통을, 왜 지금]

## What
- [ ] [결과 — 기능이 아닌 사용자가 할 수 있게 되는 것]
성공 기준: [검증 방법]

## Not
- [절대 하지 않을 것]
- [AI에게 맡기지 않을 결정]

## Learnings
[날짜별 누적]
```

**`CLAUDE.md`** — the LLM behavior contract:
- Karpathy's 4 principles (Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution)
- Intent document linkage (every task maps to Why/What, never violates Not)
- Per-task execution template

### Per-Task Template

Before every task:
```
What: [무엇이 되면 성공인가]
Not:  [이번 작업에서 건드리지 않을 것]
성공 기준: [어떻게 검증할 것인가]
```

### Credits

- [Andrej Karpathy](https://x.com/karpathy/status/2015883857489522876) — LLM coding pitfalls that inspired the guidelines
- [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) — CLAUDE.md distillation
- [Roboco Intent Engineering](https://intent.roboco.io/) — Why/What/Not framework

---

## 한국어

**로보코 의도공학**과 **Andrej Karpathy의 LLM 코딩 가이드라인**을 결합한 Claude Code 스킬입니다.

### 두 프레임워크의 접목

| 레이어 | 프레임워크 | 역할 |
|--------|-----------|------|
| 인간이 정의하는 레이어 | 의도공학 (Why/What/Not) | 경계를 긋는다 |
| LLM이 실행하는 레이어 | Karpathy 4원칙 | 경계 안에서 루프를 돈다 |

### 핵심 원칙

**의도공학에서:**
- `Why` — 왜 만드는가 (문제·목표)
- `What` — 무엇이 되면 성공인가 (결과, How 없이)
- `Not` — 절대 하지 않을 것 (AI가 넘으면 안 되는 선)
- `Learnings` — 배운 것 누적

**Karpathy에서:**
1. 코딩 전에 생각하기 — 가정을 숨기지 말고 드러낼 것
2. 단순함 우선 — 요청받은 것만큼만 구현
3. 외과적 수정 — 필요한 것만 건드릴 것
4. 목표 기반 실행 — 성공 기준으로 루프를 돌 것

### 설치

```bash
mkdir -p ~/.claude/skills/intent-init ~/.claude/skills/intent-apply

curl -o ~/.claude/skills/intent-init/SKILL.md \
  https://raw.githubusercontent.com/JeonHyunOh/WAI-Claude-Skills/main/skills/intent-init/SKILL.md

curl -o ~/.claude/skills/intent-apply/SKILL.md \
  https://raw.githubusercontent.com/JeonHyunOh/WAI-Claude-Skills/main/skills/intent-apply/SKILL.md
```

### 사용법

```
/intent-init    ← 새 프로젝트 (기획부터 시작)
/intent-apply   ← 기존 프로젝트 (프레임워크 적용)
```

### License

MIT
