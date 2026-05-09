# 결정 문서 인덱스

이 문서는 프로젝트의 주요 결정 문서를 한눈에 보기 위한 인덱스다.

## Product Decisions

| 일시 | 상태 | 제목 | 영향 범위 | 문서 |
|------|------|------|-----------|------|
| 2026-05-09 | 확정 | 구현 화면 범위는 Main / ShowCase 두 개로 제한 | 전체 화면 범위 | [문서](product/2026-05-09-limit-implementation-scope-to-main-and-showcase.md) |
| 2026-05-09 | 확정 | Main Home과 ShowCase는 동일한 공통 Header를 사용 | Header, Main, ShowCase | [문서](product/2026-05-09-use-common-header-for-main-and-showcase.md) |
| 2026-05-09 | 확정 | ShowCase Card 클릭은 dummy page로 처리 | ShowCase, Routing | [문서](product/2026-05-09-use-dummy-page-for-showcase-card-click.md) |
| 2026-05-09 | 확정 | 홈 콘텐츠는 고정 dummy data로 구성 | Main, Data | [문서](product/2026-05-09-use-fixed-dummy-data-for-home-content.md) |
| 2026-05-09 | 확정 | 대표 이미지와 상품 카드는 수동 큐레이션으로 연결 | Main, CurationBlock | [문서](product/2026-05-09-use-manual-curation-for-hero-image-and-products.md) |
| 2026-05-09 | 확정 | 큐레이션 목적이 다르면 같은 상품 중복 노출 허용 | Main, Product Card | [문서](product/2026-05-09-allow-duplicate-products-across-curations.md) |
| 2026-05-09 | 확정 | ShowCase는 slug 기반 고정 섹션 구조로 구성 | ShowCase, Data | [문서](product/2026-05-09-use-slug-based-fixed-showcase-sections.md) |
| 2026-05-09 | 확정 | 추천 정렬은 Main 홈 상품 영역에만 적용하고 ShowCase에는 적용하지 않음 | Main, ShowCase, Product Like | [문서](product/2026-05-09-limit-recommendation-sorting-to-main-home.md) |
| 2026-05-09 | 확정 | 로그인/비로그인 화면 차이는 우상단 버튼으로만 제한 | Login State, Header | [문서](product/2026-05-09-limit-login-state-ui-difference.md) |
| 2026-05-09 | 확정 | Main 홈 스크롤 인터랙션은 sticky 대표 이미지와 우측 상품 스크롤 구조로 정의 | Main, Interaction | [문서](product/2026-05-09-define-main-home-scroll-interaction.md) |
| 2026-05-09 | 확정 | Floating Button은 리디자인 시안 기준으로 유지 | Main, Floating Button | [문서](product/2026-05-09-keep-floating-button-from-redesign.md) |
| 2026-05-09 | 확인 필요 | Category Shortcut 목적지는 ShowCase slug 또는 dummy route로 결정 필요 | Main, Routing | [문서](product/2026-05-09-decide-category-shortcut-destination.md) |
| 2026-05-09 | 확인 필요 | CTA 최종 목적지는 브랜드 상세 또는 dummy brand page로 결정 필요 | Main, CTA | [문서](product/2026-05-09-decide-cta-destination.md) |
| 2026-05-09 | 확인 필요 | ShowCase 날짜는 표시용인지 필터용인지 확인 필요 | ShowCase, Data | [문서](product/2026-05-09-decide-showcase-date-usage.md) |
| 2026-05-09 | 확인 필요 | 스타일 키워드의 의미와 사용 범위 정의 필요 | Main, Data | [문서](product/2026-05-09-define-style-keyword-usage.md) |

## Technical Decisions

| 일시 | 상태 | 제목 | 영향 범위 | 문서 |
|------|------|------|-----------|------|
| 2026-05-09 | 확정 | 이미지는 S3 URL 기준으로 사용 | Image, Data | [문서](technical/2026-05-09-use-s3-url-for-images.md) |
| 2026-05-09 | 확정 | 로그인 상태는 query param backdoor로 구분 | Login State, Routing | [문서](technical/2026-05-09-use-query-param-backdoor-for-login-state.md) |
| 2026-05-09 | 확정 | Product Like Signal은 백엔드 모델을 고정하지 않는 정렬 신호로 정의 | Main, Product Like | [문서](technical/2026-05-09-define-product-like-signal-as-sorting-signal.md) |
| 2026-05-09 | 확정 | Product Like Signal 정렬은 좋아요 수 우선, fallback 안정 정렬로 처리 | Main, Product Like, Sorting | [문서](technical/2026-05-09-define-product-like-signal-sort-order.md) |
| 2026-05-09 | 확정 | 이미지 로딩은 skeleton으로 처리하고 최적화는 선택 과제로 둠 | Image Loading, UI State | [문서](technical/2026-05-09-use-skeleton-for-image-loading.md) |

## Team Operations Decisions

| 일시 | 상태 | 제목 | 영향 범위 | 문서 |
|------|------|------|-----------|------|
| 2026-05-09 | 확정 | Git 기반 decision record 구조를 사용 | Documentation, Team Ops | [문서](team-ops/2026-05-09-use-git-based-decision-records.md) |
