<!-- AUTO-GENERATED -->

## 아이디 중복 체크

### 개요

회원가입 시 입력한 userID가 이미 존재하는지 확인합니다.

### 엔드포인트

`GET /auth/check-id`

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
| userID | String | ✅ | 중복 확인할 사용자 ID | dodo123 |

### 응답 (Response)

#### 200 중복 여부 반환 (true = 중복 / false = 사용 가능)
