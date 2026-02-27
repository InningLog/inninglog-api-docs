<!-- AUTO-GENERATED -->

## 게시글 댓글 목록 조회

### 개요

특정 게시글에 작성된 댓글 목록을 조회합니다. 로그인한 사용자의 정보에 따라 댓글별 추가 정보가 함께 반환될 수 있습니다.

### 엔드포인트

`GET /community/posts/{postId}/comments`

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

#### 200 OK
