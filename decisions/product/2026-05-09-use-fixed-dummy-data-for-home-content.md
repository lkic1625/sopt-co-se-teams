# 홈 콘텐츠는 고정 dummy data로 구성

- **일시**: 2026-05-09
- **상태**: 확정
- **결정자**: @
- **분류**: product
- **영향 범위**: Main, Data

## 문제 (Problem)

Main View의 콘텐츠를 동적으로 생성할지, 고정된 데이터로 구성할지 결정해야 한다. 동적 생성은 백엔드 모델링과 API 개발이 필요하다.

## 맥락 (Context)

- 프로젝트 기간 6주
- 콘텐츠 큐레이션은 기획자가 수동으로 정리한 기준으로 연결
- 큐레이션 블록의 구조는 고정되어 있음
- 데이터 변경 빈도가 낮고, MVP에서는 콘텐츠 관리 도구가 없음

## 결정 (Decision)

**Main View의 콘텐츠는 고정된 dummy data로 구성한다.**

- 큐레이션 블록, Hero Banner, Category Shortcut 등의 콘텐츠는 JSON 파일 또는 코드 내 하드코딩으로 관리
- 백엔드 API를 통한 동적 fetch는 하지 않는다.
- 데이터 변경이 필요하면 코드 또는 JSON 파일을 직접 수정

## 이유 (Rationale)

- 백엔드 콘텐츠 관리 API와 DB 모델링을 제거하여 개발 일정 단축
- 콘텐츠 변경 빈도가 낮아 동적 관리의 이점이 적음
- FE가 독립적으로 콘텐츠 구조를 제어할 수 있어 개발 속도 향상

## 영향 (Impact)

- **개발 범위**: BE 콘텐츠 API, DB 테이블, 어드민 도구 제거
- **FE 개발**: JSON import 또는 상수로 콘텐츠 관리
- **운영**: 콘텐츠 변경 시 코드 배포 필요
- **QA**: 데이터가 고정되어 있어 테스트 시나리오 예측 가능

## 대안 (Alternatives)

- **동적 API 기반**: 콘텐츠 변경이 유연하나 BE 개발 일정 추가 필요
- **CMS 연동**: Strapi, Sanity 등 외부 CMS 사용하나 학습 및 설정 비용

## 관련 문서

- [대표 이미지와 상품 카드는 수동 큐레이션으로 연결](2026-05-09-use-manual-curation-for-hero-image-and-products.md)
- [이미지는 S3 URL 기준으로 사용](../technical/2026-05-09-use-s3-url-for-images.md)
