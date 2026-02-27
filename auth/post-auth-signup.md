<!-- AUTO-GENERATED -->

## 일반 회원가입

### 개요

일반 사용자의 회원가입을 처리합니다.
- 아이디(userID)는 중복되면 안 됩니다.
- 아이디는 영문 + 숫자 조합의 6~12자리여야 합니다.
- 비밀번호는 숫자 4자리여야 합니다.

### 엔드포인트

`POST /auth/signup`

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

#### 200 회원가입 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 이미 존재하는 아이디입니다. (EXIST_USERID) |
