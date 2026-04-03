# BMAD Method — AI 팀 시뮬레이션 개발 프레임워크

> GitHub: https://github.com/bmad-code-org/BMAD-METHOD
> 개발자: Brian Madison (bmad-code-org)
> 라이선스: MIT (100% 무료) | Stars: 43,400+ | Forks: 5,200+
> 현재 버전: v6.2.2 | 공식 문서: docs.bmad-method.org

---

## 한 줄 요약

PM, 아키텍트, 개발자, UX 디자이너 역할의 AI 에이전트 7명이 협업하는
완전한 소프트웨어 개발 생명주기 프레임워크. 4개 중 GitHub Stars 압도적 1위(43K+).

---

## 핵심 철학

> "Traditional AI tools do the thinking for you, producing average results.
> BMad agents guide you through a structured process to bring out **your best thinking**."

AI를 **자율 실행자가 아닌 전문 협업자**로 위치시킴.
인간이 주체적으로 의사결정하되, AI 에이전트가 각 전문 영역에서 체계적 질문과 검증을 수행.

---

## 7개 에이전트

| 에이전트 | 이름 | 역할 |
|---------|------|------|
| Analyst | Mary | 브레인스토밍, 시장/도메인 리서치, 제품 브리프 |
| Product Manager | John | PRD 작성, 에픽/스토리 관리 |
| Architect | Winston | 시스템 아키텍처 설계, 구현 준비 검증 |
| Developer | Amelia | 스프린트 계획, 구현, 코드 리뷰, QA |
| UX Designer | Sally | UX 설계 아티팩트 생성 |
| Tech Writer | Paige | 기술 문서 작성, 편집 |
| BMad Master | - | 다중 에이전트 오케스트레이션 |

---

## 4단계 개발 생명주기

```
Phase 1: Analysis (선택)
  Mary가 담당. 브레인스토밍, 리서치, 제품 브리프 작성
        ↓
Phase 2: Planning (필수)
  John + Sally가 담당. PRD 작성, UX 설계 아티팩트
        ↓
Phase 3: Solutioning (복잡한 프로젝트 필수)
  Winston이 담당. 시스템 아키텍처, 에픽/스토리, 구현 준비 검증
        ↓
Phase 4: Implementation (반복)
  Amelia가 담당. 스프린트 → 스토리 → 구현 → 리뷰 → 회고
```

---

## 규모별 적응 트랙

| 트랙 | 대상 | 특징 |
|------|------|------|
| Quick Flow | 버그 수정, 단순 기능 | Phase 1-3 통합 (`bmad-quick-dev`) |
| BMad Method | 제품, 복잡한 기능 | 전체 4단계 |
| Enterprise | 컴플라이언스, 대규모 | 4단계 + 강화된 검증 |

---

## 특수 기능

### Party Mode (다중 에이전트 협업)
한 대화에서 PM, 아키텍트, 개발자가 동시에 참여해 토론.
실제 팀 미팅처럼 에이전트들이 서로 동의/반대/보완.

### 적대적 리뷰 (Adversarial Review)
"문제가 없다"는 답변 금지. 리뷰어가 반드시 문제를 찾아야 함.
확인 편향 방지 + 깊은 분석 유도.

### project-context.md
모든 에이전트가 참조하는 "헌법" 문서.
기술 스택, 코딩 컨벤션, 프로젝트 규칙을 명시해 에이전트 간 일관성 보장.

---

## 프로젝트 구조

```
your-project/
├── _bmad/                      # 에이전트, 워크플로우, 설정
└── _bmad-output/
    ├── planning-artifacts/
    │   ├── PRD.md
    │   ├── architecture.md
    │   └── epics/
    ├── implementation-artifacts/
    │   └── sprint-status.yaml
    └── project-context.md
```

---

## 설치 방법

```bash
# 프로젝트별 설치
npx bmad-method install

# 전역 설치 (모든 프로젝트에서 사용)
npm install -g bmad-method
```

### 호환 AI 도구
Claude, Cursor, GitHub Copilot 등 커스텀 시스템 프롬프트 지원 도구

---

## 모듈 생태계

| 모듈 | 코드 | 설명 |
|------|------|------|
| BMad Method | `bmm` | 34+ 핵심 워크플로우 (기본) |
| BMad Builder | `bmb` | 커스텀 에이전트/워크플로우 제작 |
| Test Architect | `tea` | 리스크 기반 테스트 전략 |
| Game Dev Studio | `gds` | 게임 개발 특화 (Unity, Unreal, Godot) |
| Creative Intelligence | `cis` | 혁신/디자인 사고 프레임워크 |

---

## 강점

| 강점 | 설명 |
|------|------|
| 완전한 생명주기 | 아이디어 → 배포까지 전 과정 커버 |
| 규모 적응성 | Quick Flow ~ Enterprise 자동 조절 |
| 산출물 연쇄 | PRD → 아키텍처 → 에픽 → 구현 연결 |
| 적대적 검증 | 확인 편향 방지 메커니즘 내장 |
| 무료 오픈소스 | MIT 라이선스, 페이월 없음 |
| 확장 생태계 | 5개 모듈, 커스텀 에이전트 제작 가능 |

---

## 약점

| 약점 | 설명 |
|------|------|
| 학습 곡선 | 7개 에이전트 + 30+ 워크플로우 학습 필요 |
| AI 도구 의존성 | 특정 AI 코딩 어시스턴트 필수 |
| 단일 개발자 최적화 | "1인 + AI 팀" 시나리오에 최적화 |
| 거짓 양성 리스크 | 적대적 리뷰에서 AI가 잘못된 문제 지적 가능 |
| 프로세스 오버헤드 | 단순 프로젝트에 과잉 적용 위험 |

---

## 적합한 사용 상황
- 처음부터 새 제품/서비스를 체계적으로 기획하고 싶을 때
- PM, 아키텍트, 개발자 역할이 혼재된 1인 개발 환경
- 문서화와 추적성이 중요한 프로젝트
- 여러 관점에서 의사결정 검증이 필요한 복잡한 시스템
