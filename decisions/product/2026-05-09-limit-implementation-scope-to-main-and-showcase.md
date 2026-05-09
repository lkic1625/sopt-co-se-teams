# 구현 화면 범위는 Main / ShowCase 두 개로 제한

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: 전체 화면 범위

## 문제 (Problem)

29CM 리디자인 프로젝트에서 구현할 화면 범위를 명확히 정의해야 한다. Category Product List, ShowCase Detail, Brand Detail 등 추가 화면까지 포함하면 6주라는 제한된 기간 내에 완성하기 어렵다.

## 맥락 (Context)

- 프로젝트 기간 6주
- 팀원 4명 (FE 2명, BE 2명)
- Main View와 ShowCase View가 핵심 콘텐츠 커머스 경험의 중추
- Category Product List, ShowCase Detail, Brand Detail은 추가 탐색 경로일 뿐 핵심 가치가 아님

## 결정 (Decision)

**이번 프로젝트의 최종 구현 화면은 Main View와 ShowCase View 두 개로 제한한다.**

- Main View: 홈 화면 (Header, Hero Banner, Category Shortcut, Curation Content Block, Product Card)
- ShowCase View: 쇼케이스 목록 화면 (Header, ShowCase Section, ShowCase Card List)
- Category Product List, ShowCase Detail, Brand Detail은 별도 화면으로 구현하지 않는다.
- ShowCase Card 클릭 시와 CTA 클릭 시는 dummy page 또는 대체 화면으로 이동한다.

## 이유 (Rationale)

- 제한된 기간 안에 완성도 높은 핵심 화면을 구현하는 것이 우선
- 추가 화면은 별도 탐색 깊이로, MVP 범위에서는 오히려 복잡도만 증가
- dummy page 처리로 사용자 흐름의 단절은 최소화하면서 범위는 조절 가능

## 영향 (Impact)

- **개발 범위**: FE는 2개 화면에 집중, BE는 API 두 개 화면 기준으로 설계
- **일정**: 추가 화면 구현 일정 제거로 여유 확보
- **QA**: 테스트 범위가 2개 화면으로 명확해짐
- **사용자 경험**: ShowCase Card나 CTA 클릭 시 dummy page로 이동하여 완성도 있는 화면 전환은 제공하지 않음

## 대안 (Alternatives)

- **3개 이상 화면 구현**: Brand Detail까지 포함하면 사용자 탐색 경험은 풍부해지나 6주 내 완성 불확실
- **ShowCase Detail만 추가**: 쇼케이스 탐색의 마무리가 자연스럽지만, 모델링 복잡도 증가

## 관련 문서

- [ShowCase Card 클릭은 dummy page로 처리](2026-05-09-use-dummy-page-for-showcase-card-click.md)
- [CTA 최종 목적지는 브랜드 상세 또는 dummy brand page로 결정 필요](2026-05-09-decide-cta-destination.md)
