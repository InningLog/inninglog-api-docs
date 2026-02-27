<!-- AUTO-GENERATED -->

## 일반 로그인

### 개요

일반 사용자 로그인 처리 및 JWT 발급
- 성공 시 JWT 토큰이 반환됩니다.
- 아이디 또는 비밀번호가 틀리면 오류가 발생합니다.

### 엔드포인트

`POST /auth/login`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| userID | String | ✅ |  |  |
| password | String | ✅ |  |  |

### 응답 (Response)

#### 200 로그인 성공 / JWT 토큰 반환

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 비밀번호가 일치하지 않습니다. (INVALID_PASSWORD) |
