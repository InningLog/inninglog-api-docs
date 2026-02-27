<!-- AUTO-GENERATED -->

## 공개 직관 일지 검색

### 개요

키워드로 공개 직관 일지를 검색합니다.

📌 **검색 대상**: 후기 본문 (review_text)
📌 **팀 필터링**: teamShortCode로 팀별 필터링 가능 (기본값: ALL = 전체)
📌 **정렬**: 작성순 (createdAt DESC)
📌 **페이지네이션**: Slice 기반 무한 스크롤

✅ 예시: `/journals/search?keyword=역전승&page=0&size=10`
✅ 팀 필터: `/journals/search?keyword=역전승&teamShortCode=LG&page=0&size=10`

### 엔드포인트

`GET /journals/search`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Query Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| keyword | String | ✅ | 검색 키워드 | 역전승 |
| teamShortCode | String |  | 팀 숏코드 (ALL: 전체, LG/OB 등: 팀별 필터) | ALL |
| page | Integer |  | 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 페이지 크기 | 10 |

### 응답 (Response)

#### 200 검색 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| content | Object[] | 조회된 데이터 목록 |
| hasNext | Boolean | 다음 페이지가 존재하는지 여부 |
| page | Integer | 현재 페이지 번호 |
| size | Integer | 페이지 크기 |
