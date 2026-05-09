# 구현 화면 범위는 Main / ShowCase 두 개로 제한

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @기획 / @디자인 / @개발 합의
- **분류**: product
- **영향 범위**: 전체 화면 범위

## 문제 (Problem)

리디자인 구현 범위를 명확히 제한하지 않으면 Main, ShowCase, Category Product List, ShowCase Detail, Brand Detail까지 구현 대상이 확장될 수 있다. 이렇게 되면 핵심 화면의 완성도와 QA 안정성을 확보하기 어렵다.

## 맥락 (Context)

이번 리디자인의 핵심은 Main의 콘텐츠·상품 위계를 정리하고, ShowCase를 섹션 단위로 재구성하는 데 있다. Category Product List, ShowCase Detail, Brand Detail은 탐색 흐름을 보완하는 화면이지만, 핵심 리디자인 의도를 검증하는 데 반드시 필요한 화면은 아니다.

## 결정 (Decision)

최종 구현 화면은 `Main View`와 `ShowCase View` 두 개로 제한한다.

`Category Product List`는 이번 구현 범위에서 제외한다. `ShowCase Detail`은 구현하지 않고, ShowCase Card 클릭 시 dummy page로 이동해도 된다. `Brand Detail`은 필요 시 dummy brand page로 대체 가능하다.

## 이유 (Rationale)

Main과 ShowCase에 개발 리소스를 집중해야 리디자인의 핵심인 콘텐츠 위계, 상품 탐색, 섹션화된 쇼케이스 경험을 더 안정적으로 구현할 수 있다. 부가 화면까지 구현하면 화면 수는 늘어나지만 각 화면의 완성도, 상태 처리, QA 범위가 분산된다.

## 영향 (Impact)

화면 범위는 Main과 ShowCase로 제한된다. 사용자 흐름 중 ShowCase Card 또는 브랜드 CTA 이후의 상세 탐색은 dummy page로 처리될 수 있다. 개발 범위가 줄어들어 핵심 화면의 반응형, 인터랙션, 데이터 상태, QA 기준을 더 명확하게 잡을 수 있다.

## 대안 (Alternatives)

- Category Product List까지 구현
- ShowCase Detail까지 구현
- Brand Detail까지 구현

## 관련 문서

- [결정 문서 인덱스](../index.md)
