# enometa-report — AI 방법론 조사 프로젝트

## 프로젝트 목적

강의 과제로 시작했지만, 단순 제출에 그치지 않고 **두고두고 참고할 레퍼런스**를 만드는 것이 목표.

### 3가지 목표
1. **리포트 제출** — Google Docs 또는 PPT로 작성 후 PDF로 출력 제출
2. **노션 아카이빙** — 노션에 업로드해 지속적으로 참고
3. **실제 설치** — 4개 프레임워크를 PC에 설치하고 실습 경험을 리포트에 포함

### 리포트 방향
단순 요약 나열이 아닌 "직접 파보고 써봤다"는 열의와 태도를 어필하는 구성:
- 4개 방법론 비교 분석표
- 각 방법론의 강점/약점/적합 상황 분석
- 직접 설치 및 실습 결과 포함
- "내가 실제 프로젝트에 쓴다면?" 관점의 개인 견해

---

## 조사 대상 4개 AI 방법론

### 1. Ralph (랄프)
- GitHub: https://github.com/snarktank/ralph
- 핵심: Bash 루프 기반 자율 AI 에이전트 — PRD 작성 후 AI가 혼자 반복 실행해 완성
- 철학: "매 반복 = 새 컨텍스트" (컨텍스트 한계 극복)
- 설치 위치: `~/.claude/skills/` (Claude Code 스킬)
- 연구 완료: `docs/research/ralph.md`

### 2. BMAD Method
- GitHub: https://github.com/bmad-code-org/BMAD-METHOD
- 핵심: 7개 AI 에이전트(PM, 아키텍트, 개발자 등)가 역할 분담하는 완전한 개발 생명주기 프레임워크
- 철학: "AI가 최고의 사고를 이끌어낸다" — AI는 자율 실행자가 아닌 전문 협업자
- 설치: `npx bmad-method install` (프로젝트별) / `npm install -g bmad-method` (전역)
- GitHub Stars: 43,400+ (4개 중 가장 인기)
- 연구 완료: `docs/research/bmad.md`

### 3. Superpowers
- GitHub: https://github.com/obra/superpowers
- 핵심: 14개 스킬(TDD, 브레인스토밍, 디버깅 등)을 AI 에이전트에 주입하는 프레임워크
- 철학: TDD 절대주의 + "증거 없이 완료 없다" (24건 실패 사례에서 도출)
- 설치 상태: **전역 설치 완료** (`~/.claude/` 활성화 중)
- 연구 완료: `docs/research/superpowers.md`

### 4. MOAI ADK
- GitHub: https://github.com/modu-ai/moai-adk
- 핵심: 26개 전문 에이전트(8관리자+8전문가+3제작자+1평가자+6에이전시) + 52개 스킬, Go 단일 바이너리
- 철학: "하네스 엔지니어링" — 인간은 AI가 작동할 환경을 설계, 실행은 AI가
- 개발: 한국 팀(modu-ai) — 리포트에서 차별화 포인트로 활용 가능
- 설치: PowerShell 7.x+에서 1줄 스크립트 (전역 설치 완료)
- 연구 완료: `docs/research/moai-adk.md`

---

## 디렉토리 구조

```
enometa-report/
├── CLAUDE.md                    # 이 파일 — 프로젝트 컨텍스트
├── README.md                    # 프로젝트 개요
├── docs/
│   ├── research/
│   │   ├── ralph.md             # Ralph 심층 분석
│   │   ├── bmad.md              # BMAD 심층 분석
│   │   ├── superpowers.md       # Superpowers 심층 분석
│   │   └── moai-adk.md          # MOAI ADK 심층 분석
│   └── report/
│       ├── outline.md           # 리포트 구조
│       └── draft.md             # 리포트 초안
├── frameworks/                  # 각 프레임워크 설치/참조 파일
└── output/                      # 최종 산출물 (PDF 등)
```

---

## 작업 진행 상황

- [x] 4개 방법론 GitHub 리서치 완료
- [x] 개별 연구 문서 작성 완료
- [x] BMAD 설치 완료 (`frameworks/bmad/` + 전역)
- [x] Ralph 스킬 설치 완료 (`frameworks/ralph/` + `~/.claude/skills/`)
- [x] Superpowers 설치 완료 (`frameworks/superpowers/` + `~/.claude/` 활성화)
- [x] MOAI ADK 설치 완료 (`frameworks/moai-adk/` + 전역 바이너리)
- [x] 리포트 초안 작성 완료 (`docs/report/draft.md`)
- [ ] 노션 업로드
- [ ] PDF 출력 및 제출

---

## 모델 설정

이 프로젝트는 `opusplan` 모드 사용 권장:
- Plan 단계 (구조 설계, 분석): Opus 4.6
- 구현 단계 (문서 작성, 코드): Sonnet 4.6

```
/model opusplan
```

---

## 주요 참고 링크
- Ralph 원작자 글: https://ghuntley.com/ralph/
- BMAD 공식 문서: https://docs.bmad-method.org
- MOAI ADK 공식 문서: https://adk.mo.ai.kr
- Superpowers Discord: GitHub Issues 참조
