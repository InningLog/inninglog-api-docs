<!-- AUTO-GENERATED -->

## 게시글 단일 조회

### 개요

특정 팀에 속한 게시글을 단건 조회합니다.

- 이미지 목록 포함
- 작성자 정보 포함
- 포맷팅된 작성일(postAt) 포함 (yyyy-MM-dd HH:mm)

### 엔드포인트

`GET /community/posts/{postId}`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Path Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| postId | Long | ✅ | 게시글 ID | 1 |

### 응답 (Response)

#### 200 게시글 조회 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 404 | 게시글을 찾을 수 없음 |
