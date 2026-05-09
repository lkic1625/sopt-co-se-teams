# ShowCase는 slug 기반 고정 섹션 구조로 구성

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: ShowCase, Data

## 문제 (Problem)

ShowCase View의 콘텐츠를 어떤 기준으로 섹션화하여 보여줄지 결정해야 한다. 단순 나열은 탐색 기준이 약하고, 동적 카테고리는 구현 복잡도가 높다.

## 맥락 (Context)

- ShowCase는 쇼케이스 콘텐츠를 의미 있는 섹션 단위로 묶어 보여줌
- 섹션은 사용자에게 노출되는 label과 description을 가짐
- 각 섹션은 고정된 콘텐츠 집합을 가짐

## 결정 (Decision)

**ShowCase는 slug 기반의 고정 섹션 구조로 구성한다.**

- 섹션은 slug(예: `new-arrivals`, `editors-pick`)로 식별
- 각 섹션은 label, description, ShowCase Card 목록을 가짐
- 섹션 목록과 구성은 고정된 dummy data로 관리
- 섹션 간 순서도 고정

## 이유 (Rationale)

- slug 기반 구조는 향후 API 연동 시에도 그대로 사용 가능
- 고정 구조는 개발 복잡도를 낮추고 예측 가능한 UI 제공
- 섹션 단위로 콘텐츠를 묶어 탐색 기준을 명확히 제공

## 영향 (Impact)

- **사용자 경험**: 섹션 label과 description으로 콘텐츠를 파악할 수 있음
- **개발 범위**: 동적 섹션 생성, 드래그 앤 드롭 정렬 등 불필요
- **데이터**: 섹션 단위 JSON 구조로 관리

## 대안 (Alternatives)

- **동적 카테고리 기반**: 사용자가 필터링할 수 있으나 BE API 및 DB 설계 필요
- **날짜 기반 그룹핑**: ShowCase 날짜를 기준으로 그룹핑하나, 날짜의 의미가 아직 불명확

## 관련 문서

- [ShowCase 날짜는 표시용인지 필터용인지 확인 필요](2026-05-09-decide-showcase-date-usage.md)
