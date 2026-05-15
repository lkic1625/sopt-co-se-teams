# 추천 정렬은 Main 홈 상품 영역에만 적용하고 ShowCase에는 적용하지 않음

- **일시**: 2026-05-09
- **상태**: 대체됨
- **결정자**: @기획 / @디자인 / @개발 합의
- **분류**: product
- **영향 범위**: Main, ShowCase, Product Like

## 문제 (Problem)

Product Like Signal 기반 정렬을 Main과 ShowCase에 모두 적용하면 Product 모델과 ShowCase 모델이 강하게 결합될 수 있다. 좋아요의 대상과 정렬 기준도 화면별로 불명확해진다.

## 맥락 (Context)

이번 리디자인의 주요 개선 포인트는 Main 홈 피드와 상품 탐색 경험이다. 좋아요는 Product Card에서 발생하는 사용자 신호로 이해하는 것이 자연스럽고, ShowCase Card나 Section까지 확장하면 추천 모델의 범위가 커진다.

## 결정 (Decision)

이 결정은 [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md) 결정으로 대체되었다.

Product Like Signal 기반 정렬은 Main 홈 상품 영역에만 적용한다. ShowCase 탭에서는 추천 정렬을 적용하지 않는다.

좋아요는 Product Card에만 존재한다. Feed, Section, ShowCase Card에는 좋아요 상태를 두지 않는다. Product Like Signal은 상품 좋아요 액션, 로그, mock state 등을 포괄하는 정렬 신호로 본다. 특정 백엔드 모델을 강제하지 않는다.

## 이유 (Rationale)

ShowCase에 추천 정렬을 적용하면 ShowCase 모델과 Product 모델이 강결합될 가능성이 높고, 모델링이 깔끔하지 않다. 이번 리디자인의 주요 개선 포인트는 Main 홈 피드이므로 ShowCase 추천 정렬은 high priority가 아니다.

## 영향 (Impact)

Main 홈 상품 영역은 Product Like Signal이 있을 때 정렬 보정 대상이 된다. ShowCase는 로그인 상태나 Product Like Signal에 따라 순서가 바뀌지 않는다. QA는 Product Card 좋아요와 Main 상품 정렬 변화만 확인하면 되며, ShowCase Card에는 좋아요 UI나 추천 정렬을 기대하지 않는다.

## 대안 (Alternatives)

- ShowCase에도 Product Like 기반 정렬 적용
- Feed 또는 Section에도 좋아요 추가
- 추천 정렬 기능을 완전히 제외
- 별도 추천 알고리즘 모델 도입

## 관련 문서

- [결정 문서 인덱스](../index.md)
- [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md)
