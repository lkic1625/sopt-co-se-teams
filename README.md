# 팀 결정 문서 (Team Decisions)

> **Single Source of Truth.**  

## 목적

- **기록**: 왜 그런 결정을 남겼는지 추적 가능하게 한다.
- **공유**: 개발자, 기획자, 팀원 모두가 동일한 문맥에서 논의한다.
- **방향성**: 프로젝트의 기술/제품/운영 방향을 일관되게 유지한다.

## 범위

| 분류 | 설명 | 예시 |
|------|------|------|
| `technical` | 기술 및 아키텍처 결정 | 프레임워크 선택, API 설계, DB 마이그레이션 |
| `product` | 제품 및 기능 결정 | 기능 우선순위, 정책 변경, 사용자 흐름 |
| `team-ops` | 팀 운영 및 프로세스 결정 | 코드 리뷰 규칙, 회의 체계, 온콜 로테이션 |

## 규칙

1. **모든 중대 결정은 문서화**
   - 한 줄 짜리 판단도 문서로 남긴다. "왜"가 중요하다.
   
2. **상태 관리**
   - `제안` → `확정` → `대체` 또는 `폐기`
   - `확정`은 최소 1명의 리뷰어 승인이 필요하다.

3. **파일명 규칙**
   ```
   decisions/{분류}/YYYY-MM-DD-kebab-case-title.md
   ```
   예: `decisions/technical/2026-05-09-adopt-nextjs-app-router.md`

4. **템플릿 사용**
   - [templates/technical.md](templates/technical.md)
   - [templates/product.md](templates/product.md)
   - [templates/team-ops.md](templates/team-ops.md)

5. **SSoT**
   - 이 레포지토리에 기록되지 않은 결정은 유효하지 않다.
   - 다른 곳(노션, 슬랙, 회의록)에만 있는 결정은 이곳에 반드시 마이그레이션한다.

## 워크플로우

### 1. 결정 제안
```bash
cp templates/technical.md decisions/technical/YYYY-MM-DD-title.md
# 문서 작성
git checkout -b decisions/title
git add . && git commit -m "decisions: 제목"
git push origin decisions/title
# PR 생성
```

### 2. 리뷰 및 승인
- PR 본문에 결정 요약을 3줄 이내로 작성
- 리뷰어는 `결정`, `이유`, `영향` 섹션을 중심으로 검토
- 수정 요청 없이 승인 시 `확정` 상태로 변경 후 머지

### 3. 결정 변경
- 기존 문서를 수정하지 않는다.
- `decisions/technical/YYYY-MM-DD-overriding-title.md` 형태로 **새 문서**를 작성한다.
- 기존 문서 상태를 `대체`로 변경하고, 새 문서 링크를 `관련 문서`에 추가한다.

## 디렉토리 구조

```
.
├── README.md
├── templates/
│   ├── technical.md
│   ├── product.md
│   └── team-ops.md
└── decisions/
    ├── technical/
    ├── product/
    └── team-ops/
```

---

**이 문서 자첼도 결정이다.** 변경이 필요하면 PR을 열어 논의한다.

---

## 결정 문서

프로젝트의 주요 결정은 [decisions/README.md](decisions/README.md)에서 관리한다.

- 경미한 결정은 [decisions/index.md](decisions/index.md)에만 등록할 수 있다.
- 상세한 결정 기록이 필요한 경우에는 [템플릿](templates/decisions/)을 사용하여 별도 문서를 작성한다.
