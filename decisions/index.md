# 결정 문서 인덱스

이 문서는 프로젝트의 주요 결정 문서를 한눈에 보기 위한 인덱스다.

## Product Decisions

| 일시 | 상태 | 제목 | 영향 범위 | 문서 |
|------|------|------|-----------|------|
| 2026-05-09 | 확정 | 구현 화면 범위는 Main / ShowCase 두 개로 제한 | 전체 화면 범위 | [문서](product/2026-05-09-limit-implementation-scope-to-main-and-showcase.md) |
| 2026-05-09 | 확정 | Main Home과 ShowCase는 동일한 공통 Header를 사용 | Header, Main, ShowCase | [문서](product/2026-05-09-use-common-header-for-main-and-showcase.md) |
| 2026-05-09 | 확정 | Main 홈 스크롤 인터랙션은 sticky 대표 이미지와 우측 상품 스크롤 구조로 정의 | Main, Interaction, Floating Button | [문서](product/2026-05-09-define-main-home-scroll-interaction.md) |
| 2026-05-09 | 확정 | Main 홈 더보기 버튼은 dummy data 확장 전까지 동작하지 않음 | Main, FE, Home Feed, Load More | [문서](product/2026-05-09-disable-load-more-until-home-dummy-data-expands.md) |
| 2026-05-09 | 확정 | Main 배너 캐러셀은 5초 자동 전환을 기본 동작으로 구현 | Main, FE, Hero Banner, Carousel | [문서](product/2026-05-09-use-simple-auto-advance-for-main-banner-carousel.md) |
| 2026-05-09 | 확정 | 홈 콘텐츠는 고정 dummy data와 수동 큐레이션으로 구성 | Main, Data, CurationBlock, Product Card | [문서](product/2026-05-09-use-manual-curation-for-home-content.md) |
| 2026-05-09 | 확정 | ShowCase는 slug 기반 고정 섹션 구조로 구성 | ShowCase, Data, Section | [문서](product/2026-05-09-use-slug-based-fixed-showcase-sections.md) |
| 2026-05-09 | 확정 | 추천 정렬은 Main 홈 상품 영역에만 적용하고 ShowCase에는 적용하지 않음 | Main, ShowCase, Product Like | [문서](product/2026-05-09-limit-recommendation-sorting-to-main-home.md) |
| 2026-05-09 | 확정 | 로그인/비로그인 화면 차이는 우상단 버튼으로만 제한 | Login State, Header, Main | [문서](product/2026-05-09-limit-login-state-ui-difference.md) |

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
