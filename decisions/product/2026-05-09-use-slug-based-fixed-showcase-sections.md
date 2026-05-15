# ShowCase는 slug 기반 고정 섹션 구조로 구성

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @기획 / @디자인 / @개발 합의
- **분류**: product
- **영향 범위**: ShowCase, Data, Section

## 문제 (Problem)

ShowCase 화면을 단순 목록으로 구성하면 사용자가 콘텐츠를 탐색할 기준이 약해진다. 반대로 동적 카테고리 체계나 추천 정렬까지 포함하면 ShowCase 데이터 모델이 불필요하게 복잡해진다.

## 맥락 (Context)

리디자인의 ShowCase는 쇼케이스 콘텐츠를 의미 있는 섹션 단위로 보여주는 화면이다. Selection과 ShowCase를 별도 카테고리 체계로 분리하기보다, 사용자에게 노출되는 label과 description을 가진 고정 섹션으로 구성하는 편이 현재 구현 범위에 맞다.

## 결정 (Decision)

ShowCase 화면은 쇼케이스 콘텐츠를 단순 나열하지 않고 섹션 단위로 고정 노출한다.

ShowCase의 카테고리는 코드에 고정된 enum이 아니라 slug 역할로 본다. 각 slug는 사용자에게 노출되는 label과 description을 가진다. Selection과 ShowCase를 별도 카테고리 체계로 분리하지 않는다.

ShowCase Card에는 좋아요가 없다. ShowCase View는 기본적으로 slug 기반 섹션 구조를 유지한다. 다만 [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md) 결정에 따라, Collection에 연결된 상품의 좋아요 정보를 사용할 수 있는 경우에는 섹션 구조를 해치지 않는 범위에서 정렬할 수 있다. ShowCase 날짜가 표시용인지 필터용인지는 추가 확인이 필요하므로, 우선 `dateText`처럼 단순 표시 값으로 취급한다.

## 이유 (Rationale)

slug 기반 고정 섹션은 화면 구조를 안정적으로 유지하면서도 사용자에게 섹션별 탐색 기준을 제공한다. enum 중심 모델보다 표현 변경에 유연하고, Product Like Signal과 강결합하지 않아 ShowCase 모델을 단순하게 유지할 수 있다.

## 영향 (Impact)

ShowCase QA는 slug별 label, description, 카드 목록이 의도대로 노출되는지 확인한다. ShowCase Card 자체에는 좋아요 상태를 적용하지 않는다. Collection에 연결된 상품 좋아요 정보를 사용할 수 있는 경우에는 정렬 적용 여부를 함께 확인한다. 날짜는 현재 표시 값으로만 다루며, 필터나 정렬 조건으로 사용할지는 추후 확인이 필요하다.

## 대안 (Alternatives)

- ShowCase를 단순 최신순 목록으로 나열
- Selection과 ShowCase를 별도 카테고리로 분리
- 코드 enum 기반 카테고리 사용
- Product Like Signal을 ShowCase 정렬에도 적용

## 관련 문서

- [결정 문서 인덱스](../index.md)
- [ShowCase는 연결된 상품 좋아요 정보가 있을 때 정렬 가능](2026-05-15-sort-showcase-by-linked-product-likes-when-available.md)
- ShowCase 날짜 사용 방식은 표시용인지 필터용인지 추후 확인이 필요하다.
