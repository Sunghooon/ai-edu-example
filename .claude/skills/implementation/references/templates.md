# 구현 단계 표준 템플릿 참조

이 문서는 `implementation` 스킬이 사용하는 저장소 표준 산출물 템플릿의 위치와 사용법을 정리한다. 전체 등록 정보(템플릿 ID, 적용 산출물, 실제 파일 위치)는 `WP_Templates/PRC-TPL-001_표준 산출물 양식 등록부.xlsx`에 있다.

## 적용 템플릿

| 템플릿 ID | 용도 | 파일 위치 | 형식 |
|---|---|---|---|
| TPL-SWE4-001 | SW 단위시험 명세서 | `WP_Templates/Engineering/SoftwareUnitVerification/TPL-SWE4-001_SW 단위시험 명세서 템플릿.xlsx` | XLSX |
| TPL-SWE4-002 | SW 단위시험 결과서 | `WP_Templates/Engineering/SoftwareUnitVerification/TPL-SWE4-002_SW 단위시험 결과서 템플릿.xlsx` | XLSX |
| TPL-SBOM-001 | Python 의존성 SBOM/FOSS 라이선스 목록 | `WP_Templates/Engineering/SoftwareDetailedDesignAndUnitConstruction/TPL-SBOM-001_Python 의존성 SBOM FOSS 라이선스 목록 템플릿.xlsx` | XLSX |
| TPL-REV-001 | 단계별 인스펙션 결과(코드 리뷰 기록이 필요할 때 선택적으로 사용) | `WP_Templates/Engineering/QualityReview/TPL-REV-001_단계별 인스펙션 결과 템플릿.xlsx` | XLSX |
| TPL-TRC-001 | 양방향 요구사항 추적 매트릭스(코드/테스트까지 연계) | `WP_Templates/Engineering/Traceability/TPL-TRC-001_양방향 요구사항 추적 매트릭스 템플릿.xlsx` | XLSX |

`tdd` 스킬로 작성한 테스트와 그 결과는 TPL-SWE4-001/002에 정리한다. TPL-SBOM-001은 `detailed-design` 단계에서 계획한 의존성과 실제 구현에서 반영한 의존성이 다를 경우 갱신한다. TPL-REV-001은 사용자가 코드 리뷰/인스펙션 기록을 요청할 때만 사용한다. 이 목록에 없는 산출물이 필요하면 등록부(`PRC-TPL-001`)에서 해당 항목을 먼저 확인한다.

## 사용 규칙 (`WP_Templates/Engineering/README.md` 기준)

- **XLSX**: 기존 시트/열 구조를 그대로 유지한다. 상단의 안내/예시 행은 건드리지 않고, 10행부터 실제 데이터를 추가한다.
- 새 산출물을 만들 때는 템플릿 파일을 복사한 뒤 파일명을 `<산출물 ID>_<산출물명>.<확장자>` 형식으로 바꾸고 프로젝트/베이스라인 정보를 채운다. 템플릿 원본 파일 자체는 수정하지 않는다.

## 파일 형식별 처리 방법 (이 환경의 도구 제약)

- **XLSX**: 바이너리를 직접 편집하지 않는다. 단위시험 명세서/결과서, SBOM 작성이 필요하면 스프레드시트 처리 전용 스킬(xlsx)을 사용한다.

## 라이선스 주의

`WP_Templates/Engineering/README.md`에 따르면 이 템플릿과 관련 교육 자료의 저작권은 Synetics에 있으며, 교육 과정 밖 배포·공개·상업적 이용은 사전 서면 승인이 필요하다. 이 템플릿을 프로젝트 외부로 배포하지 않는다.
