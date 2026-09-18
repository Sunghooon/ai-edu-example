# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 소프트웨어 개발 정보

이 소프트웨어 개발은 다음의 항목을 이용해서 개발한다.

- Python 3.12
- 코드 테스트는 unittest를 활용
- 순환복잡도, 함수라인수 등 측정 지표는 오픈소스 도구를 이용한다.

## 프로젝트 개발 정책

### 개발 생명 주기

- 이 프로젝트는 **반드시** 분석, 설계, 구현, 테스트의 순서로 개발을 진행한다.
- 각 단계가 완료되었을 때, 지정된 템플릿을 이용한 산출물이 생성되어야 한다.

### 분석 지침

- 요구사항 분석 단계 수행은 requirements-analysis 서브에이전트가 담당한다.

### 아키텍처 설계 지침

- 아키텍처 설계 단계 수행은 architecture-designer 서브에이전트가 담당한다.

### 구현 지침

- 구현 단계 수행은 coding 서브에이전트가 담당한다. 
- TDD 방식으로 진행하고, TDD 스킬을 사용해야 한다.
- 다음의 품질 지표를 **반드시** 준수해야 한다. 
    - 함수 라인수는 순수코드라인 50라인 이하여야 한다.
    - 함수 순환복잡도는 10 이하여야 한다.
    - 중복 코드는 7라인까지 허용한다.
    - 주석은 Doxygen 방식으로 작성하며, 20% 이상 작성해야 한다.
- 함수명, 변수명은 3글자 이상 사용하고, 낙타 표기법을 활용한다.

### 단위 테스트 지침

- 단위 테스트는 TDD 로 대체한다.
- 단위 테스트는 Branch 커버리지 100%를 달성해야 한다. 
- 테스트 성공률은 100%여야 한다.

### 통합 테스트 지침

- 통합 테스트는 integration-tester가 수행한다.
- 테스트 성공률은 100% 여야 한다.

### 시스템 테스트 지침

- 시스템 테스트는 sw-system-tester가 수행한다.
- 테스트 성공률은 100%여야 한다.

## Git 브랜치 정책

- `main`은 보호 브랜치다. `main`에 직접 커밋/푸시하지 않고, 모든 변경은 브랜치를 만들어 Pull Request로 병합한다.
- 브랜치 이름은 목적을 접두사로 표기한다: `feature/<설명>`(기능), `fix/<설명>`(버그 수정), `chore/<설명>`(잡무/설정), `docs/<설명>`(문서).
- PR을 열거나 갱신하면(`opened`/`synchronize`/`reopened`) `.github/workflows/ci.yml`의 CI 워크플로가 자동 실행되어 지속적 통합/지속적 테스트를 수행한다: lint(flake8), 순환복잡도 게이트(xenon, 함수당 10 이하), `unittest` 전체 실행과 Branch 커버리지 100% 목표 확인.
- CI 상태 체크(`Lint, complexity, unit tests`)가 통과해야만 `main`으로 병합할 수 있도록 GitHub 저장소 설정(Settings → Branches → Branch protection rules)에서 `main`에 대해 다음을 적용한다: "Require a pull request before merging", "Require status checks to pass before merging"(위 체크 선택), "Require branches to be up to date before merging". 이 설정은 GitHub 저장소 관리 권한이 필요해 이 저장소에서 직접 적용하지 못했으므로, 저장소 관리자가 한 번 적용해야 한다.
- 병합 방식은 Squash merge를 기본으로 하고, 병합 후 브랜치를 삭제한다(히스토리를 깔끔하게 유지).
- `main`에 대한 force-push는 하지 않는다.

## OEM-A 차일드락 제어 SW 프로젝트

- 현재 개발 대상은 `OEM_Sample/OEM-SWR-001_OEM SW 요구사항 사양서.docx`(가상 OEM-A, 교육용 시나리오, 저작권 Synetics)를 고객 요구사양서로 하는 후석 좌/우 전자식 차일드락 제어 SW다. 실행환경은 Python 3.12 PC/SIL + Web 시뮬레이터이며, HIL/실차/ECU/HW/HARA/공식 인증은 범위 밖이다.
- **요구사항 ID**: `requirements-analysis` 스킬의 기본 ID 체계(`REQ-SW-Fnnn`/`REQ-SW-Nnnn`) 대신, OEM 문서 9절 추적성표가 이미 예고한 **`SWR-nnn`**(예: OEM-SR-001 → SWR-007/008)을 그대로 사용한다. 다른 스킬 문서에 등장하는 `REQ-SW-*`/`REQ-*` 표기는 이 프로젝트에서는 `SWR-nnn`으로 대체해서 읽는다.
  - OEM 문서의 추적성표는 SWR-001~021 중 **SWR-019를 어느 OEM 요구사항에도 매핑하지 않았다**. 요구사항 분석 단계에서 이 공백을 확인하고 보고해야 한다(임의로 채우지 않는다).
- **Phase 계획**(각 phase = 브랜치 1개 + PR 1개, 사용자 리뷰·승인 후 main에 squash merge):
  1. **안전 판정 코어** — 전체 요구사항 분석(G1, BL-SWR-1.0)과 전체 아키텍처(G2, BL-SWA/SWD-1.0)를 이 phase에서 먼저 확정한 뒤, 그 아키텍처 하에서 SWR-*(OEM-SR-001~004: 충돌우선해제/접근위험잠금/입력유효성·degraded/센서고장) 상세설계·구현(TDD)·통합시험까지 진행.
  2. **운전자 명령/자동잠금** — OEM-FR-001~003 상세설계·구현·통합시험.
  3. **강제조건/시동연동** — OEM-FR-005~007 상세설계·구현·통합시험.
  4. **표시·비기능** — OEM-FR-004, OEM-NFR-001(결정론)·002(이력/개인정보) 상세설계·구현·통합시험 + 전체 결정론 회귀 확인.
  5. **시스템 검증·인도** — `sw-system-tester`로 전체 OEM 요구사항 기준 시스템 테스트(G4, BL-VER-1.0), G1~G4 인도 증거 정리.
  - Phase 1 이후(2~4)는 요구사항/아키텍처를 다시 만들지 않고 해당 슬라이스의 상세설계~테스트만 반복한다.
