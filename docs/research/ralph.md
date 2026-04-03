# Ralph — 자율 AI 에이전트 루프

> GitHub: https://github.com/snarktank/ralph
> 원작자: Geoffrey Huntley / snarktank
> 라이선스: MIT | Stars: 14,276 | Forks: 1,454
> 생성일: 2026년 1월 7일

---

## 한 줄 요약

PRD(기획서)를 주면 AI가 혼자서 반복 실행해 완성하는 자율 루프 시스템.
가장 순수한 형태는 단 한 줄:

```bash
while :; do cat PROMPT.md | claude-code; done
```

---

## 핵심 철학

### "Each Iteration = Fresh Context" (매 반복 = 새로운 컨텍스트)
- 매 반복마다 **완전히 새로운 AI 인스턴스** 생성
- 컨텍스트 윈도우 한계를 근본적으로 극복
- 이전 기억은 Git 히스토리, progress.txt, prd.json으로만 전달

### 생성(Generation) vs 역압(Backpressure)
- 코드 생산은 이제 저렴함 → 스펙과 기술 표준으로 출력을 통제
- 생성이 쉬워진 만큼 **테스트와 검증이 핵심**

### AI는 도구가 아니라 기술(Skill)
> "악기처럼 연습이 필요하다. 도구 탓 전에 프롬프트 전략을 점검하라."

---

## 워크플로우

```
1. PRD 작성
   /skill prd → 명확화 질문 답변 → tasks/prd-[feature].md 생성

2. Ralph 형식 변환
   /skill ralph → prd.json 생성 (유저 스토리 JSON 배열)

3. 루프 실행
   ./ralph.sh --tool claude 10
   → 모든 스토리 passes=true 될 때까지 반복
```

### 매 반복에서 AI가 하는 일
1. feature 브랜치 생성/체크아웃
2. passes=false인 최우선 스토리 **하나** 선택
3. 구현
4. typecheck + lint + test 실행
5. 통과 시 커밋 → passes=true 업데이트
6. progress.txt에 학습 내용 추가
7. 전체 완료 시 `<promise>COMPLETE</promise>` → 루프 종료

---

## 파일 구조

| 파일 | 역할 |
|------|------|
| `ralph.sh` | 핵심 Bash 루프 스크립트 |
| `prd.json` | 유저 스토리 + passes 상태 |
| `progress.txt` | Append-only 학습 기록 |
| `CLAUDE.md` | Claude Code용 프롬프트 |
| `skills/prd/` | PRD 생성 스킬 |
| `skills/ralph/` | PRD → JSON 변환 스킬 |

---

## 강점

| 강점 | 설명 |
|------|------|
| 완전 자율 실행 | 사람 개입 없이 PRD 전체 완료 |
| 컨텍스트 한계 극복 | 매 반복이 새 컨텍스트 → 대규모 프로젝트도 처리 |
| 누적 학습 | progress.txt → AGENTS.md로 패턴 축적 |
| 비용 효율 | "$50K 규모 MVP를 $297에 완성" (원작자 사례) |
| 도구 불가지론 | Amp + Claude Code 모두 지원 |

---

## 약점

| 약점 | 설명 |
|------|------|
| 그린필드 전용 | 레거시 코드베이스 부적합 (원작자 직접 언급) |
| 90% 완성도 | 마지막 10% 폴리싱은 인간 필요 |
| PRD 품질 의존 | PRD가 모호하면 결과물도 모호 |
| 테스트 인프라 필수 | 피드백 루프 없으면 깨진 코드 누적 |
| 비용 예측 불가 | 반복 횟수 × 토큰 사용량 가변적 |

---

## 설치 방법

### Claude Code 스킬로 전역 설치
```bash
cp -r skills/prd ~/.claude/skills/
cp -r skills/ralph ~/.claude/skills/
```

### Claude Code 마켓플레이스
```bash
/plugin marketplace add snarktank/ralph
```

---

## 적합한 사용 상황
- 새 프로젝트(그린필드)를 처음부터 구축할 때
- 혼자서 빠르게 MVP를 만들어야 할 때
- PRD를 명확하게 작성할 수 있는 경우
- 테스트 인프라가 갖춰진 프로젝트

## 부적합한 사용 상황
- 기존 레거시 코드베이스 수정
- 시각적 UI 검증이 핵심인 프로젝트
- PRD를 명확히 정의하기 어려운 탐색적 개발
