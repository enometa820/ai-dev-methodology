# Superpowers — AI 에이전트 스킬 주입 프레임워크

> GitHub: https://github.com/obra/superpowers
> 개발자: Jesse Vincent, Prime Radiant
> 라이선스: MIT
> 설치 상태: **전역 설치 완료** (현재 세션에서 활성화 중)

---

## 한 줄 요약

14개 스킬을 AI 에이전트에 주입해 TDD, 체계적 디버깅, 증거 기반 검증 등
소프트웨어 공학의 고전적 방법론을 AI 개발에 강제 적용하는 프레임워크.

---

## 4대 핵심 철학

| 원칙 | 설명 |
|------|------|
| **TDD 절대주의** | 코드보다 테스트 먼저. RED-GREEN-REFACTOR. 테스트 없는 코드는 삭제 후 재작성. |
| **체계적 방법론** | "감"이 아니라 "절차"로 문제를 해결한다. |
| **복잡성 축소** | YAGNI + DRY. 단순함이 최우선. |
| **증거 기반 검증** | 실행하고 확인해라. "아마 될 거야"는 허용되지 않는다. |

> 증거 기반 검증 원칙은 **실제 24건의 실패 사례**에서 도출된 교훈.

---

## 14개 스킬 체계

### 협업 및 설계
| 스킬 | 역할 |
|------|------|
| brainstorming | 설계 승인 전 코드 작성 절대 금지. 9단계 프로세스. |
| writing-plans | 2~5분 단위 세부 작업으로 분해. 플레이스홀더 금지. |
| executing-plans | 블로커 발생 시 즉시 중단, 질문 강제. |
| subagent-driven-development | 작업별 전용 서브에이전트. 2단계 리뷰 필수. |
| dispatching-parallel-agents | 독립 작업을 병렬 에이전트로 동시 처리. |

### 품질 보증
| 스킬 | 역할 |
|------|------|
| test-driven-development | RED-GREEN-REFACTOR 절대 규칙. "테스트 후 작성"은 TDD 아님. |
| systematic-debugging | 근본 원인 없는 수정 금지. 3회 실패 시 아키텍처 재검토. |
| verification-before-completion | "should", "probably" → 경고 신호. 완료 전 반드시 실행 확인. |
| requesting-code-review | Critical → Important → Minor 우선순위 처리. |
| receiving-code-review | "맞습니다!" 수동적 동의 금지. 기술적 검증 후 대응. |

### 인프라
| 스킬 | 역할 |
|------|------|
| using-git-worktrees | 격리된 작업 공간. .gitignore 검증, 테스트 베이스라인 자동화. |
| finishing-a-development-branch | 완료 후 4가지 옵션 제시 + 워크트리 정리. |

### 메타
| 스킬 | 역할 |
|------|------|
| using-superpowers | 스킬 시스템 사용법. "스킬이 있으면 반드시 사용해야 한다." |
| writing-skills | 스킬 자체에도 TDD 적용. |

---

## 전체 워크플로우

```
[1] brainstorming
    사용자 의도 → 명확화 질문 → 접근법 제안 → 섹션별 승인
    산출물: docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md
        ↓
[2] using-git-worktrees
    워크트리 생성 → 환경 셋업 → 테스트 베이스라인 확인
        ↓
[3] writing-plans
    2~5분 단위 작업 분해 → 자체 리뷰 → 사용자 확인
    산출물: docs/superpowers/plans/YYYY-MM-DD-<feature>.md
        ↓
[4] subagent-driven-development / executing-plans
    작업별 서브에이전트 → TDD 사이클 → 2단계 리뷰
        ↓
[5] requesting-code-review
    전체 구현 종합 리뷰
        ↓
[6] finishing-a-development-branch
    테스트 통과 → 머지/PR/유지/폐기 선택 → 워크트리 정리
```

---

## 설치 방법

```bash
# Claude Code (현재 설치됨)
/plugin install superpowers@claude-plugins-official

# 업데이트
/plugin update superpowers

# Gemini CLI
gemini extensions install https://github.com/obra/superpowers

# Cursor
/add-plugin superpowers
```

### 지원 플랫폼
Claude Code, Cursor, GitHub Copilot CLI, Gemini CLI, Codex

---

## 강점

| 강점 | 설명 |
|------|------|
| 구조적 완결성 | 아이디어 → 브랜치 마무리까지 빈틈 없이 커버 |
| 자기 합리화 방지 | AI가 흔히 쓰는 변명을 사전에 차단하는 장치 내장 |
| 멀티 플랫폼 | Claude, Cursor, Gemini, Copilot 모두 지원 |
| 모듈식 구조 | 14개 스킬 독립 + 유기적 연결 |
| 스킬 자체에 TDD | 프로세스 문서의 품질도 검증 |
| 증거 기반 문화 | 24건 실패 사례에서 나온 실용적 규칙 |

---

## 약점

| 약점 | 설명 |
|------|------|
| 높은 오버헤드 | 소규모 수정에도 전체 프로세스 적용 |
| AI 에이전트 의존성 | 에이전트 없이는 활용 불가 |
| 서브에이전트 비용 | 작업당 별도 세션 → API 비용 증가 |
| 경직성 | 타협 불가 규칙 다수 → 프로토타이핑에 부적합 |
| 문서 산출물 누적 | 장기 프로젝트에서 문서 관리 부담 증가 |

---

## 학술적 의의
- **AI 에이전트 거버넌스**: 에이전트의 자기 합리화 패턴을 사전 차단하는 "합리화 테이블" 접근
- **프로세스 문서의 TDD**: 프로세스 자체를 테스트 가능한 단위로 취급
- **인간-AI 협업 패턴**: "한 번에 하나의 질문", "객관식 선호" 등의 설계가 HAI 연구 사례

---

## 적합한 사용 상황
- 품질 중심의 전문적 개발 환경
- TDD를 강제하고 싶은 팀/개인
- 체계적인 코드 리뷰 프로세스가 필요한 프로젝트
- AI 에이전트의 독단적 행동을 통제하고 싶을 때
