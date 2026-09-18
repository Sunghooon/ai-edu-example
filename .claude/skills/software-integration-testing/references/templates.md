# 소프트웨어 통합시험 표준 템플릿 참조

이 문서는 `software-integration-testing` 스킬이 사용하는 저장소 표준 산출물 템플릿의 위치와 사용법을 정리한다. 전체 등록 정보(템플릿 ID, 적용 산출물, 실제 파일 위치)는 `WP_Templates/PRC-TPL-001_표준 산출물 양식 등록부.xlsx`에 있다.

## 적용 템플릿

| 템플릿 ID | 용도 | 파일 위치 | 형식 |
|---|---|---|---|
| TPL-SWE5-001 | SW 통합전략 및 통합시험 명세서 | `WP_Templates/Engineering/SoftwareComponentVerificationAndIntegrationVerification/TPL-SWE5-001_SW 통합전략 및 통합시험 명세서 템플릿.docx` | DOCX |
| TPL-SWE5-002 | SW 통합시험 케이스 | `WP_Templates/Engineering/SoftwareComponentVerificationAndIntegrationVerification/TPL-SWE5-002_SW 통합시험 케이스 템플릿.xlsx` | XLSX |
| TPL-SWE5-003 | SW 통합시험 결과서 | `WP_Templates/Engineering/SoftwareComponentVerificationAndIntegrationVerification/TPL-SWE5-003_SW 통합시험 결과서 템플릿.xlsx` | XLSX |
| TPL-TRC-001 | 양방향 요구사항 추적 매트릭스(통합시험까지 연계) | `WP_Templates/Engineering/Traceability/TPL-TRC-001_양방향 요구사항 추적 매트릭스 템플릿.xlsx` | XLSX |

통합전략과 시험 개요는 TPL-SWE5-001에, 개별 테스트 케이스는 TPL-SWE5-002에, 실행 결과와 커버리지 결과는 TPL-SWE5-003에 기록한다. 이 목록에 없는 산출물이 필요하면 등록부(`PRC-TPL-001`)에서 해당 항목을 먼저 확인한다.

## 사용 규칙 (`WP_Templates/Engineering/README.md` 기준)

- **DOCX**: 기존 장/절 구조를 그대로 유지한다. 각 제목 아래의 작성 안내 문구를 실제 프로젝트 내용으로 교체한다. 안내 문구를 지우지 않은 채로 남겨두지 않는다.
- **XLSX**: 기존 시트/열 구조를 그대로 유지한다. 상단의 안내/예시 행은 건드리지 않고, 10행부터 실제 데이터를 추가한다.
- 새 산출물을 만들 때는 템플릿 파일을 복사한 뒤 파일명을 `<산출물 ID>_<산출물명>.<확장자>` 형식으로 바꾸고 프로젝트/베이스라인 정보를 채운다. 템플릿 원본 파일 자체는 수정하지 않는다.

## 파일 형식별 처리 방법 (이 환경의 도구 제약)

- **DOCX**: 바이너리를 직접 편집하지 않는다. Word 문서 내용을 읽거나 새로 작성해야 하면 문서 처리 전용 스킬(docx)을 사용한다.
- **XLSX**: 바이너리를 직접 편집하지 않는다. 통합시험 케이스/결과서, 추적성 매트릭스 작업이 필요하면 스프레드시트 처리 전용 스킬(xlsx)을 사용한다.

## 라이선스 주의

`WP_Templates/Engineering/README.md`에 따르면 이 템플릿과 관련 교육 자료의 저작권은 Synetics에 있으며, 교육 과정 밖 배포·공개·상업적 이용은 사전 서면 승인이 필요하다. 이 템플릿을 프로젝트 외부로 배포하지 않는다.
