# Main Home과 ShowCase는 동일한 공통 Header를 사용

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @기획 / @디자인 / @개발 합의
- **분류**: product
- **영향 범위**: Header, Main, ShowCase

## 문제 (Problem)

Main Home과 ShowCase Page에서 Header를 각각 다르게 설계하면 주요 탐색 화면 간 사용 경험이 달라지고, Header 상태와 인터랙션을 화면별로 별도 관리해야 한다.

## 맥락 (Context)

Main과 ShowCase는 같은 서비스 안에서 사용자가 가장 먼저 오가는 주요 탐색 화면이다. 리디자인 장표에서도 두 화면은 서로 다른 서비스 영역이 아니라 같은 탐색 체계 안에 있는 화면으로 이해된다. 따라서 상단 탐색의 위치, 역할, 상태 변화가 일관되어야 한다.

## 결정 (Decision)

Main Home과 ShowCase Page는 동일한 Header를 사용한다.

페이지별로 다른 Header 동작을 만들지 않는다. 헤더 hover 및 스크롤 관련 동작은 디자인 결정에 따라 일관적인 하나의 정책으로 통일한다.

## 이유 (Rationale)

Main과 ShowCase가 같은 서비스 내 주요 탐색 화면이므로 상단 탐색 경험을 일관되게 유지해야 한다. 개발 측면에서도 Header 컴포넌트를 공통화할 수 있어 중복 구현과 화면별 예외 처리를 줄일 수 있다.

## 영향 (Impact)

Header는 Main과 ShowCase에서 같은 구조와 정책을 공유한다. QA는 페이지별 Header 차이가 아니라 공통 Header가 두 화면에서 동일하게 동작하는지를 확인한다. 이후 Header 정책이 바뀌면 두 화면에 동시에 영향을 준다.

## 대안 (Alternatives)

- Main과 ShowCase에서 서로 다른 Header 사용
- ShowCase에서만 축약 Header 사용
- 스크롤 상태별로 Header 동작을 다르게 처리

## 관련 문서

- [결정 문서 인덱스](../index.md)
