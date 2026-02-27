<!-- AUTO-GENERATED -->

## 댓글 삭제

### 개요

특정 댓글을 소프트 삭제합니다.
이미 삭제된 댓글이거나 존재하지 않는 댓글 ID가 전달될 경우 에러가 발생합니다.
댓글 삭제는 실제 DB 삭제가 아닌, `isDeleted = true` 처리(soft delete) 방식으로 동작합니다.

### 엔드포인트

`DELETE /community/comments/{commentId}`

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
| commentId | Long | ✅ | 삭제할 댓글의 ID | 12 |

### 응답 (Response)

#### 200 댓글 삭제 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 404 | 댓글을 찾을 수 없음 또는 이미 삭제된 댓글 |
| 500 | 서버 내부 오류 |
