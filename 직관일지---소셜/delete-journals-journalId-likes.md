<!-- AUTO-GENERATED -->

## 직관일지 좋아요 취소

### 개요

직관일지의 좋아요를 취소합니다. 좋아요가 존재하지 않는 상태에서 요청 시 예외 발생

### 엔드포인트

`DELETE /journals/{journalId}/likes`

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
| journalId | Long | ✅ | 좋아요를 취소할 직관일지 ID | 1 |

### 응답 (Response)

#### 200 좋아요 취소 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 404 | 좋아요 기록 또는 직관일지를 찾을 수 없음 |
