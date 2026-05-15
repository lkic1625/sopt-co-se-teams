# ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능

- **일시**: 2026-05-15
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: ShowCase, Product Like, Collection, Sorting

## 문제 (Problem)

기존 결정은 ShowCase에 Product Like Signal 기반 추천 정렬을 적용하지 않도록 제한했다. 그러나 ShowCase가 Collection과 연결되어 있고, 해당 Collection에 연결된 상품의 좋아요 정보를 사용할 수 있는 경우에는 ShowCase 콘텐츠의 우선순위를 더 사용자 관심에 가깝게 조정할 수 있다.

ShowCase 자체에 좋아요 상태를 추가하지 않더라도, 연결된 상품의 좋아요 정보를 정렬 신호로 활용할 수 있는지 결정이 필요하다.

## 맥락 (Context)

ShowCase는 쇼케이스 콘텐츠를 섹션 단위로 탐색하는 화면이다. 기존에는 ShowCase 모델과 Product 모델의 강결합을 피하기 위해 Product Like Signal 기반 정렬을 적용하지 않기로 했다.

다만 ShowCase가 Collection을 통해 상품과 명시적으로 연결되어 있는 경우, 정렬 신호는 ShowCase Card의 좋아요가 아니라 연결된 상품들의 좋아요 정보에서 계산할 수 있다. 이 경우 ShowCase에 별도 좋아요 UI를 만들지 않으면서도, 사용자의 상품 관심도를 ShowCase 노출 순서에 제한적으로 반영할 수 있다.

## 결정 (Decision)

ShowCase는 Collection에 연결된 상품 정보의 좋아요를 기반으로 정렬 가능한 경우에 한해 정렬한다.

정렬은 다음 조건을 모두 만족할 때만 적용한다.

- ShowCase 또는 ShowCase 섹션이 Collection과 연결되어 있다.
- 해당 Collection에 연결된 상품 목록을 확인할 수 있다.
- 연결된 상품들의 좋아요 정보 또는 Product Like Signal을 정렬 신호로 사용할 수 있다.
- 정렬 적용 후에도 ShowCase의 slug 기반 섹션 구조와 기본 탐색 흐름이 유지된다.

위 조건을 만족하지 못하면 ShowCase는 기존의 고정 순서로 노출한다.

ShowCase Card 자체에는 좋아요 상태를 두지 않는다. 좋아요 UI도 추가하지 않는다. 정렬 신호는 ShowCase 자체의 좋아요가 아니라, Collection에 연결된 상품들의 좋아요 정보로부터 파생된 값으로 본다.

## 이유 (Rationale)

ShowCase에 독립적인 좋아요 모델을 추가하면 기존 우려처럼 ShowCase 모델과 Product Like 모델이 복잡하게 결합될 수 있다. 반면 Collection과 상품 연결 관계가 이미 존재하고 좋아요 정보가 조회 가능하다면, 별도 ShowCase 좋아요 상태를 만들지 않고도 상품 관심도를 제한적으로 반영할 수 있다.

이 방식은 ShowCase의 콘텐츠 탐색 목적을 유지하면서, 사용자가 관심을 보인 상품과 관련된 쇼케이스를 더 잘 노출할 수 있게 한다. 동시에 데이터가 부족하거나 연결 관계가 없는 경우에는 고정 순서를 유지하므로 구현과 QA 범위를 통제할 수 있다.

## 영향 (Impact)

ShowCase는 항상 정렬되는 화면이 아니라, 연결된 상품 좋아요 정보를 사용할 수 있는 경우에만 정렬되는 화면이 된다. 데이터가 없거나 정렬 신호를 계산할 수 없는 경우 기존 고정 순서가 fallback이다.

개발에서는 ShowCase 정렬 로직이 Collection-Product 연결과 Product Like Signal 조회 가능 여부를 확인해야 한다. QA는 정렬 가능한 ShowCase와 정렬 불가능한 ShowCase를 나누어 확인해야 한다. ShowCase Card에 좋아요 UI가 생기지 않는다는 점은 유지된다.

기존의 “ShowCase에는 추천 정렬을 적용하지 않는다” 결정은 이 결정으로 대체된다. 다만 ShowCase의 slug 기반 고정 섹션 구조는 유지되며, 정렬은 섹션 구조를 해치지 않는 범위에서만 적용한다.

## 대안 (Alternatives)

- ShowCase에는 어떤 경우에도 정렬을 적용하지 않음
- ShowCase Card에 별도 좋아요 상태를 추가하고 그 값을 기준으로 정렬
- Collection과 무관하게 전체 Product Like Signal을 ShowCase 추천 모델에 직접 적용
- ShowCase를 최신순 또는 수동 priority 값으로만 정렬

## 관련 문서

- [추천 정렬은 Main 홈 상품 영역에만 적용하고 ShowCase에는 적용하지 않음](2026-05-09-limit-recommendation-sorting-to-main-home.md)
- [ShowCase는 slug 기반 고정 섹션 구조로 구성](2026-05-09-use-slug-based-fixed-showcase-sections.md)
- [개인화 정렬은 Product Like Signal 기반 Main 상품 정렬로 제한](2026-05-09-limit-personalized-sorting-to-main-product-cards.md)
- [결정 문서 인덱스](../index.md)
