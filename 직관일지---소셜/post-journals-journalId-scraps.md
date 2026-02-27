<!-- AUTO-GENERATED -->

## 직관일지 스크랩

### 개요

직관일지를 스크랩합니다. 이미 스크랩한 상태에서 다시 요청 시 예외 발생

### 엔드포인트

`POST /journals/{journalId}/scraps`

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
| journalId | Long | ✅ | 스크랩할 직관일지 ID | 1 |

### 응답 (Response)

#### 200 스크랩 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 이미 스크랩한 경우 |
| 404 | 직관일지를 찾을 수 없음 |
