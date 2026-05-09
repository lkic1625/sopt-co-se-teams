# ShowCase Card 클릭은 dummy page로 처리

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: ShowCase, Routing

## 문제 (Problem)

ShowCase Card를 클릭했을 때 이동할 화면이 아직 구현 범위에 없다. ShowCase Detail 화면을 별도로 만들면 구현 범위가 확장된다.

## 맥락 (Context)

- 구현 화면 범위는 Main과 ShowCase 두 개로 제한
- ShowCase Detail은 쇼케이스 관련 콘텐츠를 상세히 보여주는 화면
- 사용자는 ShowCase Card를 클릭하여 더 자세한 정보를 기대할 수 있음

## 결정 (Decision)

**ShowCase Card 클릭은 dummy page로 처리한다.**

- 별도의 ShowCase Detail 화면은 구현하지 않는다.
- 클릭 시 간단한 dummy page로 이동하여 "준비 중" 또는 기본 정볼만 표시한다.
- 향후 ShowCase Detail이 구현되면 dummy page를 대체한다.

## 이유 (Rationale)

- 구현 범위 제한을 지키면서 사용자 클릭에 대한 피드백은 제공
- ShowCase Detail의 콘텐츠 구조와 데이터 모델링이 아직 정의되지 않음
- MVP에서 핵심은 ShowCase 목록의 탐색 경험이지 상세 페이지

## 영향 (Impact)

- **사용자 경험**: ShowCase Card 클릭 시 실제 콘텐츠가 아닌 dummy page로 이동하여 다소 실망할 수 있음
- **개발 범위**: ShowCase Detail 화면, API, 라우팅 제거
- **Routing**: `/showcase/:id` 같은 상세 경로는 dummy page로 매핑

## 대안 (Alternatives)

- **ShowCase Detail 구현**: 사용자 경험은 우수하나 범위 초과
- **클릭 무시**: 구현은 쉽으나 사용자 피드백 없음, 버그처럼 느껴질 수 있음

## 관련 문서

- [구현 화면 범위는 Main / ShowCase 두 개로 제한](2026-05-09-limit-implementation-scope-to-main-and-showcase.md)
