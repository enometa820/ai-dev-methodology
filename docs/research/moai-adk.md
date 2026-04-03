# MOAI ADK — 하네스 엔지니어링 기반 에이전틱 개발 킷

> GitHub: https://github.com/modu-ai/moai-adk
> 개발사: modu-ai (한국 팀)
> 라이선스: Apache 2.0 | Stars: 900
> 현재 버전: v2.9.1 | 공식 문서: https://adk.mo.ai.kr

---

## 한 줄 요약

"바이브 코딩의 목적은 빠른 생산성이 아니라 **코드 품질**이다."
24개 전문 에이전트 + 52개 스킬을 Go 단일 바이너리로 제공하는 Claude Code 전용 에이전틱 개발 킷.
**한국 팀이 개발** — 4개 방법론 중 유일한 국내 개발 도구.

---

## 핵심 철학: 하네스 엔지니어링 (Harness Engineering)

> "인간은 방향을 잡고, 에이전트는 실행한다."

전통적 개발에서 인간의 역할이 **코드 작성 → AI 에이전트 환경 설계**로 전환됨.
인간의 주요 업무: SPEC 문서 작성, 품질 게이트 설정, 피드백 루프 구성.

---

## 24개 전문 에이전트

| 카테고리 | 수 | 에이전트 | 역할 |
|---------|---|---------|------|
| Manager | 8 | spec, ddd, tdd, docs, quality, project, strategy, git | 워크플로우 조율, SPEC 생성, 품질 관리 |
| Expert | 8 | backend, frontend, security, devops, performance, debug, testing, refactoring | 도메인 전문 구현/분석/최적화 |
| Builder | 3 | agent, skill, plugin | 새 MoAI 컴포넌트 생성 |
| Evaluator | 1 | evaluator-active | 독립적 회의적 품질 평가 (4차원 점수) |
| Agency | 6 | planner, copywriter, designer, builder, evaluator, learner | 자기 진화형 크리에이티브 파이프라인 |

---

## 52개 스킬 — 프로그레시브 디스클로저

토큰 효율을 위한 3단계 점진적 공개:

| 레벨 | 토큰 | 로드 시점 |
|------|------|---------|
| L1 메타데이터 | ~100 | 항상 로드 |
| L2 본문 | ~5K | 트리거 매칭 시 |
| L3 번들 | 가변 | 온디맨드 |

→ 초기 토큰 소비 **67% 절감**

---

## 개발 방법론 자동 선택

프로젝트 상태를 분석해 최적 방법론 자동 적용:

| 조건 | 방법론 | 사이클 |
|------|--------|-------|
| 신규 or 테스트 커버리지 10%+ | **TDD** | RED → GREEN → REFACTOR |
| 기존 프로젝트 (커버리지 10% 미만) | **DDD** | ANALYZE → PRESERVE → IMPROVE |

---

## SPEC 기반 워크플로우

```bash
# 1. SPEC 문서 생성
/moai plan "사용자 인증 기능 추가"
# → manager-spec 에이전트가 SPEC-AUTH-001.md 생성

# 2. 구현 실행
/moai run SPEC-AUTH-001
# → manager-tdd 또는 manager-ddd가 자동 선택해 구현

# 3. 문서 동기화 및 PR 생성
/moai sync SPEC-AUTH-001
```

### 추가 명령어
```bash
/moai fix        # 버그 수정
/moai loop       # 자가 검증 루프
/moai clean      # 죽은 코드, AI Slop, 미사용 임포트 제거
/moai codemaps   # 코드베이스 아키텍처 맵 생성
/moai review     # 코드 리뷰
/moai coverage   # 테스트 커버리지 확인
```

---

## TRUST 5 프레임워크 (품질 게이트)

3단계 하네스 시스템:

| 레벨 | 사용 시점 | 내용 |
|------|---------|------|
| minimal | 단순 변경 | 빠른 검증 |
| standard | 일반 작업 | 기본 품질 체크 |
| thorough | 복잡한 SPEC | 전체 evaluator-active + TRUST 5 |

LSP 기반 품질 게이트: 컴파일 오류 0, 타입 오류 0, 린트 오류 0 요구.

---

## MX 태그 시스템

코드 내 컨텍스트 전달 어노테이션:

```typescript
// @MX:NOTE 이 함수는 멱등성이 보장되어야 함
// @MX:WARN DB 직접 접근 — 트랜잭션 주의
// @MX:ANCHOR 이 인터페이스는 변경 불가 (팬인 높음)
// @MX:TODO 페이지네이션 구현 필요
```

---

## 설치 방법

### Windows (PowerShell 7.x+)
```powershell
irm https://raw.githubusercontent.com/modu-ai/moai-adk/main/install.ps1 | iex
```

### macOS / Linux
```bash
curl -fsSL https://raw.githubusercontent.com/modu-ai/moai-adk/main/install.sh | bash
```

### 소스 빌드 (Go 1.26+)
```bash
git clone https://github.com/modu-ai/moai-adk.git
cd moai-adk && make build
```

### 프로젝트 초기화
```bash
moai init my-project  # 대화형 마법사
```

---

## 기술 스택

| 항목 | 내용 |
|------|------|
| 구현 언어 | Go (v1.26+) |
| CLI 프레임워크 | Cobra, Bubbletea |
| UI 렌더링 | Lipgloss, Glamour |
| 배포 | 크로스 플랫폼 바이너리 |
| 테스트 커버리지 | 85~100% |
| MCP 서버 | Sequential Thinking, Context7 등 |
| 지원 언어 | 16개 (Go, Python, TypeScript, Rust, Java 등) |

---

## 강점

| 강점 | 설명 |
|------|------|
| 체계적 에이전트 아키텍처 | 24개 전문 에이전트 역할 분리 |
| 품질 중심 다층 검증 | TDD/DDD + LSP + TRUST 5 + evaluator-active |
| 단일 바이너리 | 외부 의존성 없이 ~5ms 실행, 크로스 플랫폼 |
| 토큰 효율 67% | 프로그레시브 디스클로저 시스템 |
| SPEC 기반 추적성 | 계획-실행-동기화 전 과정 추적 가능 |
| 자기 확장 구조 | Builder 에이전트로 새 에이전트/스킬 생성 |
| 8개 언어 지원 UI | 한국어 포함 자동 감지 |

---

## 약점

| 약점 | 설명 |
|------|------|
| Claude Code 종속 | 다른 AI 도구(Cursor, Copilot)에서 사용 불가 |
| 높은 진입 장벽 | 24에이전트 + 52스킬 + SPEC 워크플로우 학습 필요 |
| 실험적 기능 | Agent Teams는 환경 변수 설정 필요 |
| API 비용 | 다수 에이전트 동시 호출 → 비용 상당 |
| Windows 제한 | 네이티브 cmd.exe 미지원, WSL 또는 PS7+ 필요 |
| 초기 단계 | Stars 900개 수준, 생태계 제한적 |

---

## 적합한 사용 상황
- Claude Code를 주 개발 도구로 사용하는 경우
- 품질 보증이 최우선인 중대형 프로젝트
- TDD/DDD 방법론을 체계적으로 적용하고 싶을 때
- 16개 언어 중 하나로 개발하는 경우

## 리포트 차별화 포인트
한국 팀(modu-ai)이 개발한 **국내 AI 개발 방법론**으로,
조사된 4개 방법론 중 유일하게 한국에서 탄생한 도구.
Claude Code 생태계 내에서 가장 정교한 품질 보증 시스템을 갖추고 있음.
