<!-- AUTO-GENERATED -->

## 게시글 검색

### 개요

키워드로 게시글을 검색합니다.

📌 **검색 대상**: 제목 (title) + 본문 (content)
📌 **팀 필터링**: teamShortCode로 팀별 필터링 가능 (기본값: ALL = 전체)
📌 **정렬**: 최신순 (postAt DESC)
📌 **페이지네이션**: Slice 기반 무한 스크롤

✅ 예시: `/community/posts/search?keyword=직관&page=0&size=10`
✅ 팀 필터: `/community/posts/search?keyword=직관&teamShortCode=LG&page=0&size=10`

### 엔드포인트

`GET /community/posts/search`

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
| keyword | String | ✅ | 검색 키워드 | 직관 |
| teamShortCode | String |  | 팀 숏코드 (ALL: 전체, LG/OB 등: 팀별 필터) | ALL |
| page | Integer |  | 조회할 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 한 페이지당 게시글 개수 | 10 |

### 응답 (Response)

#### 200 게시글 검색 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| content | Object[] | 조회된 데이터 목록 |
| hasNext | Boolean | 다음 페이지가 존재하는지 여부 |
| page | Integer | 현재 페이지 번호 |
| size | Integer | 페이지 크기 |
