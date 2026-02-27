<!-- AUTO-GENERATED -->

## 직관일지 댓글 생성

### 개요

특정 직관일지에 댓글을 생성합니다.

- `journalId`는 PathVariable로 전달됩니다.
- `rootCommentId`가 null이면 일반 댓글입니다.
- `rootCommentId`에 값이 있으면 해당 댓글의 대댓글(답글)로 생성됩니다.

### 엔드포인트

`POST /journals/{journalId}/comments`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Path Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| journalId | Long | ✅ | 댓글을 작성할 직관일지 ID | 1 |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| rootCommentId | Long |  |  |  |
| content | String |  |  |  |

### 응답 (Response)

#### 200 댓글 생성 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 값 |
| 401 | 인증 필요 |
| 404 | 직관일지 또는 부모 댓글을 찾을 수 없음 |
