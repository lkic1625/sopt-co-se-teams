# 개인화 정렬은 Product Like Signal 기반 Main 상품 정렬로 제한

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: Main, Product Card

## 문제 (Problem)

29CM 리디자인에서 개인화 요소를 어디까지 적용할지 결정해야 한다. 강력한 추천 알고리즘은 구현 복잡도가 높고, 완전 무개인화는 발견형 커머스의 강점을 살리지 못한다.

## 맥락 (Context)

- Main View의 큐레이션 블록 안에서 상품 카드의 노출 순서를 조정할 수 있음
- 사용자가 관심을 보인 상품(Product Like)을 신호로 활용 가능
- ShowCase View는 콘텐츠 탐색이 목적이지 상품 구매가 주 목적은 아님
- 추천 알고리즘은 showcase 관련 모델에 product와의 강결합이 필요하여 모델링이 깔끔하지 않음

## 결정 (Decision)

**개인화 정렬은 Product Like Signal을 기반으로 Main View의 상품 카드 정렬에만 적용한다.**

- Product Like는 사용자가 클릭하여 관심을 표시한 상품
- Main View의 큐레이션 블록 내에서, 사용자가 Like한 상품을 우선적으로 노출
- 정렬 신호는 백엔드 모델을 고정하지 않는 가벼운 방식으로 정의
- ShowCase View에는 기본적으로 개인화 정렬을 적용하지 않는다. 단, [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md) 결정에 따라 Collection에 연결된 상품 좋아요 정보를 사용할 수 있는 경우에는 정렬할 수 있다.
- Feed, Section, ShowCase Card에는 좋아요를 두지 않는다.

## 이유 (Rationale)

- Main View의 큐레이션 블록에서 관심 상품을 우선 노출하면 발견형 피드에서 개인화 효과를 얻을 수 있음
- 낮은 강도의 개인화로 구현 복잡도를 제어
- ShowCase는 콘텐츠 중심 탐색이므로 상품 개인화는 부적합
- 추천 알고리즘은 모델링 복잡도가 높고 MVP 범위를 벗어남

## 영향 (Impact)

- **사용자 경험**: Main에서 관심 상품을 더 잘 보이게 하여 재방문률 향상 기대
- **개발 범위**: 추천 알고리즘, 머신러닝 모델 제거
- **BE**: Product Like 수집 API와 정렬 로직만 구현
- **ShowCase**: 기본적으로 고정된 순서로 노출하되, Collection에 연결된 상품 좋아요 정보를 사용할 수 있는 경우에는 정렬 가능

## 대안 (Alternatives)

- **강력한 추천 알고리즘**: 사용자 행동 기반 추천 모델 구축하나 MVP에서는 과함
- **완전 무개인화**: 모든 사용자에게 동일한 콘텐츠 제공하나, 리디자인 목표인 관심 반영 불가

## 관련 문서

- [Product Like Signal은 백엔드 모델을 고정하지 않는 정렬 신호로 정의](../technical/2026-05-09-define-product-like-signal-as-sorting-signal.md)
- [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md)
